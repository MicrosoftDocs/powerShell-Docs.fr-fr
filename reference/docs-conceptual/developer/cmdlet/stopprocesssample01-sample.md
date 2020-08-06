---
title: Exemple StopProcessSample01 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6d4737d0526a7d142b4a986986974bcbdc12ec7e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786456"
---
# <a name="stopprocesssample01-sample"></a>Exemple StopProcessSample01

Cet exemple montre comment écrire une applet de commande qui demande des commentaires à l’utilisateur avant de tenter d’arrêter un processus, et comment implémenter un `PassThru` paramètre indiquant que l’utilisateur souhaite que l’applet de commande retourne un objet. Cette applet de commande est similaire à l’applet de commande `Stop-Process` fournie par Windows PowerShell 2,0.

### <a name="how-to-build-the-sample-by-using-visual-studio"></a>Comment générer l’exemple à l’aide de Visual Studio.

1. Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier StopProcessSample01. L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.

2. Double-cliquez sur l’icône du fichier solution (. sln). L’exemple de projet s’ouvre dans Microsoft Visual Studio.

3. Dans le menu **Générer**, sélectionnez **Générer la solution**.

    La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Créez le dossier de module suivant :

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. Copiez l’exemple d’assembly dans le dossier du module.

3. Démarrez Windows PowerShell.

4. Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :

    `import-module stopprossessample01`

5. Exécutez la commande suivante pour exécuter l’applet de commande :

    `stop-proc`

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple illustre ce qui suit.

- Déclaration d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.

- Déclaration d’un paramètre d’applet de commande à l’aide de l’attribut Parameter.

- Appel de la méthode ShouldProcess pour demander confirmation.

- Implémentation d’un `PassThru` paramètre qui indique si l’utilisateur souhaite que l’applet de commande retourne un objet. Par défaut, cette applet de commande ne retourne pas d’objet au pipeline.

## <a name="example"></a>Exemple

Cet exemple montre comment implémenter un `PassThru` paramètre qui indique que l’utilisateur souhaite que l’applet de commande retourne un objet, et comment demander des commentaires d’utilisateur par le biais d’appels aux `ShouldProcess` `ShouldContinue` méthodes et.

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
           get { return processNames; }
           set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                      WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                           ErrorCategory.ReadError, process));
                      continue;
                   }

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                          (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
