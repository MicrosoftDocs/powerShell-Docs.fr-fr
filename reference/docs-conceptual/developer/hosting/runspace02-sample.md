---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple Runspace02
description: Exemple Runspace02
ms.openlocfilehash: 0206e1a80f3e5488fd2dd5628985756a5ca343c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657907"
---
# <a name="runspace02-sample"></a>Exemple Runspace02

Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter les applets de commande d' [obtention-processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et de [Tri-objet](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) de façon synchrone. L’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne les objets [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) pour chaque processus en cours d’exécution sur l’ordinateur local, et `Sort-Object` trie les objets en fonction de leur propriété [System.Diagnostics.Process.ID *](/dotnet/api/System.Diagnostics.Process.Id) . Les résultats de ces commandes s’affichent à l’aide d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple illustre ce qui suit.

- Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter des commandes.

- Ajout de commandes au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Exécution des commandes de façon synchrone.

- Utilisation d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) pour afficher la sortie des commandes dans une application Windows Forms.

## <a name="example"></a>Exemple

Cet exemple exécute de façon synchrone les applets de commande d' [extraction](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et d' [objet de tri](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) dans l’instance d’exécution par défaut fournie par Windows PowerShell. La sortie est affichée dans un formulaire à l’aide d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une application hôte Windows PowerShell](./writing-a-windows-powershell-host-application.md)
