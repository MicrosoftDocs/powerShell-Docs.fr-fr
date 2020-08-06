---
title: Exemple Runspace10 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4d858c432c6221f2347f6de664d1e4ee299f5801
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784943"
---
# <a name="runspace10-sample"></a><span data-ttu-id="ce849-102">Exemple Runspace10</span><span class="sxs-lookup"><span data-stu-id="ce849-102">Runspace10 Sample</span></span>

<span data-ttu-id="ce849-103">Cet exemple montre comment créer un état de session initial par défaut, comment ajouter une applet de commande à l' [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), comment créer une instance d’exécution qui utilise l’état de session initial et comment exécuter la commande à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="ce849-103">This sample shows how to create a default initial session state, how to add a cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), how to create a runspace that uses the initial session state, and how to run the command by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="ce849-104">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce849-104">Requirements</span></span>

<span data-ttu-id="ce849-105">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="ce849-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ce849-106">Illustre le</span><span class="sxs-lookup"><span data-stu-id="ce849-106">Demonstrates</span></span>

<span data-ttu-id="ce849-107">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="ce849-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ce849-108">Création d’un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="ce849-108">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="ce849-109">Ajout d’une applet de commande (définie par l’application hôte) à l’objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="ce849-109">Adding a cmdlet (defined by the Host application) to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="ce849-110">Création d’un objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) qui utilise l’objet.</span><span class="sxs-lookup"><span data-stu-id="ce849-110">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the object.</span></span>

- <span data-ttu-id="ce849-111">Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) qui utilise l’objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="ce849-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="ce849-112">Ajout de la commande au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="ce849-112">Adding the command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="ce849-113">Extraction des propriétés des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) retournés par la commande.</span><span class="sxs-lookup"><span data-stu-id="ce849-113">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="ce849-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce849-114">Example</span></span>

<span data-ttu-id="ce849-115">Cet exemple crée une instance d’exécution qui utilise un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour définir les éléments qui sont disponibles lorsque l’instance d’exécution est ouverte.</span><span class="sxs-lookup"><span data-stu-id="ce849-115">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="ce849-116">Dans cet exemple, l’applet de commande « obtenir-proc » (définie par l’application hôte) est ajoutée à l’état de session initial, et l’applet de commande est exécutée de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="ce849-116">In this sample, the Get-Proc cmdlet (defined by the Host application) is added to the initial session state, and the cmdlet is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ce849-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce849-117">See Also</span></span>

[<span data-ttu-id="ce849-118">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ce849-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
