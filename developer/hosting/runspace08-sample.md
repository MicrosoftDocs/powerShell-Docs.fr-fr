---
title: Exemple de Runspace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1100d91d-249d-4af7-9854-2d6a423ac2f4
caps.latest.revision: 7
ms.openlocfilehash: ac010ee94752458c31b5b3b26c9ac17e0c56c4ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860795"
---
# <a name="runspace08-sample"></a><span data-ttu-id="09d43-102">Exemple Runspace08</span><span class="sxs-lookup"><span data-stu-id="09d43-102">Runspace08 Sample</span></span>

<span data-ttu-id="09d43-103">Cet exemple montre comment ajouter des commandes et arguments au pipeline d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet et comment exécuter les commandes de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="09d43-103">This sample shows how to add commands and arguments to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

## <a name="requirements"></a><span data-ttu-id="09d43-104">Spécifications</span><span class="sxs-lookup"><span data-stu-id="09d43-104">Requirements</span></span>

<span data-ttu-id="09d43-105">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="09d43-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="09d43-106">Montre</span><span class="sxs-lookup"><span data-stu-id="09d43-106">Demonstrates</span></span>

<span data-ttu-id="09d43-107">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="09d43-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="09d43-108">Création d’un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objet à l’aide de la [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) classe.</span><span class="sxs-lookup"><span data-stu-id="09d43-108">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object by using the [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) class.</span></span>

- <span data-ttu-id="09d43-109">Création d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet qui utilise l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="09d43-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="09d43-110">Ajout d’applets de commande pour le pipeline de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.</span><span class="sxs-lookup"><span data-stu-id="09d43-110">Adding cmdlets to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="09d43-111">Exécuter les applets de commande de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="09d43-111">Running the cmdlets synchronously.</span></span>

- <span data-ttu-id="09d43-112">Extraction des propriétés à partir de la [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objets retournés par la commande.</span><span class="sxs-lookup"><span data-stu-id="09d43-112">Extracting properties from the [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="09d43-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="09d43-113">Example</span></span>

<span data-ttu-id="09d43-114">Cet exemple exécute la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) applets de commande en utilisant un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.</span><span class="sxs-lookup"><span data-stu-id="09d43-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace08
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands. The
    /// PowerShell object builds a pipeline that include the get-process cmdlet,
    /// which is then piped to the sort-object cmdlet. Parameters are added to the
    /// sort-object cmdlet to sort the HandleCount property in descending order.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates:
    /// 1. Creating a PowerShell object
    /// 2. Adding individual commands to the PowerShell object.
    /// 3. Adding parameters to the commands.
    /// 4. Running the pipeline of the PowerShell object synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> results; // Holds the result of the pipeline execution.

      // Create the PowerShell object. Notice that no runspace is specified so a
      // new default runspace is used.
      PowerShell powershell = PowerShell.Create();

      // Use the using statement so that we can dispose of the PowerShell object
      // when we are done.
      using (powershell)
      {
        // Add the get-process cmdlet to the pipeline of the PowerShell object.
        powershell.AddCommand("get-process");

        // Add the sort-object cmdlet and its parameters to the pipeline of
        // the PowerShell object so that we can sort the HandleCount property
        //  in descending order.
        powershell.AddCommand("sort-object").AddParameter("descending").AddParameter("property", "handlecount");

        // Run the commands of the pipeline synchronously.
        results = powershell.Invoke();
      }

      // Even after disposing of the PowerShell object, we still
      // need to set the powershell variable to null so that the
      // garbage collector can clean it up.
      powershell = null;

      Console.WriteLine("Process              HandleCount");
      Console.WriteLine("--------------------------------");

      // Display the results returned by the commands.
      foreach (PSObject result in results)
      {
        Console.WriteLine(
                          "{0,-20} {1}",
                          result.Members["ProcessName"].Value,
                          result.Members["HandleCount"].Value);
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="09d43-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09d43-115">See Also</span></span>

[<span data-ttu-id="09d43-116">Écriture d’une Application hôte PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="09d43-116">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)