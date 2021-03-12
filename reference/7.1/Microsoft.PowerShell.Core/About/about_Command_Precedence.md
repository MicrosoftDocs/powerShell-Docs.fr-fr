---
description: Décrit comment PowerShell détermine la commande à exécuter.
Locale: en-US
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 30822ae18e7edfab2938c4fd697955881f64536d
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196189"
---
# <a name="about-command-precedence"></a><span data-ttu-id="ee835-103">À propos de la priorité des commandes</span><span class="sxs-lookup"><span data-stu-id="ee835-103">About Command Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="ee835-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="ee835-104">Short description</span></span>
<span data-ttu-id="ee835-105">Décrit comment PowerShell détermine la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ee835-105">Describes how PowerShell determines which command to run.</span></span>

## <a name="long-description"></a><span data-ttu-id="ee835-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="ee835-106">Long description</span></span>

<span data-ttu-id="ee835-107">La priorité des commandes décrit la façon dont PowerShell détermine la commande à exécuter lorsqu’une session contient plusieurs commandes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ee835-107">Command precedence describes how PowerShell determines which command to run when a session contains more than one command with the same name.</span></span> <span data-ttu-id="ee835-108">Les commandes d’une session peuvent être masquées ou remplacées par des commandes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ee835-108">Commands within a session can be hidden or replaced by commands with the same name.</span></span> <span data-ttu-id="ee835-109">Cet article explique comment exécuter des commandes masquées et comment éviter les conflits de noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="ee835-109">This article shows you how to run hidden commands and how to avoid command-name conflicts.</span></span>

## <a name="command-precedence"></a><span data-ttu-id="ee835-110">Priorité des commandes</span><span class="sxs-lookup"><span data-stu-id="ee835-110">Command precedence</span></span>

<span data-ttu-id="ee835-111">Lorsqu’une session PowerShell inclut plusieurs commandes portant le même nom, PowerShell détermine la commande à exécuter à l’aide des règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="ee835-111">When a PowerShell session includes more than one command that has the same name, PowerShell determines which command to run by using the following rules.</span></span>

<span data-ttu-id="ee835-112">Si vous spécifiez le chemin d’accès à une commande, PowerShell exécute la commande à l’emplacement spécifié par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ee835-112">If you specify the path to a command, PowerShell runs the command at the location specified by the path.</span></span>

<span data-ttu-id="ee835-113">Par exemple, la commande suivante exécute le script FindDocs.ps1 dans le répertoire « C : \\ TechDocs » :</span><span class="sxs-lookup"><span data-stu-id="ee835-113">For example, the following command runs the FindDocs.ps1 script in the "C:\\TechDocs" directory:</span></span>

```
C:\TechDocs\FindDocs.ps1
```

<span data-ttu-id="ee835-114">En tant que fonctionnalité de sécurité, PowerShell n’exécute pas les commandes exécutables (natives), y compris les scripts PowerShell, sauf si la commande se trouve dans un chemin d’accès qui est listé dans la variable d’environnement PATH `$env:path` ou si vous spécifiez le chemin d’accès au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="ee835-114">As a security feature, PowerShell does not run executable (native) commands, including PowerShell scripts, unless the command is located in a path that is listed in the Path environment variable `$env:path` or unless you specify the path to the script file.</span></span>

