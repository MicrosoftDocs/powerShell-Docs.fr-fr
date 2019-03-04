---
title: L’exemple GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859835"
---
# <a name="getprocesssample01-sample"></a>Exemple GetProcessSample01

Cet exemple montre comment implémenter une applet de commande qui Récupère les processus sur l’ordinateur local. Cette applet de commande est une version simplifiée de la `Get-Process` applet de commande qui est fournie par Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Guide pratique pour générer l’exemple à l’aide de Visual Studio.

1. Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier GetProcessSample01. L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Double-cliquez sur l’icône pour le fichier solution (.sln). L’exemple de projet s’ouvre dans Microsoft Visual Studio.

3. Dans le **Build** menu, sélectionnez **générer la Solution**.

  La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Ouvrez une fenêtre d'invite de commandes.

2. Accédez au répertoire contenant l’exemple de fichier .dll.

3. Exécutez installutil « GetProcessSample01.dll ».

4. Démarrez Windows PowerShell.

5. Exécutez la commande suivante pour ajouter le composant logiciel enfichable à l’interpréteur de commandes.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Entrez la commande suivante pour exécuter l’applet de commande. `get-proc`

   `get-proc`

   Il s’agit d’un exemple de sortie qui résulte de procédez comme suit.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 1.0 ou version ultérieure.

## <a name="demonstrates"></a>Montre

Cet exemple montre ce qui suit.

- Création d’une applet de commande d’exemple de base.

- Définition d’une classe de l’applet de commande à l’aide de l’attribut de l’applet de commande.

- Création d’un composant logiciel enfichable qui fonctionne avec Windows PowerShell 1.0 et de Windows PowerShell 2.0. Les exemples suivants utilisent les modules au lieu des composants logiciel enfichables afin qu’ils nécessitent Windows PowerShell 2.0.

## <a name="example"></a>Exemple

Cet exemple montre comment créer une applet de commande simple et son composant logiciel enfichable.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)