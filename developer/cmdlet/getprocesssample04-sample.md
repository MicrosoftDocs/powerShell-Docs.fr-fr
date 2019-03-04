---
title: Exemple de GetProcessSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861875"
---
# <a name="getprocesssample04-sample"></a>Exemple GetProcessSample04

Cet exemple montre comment implémenter une applet de commande qui Récupère les processus sur l’ordinateur local. Il génère une erreur sans fin d’exécution si une erreur se produit lors de la récupération d’un processus. Cette applet de commande est une version simplifiée de la `Get-Process` applet de commande fournie par Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Guide pratique pour générer l’exemple à l’aide de Visual Studio.

1. Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier GetProcessSample04. L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Double-cliquez sur l’icône pour le fichier solution (.sln). L’exemple de projet s’ouvre dans Visual Studio.

3. Dans le **Build** menu, sélectionnez **générer la Solution**.

    La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Créez le dossier de module suivant :

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Copiez l’exemple d’assembly dans le dossier de module.

3. Démarrez Windows PowerShell.

4. Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :

    `Import-module getprossessample04`

5. Exécutez la commande suivante pour exécuter l’applet de commande :

    `get-proc`

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2.0.

## <a name="demonstrates"></a>Montre

Cet exemple montre ce qui suit.

- Déclaration de la classe d’applet de commande à l’aide de l’attribut de l’applet de commande.

- Déclaration d’un paramètre de l’applet de commande à l’aide de l’attribut de paramètre.

- Spécifiant la position du paramètre.

- En spécifiant que le paramètre prend en entrée du pipeline. L’entrée peut provenir d’un objet ou une valeur d’une propriété d’un objet dont le nom propriété est le même que le nom du paramètre.

- Déclaration d’un attribut de validation pour le paramètre d’entrée.

- Interception d’une erreur sans fin d’exécution et l’écriture d’un message d’erreur dans le flux d’erreurs.

## <a name="example"></a>Exemple

Cet exemple montre comment créer une applet de commande qui gère les erreurs sans fin d’exécution et écrit les messages d’erreur dans le flux d’erreurs.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
