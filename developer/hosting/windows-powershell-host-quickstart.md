---
title: Guide de démarrage rapide de Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530622"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="408a1-102">Hôte Windows PowerShell - Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="408a1-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="408a1-103">Pour héberger Windows PowerShell dans votre application, vous utilisez le [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe.</span><span class="sxs-lookup"><span data-stu-id="408a1-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="408a1-104">Cette classe fournit des méthodes qui de créer un pipeline de commandes, puis exécutez ces commandes dans une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="408a1-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="408a1-105">Pour créer une application hôte, le plus simple consiste à utiliser l’instance d’exécution par défaut.</span><span class="sxs-lookup"><span data-stu-id="408a1-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="408a1-106">L’instance d’exécution par défaut contient toutes les commandes Windows PowerShell core.</span><span class="sxs-lookup"><span data-stu-id="408a1-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="408a1-107">Si vous souhaitez que votre application pour exposer uniquement un sous-ensemble des commandes Windows PowerShell, vous devez créer une instance d’exécution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="408a1-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="408a1-108">À l’aide de l’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="408a1-108">Using the default runspace</span></span>

<span data-ttu-id="408a1-109">Pour commencer, nous allons utiliser l’instance d’exécution par défaut et utiliser les méthodes de la [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe pour ajouter des commandes, des paramètres, des instructions et des scripts à un pipeline.</span><span class="sxs-lookup"><span data-stu-id="408a1-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="408a1-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="408a1-110">AddCommand</span></span>

<span data-ttu-id="408a1-111">Vous utilisez le [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) méthode pour ajouter des commandes au pipeline.</span><span class="sxs-lookup"><span data-stu-id="408a1-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="408a1-112">Par exemple, supposons que vous souhaitez obtenir la liste des processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="408a1-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="408a1-113">La façon d’exécuter cette commande est la suivante.</span><span class="sxs-lookup"><span data-stu-id="408a1-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="408a1-114">Créer un [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objet.</span><span class="sxs-lookup"><span data-stu-id="408a1-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="408a1-115">Ajoutez la commande que vous souhaitez exécuter.</span><span class="sxs-lookup"><span data-stu-id="408a1-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="408a1-116">Appelez la commande.</span><span class="sxs-lookup"><span data-stu-id="408a1-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="408a1-117">Si vous appelez la méthode AddCommand plusieurs fois avant d’appeler le [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode), le résultat de la première commande est dirigée vers le deuxième et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="408a1-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="408a1-118">Si vous ne souhaitez pas canalisez le résultat d’une commande à une commande précédente, ajoutez-le en appelant le [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.</span><span class="sxs-lookup"><span data-stu-id="408a1-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="408a1-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="408a1-119">AddParameter</span></span>

<span data-ttu-id="408a1-120">L’exemple précédent exécute une commande unique sans aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="408a1-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="408a1-121">Vous pouvez ajouter des paramètres à la commande à l’aide de la [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) (méthode).</span><span class="sxs-lookup"><span data-stu-id="408a1-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="408a1-122">Par exemple, le code suivant obtient une liste de tous les processus qui sont nommés `PowerShell` en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="408a1-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="408a1-123">Vous pouvez ajouter des paramètres supplémentaires en appelant la méthode de AddParameter à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="408a1-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="408a1-124">Vous pouvez également ajouter un dictionnaire de noms de paramètres et valeurs en appelant le [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (méthode).</span><span class="sxs-lookup"><span data-stu-id="408a1-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="408a1-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="408a1-125">AddStatement</span></span>

<span data-ttu-id="408a1-126">Vous pouvez simuler le traitement par lots à l’aide de la [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) (méthode), qui ajoute une instruction supplémentaire à la fin du pipeline.</span><span class="sxs-lookup"><span data-stu-id="408a1-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="408a1-127">Le code suivant obtient une liste des processus en cours avec le nom `PowerShell`, puis obtient la liste des services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="408a1-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="408a1-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="408a1-128">AddScript</span></span>

<span data-ttu-id="408a1-129">Vous pouvez exécuter un script existant en appelant le [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (méthode).</span><span class="sxs-lookup"><span data-stu-id="408a1-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="408a1-130">L’exemple suivant ajoute un script au pipeline et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="408a1-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="408a1-131">Cet exemple suppose un script nommé existe déjà `MyScript.ps1` dans un dossier nommé `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="408a1-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="408a1-132">Il existe également une version de la méthode AddScript qui accepte un paramètre booléen nommé `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="408a1-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="408a1-133">Si ce paramètre est défini sur `true`, puis le script est exécuté dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="408a1-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="408a1-134">Le code suivant exécute le script dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="408a1-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="408a1-135">Création d’une instance d’exécution personnalisée</span><span class="sxs-lookup"><span data-stu-id="408a1-135">Creating a custom runspace</span></span>

<span data-ttu-id="408a1-136">Tandis que l’instance d’exécution par défaut utilisé dans les exemples précédents charge de toutes les commandes Windows PowerShell core, vous pouvez créer une instance d’exécution personnalisée qui charge uniquement un sous-ensemble spécifié de toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="408a1-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="408a1-137">Vous pouvez souhaiter procéder ainsi pour améliorer les performances (le chargement d’un plus grand nombre de commandes est un gain de performances), ou pour limiter la capacité de l’utilisateur à effectuer des opérations.</span><span class="sxs-lookup"><span data-stu-id="408a1-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="408a1-138">Une instance d’exécution qui expose uniquement un nombre limité de commandes est appelée une instance d’exécution contrainte.</span><span class="sxs-lookup"><span data-stu-id="408a1-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="408a1-139">Pour créer une instance d’exécution limitée, vous utilisez le [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) et [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span><span class="sxs-lookup"><span data-stu-id="408a1-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="408a1-140">Création d’un objet InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="408a1-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="408a1-141">Pour créer une instance d’exécution personnalisée, vous devez d’abord créer un [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet.</span><span class="sxs-lookup"><span data-stu-id="408a1-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="408a1-142">Dans l’exemple suivant, nous utilisons le [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) pour créer une instance d’exécution après la création d’un objet de InitialSessionState par défaut.</span><span class="sxs-lookup"><span data-stu-id="408a1-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="408a1-143">Restriction de l’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="408a1-143">Constraining the runspace</span></span>

<span data-ttu-id="408a1-144">Dans l’exemple précédent, nous avons créé une valeur par défaut [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet qui charge tous des principales intégré Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="408a1-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="408a1-145">Nous pouvons également avoir appelé la [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) méthode pour créer un objet InitialSessionState qui charge uniquement les commandes dans le Microsoft.PowerShell.Core composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="408a1-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="408a1-146">Pour créer une instance d’exécution plus limité, vous devez créer un objet InitialSessionState vide en appelant le [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) (méthode), puis ajoutez les commandes pour le InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="408a1-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="408a1-147">À l’aide d’une instance d’exécution qui charge uniquement les commandes que vous spécifiez fournit des performances significativement accrues.</span><span class="sxs-lookup"><span data-stu-id="408a1-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="408a1-148">Vous utilisez les méthodes de la [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe pour définir des applets de commande pour l’état de session initiale.</span><span class="sxs-lookup"><span data-stu-id="408a1-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="408a1-149">L’exemple suivant crée un état de session initiale vide, puis définit et ajoute le `Get-Command` et `Import-Module` commandes à l’état de session initiale.</span><span class="sxs-lookup"><span data-stu-id="408a1-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="408a1-150">Nous avons créer une instance d’exécution limitée par cet état de session initial et que vous exécutez les commandes dans cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="408a1-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="408a1-151">Créer l’état de session initiale.</span><span class="sxs-lookup"><span data-stu-id="408a1-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="408a1-152">Définir et ajouter des commandes à l’état de session initiale.</span><span class="sxs-lookup"><span data-stu-id="408a1-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="408a1-153">Créez et ouvrez l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="408a1-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="408a1-154">Exécuter une commande et afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="408a1-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="408a1-155">Lors de l’exécution, la sortie de ce code se présentera comme suit.</span><span class="sxs-lookup"><span data-stu-id="408a1-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
