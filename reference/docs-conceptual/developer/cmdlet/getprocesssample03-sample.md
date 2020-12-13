---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple GetProcessSample03
description: Exemple GetProcessSample03
ms.openlocfilehash: 7827247238f3dad2018b55e396b73d1fa434eb97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660725"
---
# <a name="getprocesssample03-sample"></a>Exemple GetProcessSample03

Cet exemple montre comment implémenter une applet de commande qui récupère les processus sur l’ordinateur local. Il fournit un `Name` paramètre qui peut accepter un objet du pipeline ou une valeur d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre. Cette applet de commande est une version simplifiée de l’applet de commande `Get-Process` fournie par Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Comment générer l’exemple à l’aide de Visual Studio.

1. Une fois le kit de développement logiciel (SDK) 2,0 Windows PowerShell installé, accédez au dossier GetProcessSample03. L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.

2. Double-cliquez sur l’icône du fichier solution (. sln). L’exemple de projet s’ouvre dans Visual Studio.

3. Dans le menu **Générer**, sélectionnez **Générer la solution**.

    La bibliothèque de l’exemple sera générée dans les dossiers \bin ou \bin\debug par défaut.

### <a name="how-to-run-the-sample"></a>Comment exécuter l’exemple

1. Créez le dossier de module suivant :

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. Copiez l’exemple d’assembly dans le dossier du module.

3. Démarrez Windows PowerShell.

4. Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :

    `Import-module getprossessample03`

5. Exécutez la commande suivante pour exécuter l’applet de commande :

    `get-proc`

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple illustre ce qui suit.

- Déclaration d’une classe d’applet de commande à l’aide de l’attribut d’applet de commande.

- Déclaration d’un paramètre d’applet de commande à l’aide de l’attribut Parameter.

- Spécification de la position du paramètre.

- Spécifie que le paramètre prend l’entrée du pipeline. L’entrée peut être extraite à partir d’un objet ou d’une valeur d’une propriété d’un objet dont le nom de la propriété est le même que le nom du paramètre.

- Déclaration d’un attribut de validation pour l’entrée de paramètre.

## <a name="example"></a>Exemple

Cet exemple illustre une implémentation de l’applet de commande Get-Proc qui comprend un `Name` paramètre acceptant l’entrée du pipeline.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
