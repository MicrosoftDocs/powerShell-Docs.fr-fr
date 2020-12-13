---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple Runspace05
description: Exemple Runspace05
ms.openlocfilehash: 67a372eecba30452587471328412e8a2bdd9ec5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657730"
---
# <a name="runspace05-sample"></a>Exemple Runspace05

Cet exemple montre comment ajouter un composant logiciel enfichable à un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour que l’applet de commande du composant logiciel enfichable soit disponible quand l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une applet de commande Get-Proc (définie par l' [exemple GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) qui est exécutée de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustre le

Cet exemple illustre ce qui suit.

- Création d’un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Ajout du composant logiciel enfichable au [System.Management.Automation.Runspaces.Iniobjet tialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Création d’un objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) qui utilise l’objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) qui utilise l’instance d’exécution.

- Ajout de l’applet de commande « main-proc » du composant logiciel enfichable au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

- Exécution de la commande de façon synchrone.

- Extraction des propriétés des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) retournés par la commande.

## <a name="example"></a>Exemple

Cet exemple crée une instance d’exécution qui utilise un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour définir les éléments qui sont disponibles lorsque l’instance d’exécution est ouverte. Dans cet exemple, un composant logiciel enfichable qui définit une applet de commande Get-Proc est ajouté à l’état de session initial.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
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
