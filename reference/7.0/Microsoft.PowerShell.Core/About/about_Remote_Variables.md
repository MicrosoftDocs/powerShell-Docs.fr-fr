---
description: Explique comment utiliser des variables locales et distantes dans des commandes distantes.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 2260e1a6ba4553cbdba0057972f491d17c61382d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208154"
---
# <a name="about-remote-variables"></a><span data-ttu-id="d724e-104">À propos des variables distantes</span><span class="sxs-lookup"><span data-stu-id="d724e-104">About Remote Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="d724e-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="d724e-105">Short description</span></span>

<span data-ttu-id="d724e-106">Explique comment utiliser des variables locales et distantes dans des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="d724e-106">Explains how to use local and remote variables in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="d724e-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="d724e-107">Long description</span></span>

<span data-ttu-id="d724e-108">Vous pouvez utiliser des variables dans les commandes que vous exécutez sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="d724e-108">You can use variables in commands that you run on remote computers.</span></span> <span data-ttu-id="d724e-109">Assignez une valeur à la variable, puis utilisez la variable à la place de la valeur.</span><span class="sxs-lookup"><span data-stu-id="d724e-109">Assign a value to the variable and then use the variable in place of the value.</span></span>

<span data-ttu-id="d724e-110">Par défaut, les variables des commandes distantes sont supposées être définies dans la session qui exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="d724e-110">By default, the variables in remote commands are assumed to be defined in the session that runs the command.</span></span> <span data-ttu-id="d724e-111">Les variables définies dans une session locale doivent être identifiées en tant que variables locales dans la commande.</span><span class="sxs-lookup"><span data-stu-id="d724e-111">Variables that are defined in a local session, must be identified as local variables in the command.</span></span>

## <a name="using-remote-variables"></a><span data-ttu-id="d724e-112">Utilisation de variables distantes</span><span class="sxs-lookup"><span data-stu-id="d724e-112">Using remote variables</span></span>

<span data-ttu-id="d724e-113">PowerShell suppose que les variables utilisées dans les commandes distantes sont définies dans la session dans laquelle la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d724e-113">PowerShell assumes that the variables used in remote commands are defined in the session in which the command runs.</span></span>

<span data-ttu-id="d724e-114">Dans cet exemple, la `$ps` variable est définie dans la session temporaire dans laquelle la `Get-WinEvent` commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d724e-114">In this example, the `$ps` variable is defined in the temporary session in which the `Get-WinEvent` command runs.</span></span>

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

<span data-ttu-id="d724e-115">Lorsque la commande s’exécute dans une session persistante, **PSSession** , la variable distante doit être définie dans cette session.</span><span class="sxs-lookup"><span data-stu-id="d724e-115">When the command runs in a persistent session, **PSSession** , the remote variable must be defined in that session.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a><span data-ttu-id="d724e-116">Utilisation de variables locales</span><span class="sxs-lookup"><span data-stu-id="d724e-116">Using local variables</span></span>

<span data-ttu-id="d724e-117">Vous pouvez utiliser des variables locales dans des commandes distantes, mais la variable doit être définie dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="d724e-117">You can use local variables in remote commands, but the variable must be defined in the local session.</span></span>

<span data-ttu-id="d724e-118">À compter de PowerShell 3,0, vous pouvez utiliser le `Using` modificateur de portée pour identifier une variable locale dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="d724e-118">Beginning in PowerShell 3.0, you can use the `Using` scope modifier to identify a local variable in a remote command.</span></span>

<span data-ttu-id="d724e-119">La syntaxe de `Using` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d724e-119">The syntax of `Using` is as follows:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="d724e-120">Dans l’exemple suivant, la `$ps` variable est créée dans la session locale, mais elle est utilisée dans la session dans laquelle la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d724e-120">In the following example, the `$ps` variable is created in the local session, but is used in the session in which the command runs.</span></span> <span data-ttu-id="d724e-121">Le `Using` modificateur de portée identifie `$ps` en tant que variable locale.</span><span class="sxs-lookup"><span data-stu-id="d724e-121">The `Using` scope modifier identifies `$ps` as a local variable.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

<span data-ttu-id="d724e-122">Le `Using` modificateur de portée peut être utilisé dans une **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="d724e-122">The `Using` scope modifier can be used in a **PSSession** .</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

