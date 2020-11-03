---
description: Explique le concept de portée dans PowerShell et montre comment définir et modifier l’étendue des éléments.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 8517a5c077aa8c5b769bc74e13bc56ef6a6bb355
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207561"
---
# <a name="about-scopes"></a><span data-ttu-id="e999b-104">À propos des étendues</span><span class="sxs-lookup"><span data-stu-id="e999b-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="e999b-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="e999b-105">Short description</span></span>
<span data-ttu-id="e999b-106">Explique le concept de portée dans PowerShell et montre comment définir et modifier l’étendue des éléments.</span><span class="sxs-lookup"><span data-stu-id="e999b-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="e999b-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="e999b-107">Long description</span></span>

<span data-ttu-id="e999b-108">PowerShell protège l’accès aux variables, aux alias, aux fonctions et aux lecteurs PowerShell (PSDrives) en limitant l’emplacement où ils peuvent être lus et modifiés.</span><span class="sxs-lookup"><span data-stu-id="e999b-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="e999b-109">PowerShell utilise des règles d’étendue pour s’assurer que vous ne modifiez pas par inadvertance un élément qui ne doit pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="e999b-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="e999b-110">Voici les règles de base de l’étendue :</span><span class="sxs-lookup"><span data-stu-id="e999b-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="e999b-111">Les étendues peuvent s’imbriquer.</span><span class="sxs-lookup"><span data-stu-id="e999b-111">Scopes may nest.</span></span> <span data-ttu-id="e999b-112">Une étendue externe est appelée étendue parente.</span><span class="sxs-lookup"><span data-stu-id="e999b-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="e999b-113">Toutes les étendues imbriquées sont des portées enfants de ce parent.</span><span class="sxs-lookup"><span data-stu-id="e999b-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="e999b-114">Un élément est visible dans l’étendue dans laquelle il a été créé et dans toutes les portées enfants, sauf si vous le rendez explicitement privé.</span><span class="sxs-lookup"><span data-stu-id="e999b-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="e999b-115">Vous pouvez placer des variables, des alias, des fonctions ou des lecteurs PowerShell dans une ou plusieurs étendues.</span><span class="sxs-lookup"><span data-stu-id="e999b-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="e999b-116">Un élément que vous avez créé dans une étendue peut être modifié uniquement dans l’étendue dans laquelle il a été créé, sauf si vous spécifiez explicitement une autre portée.</span><span class="sxs-lookup"><span data-stu-id="e999b-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="e999b-117">Si vous créez un élément dans une étendue et que l’élément partage son nom avec un élément dans une étendue différente, l’élément d’origine peut être masqué sous le nouvel élément, mais il n’est pas substitué ou modifié.</span><span class="sxs-lookup"><span data-stu-id="e999b-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="e999b-118">Étendues PowerShell</span><span class="sxs-lookup"><span data-stu-id="e999b-118">PowerShell Scopes</span></span>

<span data-ttu-id="e999b-119">PowerShell prend en charge les étendues suivantes :</span><span class="sxs-lookup"><span data-stu-id="e999b-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="e999b-120">Global : étendue en vigueur au démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e999b-120">Global: The scope that is in effect when PowerShell starts.</span></span> <span data-ttu-id="e999b-121">Les variables et les fonctions qui sont présentes au démarrage de PowerShell ont été créées dans la portée globale, telles que les variables automatiques et les variables de préférence.</span><span class="sxs-lookup"><span data-stu-id="e999b-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="e999b-122">Les variables, les alias et les fonctions de vos profils PowerShell sont également créés dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="e999b-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span>

- <span data-ttu-id="e999b-123">Local : étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-123">Local: The current scope.</span></span> <span data-ttu-id="e999b-124">La portée locale peut être la portée globale ou toute autre étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-124">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="e999b-125">Script : étendue créée pendant l’exécution d’un fichier de script.</span><span class="sxs-lookup"><span data-stu-id="e999b-125">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="e999b-126">Seules les commandes du script s’exécutent dans l’étendue du script.</span><span class="sxs-lookup"><span data-stu-id="e999b-126">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="e999b-127">Pour les commandes dans un script, la portée de script est l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="e999b-127">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="e999b-128">**Private** n’est pas une étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-128">**Private** is not a scope.</span></span> <span data-ttu-id="e999b-129">Il s’agit d’une [option](#private-option) qui modifie la visibilité d’un élément en dehors de l’étendue dans laquelle l’élément est défini.</span><span class="sxs-lookup"><span data-stu-id="e999b-129">It is an [option](#private-option) that changes the visibility of an item outside of the the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="e999b-130">Étendues parent et enfant</span><span class="sxs-lookup"><span data-stu-id="e999b-130">Parent and Child Scopes</span></span>

