---
title: Exemple Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367418"
---
# <a name="runspace01-sample"></a><span data-ttu-id="67809-102">Exemple Runspace01</span><span class="sxs-lookup"><span data-stu-id="67809-102">Runspace01 Sample</span></span>

<span data-ttu-id="67809-103">Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter l’applet de commande d' [obtention de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="67809-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="67809-104">L’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne les objets [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) pour chaque processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="67809-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="67809-105">Les valeurs des propriétés [System. Diagnostics. Process. ProcessName \*](/dotnet/api/System.Diagnostics.Process.ProcessName) et [System. Diagnostics. Process. HandleCount \*](/dotnet/api/System.Diagnostics.Process.Handlecount) sont ensuite extraites des objets retournés et affichées dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="67809-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="67809-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="67809-106">Requirements</span></span>

 <span data-ttu-id="67809-107">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="67809-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="67809-108">Illustré</span><span class="sxs-lookup"><span data-stu-id="67809-108">Demonstrates</span></span>

- <span data-ttu-id="67809-109">Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="67809-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="67809-110">Ajout d’une commande au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="67809-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="67809-111">Exécution de la commande de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="67809-111">Running the command synchronously.</span></span>

- <span data-ttu-id="67809-112">Utilisation des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) pour extraire les propriétés des objets retournés par la commande.</span><span class="sxs-lookup"><span data-stu-id="67809-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="67809-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="67809-113">Example</span></span>

 <span data-ttu-id="67809-114">Cet exemple exécute l’applet de commande d' [extraction de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de façon synchrone dans l’instance d’exécution par défaut fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67809-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="67809-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67809-115">See Also</span></span>
