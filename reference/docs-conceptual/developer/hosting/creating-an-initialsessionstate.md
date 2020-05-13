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
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271880"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="283e3-102">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="283e3-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="283e3-103">Les commandes PowerShell s’exécutent dans une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="283e3-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="283e3-104">Pour héberger PowerShell dans votre application, vous devez créer un objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="283e3-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="283e3-105">Chaque instance d’exécution est associée à un objet [System. Management. Automation. instances d’exécution. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="283e3-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="283e3-106">Le InitialSessionState spécifie les caractéristiques de l’instance d’exécution, telles que les commandes, les variables et les modules disponibles pour cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="283e3-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="283e3-107">Créer un InitialSessionState par défaut</span><span class="sxs-lookup"><span data-stu-id="283e3-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="283e3-108">Les méthodes [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) et [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) de la classe **InitialSessionState** peuvent être utilisées pour créer un objet **InitialSessionState** .</span><span class="sxs-lookup"><span data-stu-id="283e3-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="283e3-109">La méthode **CreateDefault** crée un **InitialSessionState** avec toutes les commandes intégrées chargées, tandis que la méthode **CreateDefault2** charge uniquement les commandes requises pour héberger PowerShell (les commandes du module Microsoft. PowerShell. Core).</span><span class="sxs-lookup"><span data-stu-id="283e3-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="283e3-110">Si vous souhaitez limiter davantage les commandes disponibles dans votre application hôte, vous devez créer une instance d’exécution limitée.</span><span class="sxs-lookup"><span data-stu-id="283e3-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="283e3-111">Pour plus d’informations, consultez [création d’une instance d’exécution avec restriction](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="283e3-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="283e3-112">Le code suivant montre comment créer un **InitialSessionState**, l’assigner à une instance d’exécution, ajouter des commandes au pipeline dans cette instance d’exécution et appeler les commandes.</span><span class="sxs-lookup"><span data-stu-id="283e3-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="283e3-113">Pour plus d’informations sur l’ajout et l’appel de commandes, consultez [Ajout et appel de commandes](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="283e3-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="283e3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="283e3-114">See Also</span></span>

[<span data-ttu-id="283e3-115">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="283e3-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="283e3-116">Ajout et appel de commandes</span><span class="sxs-lookup"><span data-stu-id="283e3-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