<span data-ttu-id="ee835-115">Pour exécuter un script qui se trouve dans le répertoire actif, spécifiez le chemin d’accès complet ou tapez un point `.\` pour représenter le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ee835-115">To run a script that is in the current directory, specify the full path, or type a dot `.\` to represent the current directory.</span></span>

<span data-ttu-id="ee835-116">Par exemple, pour exécuter le fichier FindDocs.ps1 dans le répertoire actif, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee835-116">For example, to run the FindDocs.ps1 file in the current directory, type:</span></span>

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a><span data-ttu-id="ee835-117">Utilisation de caractères génériques dans l’exécution</span><span class="sxs-lookup"><span data-stu-id="ee835-117">Using wildcards in execution</span></span>

<span data-ttu-id="ee835-118">Vous pouvez utiliser des caractères génériques dans l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="ee835-118">You may use wildcards in command execution.</span></span> <span data-ttu-id="ee835-119">L’utilisation de caractères génériques est également appelée *globbing*.</span><span class="sxs-lookup"><span data-stu-id="ee835-119">Using wildcard characters is also known as *globbing*.</span></span>

<span data-ttu-id="ee835-120">PowerShell exécute un fichier avec une correspondance de caractère générique, avant qu’un littéral ne corresponde.</span><span class="sxs-lookup"><span data-stu-id="ee835-120">PowerShell executes a file that has a wildcard match, before a literal match.</span></span>

<span data-ttu-id="ee835-121">Prenons l’exemple d’un répertoire contenant les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="ee835-121">For example, consider a directory with the following files:</span></span>

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

<span data-ttu-id="ee835-122">Les deux fichiers de script ont le même contenu : `$MyInvocation.MyCommand.Path` .</span><span class="sxs-lookup"><span data-stu-id="ee835-122">Both script files have the same content: `$MyInvocation.MyCommand.Path`.</span></span>
<span data-ttu-id="ee835-123">Cette commande affiche le nom du script qui est appelé.</span><span class="sxs-lookup"><span data-stu-id="ee835-123">This command displays the name of the script that is invoked.</span></span>

<span data-ttu-id="ee835-124">Lorsque vous exécutez `[a1].ps1` , le fichier `a.ps1` est exécuté même si le fichier `[a1].ps1` est une correspondance littérale.</span><span class="sxs-lookup"><span data-stu-id="ee835-124">When you run `[a1].ps1`, the file `a.ps1` is executed even though the file `[a1].ps1` is a literal match.</span></span>

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

<span data-ttu-id="ee835-125">À présent, nous allons supprimer le `a.ps1` fichier et tenter de l’exécuter à nouveau.</span><span class="sxs-lookup"><span data-stu-id="ee835-125">Now let's delete the `a.ps1` file and attempt to run it again.</span></span>

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

<span data-ttu-id="ee835-126">Vous pouvez voir à partir de la sortie qui `[a1].ps1` s’exécute cette fois, car la correspondance littérale est la seule correspondance de fichier pour ce modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="ee835-126">You can see from the output that `[a1].ps1` runs this time because the literal match is the only file match for that wildcard pattern.</span></span>

<span data-ttu-id="ee835-127">Pour plus d’informations sur la façon dont PowerShell utilise les caractères génériques, consultez [about_Wildcards](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="ee835-127">For more information about how PowerShell uses wildcards, see [about_Wildcards](about_Wildcards.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ee835-128">Pour limiter la recherche à un chemin d’accès relatif, vous devez faire précéder le nom du script du `.\` chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ee835-128">To limit the search to a relative path, you must prefix the script name with the `.\` path.</span></span> <span data-ttu-id="ee835-129">Cela limite la recherche de commandes aux fichiers dans ce chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="ee835-129">This limits the search for commands to files in that relative path.</span></span> <span data-ttu-id="ee835-130">Sans ce préfixe, d’autres syntaxes PowerShell peuvent entrer en conflit et il existe peu de garantie que le fichier sera trouvé.</span><span class="sxs-lookup"><span data-stu-id="ee835-130">Without this prefix, other PowerShell syntax may conflict and there are few guarantees that the file will be found.</span></span>

<span data-ttu-id="ee835-131">Si vous ne spécifiez pas de chemin d’accès, PowerShell utilise l’ordre de priorité suivant lorsqu’il exécute des commandes pour tous les éléments chargés dans la session active :</span><span class="sxs-lookup"><span data-stu-id="ee835-131">If you do not specify a path, PowerShell uses the following precedence order when it runs commands for all items loaded in the current session:</span></span>

  1. <span data-ttu-id="ee835-132">Alias</span><span class="sxs-lookup"><span data-stu-id="ee835-132">Alias</span></span>
  2. <span data-ttu-id="ee835-133">Fonction</span><span class="sxs-lookup"><span data-stu-id="ee835-133">Function</span></span>
  3. <span data-ttu-id="ee835-134">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="ee835-134">Cmdlet</span></span>
  4. <span data-ttu-id="ee835-135">Fichiers exécutables externes (programmes et scripts non-PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ee835-135">External executable files (programs and non-PowerShell scripts)</span></span>

<span data-ttu-id="ee835-136">Par conséquent, si vous tapez « help », PowerShell recherche d’abord un alias nommé `help` , puis une fonction nommée `Help` et enfin une applet de commande nommée `Help` .</span><span class="sxs-lookup"><span data-stu-id="ee835-136">Therefore, if you type "help", PowerShell first looks for an alias named `help`, then a function named `Help`, and finally a cmdlet named `Help`.</span></span> <span data-ttu-id="ee835-137">Elle exécute le premier `help` élément qu’elle trouve.</span><span class="sxs-lookup"><span data-stu-id="ee835-137">It runs the first `help` item that it finds.</span></span>

<span data-ttu-id="ee835-138">Par exemple, si votre session contient une applet de commande et une fonction, toutes deux nommées `Get-Map` , lorsque vous tapez `Get-Map` , PowerShell exécute la fonction.</span><span class="sxs-lookup"><span data-stu-id="ee835-138">For example, if your session contains a cmdlet and a function, both named `Get-Map`, when you type `Get-Map`, PowerShell runs the function.</span></span>

> [!NOTE]
> <span data-ttu-id="ee835-139">Cela s’applique uniquement aux commandes chargées.</span><span class="sxs-lookup"><span data-stu-id="ee835-139">This only applies to loaded commands.</span></span> <span data-ttu-id="ee835-140">S’il existe un `build` exécutable et un alias `build` pour une fonction avec le nom de `Invoke-Build` à l’intérieur d’un module qui n’est pas chargé dans la session active, PowerShell exécute le `build` fichier exécutable à la place.</span><span class="sxs-lookup"><span data-stu-id="ee835-140">If there is a `build` executable and an Alias `build` for a function with the name of `Invoke-Build` inside a module that is not loaded into the current session, PowerShell runs the `build` executable instead.</span></span> <span data-ttu-id="ee835-141">Il ne charge pas les modules automatiquement s’il trouve l’exécutable externe dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="ee835-141">It does not auto-load modules if it finds the external executable in this case.</span></span> <span data-ttu-id="ee835-142">C’est uniquement lorsqu’aucun exécutable externe n’est trouvé qu’un alias, une fonction ou une applet de commande avec le nom donné est appelé, ce qui déclenche le chargement automatique de son module.</span><span class="sxs-lookup"><span data-stu-id="ee835-142">It is only when no external executable is found that an alias, function, or cmdlet with the given name is invoked, thereby triggering auto-loading of its module.</span></span>

<span data-ttu-id="ee835-143">Lorsque la session contient des éléments du même type qui ont le même nom, PowerShell exécute l’élément le plus récent.</span><span class="sxs-lookup"><span data-stu-id="ee835-143">When the session contains items of the same type that have the same name, PowerShell runs the newer item.</span></span>

<span data-ttu-id="ee835-144">Par exemple, si vous importez une autre `Get-Date` applet de commande à partir d’un module, lorsque vous tapez `Get-Date` , PowerShell exécute la version importée sur le natif.</span><span class="sxs-lookup"><span data-stu-id="ee835-144">For example, if you import another `Get-Date` cmdlet from a module, when you type `Get-Date`, PowerShell runs the imported version over the native one.</span></span>

## <a name="hidden-and-replaced-items"></a><span data-ttu-id="ee835-145">Éléments masqués et remplacés</span><span class="sxs-lookup"><span data-stu-id="ee835-145">Hidden and replaced items</span></span>

<span data-ttu-id="ee835-146">À la suite de ces règles, les éléments peuvent être remplacés ou masqués par des éléments portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ee835-146">As a result of these rules, items can be replaced or hidden by items with the same name.</span></span>

<span data-ttu-id="ee835-147">Les éléments sont « masqués » ou « occultés » si vous pouvez toujours accéder à l’élément d’origine, par exemple en qualifiant le nom de l’élément avec un nom de module ou de composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="ee835-147">Items are "hidden" or "shadowed" if you can still access the original item, such as by qualifying the item name with a module or snap-in name.</span></span>

<span data-ttu-id="ee835-148">Par exemple, si vous importez une fonction qui porte le même nom qu’une applet de commande dans la session, l’applet de commande est masquée (mais pas remplacée), car elle a été importée à partir d’un composant logiciel enfichable ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="ee835-148">For example, if you import a function that has the same name as a cmdlet in the session, the cmdlet is hidden (but not replaced) because it was imported from a snap-in or module.</span></span>

<span data-ttu-id="ee835-149">Les éléments sont « remplacés » ou « remplacés » si vous ne pouvez plus accéder à l’élément d’origine.</span><span class="sxs-lookup"><span data-stu-id="ee835-149">Items are "replaced" or "overwritten" if you can no longer access the original item.</span></span>

<span data-ttu-id="ee835-150">Par exemple, si vous importez une variable qui porte le même nom qu’une variable de la session, la variable d’origine est remplacée et n’est plus accessible.</span><span class="sxs-lookup"><span data-stu-id="ee835-150">For example, if you import a variable that has the same name as a variable in the session, the original variable is replaced and is no longer accessible.</span></span>
<span data-ttu-id="ee835-151">Vous ne pouvez pas qualifier une variable avec un nom de module.</span><span class="sxs-lookup"><span data-stu-id="ee835-151">You cannot qualify a variable with a module name.</span></span>

<span data-ttu-id="ee835-152">De même, si vous tapez une fonction sur la ligne de commande, puis que vous importez une fonction portant le même nom, la fonction d’origine est remplacée et n’est plus accessible.</span><span class="sxs-lookup"><span data-stu-id="ee835-152">Also, if you type a function at the command line and then import a function with the same name, the original function is replaced and is no longer accessible.</span></span>

### <a name="finding-hidden-commands"></a><span data-ttu-id="ee835-153">Recherche de commandes masquées</span><span class="sxs-lookup"><span data-stu-id="ee835-153">Finding hidden commands</span></span>

<span data-ttu-id="ee835-154">Le paramètre **All** de l’applet de [commande obtenir-Command](xref:Microsoft.PowerShell.Core.Get-Command) obtient toutes les commandes portant le nom spécifié, même si elles sont masquées ou remplacées.</span><span class="sxs-lookup"><span data-stu-id="ee835-154">The **All** parameter of the [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet gets all commands with the specified name, even if they are hidden or replaced.</span></span> <span data-ttu-id="ee835-155">À compter de PowerShell 3,0, par défaut, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="ee835-155">Beginning in PowerShell 3.0, by default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="ee835-156">Dans les exemples suivants, la session comprend une `Get-Date` fonction et une applet de commande [« obtenir-date »](xref:Microsoft.PowerShell.Utility.Get-Date) .</span><span class="sxs-lookup"><span data-stu-id="ee835-156">In the following examples, the session includes a `Get-Date` function and a [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span></span>

<span data-ttu-id="ee835-157">La commande suivante obtient la `Get-Date` commande qui s’exécute lorsque vous tapez `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="ee835-157">The following command gets the `Get-Date` command that runs when you type `Get-Date`.</span></span>

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

