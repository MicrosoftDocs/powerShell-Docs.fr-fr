---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple Runspace10
description: Exemple Runspace10
ms.openlocfilehash: fd58cea553e6b830a56df7edfa7901d39f46a06c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657585"
---
# <a name="runspace10-sample"></a>Exemple Runspace10

Cet exemple montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à l' [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple illustre ce qui suit.

- Création d’un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Ajout d’une applet de commande (définie par l’application hôte) à l’objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Création d’un objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) qui utilise l’objet.

- Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) qui utilise l’objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .

- Ajout de la commande au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Extraction des propriétés des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) retournés par la commande.

## <a name="example"></a>Exemple

Cet exemple crée une instance d’exécution qui utilise un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour définir les éléments qui sont disponibles lorsque l’instance d’exécution est ouverte. Dans cet exemple, l’applet de commande Get-Proc (définie par l’application hôte) est ajoutée à l’état de session initial, et l’applet de commande est exécutée de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une application hôte Windows PowerShell](./writing-a-windows-powershell-host-application.md)
