---
title: Démarrage rapide de l’hôte Windows PowerShell | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: fea6bd5ae49ecf552c583271ee9d869b1ccebae8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779401"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="0bdc7-102">Hôte Windows PowerShell - Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="0bdc7-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="0bdc7-103">Pour héberger Windows PowerShell dans votre application, vous utilisez la classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="0bdc7-104">Cette classe fournit des méthodes qui créent un pipeline de commandes, puis exécutent ces commandes dans une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="0bdc7-105">La façon la plus simple de créer une application hôte consiste à utiliser l’instance d’exécution par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="0bdc7-106">L’instance d’exécution par défaut contient toutes les commandes Windows PowerShell de base.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="0bdc7-107">Si vous souhaitez que votre application expose uniquement un sous-ensemble des commandes Windows PowerShell, vous devez créer une instance d’exécution personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="0bdc7-108">Utilisation de l’instance d’exécution par défaut</span><span class="sxs-lookup"><span data-stu-id="0bdc7-108">Using the default runspace</span></span>

<span data-ttu-id="0bdc7-109">Pour commencer, nous allons utiliser l’instance d’exécution par défaut et utiliser les méthodes de la classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) pour ajouter des commandes, des paramètres, des instructions et des scripts à un pipeline.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="0bdc7-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="0bdc7-110">AddCommand</span></span>

<span data-ttu-id="0bdc7-111">Vous utilisez la méthode [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) pour ajouter des commandes au pipeline.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="0bdc7-112">Par exemple, supposons que vous souhaitez obtenir la liste des processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="0bdc7-113">Pour exécuter cette commande, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="0bdc7-114">Créez un objet [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="0bdc7-115">Ajoutez la commande que vous souhaitez exécuter.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="0bdc7-116">Appelez la commande.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="0bdc7-117">Si vous appelez la méthode AddCommand plusieurs fois avant d’appeler la méthode [System. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , le résultat de la première commande est dirigé vers le deuxième, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="0bdc7-118">Si vous ne souhaitez pas diriger le résultat d’une commande précédente vers une commande, ajoutez-le en appelant [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="0bdc7-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="0bdc7-119">AddParameter</span></span>

<span data-ttu-id="0bdc7-120">L’exemple précédent exécute une seule commande sans aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="0bdc7-121">Vous pouvez ajouter des paramètres à la commande à l’aide de la méthode [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="0bdc7-122">Par exemple, le code suivant obtient une liste de tous les processus nommés `PowerShell` en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="0bdc7-123">Vous pouvez ajouter des paramètres supplémentaires en appelant la méthode AddParameter de façon répétée.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="0bdc7-124">Vous pouvez également ajouter un dictionnaire de noms et de valeurs de paramètres en appelant la méthode [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="0bdc7-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="0bdc7-125">AddStatement</span></span>

<span data-ttu-id="0bdc7-126">Vous pouvez simuler le traitement par lot à l’aide de la méthode [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , qui ajoute une instruction supplémentaire à la fin du pipeline.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="0bdc7-127">Le code suivant obtient une liste des processus en cours d’exécution portant le nom `PowerShell` , puis obtient la liste des services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="0bdc7-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="0bdc7-128">AddScript</span></span>

<span data-ttu-id="0bdc7-129">Vous pouvez exécuter un script existant en appelant la méthode [System. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="0bdc7-130">L’exemple suivant ajoute un script au pipeline et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="0bdc7-131">Cet exemple suppose qu’il existe déjà un script nommé `MyScript.ps1` dans un dossier nommé `D:\PSScripts` .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="0bdc7-132">Il existe également une version de la méthode AddScript qui accepte un paramètre booléen nommé `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="0bdc7-133">Si ce paramètre a la valeur `true` , le script est exécuté dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="0bdc7-134">Le code suivant exécute le script dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="0bdc7-135">Création d’une instance d’exécution personnalisée</span><span class="sxs-lookup"><span data-stu-id="0bdc7-135">Creating a custom runspace</span></span>

<span data-ttu-id="0bdc7-136">Tandis que l’instance d’exécution par défaut utilisée dans les exemples précédents charge toutes les commandes Windows PowerShell de base, vous pouvez créer une instance d’exécution personnalisée qui charge uniquement un sous-ensemble spécifié de toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="0bdc7-137">Vous pouvez le faire pour améliorer les performances (le chargement d’un plus grand nombre de commandes est un gain de performances) ou pour limiter la capacité de l’utilisateur à effectuer des opérations.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="0bdc7-138">Une instance d’exécution qui expose uniquement un nombre limité de commandes est appelée une instance d’exécution limitée.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="0bdc7-139">Pour créer une instance d’exécution avec restriction, vous utilisez les classes [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) et [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="0bdc7-140">Création d’un objet InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0bdc7-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="0bdc7-141">Pour créer une instance d’exécution personnalisée, vous devez d’abord créer un objet [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="0bdc7-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="0bdc7-142">Dans l’exemple suivant, nous utilisons [System. Management. Automation. instances d’exécution. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) pour créer une instance d’exécution après la création d’un objet InitialSessionState par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="0bdc7-143">Restriction de l’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="0bdc7-143">Constraining the runspace</span></span>

<span data-ttu-id="0bdc7-144">Dans l’exemple précédent, nous avons créé un objet [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) par défaut qui charge l’ensemble du noyau Windows PowerShell intégré.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="0bdc7-145">Nous aurions pu également appeler la méthode [System.Management.Automation.Runspaces.InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) pour créer un objet InitialSessionState qui chargera uniquement les commandes dans le composant logiciel enfichable Microsoft. PowerShell. Core.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="0bdc7-146">Pour créer une instance d’exécution plus restreinte, vous devez créer un objet InitialSessionState vide en appelant la méthode [System.Management.Automation.Runspaces.InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) , puis ajouter des commandes au InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="0bdc7-147">L’utilisation d’une instance d’exécution qui charge uniquement les commandes que vous spécifiez fournit des performances considérablement améliorées.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="0bdc7-148">Vous utilisez les méthodes de la classe [System. Management. Automation. instances d’exécution. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) pour définir des applets de commande pour l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="0bdc7-149">L’exemple suivant crée un état de session initial vide, puis définit et ajoute `Get-Command` les `Import-Module` commandes et à l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="0bdc7-150">Nous créons ensuite une instance d’exécution restreinte par cet état de session initial, puis nous exécutons les commandes dans cette instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="0bdc7-151">Créez l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="0bdc7-152">Définir et ajouter des commandes à l’état de session initial.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="0bdc7-153">Créez et ouvrez l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="0bdc7-154">Exécutez une commande et affichez le résultat.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="0bdc7-155">Une fois exécuté, le résultat de ce code se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="0bdc7-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
