---
title: Exemple Runspace02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360978"
---
# <a name="runspace02-sample"></a><span data-ttu-id="eb3ca-102">Exemple Runspace02</span><span class="sxs-lookup"><span data-stu-id="eb3ca-102">Runspace02 Sample</span></span>

<span data-ttu-id="eb3ca-103">Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter les applets de commande d' [obtention-processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et de [Tri-objet](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="eb3ca-104">L’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne les objets [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) pour chaque processus en cours d’exécution sur l’ordinateur local, et le `Sort-Object` trie les objets en fonction de leur propriété [System.Diagnostics.Process.ID \*](/dotnet/api/System.Diagnostics.Process.Id) .</span><span class="sxs-lookup"><span data-stu-id="eb3ca-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="eb3ca-105">Les résultats de ces commandes s’affichent à l’aide d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .</span><span class="sxs-lookup"><span data-stu-id="eb3ca-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb3ca-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eb3ca-106">Requirements</span></span>

<span data-ttu-id="eb3ca-107">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eb3ca-108">Démontre</span><span class="sxs-lookup"><span data-stu-id="eb3ca-108">Demonstrates</span></span>

<span data-ttu-id="eb3ca-109">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="eb3ca-110">Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="eb3ca-111">Ajout de commandes au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="eb3ca-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="eb3ca-112">Exécution des commandes de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="eb3ca-113">Utilisation d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) pour afficher la sortie des commandes dans une application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="eb3ca-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb3ca-114">Example</span></span>

<span data-ttu-id="eb3ca-115">Cet exemple exécute de façon synchrone les applets de commande d' [extraction](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et d' [objet de tri](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) dans l’instance d’exécution par défaut fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb3ca-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="eb3ca-116">La sortie est affichée dans un formulaire à l’aide d’un contrôle [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .</span><span class="sxs-lookup"><span data-stu-id="eb3ca-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eb3ca-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb3ca-117">See Also</span></span>

[<span data-ttu-id="eb3ca-118">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb3ca-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)