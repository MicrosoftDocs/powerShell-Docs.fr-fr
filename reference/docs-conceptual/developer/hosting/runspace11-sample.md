---
title: Exemple Runspace11 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c90d268-730b-4e73-9dfd-5f288c27aed0
caps.latest.revision: 8
ms.openlocfilehash: 74d7c9e9cb0d7ce829635e6aff994473e09e7479
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360848"
---
# <a name="runspace11-sample"></a><span data-ttu-id="873bf-102">Exemple Runspace11</span><span class="sxs-lookup"><span data-stu-id="873bf-102">Runspace11 Sample</span></span>

<span data-ttu-id="873bf-103">Cet exemple montre comment utiliser la classe [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) pour créer une commande de proxy qui appelle une applet de commande existante, mais qui limite l’ensemble des paramètres disponibles.</span><span class="sxs-lookup"><span data-stu-id="873bf-103">This sample shows how to use the [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span> <span data-ttu-id="873bf-104">La commande proxy est ensuite ajoutée à un état de session initial qui sert à créer une instance d’exécution contrainte.</span><span class="sxs-lookup"><span data-stu-id="873bf-104">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span> <span data-ttu-id="873bf-105">Cela signifie que l’utilisateur ne peut accéder à la fonctionnalité de l’applet de commande qu’au moyen de la commande proxy.</span><span class="sxs-lookup"><span data-stu-id="873bf-105">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

## <a name="requirements"></a><span data-ttu-id="873bf-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="873bf-106">Requirements</span></span>

<span data-ttu-id="873bf-107">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="873bf-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="873bf-108">Démontre</span><span class="sxs-lookup"><span data-stu-id="873bf-108">Demonstrates</span></span>

<span data-ttu-id="873bf-109">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="873bf-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="873bf-110">Création d’un objet [System. Management. Automation. Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) qui décrit les métadonnées d’une applet de commande existante.</span><span class="sxs-lookup"><span data-stu-id="873bf-110">Creating a [System.Management.Automation.Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) object that describes the metadata of an existing cmdlet.</span></span>

- <span data-ttu-id="873bf-111">Création d’un objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="873bf-111">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="873bf-112">Modification des métadonnées de l’applet de commande pour supprimer un paramètre de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="873bf-112">Modifying the cmdlet metadata to remove a parameter of the cmdlet.</span></span>

- <span data-ttu-id="873bf-113">Ajout de l’applet de commande à l’objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) et création de l’applet de commande privée.</span><span class="sxs-lookup"><span data-stu-id="873bf-113">Adding the cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and making the cmdlet private.</span></span>

- <span data-ttu-id="873bf-114">Création d’une fonction proxy qui appelle l’applet de commande existante, mais expose uniquement un jeu restreint de paramètres.</span><span class="sxs-lookup"><span data-stu-id="873bf-114">Creating a proxy function that calls the existing cmdlet, but exposes only a restricted set of parameters.</span></span>

- <span data-ttu-id="873bf-115">Ajout de la fonction de proxy à l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="873bf-115">Adding the proxy function to the initial session state.</span></span>

- <span data-ttu-id="873bf-116">Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) qui utilise l’objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="873bf-116">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="873bf-117">Appel de l’applet de commande privée et de la fonction proxy à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour illustrer l’instance d’exécution limitée.</span><span class="sxs-lookup"><span data-stu-id="873bf-117">Calling the private cmdlet and the proxy function using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to demonstrate the constrained runspace.</span></span>

## <a name="example"></a><span data-ttu-id="873bf-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="873bf-118">Example</span></span>

<span data-ttu-id="873bf-119">Cela crée une commande de proxy pour une applet de commande privée afin d’illustrer une instance d’exécution limitée.</span><span class="sxs-lookup"><span data-stu-id="873bf-119">This creates a proxy command for a private cmdlet to demonstrate a constrained runspace.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet. It has been copied
  /// verbatim from the GetProcessSample02.cs sample.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes to act on.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // if (processNames...
    } // ProcessRecord

    #endregion Cmdlet Overrides
  } // GetProcCommand

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace11
  {
    /// <summary>
    /// This shows how to use the ProxyCommand class to create a proxy
    /// command that calls an existing cmdlet, but restricts the set of
    /// available parameters. The proxy command is then added to an initial
    /// session state that is used to create a constrained runspace. This
    /// means that the user can access the cmdlet only through the proxy
    /// command.
    /// </summary>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a CommandMetadata object that describes the metadata of an
    ///    existing cmdlet.
    /// 2. Modifying the cmdlet metadata to remove a parameter of the cmdlet.
    /// 3. Adding the cmdlet to an initial session state and making it private.
    /// 4. Creating a proxy function that calls the existing cmdlet, but exposes
    ///    only a restricted set of parameters.
    /// 6. Adding the proxy function to the initial session state.
    /// 7. Calling the private cmdlet and the proxy function to demonstrate the
    ///    constrained runspace.
    /// </remarks>
    private static void Main()
    {
      // Create a default initial session state. The default initial session state
      // includes all the elements that are provided by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the initial session state.
      SessionStateCmdletEntry cmdletEntry = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(cmdletEntry);

      // Make the cmdlet private so that it is not accessible.
      cmdletEntry.Visibility = SessionStateEntryVisibility.Private;

      // Set the language mode of the initial session state to NoLanguage to
      //prevent users from using language features. Only the invocation of
      // public commands is allowed.
      iss.LanguageMode = PSLanguageMode.NoLanguage;

      // Create the proxy command using cmdlet metadata to expose the
      // get-proc cmdlet.
      CommandMetadata cmdletMetadata = new CommandMetadata(typeof(GetProcCommand));

      // Remove one of the parameters from the command metadata.
      cmdletMetadata.Parameters.Remove("Name");

      // Generate the body of a proxy function that calls the original cmdlet,
      // but does not have the removed parameter.
      string bodyOfProxyFunction = ProxyCommand.Create(cmdletMetadata);

      // Add the proxy function to the initial session state. The name of the proxy
      // function can be the same as the name of the cmdlet, but to clearly
      // demonstrate that the original cmdlet is not available a different name is
      // used for the proxy function.
      iss.Commands.Add(new SessionStateFunctionEntry("get-procProxy", bodyOfProxyFunction));

      // Create the constrained runspace using the initial session state.
      using (Runspace myRunspace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunspace.Open();

        // Call the private cmdlet to demonstrate that it is not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-proc").AddParameter("Name", "*explore*");
            powershell.Invoke();
          }
        }
        catch (CommandNotFoundException e)
        {
          System.Console.WriteLine(
                        "Invoking 'get-proc' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that the -Name parameter is
        // not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-procProxy").AddParameter("Name", "idle");
            powershell.Invoke();
          }
        }
        catch (ParameterBindingException e)
        {
          System.Console.WriteLine(
                        "\nInvoking 'get-procProxy -Name idle' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that it calls into the
        // private cmdlet to retrieve the processes.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunspace;
          powershell.AddCommand("get-procProxy");
          List<Process> processes = new List<Process>(powershell.Invoke<Process>());
          System.Console.WriteLine(
                        "\nInvoking the get-procProxy function called into the get-proc cmdlet and returned {0} processes",
                        processes.Count);
        }

        // Close the runspace to release resources.
        myRunspace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="873bf-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="873bf-120">See Also</span></span>

[<span data-ttu-id="873bf-121">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="873bf-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)