<span data-ttu-id="ee835-158">La commande suivante utilise le paramètre **All** pour récupérer toutes les `Get-Date` commandes.</span><span class="sxs-lookup"><span data-stu-id="ee835-158">The following command uses the **All** parameter to get all `Get-Date` commands.</span></span>

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a><span data-ttu-id="ee835-159">Exécution de commandes masquées</span><span class="sxs-lookup"><span data-stu-id="ee835-159">Running hidden commands</span></span>

<span data-ttu-id="ee835-160">Vous pouvez exécuter des commandes particulières en spécifiant des propriétés d’élément qui distinguent la commande des autres commandes qui peuvent avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="ee835-160">You can run particular commands by specifying item properties that distinguish the command from other commands that might have the same name.</span></span> <span data-ttu-id="ee835-161">Vous pouvez utiliser cette méthode pour exécuter une commande, mais elle est particulièrement utile pour exécuter des commandes masquées.</span><span class="sxs-lookup"><span data-stu-id="ee835-161">You can use this method to run any command, but it is especially useful for running hidden commands.</span></span>

#### <a name="qualified-names"></a><span data-ttu-id="ee835-162">Noms qualifiés</span><span class="sxs-lookup"><span data-stu-id="ee835-162">Qualified names</span></span>

<span data-ttu-id="ee835-163">L’utilisation du nom qualifié du module d’une applet de commande vous permet d’exécuter des commandes masquées par un élément portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ee835-163">Using the module-qualified name of a cmdlet allows you to run commands hidden by an item with the same name.</span></span> <span data-ttu-id="ee835-164">Par exemple, vous pouvez exécuter l' `Get-Date` applet de commande en la qualifiant avec son nom de module **Microsoft. PowerShell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="ee835-164">For example, you can run the `Get-Date` cmdlet by qualifying it with its module name **Microsoft.PowerShell.Utility**.</span></span>

