---
title: Exemple de Runspace03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 39495f7813aecf5d0210866fc11f94557fdb0cd9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058995"
---
# <a name="runspace03-sample"></a><span data-ttu-id="0c090-102">Exemple Runspace03</span><span class="sxs-lookup"><span data-stu-id="0c090-102">Runspace03 Sample</span></span>

<span data-ttu-id="0c090-103">Cet exemple montre comment utiliser le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe pour exécuter un script de façon synchrone et comment gérer les erreurs sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c090-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="0c090-104">Le script reçoit une liste de noms de processus et récupère ensuite ces processus.</span><span class="sxs-lookup"><span data-stu-id="0c090-104">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="0c090-105">Le résultat du script, notamment les erreurs sans fin d’exécution qui ont été générées pendant l’exécution du script, s’affiche dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="0c090-105">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c090-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0c090-106">Requirements</span></span>

<span data-ttu-id="0c090-107">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="0c090-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0c090-108">Montre</span><span class="sxs-lookup"><span data-stu-id="0c090-108">Demonstrates</span></span>

<span data-ttu-id="0c090-109">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="0c090-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0c090-110">Création d’un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet pour exécuter un script.</span><span class="sxs-lookup"><span data-stu-id="0c090-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="0c090-111">Ajout d’un script au pipeline de la [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.</span><span class="sxs-lookup"><span data-stu-id="0c090-111">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="0c090-112">Passage à des objets d’entrée pour le script du programme appelant.</span><span class="sxs-lookup"><span data-stu-id="0c090-112">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="0c090-113">Exécuter le script de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="0c090-113">Running the script synchronously.</span></span>

- <span data-ttu-id="0c090-114">À l’aide de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objets pour extraire et afficher les propriétés à partir des objets retournés par le script.</span><span class="sxs-lookup"><span data-stu-id="0c090-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="0c090-115">Récupération et affichage des enregistrements d’erreur qui ont été générés lors de l’exécution du script.</span><span class="sxs-lookup"><span data-stu-id="0c090-115">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="0c090-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c090-116">Example</span></span>

<span data-ttu-id="0c090-117">Cet exemple exécute un script de façon synchrone dans l’instance d’exécution par défaut fourni par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c090-117">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="0c090-118">La sortie du script et les erreurs sans fin d’exécution qui ont été générées sont affichés dans une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="0c090-118">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="0c090-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c090-119">See Also</span></span>

[<span data-ttu-id="0c090-120">Écriture d’une Application hôte PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="0c090-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)