---
title: Ajout et l’appel des commandes | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057652"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="12065-102">Ajout et appel de commandes</span><span class="sxs-lookup"><span data-stu-id="12065-102">Adding and invoking commands</span></span>

<span data-ttu-id="12065-103">Après avoir créé une instance d’exécution, vous pouvez ajouter des PowerShellcommands de Windows et les scripts à un pipeline et puis appelez le pipeline de manière synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="12065-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="12065-104">Création d’un pipeline</span><span class="sxs-lookup"><span data-stu-id="12065-104">Creating a pipeline</span></span>

 <span data-ttu-id="12065-105">Le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe fournit plusieurs méthodes pour ajouter des commandes, des paramètres et des scripts au pipeline.</span><span class="sxs-lookup"><span data-stu-id="12065-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="12065-106">Vous pouvez appeler le pipeline de façon synchrone en appelant une surcharge de la [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode), ou de façon asynchrone en appelant une surcharge de la [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) , puis le [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12065-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="12065-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="12065-107">AddCommand</span></span>

1. <span data-ttu-id="12065-108">Créer un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.</span><span class="sxs-lookup"><span data-stu-id="12065-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="12065-109">Ajoutez la commande que vous souhaitez exécuter.</span><span class="sxs-lookup"><span data-stu-id="12065-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="12065-110">Appelez la commande.</span><span class="sxs-lookup"><span data-stu-id="12065-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="12065-111">Si vous appelez le [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) méthode plusieurs fois avant d’appeler le [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode), le résultat de la première commande est dirigée vers le deuxième et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="12065-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="12065-112">Si vous ne souhaitez pas canalisez le résultat d’une commande à une commande précédente, ajoutez-le en appelant le [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.</span><span class="sxs-lookup"><span data-stu-id="12065-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="12065-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="12065-113">AddParameter</span></span>

 <span data-ttu-id="12065-114">L’exemple précédent exécute une commande unique sans aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="12065-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="12065-115">Vous pouvez ajouter des paramètres à la commande à l’aide de la [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) (méthode), par exemple, le code suivant obtient une liste de tous les processus qui sont nommés `PowerShell` en cours d’exécution le machine.</span><span class="sxs-lookup"><span data-stu-id="12065-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="12065-116">Vous pouvez ajouter des paramètres supplémentaires en appelant [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="12065-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="12065-117">Vous pouvez également ajouter un dictionnaire de noms de paramètres et valeurs en appelant le [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12065-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="12065-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="12065-118">AddStatement</span></span>

 <span data-ttu-id="12065-119">Vous pouvez simuler le traitement par lots à l’aide de la [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) (méthode), qui ajoute une instruction supplémentaire à la fin du pipeline, le code suivant obtient une liste des processus en cours avec le nom `PowerShell`, puis obtient la liste des services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="12065-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="12065-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="12065-120">AddScript</span></span>

 <span data-ttu-id="12065-121">Vous pouvez exécuter un script existant en appelant le [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12065-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="12065-122">L’exemple suivant ajoute un script au pipeline et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="12065-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="12065-123">Cet exemple suppose un script nommé existe déjà `MyScript.ps1` dans un dossier nommé `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="12065-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="12065-124">Il existe également une version de la [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) méthode qui accepte un paramètre booléen nommé `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="12065-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="12065-125">Si ce paramètre est défini sur `true`, puis le script est exécuté dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="12065-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="12065-126">Le code suivant exécute le script dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="12065-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="12065-127">Appel de façon synchrone un pipeline</span><span class="sxs-lookup"><span data-stu-id="12065-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="12065-128">Après avoir ajouté des éléments dans le pipeline, vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="12065-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="12065-129">Pour appeler le pipeline de manière synchrone, vous appelez une surcharge de la [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12065-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="12065-130">L’exemple suivant montre comment appeler de façon synchrone un pipeline.</span><span class="sxs-lookup"><span data-stu-id="12065-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="12065-131">Appelle de façon asynchrone un pipeline</span><span class="sxs-lookup"><span data-stu-id="12065-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="12065-132">Vous appelez un pipeline de façon asynchrone en appelant une surcharge de la [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) pour créer un [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objet, puis en appelant le [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (méthode).</span><span class="sxs-lookup"><span data-stu-id="12065-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="12065-133">L’exemple suivant montre comment appeler un pipeline de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="12065-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="12065-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12065-134">See Also</span></span>

 [<span data-ttu-id="12065-135">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="12065-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="12065-136">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="12065-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