<span data-ttu-id="e999b-131">Vous pouvez créer une nouvelle étendue en exécutant un script ou une fonction, en créant une session ou en démarrant une nouvelle instance de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e999b-131">You can create a new scope by running a script or function, by creating a session, or by starting a new instance of PowerShell.</span></span> <span data-ttu-id="e999b-132">Lorsque vous créez une étendue, le résultat est une étendue parente (étendue d’origine) et une étendue enfant (l’étendue que vous avez créée).</span><span class="sxs-lookup"><span data-stu-id="e999b-132">When you create a new scope, the result is a parent scope (the original scope) and a child scope (the scope that you created).</span></span>

<span data-ttu-id="e999b-133">Dans PowerShell, toutes les étendues sont des étendues enfants de l’étendue globale, mais vous pouvez créer de nombreuses étendues et de nombreuses étendues récursives.</span><span class="sxs-lookup"><span data-stu-id="e999b-133">In PowerShell, all scopes are child scopes of the global scope, but you can create many scopes and many recursive scopes.</span></span>

<span data-ttu-id="e999b-134">Sauf si vous rendez explicitement les éléments privés, les éléments de l’étendue parente sont disponibles pour l’étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="e999b-134">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="e999b-135">Toutefois, les éléments que vous créez et modifiez dans l’étendue enfant n’affectent pas l’étendue parente, sauf si vous spécifiez explicitement l’étendue lors de la création des éléments.</span><span class="sxs-lookup"><span data-stu-id="e999b-135">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

## <a name="inheritance"></a><span data-ttu-id="e999b-136">Héritage</span><span class="sxs-lookup"><span data-stu-id="e999b-136">Inheritance</span></span>

<span data-ttu-id="e999b-137">Une étendue enfant n’hérite pas des variables, des alias et des fonctions de l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="e999b-137">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="e999b-138">À moins qu’un élément ne soit privé, l’étendue enfant peut afficher les éléments dans l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="e999b-138">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="e999b-139">De plus, il peut modifier les éléments en spécifiant explicitement l’étendue parent, mais les éléments ne font pas partie de l’étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="e999b-139">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="e999b-140">Toutefois, une étendue enfant est créée avec un ensemble d’éléments.</span><span class="sxs-lookup"><span data-stu-id="e999b-140">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="e999b-141">En règle générale, il comprend tous les alias qui ont l’option **options AllScope** .</span><span class="sxs-lookup"><span data-stu-id="e999b-141">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="e999b-142">Cette option est décrite plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="e999b-142">This option is discussed later in this article.</span></span> <span data-ttu-id="e999b-143">Elle comprend toutes les variables qui ont l’option **options AllScope** , ainsi que certaines variables automatiques.</span><span class="sxs-lookup"><span data-stu-id="e999b-143">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="e999b-144">Pour rechercher les éléments dans une étendue particulière, utilisez le paramètre scope de `Get-Variable` ou `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="e999b-144">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="e999b-145">Par exemple, pour obtenir toutes les variables dans la portée locale, tapez :</span><span class="sxs-lookup"><span data-stu-id="e999b-145">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="e999b-146">Pour récupérer toutes les variables dans la portée globale, tapez :</span><span class="sxs-lookup"><span data-stu-id="e999b-146">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="e999b-147">Modificateurs d’étendue</span><span class="sxs-lookup"><span data-stu-id="e999b-147">Scope Modifiers</span></span>

<span data-ttu-id="e999b-148">Une variable, un alias ou un nom de fonction peut inclure l’un des modificateurs d’étendue facultatifs suivants :</span><span class="sxs-lookup"><span data-stu-id="e999b-148">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="e999b-149">`global:` : Spécifie que le nom existe dans la portée **globale** .</span><span class="sxs-lookup"><span data-stu-id="e999b-149">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="e999b-150">`local:` : Spécifie que le nom existe dans l’étendue **locale** .</span><span class="sxs-lookup"><span data-stu-id="e999b-150">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="e999b-151">La portée actuelle est toujours l’étendue **locale** .</span><span class="sxs-lookup"><span data-stu-id="e999b-151">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="e999b-152">`private:` : Spécifie que le nom est **privé** et visible uniquement pour l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-152">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="e999b-153">`script:` : Spécifie que le nom existe dans l’étendue du **script** .</span><span class="sxs-lookup"><span data-stu-id="e999b-153">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="e999b-154">La portée du **script** est l’étendue du fichier de script ancêtre le plus proche ou **globale** s’il n’existe pas de fichier de script ancêtre le plus proche.</span><span class="sxs-lookup"><span data-stu-id="e999b-154">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="e999b-155">`using:` -Utilisé pour accéder aux variables définies dans une autre portée lors de l’exécution de scripts via des applets de commande telles que `Start-Job` et `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e999b-155">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="e999b-156">`workflow:` : Spécifie que le nom existe dans un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e999b-156">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="e999b-157">Remarque : les flux de travail ne sont pas pris en charge dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e999b-157">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="e999b-158">`<variable-namespace>` -Modificateur créé par un fournisseur de PowerShell PSDrive.</span><span class="sxs-lookup"><span data-stu-id="e999b-158">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="e999b-159">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e999b-159">For example:</span></span>

  |  <span data-ttu-id="e999b-160">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e999b-160">Namespace</span></span>  |                    <span data-ttu-id="e999b-161">Description</span><span class="sxs-lookup"><span data-stu-id="e999b-161">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="e999b-162">Alias définis dans l’étendue actuelle</span><span class="sxs-lookup"><span data-stu-id="e999b-162">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="e999b-163">Variables d’environnement définies dans la portée actuelle</span><span class="sxs-lookup"><span data-stu-id="e999b-163">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="e999b-164">Fonctions définies dans l’étendue actuelle</span><span class="sxs-lookup"><span data-stu-id="e999b-164">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="e999b-165">Variables définies dans la portée actuelle</span><span class="sxs-lookup"><span data-stu-id="e999b-165">Variables defined in the current scope</span></span>             |

