---
title: Exemple de Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082785"
---
# <a name="runspace01-sample"></a><span data-ttu-id="d2daa-102">Exemple Runspace01</span><span class="sxs-lookup"><span data-stu-id="d2daa-102">Runspace01 Sample</span></span>

<span data-ttu-id="d2daa-103">Cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande synchrone.</span><span class="sxs-lookup"><span data-stu-id="d2daa-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="d2daa-104">Le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande renvoie [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objets pour chaque processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d2daa-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="d2daa-105">Les valeurs de la [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) et [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) propriétés sont ensuite extraites les objets retournés et affichées dans une console fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d2daa-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2daa-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d2daa-106">Requirements</span></span>

 <span data-ttu-id="d2daa-107">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="d2daa-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d2daa-108">Montre</span><span class="sxs-lookup"><span data-stu-id="d2daa-108">Demonstrates</span></span>

- <span data-ttu-id="d2daa-109">Création d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="d2daa-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="d2daa-110">Ajout d’une commande au pipeline de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.</span><span class="sxs-lookup"><span data-stu-id="d2daa-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="d2daa-111">Exécuter la commande de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="d2daa-111">Running the command synchronously.</span></span>

- <span data-ttu-id="d2daa-112">À l’aide de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objets pour extraire les propriétés d’objets retournés par la commande.</span><span class="sxs-lookup"><span data-stu-id="d2daa-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="d2daa-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2daa-113">Example</span></span>

 <span data-ttu-id="d2daa-114">Cet exemple exécute la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande synchrone dans l’instance d’exécution par défaut fourni par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d2daa-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2daa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2daa-115">See Also</span></span>
