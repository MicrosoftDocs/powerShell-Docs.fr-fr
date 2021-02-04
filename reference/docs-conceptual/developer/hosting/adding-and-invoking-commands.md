---
ms.date: 09/13/2016
ms.topic: reference
title: Ajout et appel de commandes
description: Ajout et appel de commandes
ms.openlocfilehash: f539172eaf119fe5774e158c77a00276c8ba9e0a
ms.sourcegitcommit: 880b00218708724a76503000c9eca181f4e00891
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99049423"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="68b92-103">Ajout et appel de commandes</span><span class="sxs-lookup"><span data-stu-id="68b92-103">Adding and invoking commands</span></span>

<span data-ttu-id="68b92-104">Après avoir créé une instance d’exécution, vous pouvez ajouter des PowerShellcommands et des scripts Windows à un pipeline, puis appeler le pipeline de manière synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="68b92-104">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="68b92-105">Création d’un pipeline</span><span class="sxs-lookup"><span data-stu-id="68b92-105">Creating a pipeline</span></span>

<span data-ttu-id="68b92-106">La classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) fournit plusieurs méthodes permettant d’ajouter des commandes, des paramètres et des scripts au pipeline.</span><span class="sxs-lookup"><span data-stu-id="68b92-106">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="68b92-107">Vous pouvez appeler le pipeline de façon synchrone en appelant une surcharge de la méthode [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , ou de façon asynchrone en appelant une surcharge de [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) , puis la méthode [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="68b92-107">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="68b92-108">AddCommand</span><span class="sxs-lookup"><span data-stu-id="68b92-108">AddCommand</span></span>

1. <span data-ttu-id="68b92-109">Créez un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="68b92-109">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="68b92-110">Ajoutez la commande que vous souhaitez exécuter.</span><span class="sxs-lookup"><span data-stu-id="68b92-110">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="68b92-111">Appelez la commande.</span><span class="sxs-lookup"><span data-stu-id="68b92-111">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="68b92-112">Si vous appelez la méthode [System. Management. Automation. PowerShell. AddCommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) plusieurs fois avant d’appeler la méthode [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , le résultat de la première commande est dirigé vers le deuxième, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="68b92-112">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="68b92-113">Si vous ne souhaitez pas diriger le résultat d’une commande précédente vers une commande, ajoutez-le en appelant [System. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.</span><span class="sxs-lookup"><span data-stu-id="68b92-113">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="68b92-114">AddParameter</span><span class="sxs-lookup"><span data-stu-id="68b92-114">AddParameter</span></span>

 <span data-ttu-id="68b92-115">L’exemple précédent exécute une seule commande sans aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="68b92-115">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="68b92-116">Vous pouvez ajouter des paramètres à la commande à l’aide de la méthode [System. Management. Automation. PSCommand. AddParameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) . par exemple, le code suivant obtient une liste de tous les processus nommés `PowerShell` en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="68b92-116">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="68b92-117">Vous pouvez ajouter des paramètres supplémentaires en appelant [System. Management. Automation. PSCommand. AddParameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="68b92-117">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

<span data-ttu-id="68b92-118">Vous pouvez également ajouter un dictionnaire de noms et de valeurs de paramètres en appelant la méthode [System. Management. Automation. PowerShell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="68b92-118">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="68b92-119">AddStatement</span><span class="sxs-lookup"><span data-stu-id="68b92-119">AddStatement</span></span>

<span data-ttu-id="68b92-120">Vous pouvez simuler le traitement par lot à l’aide de la méthode [System. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , qui ajoute une instruction supplémentaire à la fin du pipeline. le code suivant obtient une liste des processus en cours d’exécution avec le nom `PowerShell` , puis obtient la liste des services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="68b92-120">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="68b92-121">AddScript</span><span class="sxs-lookup"><span data-stu-id="68b92-121">AddScript</span></span>

<span data-ttu-id="68b92-122">Vous pouvez exécuter un script existant en appelant la méthode [System. Management. Automation. PowerShell. addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="68b92-122">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="68b92-123">L’exemple suivant ajoute un script au pipeline et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="68b92-123">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="68b92-124">Cet exemple suppose qu’il existe déjà un script nommé `MyScript.ps1` dans un dossier nommé `D:\PSScripts` .</span><span class="sxs-lookup"><span data-stu-id="68b92-124">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1")).Invoke();
```

<span data-ttu-id="68b92-125">Il existe également une version de la méthode [System. Management. Automation. PowerShell. addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) qui accepte un paramètre booléen nommé `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="68b92-125">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="68b92-126">Si ce paramètre a la valeur `true` , le script est exécuté dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="68b92-126">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="68b92-127">Le code suivant exécute le script dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="68b92-127">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1"), true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="68b92-128">Appel d’un pipeline de façon synchrone</span><span class="sxs-lookup"><span data-stu-id="68b92-128">Invoking a pipeline synchronously</span></span>

<span data-ttu-id="68b92-129">Une fois que vous avez ajouté des éléments au pipeline, vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="68b92-129">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="68b92-130">Pour appeler le pipeline de façon synchrone, vous appelez une surcharge de la méthode [System. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="68b92-130">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="68b92-131">L’exemple suivant montre comment appeler de manière synchrone un pipeline.</span><span class="sxs-lookup"><span data-stu-id="68b92-131">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="68b92-132">Appel d’un pipeline de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="68b92-132">Invoking a pipeline asynchronously</span></span>

<span data-ttu-id="68b92-133">Vous appelez un pipeline de manière asynchrone en appelant une surcharge de [System. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) pour créer un objet [IAsyncResult](/dotnet/api/system.iasyncresult) , puis en appelant la méthode [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="68b92-133">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](/dotnet/api/system.iasyncresult) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="68b92-134">L’exemple suivant montre comment appeler un pipeline de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="68b92-134">The following example shows how to invoke a pipeline asynchronously.</span></span>

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
      IAsyncResult asyncpl = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(asyncpl))
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

## <a name="see-also"></a><span data-ttu-id="68b92-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68b92-135">See Also</span></span>

 [<span data-ttu-id="68b92-136">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="68b92-136">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="68b92-137">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="68b92-137">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
