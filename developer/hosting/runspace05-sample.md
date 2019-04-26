---
title: Exemple de Runspace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: eb227b5fa5e91f59b6fc99981ff5affca1cf63fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082700"
---
# <a name="runspace05-sample"></a>Exemple Runspace05

Cet exemple montre comment ajouter un composant logiciel enfichable à une [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet afin que l’applet de commande de l’utilisation du composant logiciel enfichable est disponible lorsque l’instance d’exécution est ouverte. Le composant logiciel enfichable fournit une applet de commande Get-Process (définie par le [exemple GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) qui est exécutée de façon synchrone à l’aide un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

## <a name="requirements"></a>Spécifications

Cet exemple requiert Windows PowerShell 2.0.

## <a name="demonstrates"></a>Montre

Cet exemple montre ce qui suit.

- Création d’un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet.

- Ajouter le composant logiciel enfichable dans le [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet.

- Création d’un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objet qui utilise le [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet.

- Création d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet qui utilise l’instance d’exécution.

- Ajouter applet de commande get-Process du logiciel enfichable au pipeline de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

- Exécuter la commande de façon synchrone.

- Extraction des propriétés à partir de la [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objets retournés par la commande.

## <a name="example"></a>Exemple

Cet exemple crée une instance d’exécution qui utilise un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet pour définir les éléments qui sont disponibles lorsque l’instance d’exécution est ouverte. Dans cet exemple, un composant logiciel enfichable qui définit une applet de commande Get-Process est ajouté à l’état de session initiale.

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

[Écriture d’une Application hôte PowerShell de Windows](./writing-a-windows-powershell-host-application.md)