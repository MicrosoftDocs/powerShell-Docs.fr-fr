---
ms.date: 09/13/2016
ms.topic: reference
title: Création de plusieurs instances d’exécution
description: Création de plusieurs instances d’exécution
ms.openlocfilehash: 2dc9cc0397178d679a4d418b7b19fb0895a4e1b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649394"
---
# <a name="creating-multiple-runspaces"></a>Création de plusieurs instances d’exécution

Si vous créez un grand nombre de instances d’exécution, vous pouvez envisager de créer un pool d’instances d’exécution. L’utilisation d’un objet [System. Management. Automation. instances d’exécution. Runspacepool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) , au lieu de créer un grand nombre de instances d’exécution individuelles avec les mêmes caractéristiques, peut améliorer les performances.

## <a name="creating-and-using-a-runspace-pool"></a>Création et utilisation d’un pool d’instances d’exécution.

 L’exemple suivant montre comment créer un pool d’instances d’exécution et comment exécuter une commande de façon asynchrone dans une instance d’exécution du pool.

```csharp
namespace HostRunspacePool
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  /// <summary>
  /// This class provides the Main entry point for the Host application.
  /// </summary>
  internal class HostRunspacePool
  {
    /// <summary>
    /// This sample demonstrates the following.
    /// 1. Creating and opening a runspace pool.
    /// 2. Creating a PowerShell object.
    /// 3. Adding commands and arguments to the PowerShell object.
    /// 4. Running the commands asynchronously using the runspace
    ///    of the runspace pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    private static void Main(string[] args)
    {
      // Create a pool of runspaces.
      using (RunspacePool rsp = RunspaceFactory.CreateRunspacePool())
      {
        rsp.Open();

        // Create a PowerShell object to run the following command.
        //  get-process wmi*
        PowerShell gpc = PowerShell.Create();
        // Specify the runspace to use and add commands.
        gpc.RunspacePool = rsp;
        gpc.AddCommand("Get-Process").AddArgument("wmi*");

        // Invoke the command asynchronously.
        IAsyncResult gpcAsyncResult = gpc.BeginInvoke();
        // Get the results of running the command.
        PSDataCollection<PSObject> gpcOutput = gpc.EndInvoke(gpcAsyncResult);

        // Process the output.
        Console.WriteLine("The output from running the command: get-process wmi*");
        for (int i= 0; i < gpcOutput.Count; i++)
        {
         Console.WriteLine(
                           "Process Name: {0} Process Id: {1}",
                           gpcOutput[i].Properties["ProcessName"].Value,
                           gpcOutput[i].Properties["Id"].Value);
        }
      } // End using.
    } // End Main entry point.
  } // End HostPs5 class.
}
```

## <a name="see-also"></a>Voir aussi

 [Création d’un InitialSessionState](./creating-an-initialsessionstate.md)