<span data-ttu-id="ee835-165">Utilisez cette méthode préférée lorsque vous écrivez des scripts que vous envisagez de distribuer.</span><span class="sxs-lookup"><span data-stu-id="ee835-165">Use this preferred method when writing scripts that you intend to distribute.</span></span> <span data-ttu-id="ee835-166">Vous ne pouvez pas prédire les commandes qui peuvent être présentes dans la session dans laquelle le script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ee835-166">You cannot predict which commands might be present in the session in which the script runs.</span></span>

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

<span data-ttu-id="ee835-167">Pour exécuter une `New-Map` commande qui a été ajoutée par le `MapFunctions` module, utilisez son nom qualifié de module :</span><span class="sxs-lookup"><span data-stu-id="ee835-167">To run a `New-Map` command that was added by the `MapFunctions` module, use its module-qualified name:</span></span>

```powershell
MapFunctions\New-Map
```

<span data-ttu-id="ee835-168">Pour rechercher le module à partir duquel une commande a été importée, utilisez la propriété **modulename** des commandes.</span><span class="sxs-lookup"><span data-stu-id="ee835-168">To find the module from which a command was imported, use the **ModuleName** property of commands.</span></span>

```
(Get-Command <command-name>).ModuleName
```

<span data-ttu-id="ee835-169">Par exemple, pour trouver la source de l' `Get-Date` applet de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee835-169">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> <span data-ttu-id="ee835-170">Vous ne pouvez pas qualifier de variables ou d’alias.</span><span class="sxs-lookup"><span data-stu-id="ee835-170">You cannot qualify variables or aliases.</span></span>