<span data-ttu-id="d724e-123">Une référence de variable telle que `$using:var` s’étend à la valeur de la variable `$var` à partir du contexte de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="d724e-123">A variable reference such as `$using:var` expands to the value of variable `$var` from the caller's context.</span></span> <span data-ttu-id="d724e-124">Vous n’accédez pas à l’objet variable de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="d724e-124">You do not get access to the caller's variable object.</span></span>
<span data-ttu-id="d724e-125">Le `Using` modificateur de portée ne peut pas être utilisé pour modifier une variable locale au sein de la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="d724e-125">The `Using` scope modifier cannot be used to modify a local variable within the **PSSession** .</span></span> <span data-ttu-id="d724e-126">Par exemple, le code suivant ne fonctionne pas :</span><span class="sxs-lookup"><span data-stu-id="d724e-126">For example, the following code does not work:</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

<span data-ttu-id="d724e-127">Pour plus d’informations sur `Using` , consultez [about_Scopes](./about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="d724e-127">For more information about `Using`, see [about_Scopes](./about_Scopes.md)</span></span>

### <a name="using-splatting"></a><span data-ttu-id="d724e-128">Utilisation de la projection</span><span class="sxs-lookup"><span data-stu-id="d724e-128">Using splatting</span></span>

<span data-ttu-id="d724e-129">La projection PowerShell passe une collection de noms et de valeurs de paramètres à une commande.</span><span class="sxs-lookup"><span data-stu-id="d724e-129">PowerShell splatting passes a collection of parameter names and values to a command.</span></span> <span data-ttu-id="d724e-130">Pour plus d’informations, consultez [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="d724e-130">For more information, see [about_Splatting](about_Splatting.md).</span></span>

<span data-ttu-id="d724e-131">Dans cet exemple, la variable de projection `$Splat` est une table de hachage configurée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d724e-131">In this example, the splatting variable, `$Splat` is a hash table that is set up on the local computer.</span></span> <span data-ttu-id="d724e-132">Le `Invoke-Command` se connecte à une session de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="d724e-132">The `Invoke-Command` connects to a remote computer session.</span></span> <span data-ttu-id="d724e-133">Le **scriptblock** utilise le `Using` modificateur de portée avec le symbole at ( `@` ) pour représenter la variable dans le volet.</span><span class="sxs-lookup"><span data-stu-id="d724e-133">The **ScriptBlock** uses the `Using` scope modifier with the At (`@`) symbol to represent the splatted variable.</span></span>

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a><span data-ttu-id="d724e-134">Autres situations où le modificateur de portée’Using’est nécessaire</span><span class="sxs-lookup"><span data-stu-id="d724e-134">Other situations where the 'Using' scope modifier is needed</span></span>

<span data-ttu-id="d724e-135">Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder.</span><span class="sxs-lookup"><span data-stu-id="d724e-135">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="d724e-136">Le `Using` modificateur de portée est pris en charge dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="d724e-136">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="d724e-137">Exécuter des commandes à distance, démarré avec `Invoke-Command` à l’aide des paramètres **ComputerName** , **hostname** , **SSHConnection** ou **session** (session à distance)</span><span class="sxs-lookup"><span data-stu-id="d724e-137">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="d724e-138">Travaux en arrière-plan, démarrés avec `Start-Job` (session hors processus)</span><span class="sxs-lookup"><span data-stu-id="d724e-138">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="d724e-139">Travaux de thread, démarrés via `Start-ThreadJob` ou `ForEach-Object -Parallel` (session de threads distincte)</span><span class="sxs-lookup"><span data-stu-id="d724e-139">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="d724e-140">Selon le contexte, les valeurs des variables incorporées sont soit des copies indépendantes des données dans la portée de l’appelant, soit des références à celles-ci.</span><span class="sxs-lookup"><span data-stu-id="d724e-140">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="d724e-141">Dans les sessions à distance et hors processus, il s’agit toujours de copies indépendantes.</span><span class="sxs-lookup"><span data-stu-id="d724e-141">In remote and out-of-process sessions, they are always independent copies.</span></span> <span data-ttu-id="d724e-142">Dans les sessions de thread, elles sont passées par référence.</span><span class="sxs-lookup"><span data-stu-id="d724e-142">In thread sessions, they are passed by reference.</span></span>

## <a name="serialization-of-variable-values"></a><span data-ttu-id="d724e-143">Sérialisation de valeurs de variables</span><span class="sxs-lookup"><span data-stu-id="d724e-143">Serialization of variable values</span></span>

<span data-ttu-id="d724e-144">Les commandes exécutées à distance et les travaux en arrière-plan s’exécutent hors processus.</span><span class="sxs-lookup"><span data-stu-id="d724e-144">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="d724e-145">Les sessions hors processus utilisent la sérialisation et la désérialisation basées sur XML pour rendre les valeurs des variables disponibles dans les limites du processus.</span><span class="sxs-lookup"><span data-stu-id="d724e-145">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="d724e-146">Le processus de sérialisation convertit des objets en **PSObject** qui contient les propriétés des objets d’origine, mais pas ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="d724e-146">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="d724e-147">Pour un ensemble limité de types, la désérialisation réalimente les objets dans le type d’origine.</span><span class="sxs-lookup"><span data-stu-id="d724e-147">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="d724e-148">L’objet réalimenté est une copie de l’instance d’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="d724e-148">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="d724e-149">Il a les propriétés et les méthodes de type.</span><span class="sxs-lookup"><span data-stu-id="d724e-149">It has the type properties and methods.</span></span> <span data-ttu-id="d724e-150">Pour les types simples, tels que **System. version** , la copie est exacte.</span><span class="sxs-lookup"><span data-stu-id="d724e-150">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="d724e-151">Pour les types complexes, la copie n’est pas parfaite.</span><span class="sxs-lookup"><span data-stu-id="d724e-151">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="d724e-152">Par exemple, les objets de certificat réalimentés n’incluent pas la clé privée.</span><span class="sxs-lookup"><span data-stu-id="d724e-152">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="d724e-153">Les instances de tous les autres types sont des instances **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="d724e-153">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="d724e-154">La propriété **PSTypeNames** contient le nom du type d’origine préfixé avec **désérialisé** , par exemple, **Deserialized.SysTEM. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="d724e-154">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

## <a name="using-local-variables-with-argumentlist-parameter"></a><span data-ttu-id="d724e-155">Utilisation de variables locales avec le paramètre **argumentlist**</span><span class="sxs-lookup"><span data-stu-id="d724e-155">Using local variables with **ArgumentList** parameter</span></span>

<span data-ttu-id="d724e-156">Vous pouvez utiliser des variables locales dans une commande à distance en définissant les paramètres de la commande distante et en utilisant le paramètre **argumentlist** de l' `Invoke-Command` applet de commande pour spécifier la variable locale comme valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="d724e-156">You can use local variables in a remote command by defining parameters for the remote command and using the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

- <span data-ttu-id="d724e-157">Utilisez le `param` mot clé pour définir les paramètres de la commande distante.</span><span class="sxs-lookup"><span data-stu-id="d724e-157">Use the `param` keyword to define parameters for the remote command.</span></span> <span data-ttu-id="d724e-158">Les noms de paramètres sont des espaces réservés qui n’ont pas besoin de correspondre au nom de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="d724e-158">The parameter names are placeholders that don't need to match the local variable's name.</span></span>

- <span data-ttu-id="d724e-159">Utilisez les paramètres définis par le `param` mot clé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="d724e-159">Use the parameters defined by the `param` keyword in the command.</span></span>

- <span data-ttu-id="d724e-160">Utilisez le paramètre **argumentlist** de l' `Invoke-Command` applet de commande pour spécifier la variable locale comme valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="d724e-160">Use the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

<span data-ttu-id="d724e-161">Par exemple, les commandes suivantes définissent la `$ps` variable dans la session locale, puis l’utilisent dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="d724e-161">For example, the following commands define the `$ps` variable in the local session and then use it in a remote command.</span></span> <span data-ttu-id="d724e-162">La commande utilise `$log` comme nom de paramètre et la variable locale, `$ps` , comme valeur.</span><span class="sxs-lookup"><span data-stu-id="d724e-162">The command uses `$log` as the parameter name and the local variable, `$ps`, as its value.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a><span data-ttu-id="d724e-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d724e-163">See also</span></span>

[<span data-ttu-id="d724e-164">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="d724e-164">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="d724e-165">about_Remote</span><span class="sxs-lookup"><span data-stu-id="d724e-165">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="d724e-166">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="d724e-166">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="d724e-167">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="d724e-167">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="d724e-168">about_Variables</span><span class="sxs-lookup"><span data-stu-id="d724e-168">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="d724e-169">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="d724e-169">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="d724e-170">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="d724e-170">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="d724e-171">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d724e-171">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="d724e-172">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="d724e-172">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

[<span data-ttu-id="d724e-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d724e-173">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
