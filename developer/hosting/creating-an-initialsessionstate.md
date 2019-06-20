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
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263839"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="67aef-102">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="67aef-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="67aef-103">Commandes de PowerShell s’exécutent dans une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="67aef-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="67aef-104">Pour héberger PowerShell dans votre application, vous devez créer un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objet.</span><span class="sxs-lookup"><span data-stu-id="67aef-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="67aef-105">Chaque instance d’exécution a une [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet associé.</span><span class="sxs-lookup"><span data-stu-id="67aef-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="67aef-106">Le InitialSessionState spécifie les caractéristiques de l’instance d’exécution, tels que les commandes, les variables et les modules sont disponibles pour cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="67aef-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="67aef-107">Créer une valeur par défaut InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="67aef-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="67aef-108">Le [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) et [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) méthodes de la **InitialSessionState** classe peut être utilisée pour créer un **InitialSessionState**objet.</span><span class="sxs-lookup"><span data-stu-id="67aef-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="67aef-109">Le **CreateDefault** méthode crée un **InitialSessionState** avec toutes les commandes intégrées chargés lors de la **CreateDefault2** méthode charge uniquement les commandes requis pour l’hôte PowerShell (les commandes à partir du module Microsoft.PowerShell.Core).</span><span class="sxs-lookup"><span data-stu-id="67aef-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="67aef-110">Si vous souhaitez limiter davantage les commandes disponibles dans votre application hôte, vous devez créer une instance d’exécution contrainte.</span><span class="sxs-lookup"><span data-stu-id="67aef-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="67aef-111">Pour plus d’informations, consultez [création d’une instance d’exécution contrainte](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="67aef-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="67aef-112">Le code suivant montre comment créer un **InitialSessionState**, affectez-le à une instance d’exécution, ajouter des commandes vers le pipeline dans cette instance d’exécution et appeler les commandes.</span><span class="sxs-lookup"><span data-stu-id="67aef-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="67aef-113">Pour plus d’informations sur l’ajout et l’appel des commandes, consultez [Ajout et l’appel des commandes](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="67aef-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="67aef-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67aef-114">See Also</span></span>

[<span data-ttu-id="67aef-115">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="67aef-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="67aef-116">Ajout et l’appel des commandes</span><span class="sxs-lookup"><span data-stu-id="67aef-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
