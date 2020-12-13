---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple StopProcessSample02
description: Exemple StopProcessSample02
ms.openlocfilehash: 96171413f9f04d12460d48ba91c2c927e1856fd1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666890"
---
# <a name="stopprocesssample02-sample"></a><span data-ttu-id="b8f40-103">Exemple StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="b8f40-103">StopProcessSample02 Sample</span></span>

<span data-ttu-id="b8f40-104">Cet exemple montre comment écrire une applet de commande qui écrit des messages de débogage (WriteDebug), détaillé (WriteVerbose) et d’avertissement (WriteWarning) tout en arrêtant les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b8f40-104">This sample shows how to write a cmdlet that writes debug (WriteDebug), verbose (WriteVerbose), and warning (WriteWarning) messages while stopping processes on the local computer.</span></span> <span data-ttu-id="b8f40-105">Cette applet de commande est similaire à l’applet de commande `Stop-Process` fournie par Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="b8f40-105">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="b8f40-106">Comment générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8f40-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="b8f40-107">Ouvrez Windows Internet Explorer et accédez au répertoire StopProcessSample02 sous le répertoire Samples.</span><span class="sxs-lookup"><span data-stu-id="b8f40-107">Open Windows Internet Explorer and navigate to the StopProcessSample02 directory under the Samples directory.</span></span>

    <span data-ttu-id="b8f40-108">Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier StopProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="b8f40-108">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample02 folder.</span></span> <span data-ttu-id="b8f40-109">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="b8f40-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span></span>

2. <span data-ttu-id="b8f40-110">Double-cliquez sur l’icône du fichier solution (. sln).</span><span class="sxs-lookup"><span data-stu-id="b8f40-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="b8f40-111">L’exemple de projet s’ouvre dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8f40-111">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="b8f40-112">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="b8f40-112">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="b8f40-113">La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="b8f40-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="b8f40-114">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="b8f40-114">How to run the sample</span></span>

1. <span data-ttu-id="b8f40-115">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="b8f40-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample02`

2. <span data-ttu-id="b8f40-116">Copiez l’exemple d’assembly dans le dossier du module.</span><span class="sxs-lookup"><span data-stu-id="b8f40-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="b8f40-117">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8f40-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="b8f40-118">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="b8f40-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample02`

5. <span data-ttu-id="b8f40-119">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="b8f40-119">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="b8f40-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8f40-120">Requirements</span></span>

<span data-ttu-id="b8f40-121">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="b8f40-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b8f40-122">Illustre le</span><span class="sxs-lookup"><span data-stu-id="b8f40-122">Demonstrates</span></span>

<span data-ttu-id="b8f40-123">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="b8f40-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="b8f40-124">Déclaration d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b8f40-124">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="b8f40-125">Déclaration d’un paramètre d’applet de commande à l’aide de l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="b8f40-125">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="b8f40-126">Écriture de messages détaillés.</span><span class="sxs-lookup"><span data-stu-id="b8f40-126">Writing verbose messages.</span></span> <span data-ttu-id="b8f40-127">Pour plus d’informations sur la méthode utilisée pour écrire des messages détaillés, consultez [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)de commande. WriteVerbose.</span><span class="sxs-lookup"><span data-stu-id="b8f40-127">For more information about the method used to write verbose messages, see [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

- <span data-ttu-id="b8f40-128">Écriture des messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b8f40-128">Writing error messages.</span></span> <span data-ttu-id="b8f40-129">Pour plus d’informations sur la méthode utilisée pour écrire des messages d’erreur, consultez [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span><span class="sxs-lookup"><span data-stu-id="b8f40-129">For more information about the method used to write error messages, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span></span>

- <span data-ttu-id="b8f40-130">Écriture des messages d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="b8f40-130">Writing warning messages.</span></span> <span data-ttu-id="b8f40-131">Pour plus d’informations sur la méthode utilisée pour écrire des messages d’avertissement, consultez [System. Management. Automation. applet de commande. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span><span class="sxs-lookup"><span data-stu-id="b8f40-131">For more information about the method used to write warning messages, see [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span></span>

## <a name="example"></a><span data-ttu-id="b8f40-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8f40-132">Example</span></span>

<span data-ttu-id="b8f40-133">Cet exemple montre comment écrire des messages de débogage, de commentaires et d’avertissement à l’aide des `WriteDebug` `WriteVerbose` méthodes, et `WriteWarning` .</span><span class="sxs-lookup"><span data-stu-id="b8f40-133">This sample shows how to write debug, verbose, and warning messages by using the `WriteDebug`, `WriteVerbose`, and `WriteWarning` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
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
               string message = null;

               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.

               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               message = String.Format(CultureInfo.CurrentCulture,
                              "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,
                                     "UnableToAccessProcessByName",
                                         ErrorCategory.InvalidOperation,
                                             name));
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
                                         ErrorCategory.ObjectNotFound, process));
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                 "Acquired name for pid {0} : \"{1}\"",
                                        process.Id, processName);
                   WriteDebug(message);

                   // Confirm the operation first.
                   // This is always false if the WhatIf parameter is specified.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                                        "{0} ({1})",
                                            processName, process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that can possibly stop the computer.
                   bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess && !force)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
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

                   // Display a warning message if the cmdlet is stopping a
                   // critical process.
                   if (criticalProcess)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Stopping the critical process \"{0}\".",
                                          processName);
                       WriteWarning(message);
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
                           WriteError(new ErrorRecord(
                                            e,
                                            "CouldNotStopProcess",
                                            ErrorCategory.CloseError,
                                            process)
                                      );
                           continue;
                       } // if ((e is...
                           else throw;
                   } // catch

                   message = String.Format(CultureInfo.CurrentCulture,
                                  "Stopped process \"{0}\", pid {1}.",
                                        processName, process.Id);

                   WriteVerbose(message);

                   // If the PassThru parameter is specified,
                   // return the terminated process object to the pipeline.
                   if (passThru)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Writing process \"{0}\" to pipeline",
                                          processName);
                       WriteDebug(message);
                       WriteObject(process);
                   } // if (passThru...
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

## <a name="see-also"></a><span data-ttu-id="b8f40-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8f40-134">See Also</span></span>

[<span data-ttu-id="b8f40-135">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f40-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
