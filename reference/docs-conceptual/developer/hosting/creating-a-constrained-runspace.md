---
title: Création d’une instance d’exécution restreinte | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 30ecb80dbd96278ee9aa5a609d27bfc4eaa423e9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779809"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="f96b0-102">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="f96b0-102">Creating a constrained runspace</span></span>

<span data-ttu-id="f96b0-103">Pour des raisons de performances ou de sécurité, vous souhaiterez peut-être restreindre les commandes Windows PowerShell disponibles pour votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="f96b0-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="f96b0-104">Pour ce faire, vous devez créer un [System.Management.Automation.Runspaces.Inivide tialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) en appelant l' [System.Management.Automation.Runspaces.Initialsessionstate. Créez \*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) , puis ajoutez uniquement les commandes que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="f96b0-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="f96b0-105">L’utilisation d’une instance d’exécution qui charge uniquement les commandes que vous spécifiez fournit des performances considérablement améliorées.</span><span class="sxs-lookup"><span data-stu-id="f96b0-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="f96b0-106">Vous utilisez les méthodes de la classe [System. Management. Automation. instances d’exécution. Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) pour définir des applets de commande pour l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="f96b0-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="f96b0-107">Vous pouvez également rendre les commandes privées.</span><span class="sxs-lookup"><span data-stu-id="f96b0-107">You can also make commands private.</span></span> <span data-ttu-id="f96b0-108">Les commandes privées peuvent être utilisées par l’application hôte, mais pas par les utilisateurs de l’application.</span><span class="sxs-lookup"><span data-stu-id="f96b0-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="f96b0-109">Ajout de commandes à une instance d’exécution vide</span><span class="sxs-lookup"><span data-stu-id="f96b0-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="f96b0-110">L’exemple suivant montre comment créer un InitialSessionState vide et y ajouter des commandes.</span><span class="sxs-lookup"><span data-stu-id="f96b0-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

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

## <a name="making-commands-private"></a><span data-ttu-id="f96b0-111">Rendre les commandes privées</span><span class="sxs-lookup"><span data-stu-id="f96b0-111">Making commands private</span></span>

 <span data-ttu-id="f96b0-112">Vous pouvez également rendre une commande privée, en affectant à sa propriété [System. Management. Automation. CommandInfo. Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) la valeur [System. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span><span class="sxs-lookup"><span data-stu-id="f96b0-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span></span> <span data-ttu-id="f96b0-113">L’application hôte et d’autres commandes peuvent appeler cette commande, mais l’utilisateur de l’application ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="f96b0-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="f96b0-114">Dans l’exemple suivant, la commande [obten-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) est privée.</span><span class="sxs-lookup"><span data-stu-id="f96b0-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="f96b0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f96b0-115">See Also</span></span>

 [<span data-ttu-id="f96b0-116">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="f96b0-116">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
