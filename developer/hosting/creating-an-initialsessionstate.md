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
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082989"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="e7389-102">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="e7389-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="e7389-103">Commandes de Windows PowerShell s’exécutent dans une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e7389-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="e7389-104">Pour héberger Windows PowerShell dans votre application, vous devez créer un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objet.</span><span class="sxs-lookup"><span data-stu-id="e7389-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="e7389-105">Chaque instance d’exécution a une [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet associé.</span><span class="sxs-lookup"><span data-stu-id="e7389-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="e7389-106">Le [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) spécifie les caractéristiques de l’instance d’exécution, tels que les commandes, les variables et les modules sont disponibles pour cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e7389-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="e7389-107">Créer une valeur par défaut InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="e7389-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="e7389-108">Le [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)et [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) méthodes peuvent être utilisées. Pour créer [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objets.</span><span class="sxs-lookup"><span data-stu-id="e7389-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="e7389-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) crée un InitialSessionState avec toutes les commandes intégrées chargé lors de la [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) charge uniquement les commandes nécessaires à l’hôte Windows PowerShell (les commandes à partir du module Microsoft.PowerShell.Core.</span><span class="sxs-lookup"><span data-stu-id="e7389-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="e7389-110">Si vous souhaitez limiter davantage les commandes disponibles dans votre application hôte, vous devez créer une instance d’exécution contrainte.</span><span class="sxs-lookup"><span data-stu-id="e7389-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="e7389-111">Pour plus d’informations, consultez Création d’une instance d’exécution contrainte.</span><span class="sxs-lookup"><span data-stu-id="e7389-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="e7389-112">Le code suivant montre comment créer un InitialSessionState, affectez-le à une instance d’exécution, ajouter des commandes vers le pipeline dans cette instance d’exécution et appeler les commandes.</span><span class="sxs-lookup"><span data-stu-id="e7389-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="e7389-113">Pour plus d’informations sur l’ajout et l’appel des commandes, consultez Ajout et l’appel des commandes.</span><span class="sxs-lookup"><span data-stu-id="e7389-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

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

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
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

## <a name="see-also"></a><span data-ttu-id="e7389-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7389-114">See Also</span></span>

 [<span data-ttu-id="e7389-115">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="e7389-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