#### <a name="call-operator"></a><span data-ttu-id="ee835-171">Opérateur d’appel</span><span class="sxs-lookup"><span data-stu-id="ee835-171">Call operator</span></span>

<span data-ttu-id="ee835-172">Vous pouvez également utiliser l' `Call` opérateur `&` pour exécuter des commandes masquées en les associant à un appel à la commande [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (l’alias est « dir ») ou à l’opération « `Get-Command` [obtenir-module](xref:Microsoft.PowerShell.Core.Get-Module)».</span><span class="sxs-lookup"><span data-stu-id="ee835-172">You can also use the `Call` operator `&` to run hidden commands by combining it with a call to [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (the alias is "dir"), `Get-Command` or [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

<span data-ttu-id="ee835-173">L’opérateur d’appel exécute des chaînes et des blocs de script dans une étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="ee835-173">The call operator executes strings and script blocks in a child scope.</span></span> <span data-ttu-id="ee835-174">Pour plus d’informations, consultez [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="ee835-174">For more information, see [about_Operators](about_Operators.md).</span></span>

<span data-ttu-id="ee835-175">Par exemple, si vous avez une fonction nommée `Map` qui est masquée par un alias nommé `Map` , utilisez la commande suivante pour exécuter la fonction.</span><span class="sxs-lookup"><span data-stu-id="ee835-175">For example, if you have a function named `Map` that is hidden by an alias named `Map`, use the following command to run the function.</span></span>

```powershell
&(Get-Command -Name Map -CommandType Function)
```

<span data-ttu-id="ee835-176">ou</span><span class="sxs-lookup"><span data-stu-id="ee835-176">or</span></span>

```powershell
&(dir Function:\map)
```

<span data-ttu-id="ee835-177">Vous pouvez également enregistrer votre commande masquée dans une variable pour faciliter son exécution.</span><span class="sxs-lookup"><span data-stu-id="ee835-177">You can also save your hidden command in a variable to make it easier to run.</span></span>

<span data-ttu-id="ee835-178">Par exemple, la commande suivante enregistre la `Map` fonction dans la `$myMap` variable, puis utilise l' `Call` opérateur pour l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ee835-178">For example, the following command saves the `Map` function in the `$myMap` variable and then uses the `Call` operator to run it.</span></span>

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a><span data-ttu-id="ee835-179">Éléments remplacés</span><span class="sxs-lookup"><span data-stu-id="ee835-179">Replaced items</span></span>

<span data-ttu-id="ee835-180">Un élément « remplacé » est un élément auquel vous ne pouvez plus accéder.</span><span class="sxs-lookup"><span data-stu-id="ee835-180">A "replaced" item is one that you can no longer access.</span></span> <span data-ttu-id="ee835-181">Vous pouvez remplacer des éléments en important des éléments portant le même nom à partir d’un module ou d’un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="ee835-181">You can replace items by importing items of the same name from a module or snap-in.</span></span>

<span data-ttu-id="ee835-182">Par exemple, si vous tapez une `Get-Map` fonction dans votre session et que vous importez une fonction appelée `Get-Map` , elle remplace la fonction d’origine.</span><span class="sxs-lookup"><span data-stu-id="ee835-182">For example, if you type a `Get-Map` function in your session, and you import a function called `Get-Map`, it replaces the original function.</span></span> <span data-ttu-id="ee835-183">Vous ne pouvez pas le récupérer dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ee835-183">You cannot retrieve it in the current session.</span></span>

<span data-ttu-id="ee835-184">Les variables et les alias ne peuvent pas être masqués, car vous ne pouvez pas utiliser un opérateur d’appel ou un nom qualifié pour les exécuter.</span><span class="sxs-lookup"><span data-stu-id="ee835-184">Variables and aliases cannot be hidden because you cannot use a call operator or a qualified name to run them.</span></span> <span data-ttu-id="ee835-185">Lorsque vous importez des variables et des alias à partir d’un module ou d’un composant logiciel enfichable, ils remplacent les variables dans la session portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ee835-185">When you import variables and aliases from a module or snap-in, they replace variables in the session with the same name.</span></span>

### <a name="avoiding-name-conflicts"></a><span data-ttu-id="ee835-186">Éviter les conflits de noms</span><span class="sxs-lookup"><span data-stu-id="ee835-186">Avoiding name conflicts</span></span>

<span data-ttu-id="ee835-187">La meilleure façon de gérer les conflits de noms de commande consiste à les empêcher.</span><span class="sxs-lookup"><span data-stu-id="ee835-187">The best way to manage command name conflicts is to prevent them.</span></span> <span data-ttu-id="ee835-188">Lorsque vous nommez vos commandes, utilisez un nom unique.</span><span class="sxs-lookup"><span data-stu-id="ee835-188">When you name your commands, use a unique name.</span></span> <span data-ttu-id="ee835-189">Par exemple, ajoutez vos initiales ou acronyme de nom de société aux noms de vos commandes.</span><span class="sxs-lookup"><span data-stu-id="ee835-189">For example, add your initials or company name acronym to the nouns in your commands.</span></span>

<span data-ttu-id="ee835-190">En outre, lorsque vous importez des commandes dans votre session à partir d’un module PowerShell ou d’une autre session, utilisez le `Prefix` paramètre de la commande [import-module](xref:Microsoft.PowerShell.Core.Import-Module) ou</span><span class="sxs-lookup"><span data-stu-id="ee835-190">Also, when you import commands into your session from a PowerShell module or from another session, use the `Prefix` parameter of the [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) or</span></span>

<span data-ttu-id="ee835-191">Applet de commande [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) pour ajouter un préfixe aux noms des commandes.</span><span class="sxs-lookup"><span data-stu-id="ee835-191">[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet to add a prefix to the nouns in the names of commands.</span></span>

<span data-ttu-id="ee835-192">Par exemple, la commande suivante évite tout conflit avec les `Get-Date` applets de commande et `Set-Date` fournies avec PowerShell lorsque vous importez le `DateFunctions` module.</span><span class="sxs-lookup"><span data-stu-id="ee835-192">For example, the following command avoids any conflict with the `Get-Date` and `Set-Date` cmdlets that come with PowerShell when you import the `DateFunctions` module.</span></span>

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

<span data-ttu-id="ee835-193">Pour plus d’informations, consultez `Import-Module` et `Import-PSSession` ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ee835-193">For more information, see `Import-Module` and `Import-PSSession` below.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee835-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee835-194">See also</span></span>

- [<span data-ttu-id="ee835-195">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="ee835-195">about_Path_Syntax</span></span>](about_Path_Syntax.md)
- [<span data-ttu-id="ee835-196">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="ee835-196">about_Aliases</span></span>](about_Aliases.md)
- [<span data-ttu-id="ee835-197">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ee835-197">about_Functions</span></span>](about_Functions.md)
- [<span data-ttu-id="ee835-198">Alias-Provider</span><span class="sxs-lookup"><span data-stu-id="ee835-198">Alias-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [<span data-ttu-id="ee835-199">Function-Provider</span><span class="sxs-lookup"><span data-stu-id="ee835-199">Function-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [<span data-ttu-id="ee835-200">Get-Command</span><span class="sxs-lookup"><span data-stu-id="ee835-200">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="ee835-201">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="ee835-201">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="ee835-202">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="ee835-202">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

