---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple Runspace01
description: Exemple Runspace01
ms.openlocfilehash: f47f79dd507db258119016353dc5a72d110d9252
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657911"
---
# <a name="runspace01-sample"></a>Exemple Runspace01

Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter l’applet de commande d' [obtention de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de façon synchrone. L’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne les objets [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) pour chaque processus en cours d’exécution sur l’ordinateur local. Les valeurs des propriétés [System. Diagnostics. Process. ProcessName *](/dotnet/api/System.Diagnostics.Process.ProcessName) et [System. Diagnostics. Process. HandleCount *](/dotnet/api/System.Diagnostics.Process.Handlecount) sont ensuite extraites des objets retournés et affichées dans une fenêtre de console.

## <a name="requirements"></a>Spécifications

 Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

- Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter une commande.

- Ajout d’une commande au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Exécution de la commande de façon synchrone.

- Utilisation des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) pour extraire les propriétés des objets retournés par la commande.

## <a name="example"></a>Exemple

 Cet exemple exécute l’applet de commande d' [extraction de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de façon synchrone dans l’instance d’exécution par défaut fournie par Windows PowerShell.

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

## <a name="see-also"></a>Voir aussi
