---
title: Exemple de Runspace02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082717"
---
# <a name="runspace02-sample"></a>Exemple Runspace02

Cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) applets de commande de façon synchrone. Le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande renvoie [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objets pour chaque processus en cours d’exécution sur l’ordinateur local et le `Sort-Object` trie les objets selon leurs [ System.Diagnostics.Process.Id*](/dotnet/api/System.Diagnostics.Process.Id) propriété. Les résultats de ces commandes s’affiche à l’aide un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) contrôle.

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2.0.

## <a name="demonstrates"></a>Montre

Cet exemple montre ce qui suit.

- Création d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet pour exécuter des commandes.

- Ajout de commandes au pipeline de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

- Exécuter les commandes de façon synchrone.

- À l’aide un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) contrôle pour afficher la sortie des commandes dans une application Windows Forms.

## <a name="example"></a>Exemple

Cet exemple exécute la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) applets de commande de façon synchrone dans l’instance d’exécution par défaut fourni par Windows PowerShell. La sortie s’affiche dans un formulaire à l’aide un [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) contrôle.

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

[Écriture d’une Application hôte PowerShell de Windows](./writing-a-windows-powershell-host-application.md)