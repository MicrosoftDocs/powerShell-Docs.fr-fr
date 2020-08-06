---
title: Exemple Runspace04 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 73f48c797a4ce9bf4bc78ff34abb5efa41cda121
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779503"
---
# <a name="runspace04-sample"></a><span data-ttu-id="6a75a-102">Exemple Runspace04</span><span class="sxs-lookup"><span data-stu-id="6a75a-102">Runspace04 Sample</span></span>

<span data-ttu-id="6a75a-103">Cet exemple montre comment utiliser la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) pour exécuter des commandes et comment intercepter les erreurs de fin levées lors de l’exécution des commandes.</span><span class="sxs-lookup"><span data-stu-id="6a75a-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="6a75a-104">Les commandes exécutées sont au nombre de deux, et la dernière se voit transmettre un argument de paramètre non valide.</span><span class="sxs-lookup"><span data-stu-id="6a75a-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="6a75a-105">Par conséquent, aucun objet n’est retourné et une erreur avec fin d’exécution est levée.</span><span class="sxs-lookup"><span data-stu-id="6a75a-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a75a-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6a75a-106">Requirements</span></span>

<span data-ttu-id="6a75a-107">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="6a75a-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6a75a-108">Illustre le</span><span class="sxs-lookup"><span data-stu-id="6a75a-108">Demonstrates</span></span>

<span data-ttu-id="6a75a-109">Cet exemple illustre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6a75a-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="6a75a-110">Création d’un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="6a75a-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="6a75a-111">Ajout de commandes au pipeline de l’objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="6a75a-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="6a75a-112">Ajout d’arguments de paramètre au pipeline.</span><span class="sxs-lookup"><span data-stu-id="6a75a-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="6a75a-113">Appel des commandes de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="6a75a-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="6a75a-114">À l’aide des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) pour extraire et afficher les propriétés des objets retournés par les commandes.</span><span class="sxs-lookup"><span data-stu-id="6a75a-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="6a75a-115">Récupération et affichage des enregistrements d’erreurs qui ont été générés pendant l’exécution des commandes.</span><span class="sxs-lookup"><span data-stu-id="6a75a-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="6a75a-116">Interception et affichage des exceptions de fin levées par les commandes.</span><span class="sxs-lookup"><span data-stu-id="6a75a-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="6a75a-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a75a-117">Example</span></span>

<span data-ttu-id="6a75a-118">Cet exemple exécute des commandes de façon synchrone dans l’instance d’exécution par défaut fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a75a-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="6a75a-119">La dernière commande lève une erreur de fin, car un argument de paramètre non valide est passé à la commande.</span><span class="sxs-lookup"><span data-stu-id="6a75a-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="6a75a-120">L’erreur de fin est interceptée et affichée.</span><span class="sxs-lookup"><span data-stu-id="6a75a-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
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
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="6a75a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a75a-121">See Also</span></span>

[<span data-ttu-id="6a75a-122">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a75a-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
