---
title: Exemple Runspace06 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c16324c61ee3c7123777294952999f75b2f7aef2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771989"
---
# <a name="runspace06-sample"></a><span data-ttu-id="25793-102">Exemple Runspace06</span><span class="sxs-lookup"><span data-stu-id="25793-102">Runspace06 Sample</span></span>

<span data-ttu-id="25793-103">Cet exemple montre comment ajouter un module à un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) afin que le module soit chargé lorsque l’instance d’exécution est ouverte.</span><span class="sxs-lookup"><span data-stu-id="25793-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="25793-104">Le module fournit une applet de commande Run-proc (définie par l' [exemple GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) qui est exécutée de façon synchrone à l’aide d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="25793-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="25793-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="25793-105">Requirements</span></span>

<span data-ttu-id="25793-106">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="25793-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="25793-107">Illustre le</span><span class="sxs-lookup"><span data-stu-id="25793-107">Demonstrates</span></span>

<span data-ttu-id="25793-108">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="25793-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="25793-109">Création d’un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="25793-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="25793-110">Ajout du module à l’objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="25793-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="25793-111">Création d’un objet [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) qui utilise l’objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="25793-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="25793-112">Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) qui utilise l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="25793-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="25793-113">Ajout de l’applet de commande-Process-proc du module au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="25793-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="25793-114">Exécution de la commande de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="25793-114">Running the command synchronously.</span></span>

- <span data-ttu-id="25793-115">Extraction des propriétés des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) retournés par la commande.</span><span class="sxs-lookup"><span data-stu-id="25793-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="25793-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="25793-116">Example</span></span>

<span data-ttu-id="25793-117">Cet exemple crée une instance d’exécution qui utilise un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour définir les éléments qui sont disponibles lorsque l’instance d’exécution est ouverte.</span><span class="sxs-lookup"><span data-stu-id="25793-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="25793-118">Dans cet exemple, un module qui définit une applet de commande obtenir-proc est ajouté à l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="25793-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

## <a name="see-also"></a><span data-ttu-id="25793-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25793-119">See Also</span></span>

[<span data-ttu-id="25793-120">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25793-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
