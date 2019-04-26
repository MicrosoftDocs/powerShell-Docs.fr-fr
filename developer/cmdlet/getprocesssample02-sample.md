---
title: L’exemple GetProcessSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068077"
---
# <a name="getprocesssample02-sample"></a>Exemple GetProcessSample02

Cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local. Il fournit un `Name` paramètre qui peut être utilisé pour spécifier les processus à récupérer. Cette applet de commande est une version simplifiée de la `Get-Process` applet de commande fournie par Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Guide pratique pour générer l’exemple à l’aide de Visual Studio.

1. Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier GetProcessSample02. L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Double-cliquez sur l’icône pour le fichier solution (.sln). L’exemple de projet s’ouvre dans Visual Studio.

3. Dans le **Build** menu, sélectionnez **générer la Solution**.

    La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Créez le dossier de module suivant :

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Copiez l’exemple d’assembly dans le dossier de module.

3. Démarrez Windows PowerShell.

4. Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :

    `import-module getprossessample02`

5. Exécutez la commande suivante pour exécuter l’applet de commande :

    `get-proc`

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2.0.

## <a name="demonstrates"></a>Montre

Cet exemple montre ce qui suit.

- Déclaration de la classe d’applet de commande à l’aide de l’attribut de l’applet de commande.

- Déclaration d’un paramètre de l’applet de commande à l’aide de l’attribut de paramètre.

- Spécifiant la position du paramètre.

- Déclaration d’un attribut de validation pour le paramètre d’entrée.

## <a name="example"></a>Exemple

Cet exemple illustre une implémentation de l’applet de commande Get-Process qui inclut un `Name` paramètre.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
