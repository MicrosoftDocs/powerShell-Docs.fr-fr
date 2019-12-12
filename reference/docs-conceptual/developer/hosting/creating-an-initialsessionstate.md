---
title: Création d’un InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367618"
---
# <a name="creating-an-initialsessionstate"></a>Création d’un InitialSessionState

Les commandes PowerShell s’exécutent dans une instance d’exécution.
Pour héberger PowerShell dans votre application, vous devez créer un objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .
Chaque instance d’exécution est associée à un objet [System. Management. Automation. instances d’exécution. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .
Le InitialSessionState spécifie les caractéristiques de l’instance d’exécution, telles que les commandes, les variables et les modules disponibles pour cette instance d’exécution.

## <a name="create-a-default-initialsessionstate"></a>Créer un InitialSessionState par défaut

Les méthodes [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) et [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) de la classe **InitialSessionState** peuvent être utilisées pour créer un objet **InitialSessionState** .
La méthode **CreateDefault** crée un **InitialSessionState** avec toutes les commandes intégrées chargées, tandis que la méthode **CreateDefault2** charge uniquement les commandes requises pour héberger PowerShell (les commandes du module Microsoft. PowerShell. Core).

Si vous souhaitez limiter davantage les commandes disponibles dans votre application hôte, vous devez créer une instance d’exécution limitée.
Pour plus d’informations, consultez [création d’une instance d’exécution avec restriction](creating-a-constrained-runspace.md).

Le code suivant montre comment créer un **InitialSessionState**, l’assigner à une instance d’exécution, ajouter des commandes au pipeline dans cette instance d’exécution et appeler les commandes.
Pour plus d’informations sur l’ajout et l’appel de commandes, consultez [Ajout et appel de commandes](adding-and-invoking-commands.md).

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Voir aussi

[Création d’une instance d’exécution avec restriction](creating-a-constrained-runspace.md)

[Ajout et appel de commandes](adding-and-invoking-commands.md)