<span data-ttu-id="e999b-166">L’étendue par défaut des scripts est l’étendue du script.</span><span class="sxs-lookup"><span data-stu-id="e999b-166">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="e999b-167">L’étendue par défaut des fonctions et des alias est l’étendue locale, même si elles sont définies dans un script.</span><span class="sxs-lookup"><span data-stu-id="e999b-167">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="e999b-168">Utilisation de modificateurs d’étendue</span><span class="sxs-lookup"><span data-stu-id="e999b-168">Using scope modifiers</span></span>

<span data-ttu-id="e999b-169">Pour spécifier l’étendue d’une nouvelle variable, d’un alias ou d’une fonction, utilisez un modificateur d’étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-169">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="e999b-170">La syntaxe d’un modificateur de portée dans une variable est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-170">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="e999b-171">La syntaxe d’un modificateur de portée dans une fonction est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-171">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="e999b-172">La commande suivante, qui n’utilise pas de modificateur de portée, crée une variable dans l’étendue actuelle ou **locale** :</span><span class="sxs-lookup"><span data-stu-id="e999b-172">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="e999b-173">Pour créer la même variable dans la portée **globale** , utilisez le `global:` modificateur de portée :</span><span class="sxs-lookup"><span data-stu-id="e999b-173">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="e999b-174">Pour créer la même variable dans la portée de **script** , utilisez le `script:` modificateur de portée :</span><span class="sxs-lookup"><span data-stu-id="e999b-174">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="e999b-175">Vous pouvez également utiliser un modificateur d’étendue avec des fonctions.</span><span class="sxs-lookup"><span data-stu-id="e999b-175">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="e999b-176">La définition de fonction suivante crée une fonction dans la portée **globale** :</span><span class="sxs-lookup"><span data-stu-id="e999b-176">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="e999b-177">Vous pouvez également utiliser des modificateurs de portée pour faire référence à une variable dans une étendue différente.</span><span class="sxs-lookup"><span data-stu-id="e999b-177">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="e999b-178">La commande suivante fait référence à la `$test` variable, d’abord dans l’étendue locale, puis dans la portée globale :</span><span class="sxs-lookup"><span data-stu-id="e999b-178">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="e999b-179">`Using:`Modificateur de portée</span><span class="sxs-lookup"><span data-stu-id="e999b-179">The `Using:` scope modifier</span></span>

<span data-ttu-id="e999b-180">L’utilisation de est un modificateur d’étendue spécial qui identifie une variable locale dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="e999b-180">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="e999b-181">Sans modificateur, PowerShell s’attend à ce que les variables des commandes distantes soient définies dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="e999b-181">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="e999b-182">Le `Using` modificateur de portée est introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e999b-182">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="e999b-183">Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder.</span><span class="sxs-lookup"><span data-stu-id="e999b-183">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="e999b-184">Le `Using` modificateur de portée est pris en charge dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="e999b-184">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="e999b-185">Commandes exécutées à distance, démarrées avec `Invoke-Command` à l’aide du paramètre **ComputerName** ou **session** (session à distance)</span><span class="sxs-lookup"><span data-stu-id="e999b-185">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** or **Session** parameter (remote session)</span></span>
- <span data-ttu-id="e999b-186">Travaux en arrière-plan, démarrés avec `Start-Job` (session hors processus)</span><span class="sxs-lookup"><span data-stu-id="e999b-186">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="e999b-187">Travaux de thread, démarrés via `Start-ThreadJob` ou `ForEach-Object -Parallel` (session de threads distincte)</span><span class="sxs-lookup"><span data-stu-id="e999b-187">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="e999b-188">Selon le contexte, les valeurs des variables incorporées sont soit des copies indépendantes des données dans la portée de l’appelant, soit des références à celles-ci.</span><span class="sxs-lookup"><span data-stu-id="e999b-188">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="e999b-189">Dans les sessions à distance et hors processus, il s’agit toujours de copies indépendantes.</span><span class="sxs-lookup"><span data-stu-id="e999b-189">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="e999b-190">Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e999b-190">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="e999b-191">Dans les sessions de thread, elles sont passées par référence.</span><span class="sxs-lookup"><span data-stu-id="e999b-191">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="e999b-192">Cela signifie qu’il est possible de modifier les variables d’étendue d’appel dans un thread différent.</span><span class="sxs-lookup"><span data-stu-id="e999b-192">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="e999b-193">La modification en toute sécurité des variables requiert la synchronisation des threads.</span><span class="sxs-lookup"><span data-stu-id="e999b-193">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="e999b-194">Pour plus d’informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="e999b-194">For more information see:</span></span>

