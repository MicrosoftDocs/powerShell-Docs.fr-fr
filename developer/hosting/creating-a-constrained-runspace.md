---
title: Création d’une instance d’exécution contrainte | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 29f1be6a1215219ddd16367a31f528a4f0dbc2e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083006"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="158b3-102">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="158b3-102">Creating a constrained runspace</span></span>

<span data-ttu-id="158b3-103">Pour des raisons de sécurité ou des performances, vous souhaiterez peut-être limiter les commandes Windows PowerShell disponibles pour votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="158b3-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="158b3-104">Pour ce faire, vous créez un vide [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) en appelant le [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) (méthode), puis ajoutez uniquement les commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="158b3-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="158b3-105">À l’aide d’une instance d’exécution qui charge uniquement les commandes que vous spécifiez fournit des performances significativement accrues.</span><span class="sxs-lookup"><span data-stu-id="158b3-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="158b3-106">Vous utilisez les méthodes de la [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe pour définir des applets de commande pour l’état de session initiale.</span><span class="sxs-lookup"><span data-stu-id="158b3-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="158b3-107">Vous pouvez également rendre commandes privé.</span><span class="sxs-lookup"><span data-stu-id="158b3-107">You can also make commands private.</span></span> <span data-ttu-id="158b3-108">Commandes privées peuvent être utilisées par l’application hôte, mais pas par les utilisateurs de l’application.</span><span class="sxs-lookup"><span data-stu-id="158b3-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="158b3-109">Ajout de commandes à une instance d’exécution vide</span><span class="sxs-lookup"><span data-stu-id="158b3-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="158b3-110">L’exemple suivant montre comment créer un InitialSessionState vide et ajouter des commandes.</span><span class="sxs-lookup"><span data-stu-id="158b3-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a><span data-ttu-id="158b3-111">Commandes de rendre privés</span><span class="sxs-lookup"><span data-stu-id="158b3-111">Making commands private</span></span>

 <span data-ttu-id="158b3-112">Vous pouvez également rendre une commande privé, en lui affectant de [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) propriété [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) .</span><span class="sxs-lookup"><span data-stu-id="158b3-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span></span> <span data-ttu-id="158b3-113">L’application hôte et autres commandes peuvent appeler cette commande, mais pas de l’utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="158b3-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="158b3-114">Dans l’exemple suivant, le [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) commande est privée.</span><span class="sxs-lookup"><span data-stu-id="158b3-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="158b3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="158b3-115">See Also</span></span>

 [<span data-ttu-id="158b3-116">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="158b3-116">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