- [<span data-ttu-id="e999b-195">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="e999b-195">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="e999b-196">Sérialisation de valeurs de variables</span><span class="sxs-lookup"><span data-stu-id="e999b-196">Serialization of variable values</span></span>

<span data-ttu-id="e999b-197">Les commandes exécutées à distance et les travaux en arrière-plan s’exécutent hors processus.</span><span class="sxs-lookup"><span data-stu-id="e999b-197">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="e999b-198">Les sessions hors processus utilisent la sérialisation et la désérialisation basées sur XML pour rendre les valeurs des variables disponibles dans les limites du processus.</span><span class="sxs-lookup"><span data-stu-id="e999b-198">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="e999b-199">Le processus de sérialisation convertit des objets en **PSObject** qui contient les propriétés des objets d’origine, mais pas ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="e999b-199">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="e999b-200">Pour un ensemble limité de types, la désérialisation réalimente les objets dans le type d’origine.</span><span class="sxs-lookup"><span data-stu-id="e999b-200">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="e999b-201">L’objet réalimenté est une copie de l’instance d’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="e999b-201">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="e999b-202">Il a les propriétés et les méthodes de type.</span><span class="sxs-lookup"><span data-stu-id="e999b-202">It has the type properties and methods.</span></span> <span data-ttu-id="e999b-203">Pour les types simples, tels que **System. version** , la copie est exacte.</span><span class="sxs-lookup"><span data-stu-id="e999b-203">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="e999b-204">Pour les types complexes, la copie n’est pas parfaite.</span><span class="sxs-lookup"><span data-stu-id="e999b-204">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="e999b-205">Par exemple, les objets de certificat réalimentés n’incluent pas la clé privée.</span><span class="sxs-lookup"><span data-stu-id="e999b-205">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="e999b-206">Les instances de tous les autres types sont des instances **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="e999b-206">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="e999b-207">La propriété **PSTypeNames** contient le nom du type d’origine préfixé avec **désérialisé** , par exemple, **Deserialized.SysTEM. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="e999b-207">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="e999b-208">Option Options AllScope</span><span class="sxs-lookup"><span data-stu-id="e999b-208">The AllScope Option</span></span>

<span data-ttu-id="e999b-209">Les variables et les alias ont une propriété **option** qui peut prendre la valeur **options AllScope** .</span><span class="sxs-lookup"><span data-stu-id="e999b-209">Variables and aliases have an **Option** property that can take a value of **AllScope** .</span></span> <span data-ttu-id="e999b-210">Les éléments qui ont la propriété **options AllScope** deviennent partie intégrante des portées enfants que vous créez, bien qu’elles ne soient pas héritées rétroactivement par les étendues parentes.</span><span class="sxs-lookup"><span data-stu-id="e999b-210">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="e999b-211">Un élément qui a la propriété **options AllScope** est visible dans la portée enfant et fait partie de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-211">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="e999b-212">Les modifications apportées à l’élément dans toute portée affectent toutes les étendues dans lesquelles la variable est définie.</span><span class="sxs-lookup"><span data-stu-id="e999b-212">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="e999b-213">Gestion de l’étendue</span><span class="sxs-lookup"><span data-stu-id="e999b-213">Managing Scope</span></span>

<span data-ttu-id="e999b-214">Plusieurs applets de commande ont un paramètre d' **étendue** qui vous permet d’obtenir ou de définir (créer et modifier) des éléments dans une étendue particulière.</span><span class="sxs-lookup"><span data-stu-id="e999b-214">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="e999b-215">Utilisez la commande suivante pour rechercher toutes les applets de commande de votre session qui ont un paramètre d' **étendue** :</span><span class="sxs-lookup"><span data-stu-id="e999b-215">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="e999b-216">Pour rechercher les variables qui sont visibles dans une étendue particulière, utilisez le `Scope` paramètre de `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="e999b-216">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="e999b-217">Les variables visibles incluent des variables globales, des variables dans l’étendue parente et des variables dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-217">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="e999b-218">Par exemple, la commande suivante obtient les variables qui sont visibles dans l’étendue locale :</span><span class="sxs-lookup"><span data-stu-id="e999b-218">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="e999b-219">Pour créer une variable dans une étendue particulière, utilisez un modificateur d’étendue ou le paramètre **scope** de `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="e999b-219">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="e999b-220">La commande suivante crée une variable dans la portée globale :</span><span class="sxs-lookup"><span data-stu-id="e999b-220">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="e999b-221">Vous pouvez également utiliser le paramètre scope des `New-Alias` applets de commande, `Set-Alias` ou `Get-Alias` pour spécifier l’étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-221">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="e999b-222">La commande suivante crée un alias dans l’étendue globale :</span><span class="sxs-lookup"><span data-stu-id="e999b-222">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="e999b-223">Pour obtenir les fonctions dans une portée particulière, utilisez l' `Get-Item` applet de commande lorsque vous êtes dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-223">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="e999b-224">L' `Get-Item` applet de commande n’a pas de paramètre d' **étendue** .</span><span class="sxs-lookup"><span data-stu-id="e999b-224">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="e999b-225">Pour les applets de commande qui utilisent le paramètre **scope** , vous pouvez également faire référence aux étendues par numéro.</span><span class="sxs-lookup"><span data-stu-id="e999b-225">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="e999b-226">Le nombre décrit la position relative d’une étendue à une autre.</span><span class="sxs-lookup"><span data-stu-id="e999b-226">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="e999b-227">La portée 0 représente l’étendue actuelle, ou locale.</span><span class="sxs-lookup"><span data-stu-id="e999b-227">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="e999b-228">L’étendue 1 indique l’étendue parente immédiate.</span><span class="sxs-lookup"><span data-stu-id="e999b-228">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="e999b-229">L’étendue 2 indique le parent de l’étendue parent, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e999b-229">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="e999b-230">Les étendues numérotées sont utiles si vous avez créé de nombreuses étendues récursives.</span><span class="sxs-lookup"><span data-stu-id="e999b-230">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="e999b-231">Utilisation de la notation de source de point avec l’étendue</span><span class="sxs-lookup"><span data-stu-id="e999b-231">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="e999b-232">Les scripts et les fonctions suivent toutes les règles de portée.</span><span class="sxs-lookup"><span data-stu-id="e999b-232">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="e999b-233">Vous les créez dans une étendue particulière, et elles affectent uniquement cette étendue, sauf si vous utilisez un paramètre d’applet de commande ou un modificateur de portée pour modifier cette étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-233">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="e999b-234">Toutefois, vous pouvez ajouter un script ou une fonction à l’étendue actuelle à l’aide de la notation par point source.</span><span class="sxs-lookup"><span data-stu-id="e999b-234">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="e999b-235">Ensuite, lorsqu’un script s’exécute dans l’étendue actuelle, toutes les fonctions, tous les alias et toutes les variables créés par le script sont disponibles dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-235">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="e999b-236">Pour ajouter une fonction à l’étendue actuelle, tapez un point (.) et un espace avant le chemin d’accès et le nom de la fonction dans l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="e999b-236">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="e999b-237">Par exemple, pour exécuter le script Sample.ps1 à partir du répertoire C:\Scripts dans l’étendue du script (par défaut pour les scripts), utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-237">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="e999b-238">Pour exécuter le script de Sample.ps1 dans l’étendue locale, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-238">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="e999b-239">Lorsque vous utilisez l’opérateur d’appel (&) pour exécuter une fonction ou un script, il n’est pas ajouté à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-239">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="e999b-240">L’exemple suivant utilise l’opérateur d’appel :</span><span class="sxs-lookup"><span data-stu-id="e999b-240">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="e999b-241">Vous pouvez en savoir plus sur l’opérateur d’appel dans [about_Operators](about_operators.md).</span><span class="sxs-lookup"><span data-stu-id="e999b-241">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="e999b-242">Les alias, fonctions ou variables créés par le script de Sample.ps1 ne sont pas disponibles dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-242">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="e999b-243">Restriction sans étendue</span><span class="sxs-lookup"><span data-stu-id="e999b-243">Restricting Without Scope</span></span>

<span data-ttu-id="e999b-244">Quelques concepts de PowerShell sont similaires à l’étendue ou à l’interaction avec l’étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-244">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="e999b-245">Ces concepts peuvent être confondus avec l’étendue ou le comportement de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-245">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="e999b-246">Les sessions, les modules et les invites imbriquées sont des environnements autonomes, mais il ne s’agit pas de portées enfants de la portée globale dans la session.</span><span class="sxs-lookup"><span data-stu-id="e999b-246">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="e999b-247">Sessions</span><span class="sxs-lookup"><span data-stu-id="e999b-247">Sessions</span></span>

<span data-ttu-id="e999b-248">Une session est un environnement dans lequel PowerShell s’exécute.</span><span class="sxs-lookup"><span data-stu-id="e999b-248">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="e999b-249">Lorsque vous créez une session sur un ordinateur distant, PowerShell établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e999b-249">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="e999b-250">La connexion persistante vous permet d’utiliser la session pour plusieurs commandes associées.</span><span class="sxs-lookup"><span data-stu-id="e999b-250">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="e999b-251">Étant donné qu’une session est un environnement contenu, elle a sa propre étendue, mais une session n’est pas une étendue enfant de la session dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="e999b-251">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="e999b-252">La session commence par sa propre étendue globale.</span><span class="sxs-lookup"><span data-stu-id="e999b-252">The session starts with its own global scope.</span></span> <span data-ttu-id="e999b-253">Cette étendue est indépendante de l’étendue globale de la session.</span><span class="sxs-lookup"><span data-stu-id="e999b-253">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="e999b-254">Vous pouvez créer des étendues enfants dans la session.</span><span class="sxs-lookup"><span data-stu-id="e999b-254">You can create child scopes in the session.</span></span> <span data-ttu-id="e999b-255">Par exemple, vous pouvez exécuter un script pour créer une étendue enfant dans une session.</span><span class="sxs-lookup"><span data-stu-id="e999b-255">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="e999b-256">Modules</span><span class="sxs-lookup"><span data-stu-id="e999b-256">Modules</span></span>

<span data-ttu-id="e999b-257">Vous pouvez utiliser un module PowerShell pour partager et fournir des outils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e999b-257">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="e999b-258">Un module est une unité qui peut contenir des applets de commande, des scripts, des fonctions, des variables, des alias et d’autres éléments utiles.</span><span class="sxs-lookup"><span data-stu-id="e999b-258">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="e999b-259">Sauf définition explicite, les éléments d’un module ne sont pas accessibles à l’extérieur du module.</span><span class="sxs-lookup"><span data-stu-id="e999b-259">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="e999b-260">Par conséquent, vous pouvez ajouter le module à votre session et utiliser les éléments publics sans vous soucier que les autres éléments peuvent remplacer les applets de commande, les scripts, les fonctions et d’autres éléments de votre session.</span><span class="sxs-lookup"><span data-stu-id="e999b-260">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="e999b-261">Par défaut, les modules sont chargés dans le niveau supérieur de l' _État de session_ actuel et non dans l' _étendue_ actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-261">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_ .</span></span> <span data-ttu-id="e999b-262">L’état actuel de la session peut être un état de session de module ou l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="e999b-262">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="e999b-263">L’ajout d’un module à une session ne modifie pas l’étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-263">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="e999b-264">Si vous êtes dans la portée globale, les modules sont chargés dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="e999b-264">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="e999b-265">Toutes les exportations sont placées dans les tables globales.</span><span class="sxs-lookup"><span data-stu-id="e999b-265">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="e999b-266">Si vous chargez Module2 _à partir_ de Module1, Module2 est chargé dans l’état de session de Module1, et non dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="e999b-266">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="e999b-267">Toutes les exportations à partir de Module2 sont placées en haut de l’état de la session Module1.</span><span class="sxs-lookup"><span data-stu-id="e999b-267">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="e999b-268">Si vous utilisez `Import-Module -Scope local` , les exportations sont placées dans l’objet de portée actuel plutôt que au niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="e999b-268">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="e999b-269">Si vous êtes _dans un module_ et utilisez `Import-Module -Scope global` (ou `Import-Module -Global` ) pour charger un autre module, ce module et ses exportations sont chargés dans l’état de session global, et non dans l’état de session local du module.</span><span class="sxs-lookup"><span data-stu-id="e999b-269">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="e999b-270">Cette fonctionnalité a été conçue pour écrire un module qui manipule des modules.</span><span class="sxs-lookup"><span data-stu-id="e999b-270">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="e999b-271">Le module **WindowsCompatibility** effectue cette importation pour importer des modules de proxy dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="e999b-271">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="e999b-272">Dans l’état de session, les modules ont leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-272">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="e999b-273">Prenons le module suivant `C:\temp\mod1.psm1` :</span><span class="sxs-lookup"><span data-stu-id="e999b-273">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="e999b-274">Maintenant, nous créons une variable globale `$a` , lui attribuons une valeur et appelons la fonction **foo** .</span><span class="sxs-lookup"><span data-stu-id="e999b-274">Now we create a global variable `$a`, give it a value and call the function **foo** .</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="e999b-275">Le module déclare la variable `$a` dans la portée du module, puis la fonction **foo** génère la valeur de la variable dans les deux étendues.</span><span class="sxs-lookup"><span data-stu-id="e999b-275">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="e999b-276">Invites imbriquées</span><span class="sxs-lookup"><span data-stu-id="e999b-276">Nested Prompts</span></span>

<span data-ttu-id="e999b-277">Les invites imbriquées n’ont pas leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-277">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="e999b-278">Lorsque vous entrez une invite imbriquée, l’invite imbriquée est un sous-ensemble de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="e999b-278">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="e999b-279">Toutefois, vous restez dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="e999b-279">But, you remain within the local scope.</span></span>

<span data-ttu-id="e999b-280">Les scripts ont leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-280">Scripts do have their own scope.</span></span> <span data-ttu-id="e999b-281">Si vous déboguez un script et que vous atteignez un point d’arrêt dans le script, vous entrez la portée du script.</span><span class="sxs-lookup"><span data-stu-id="e999b-281">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="e999b-282">Option privée</span><span class="sxs-lookup"><span data-stu-id="e999b-282">Private Option</span></span>

<span data-ttu-id="e999b-283">Les alias et les variables ont une propriété **option** qui peut prendre la valeur **Private** .</span><span class="sxs-lookup"><span data-stu-id="e999b-283">Aliases and variables have an **Option** property that can take a value of **Private** .</span></span> <span data-ttu-id="e999b-284">Les éléments qui ont l’option **Private** peuvent être affichés et modifiés dans l’étendue dans laquelle ils sont créés, mais ils ne peuvent pas être affichés ou modifiés en dehors de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-284">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="e999b-285">Par exemple, si vous créez une variable qui a une option privée dans l’étendue globale, puis exécutez un script, `Get-Variable` les commandes du script n’affichent pas la variable privée.</span><span class="sxs-lookup"><span data-stu-id="e999b-285">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="e999b-286">L’utilisation du modificateur de portée globale dans cette instance n’affiche pas la variable privée.</span><span class="sxs-lookup"><span data-stu-id="e999b-286">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="e999b-287">Vous pouvez utiliser le paramètre option des applets de commande,, `New-Variable` `Set-Variable` `New-Alias` et `Set-Alias` pour définir la valeur de la propriété option sur Private.</span><span class="sxs-lookup"><span data-stu-id="e999b-287">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="e999b-288">Visibilité</span><span class="sxs-lookup"><span data-stu-id="e999b-288">Visibility</span></span>

<span data-ttu-id="e999b-289">La propriété **Visibility** d’une variable ou d’un alias détermine si vous pouvez voir l’élément en dehors du conteneur, dans lequel il a été créé.</span><span class="sxs-lookup"><span data-stu-id="e999b-289">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="e999b-290">Un conteneur peut être un module, un script ou un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="e999b-290">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="e999b-291">La visibilité est conçue pour les conteneurs de la même façon que la valeur **privée** de la propriété **option** est conçue pour les étendues.</span><span class="sxs-lookup"><span data-stu-id="e999b-291">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="e999b-292">La propriété **Visibility** prend les valeurs **publiques** et **privées** .</span><span class="sxs-lookup"><span data-stu-id="e999b-292">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="e999b-293">Les éléments qui ont une visibilité privée peuvent être affichés et modifiés uniquement dans le conteneur dans lequel ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="e999b-293">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="e999b-294">Si le conteneur est ajouté ou importé, les éléments qui ont une visibilité privée ne peuvent pas être affichés ou modifiés.</span><span class="sxs-lookup"><span data-stu-id="e999b-294">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="e999b-295">Étant donné que la visibilité est conçue pour les conteneurs, elle fonctionne différemment dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-295">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="e999b-296">Si vous créez un élément qui a une visibilité privée dans l’étendue globale, vous ne pouvez pas afficher ou modifier l’élément dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="e999b-296">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="e999b-297">Si vous essayez d’afficher ou de modifier la valeur d’une variable qui a une visibilité privée, PowerShell retourne un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e999b-297">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="e999b-298">Vous pouvez utiliser les `New-Variable` applets de commande et `Set-Variable` pour créer une variable qui a une visibilité privée.</span><span class="sxs-lookup"><span data-stu-id="e999b-298">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="e999b-299">Exemples</span><span class="sxs-lookup"><span data-stu-id="e999b-299">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="e999b-300">Exemple 1 : modifier une valeur de variable uniquement dans un script</span><span class="sxs-lookup"><span data-stu-id="e999b-300">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="e999b-301">La commande suivante modifie la valeur de la `$ConfirmPreference` variable dans un script.</span><span class="sxs-lookup"><span data-stu-id="e999b-301">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="e999b-302">La modification n’affecte pas la portée globale.</span><span class="sxs-lookup"><span data-stu-id="e999b-302">The change does not affect the global scope.</span></span>

<span data-ttu-id="e999b-303">Tout d’abord, pour afficher la valeur de la `$ConfirmPreference` variable dans l’étendue locale, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-303">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="e999b-304">Créez un script de Scope.ps1 qui contient les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e999b-304">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="e999b-305">Exécutez le script.</span><span class="sxs-lookup"><span data-stu-id="e999b-305">Run the script.</span></span> <span data-ttu-id="e999b-306">Le script modifie la valeur de la `$ConfirmPreference` variable, puis indique sa valeur dans la portée du script.</span><span class="sxs-lookup"><span data-stu-id="e999b-306">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="e999b-307">La sortie doit ressembler à la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-307">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="e999b-308">Ensuite, testez la valeur actuelle de la `$ConfirmPreference` variable dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="e999b-308">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="e999b-309">Cet exemple montre que les modifications apportées à la valeur d’une variable dans la portée du script n’affectent pas la valeur de la variable dans l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="e999b-309">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="e999b-310">Exemple 2 : afficher une valeur de variable dans différentes portées</span><span class="sxs-lookup"><span data-stu-id="e999b-310">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="e999b-311">Vous pouvez utiliser les modificateurs d’étendue pour afficher la valeur d’une variable dans la portée locale et dans une étendue parente.</span><span class="sxs-lookup"><span data-stu-id="e999b-311">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="e999b-312">Tout d’abord, définissez une `$test` variable dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="e999b-312">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="e999b-313">Ensuite, créez un script de Sample.ps1 qui définit la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="e999b-313">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="e999b-314">Dans le script, utilisez un modificateur de portée pour faire référence à la version globale ou locale de la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="e999b-314">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="e999b-315">Dans Sample.ps1 :</span><span class="sxs-lookup"><span data-stu-id="e999b-315">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="e999b-316">Lorsque vous exécutez Sample.ps1, la sortie doit ressembler à la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e999b-316">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="e999b-317">Une fois le script terminé, seule la valeur globale de `$test` est définie dans la session.</span><span class="sxs-lookup"><span data-stu-id="e999b-317">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="e999b-318">Exemple 3 : modifier la valeur d’une variable dans une étendue parente</span><span class="sxs-lookup"><span data-stu-id="e999b-318">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="e999b-319">Sauf si vous protégez un élément à l’aide de l’option Private ou d’une autre méthode, vous pouvez afficher et modifier la valeur d’une variable dans une étendue parente.</span><span class="sxs-lookup"><span data-stu-id="e999b-319">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="e999b-320">Tout d’abord, définissez une `$test` variable dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="e999b-320">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="e999b-321">Ensuite, créez un script de Sample.ps1 qui définit la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="e999b-321">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="e999b-322">Dans le script, utilisez un modificateur de portée pour faire référence à la version globale ou locale de la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="e999b-322">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="e999b-323">Dans Sample.ps1 :</span><span class="sxs-lookup"><span data-stu-id="e999b-323">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="e999b-324">Une fois le script terminé, la valeur globale de `$test` est modifiée.</span><span class="sxs-lookup"><span data-stu-id="e999b-324">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="e999b-325">Exemple 4 : création d’une variable privée</span><span class="sxs-lookup"><span data-stu-id="e999b-325">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="e999b-326">Une variable privée est une variable qui a une propriété **option** dont la valeur est *Private* .</span><span class="sxs-lookup"><span data-stu-id="e999b-326">A private variable is a variable that has an **Option** property that has a value of *Private* .</span></span> <span data-ttu-id="e999b-327">Les variables *privées* sont héritées par l’étendue enfant, mais elles ne peuvent être affichées ou modifiées que dans l’étendue dans laquelle elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="e999b-327">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="e999b-328">La commande suivante crée une variable privée appelée `$ptest` dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="e999b-328">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="e999b-329">Vous pouvez afficher et modifier la valeur de `$ptest` dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="e999b-329">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="e999b-330">Ensuite, créez un Sample.ps1 script qui contient les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="e999b-330">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="e999b-331">La commande tente d’afficher et de modifier la valeur de `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="e999b-331">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="e999b-332">Dans Sample.ps1 :</span><span class="sxs-lookup"><span data-stu-id="e999b-332">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="e999b-333">La `$ptest` variable n’est pas visible dans l’étendue du script, la sortie est vide.</span><span class="sxs-lookup"><span data-stu-id="e999b-333">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="e999b-334">Exemple 5 : utilisation d’une variable locale dans une commande à distance</span><span class="sxs-lookup"><span data-stu-id="e999b-334">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="e999b-335">Pour les variables d’une commande distante créée dans la session locale, utilisez le `Using` modificateur de portée.</span><span class="sxs-lookup"><span data-stu-id="e999b-335">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="e999b-336">PowerShell suppose que les variables des commandes distantes ont été créées dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="e999b-336">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="e999b-337">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="e999b-337">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="e999b-338">Par exemple, les commandes suivantes créent une `$Cred` variable dans la session locale, puis utilisent la `$Cred` variable dans une commande distante :</span><span class="sxs-lookup"><span data-stu-id="e999b-338">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="e999b-339">L’étendue using a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e999b-339">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e999b-340">Dans PowerShell 2,0, pour indiquer qu’une variable a été créée dans la session locale, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="e999b-340">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="e999b-341">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e999b-341">See also</span></span>

[<span data-ttu-id="e999b-342">about_Variables</span><span class="sxs-lookup"><span data-stu-id="e999b-342">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="e999b-343">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="e999b-343">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="e999b-344">about_Functions</span><span class="sxs-lookup"><span data-stu-id="e999b-344">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="e999b-345">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="e999b-345">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="e999b-346">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="e999b-346">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)