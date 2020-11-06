---
description: Explique le concept de portée dans PowerShell et montre comment définir et modifier l’étendue des éléments.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 6a86348bb70afdcbd8ffe00339d1597efd8f88c4
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354573"
---
# <a name="about-scopes"></a><span data-ttu-id="ec402-104">À propos des étendues</span><span class="sxs-lookup"><span data-stu-id="ec402-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="ec402-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="ec402-105">Short description</span></span>
<span data-ttu-id="ec402-106">Explique le concept de portée dans PowerShell et montre comment définir et modifier l’étendue des éléments.</span><span class="sxs-lookup"><span data-stu-id="ec402-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="ec402-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="ec402-107">Long description</span></span>

<span data-ttu-id="ec402-108">PowerShell protège l’accès aux variables, aux alias, aux fonctions et aux lecteurs PowerShell (PSDrives) en limitant l’emplacement où ils peuvent être lus et modifiés.</span><span class="sxs-lookup"><span data-stu-id="ec402-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="ec402-109">PowerShell utilise des règles d’étendue pour s’assurer que vous ne modifiez pas par inadvertance un élément qui ne doit pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="ec402-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="ec402-110">Voici les règles de base de l’étendue :</span><span class="sxs-lookup"><span data-stu-id="ec402-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="ec402-111">Les étendues peuvent s’imbriquer.</span><span class="sxs-lookup"><span data-stu-id="ec402-111">Scopes may nest.</span></span> <span data-ttu-id="ec402-112">Une étendue externe est appelée étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="ec402-113">Toutes les étendues imbriquées sont des portées enfants de ce parent.</span><span class="sxs-lookup"><span data-stu-id="ec402-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="ec402-114">Un élément est visible dans l’étendue dans laquelle il a été créé et dans toutes les portées enfants, sauf si vous le rendez explicitement privé.</span><span class="sxs-lookup"><span data-stu-id="ec402-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="ec402-115">Vous pouvez placer des variables, des alias, des fonctions ou des lecteurs PowerShell dans une ou plusieurs étendues.</span><span class="sxs-lookup"><span data-stu-id="ec402-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="ec402-116">Un élément que vous avez créé dans une étendue peut être modifié uniquement dans l’étendue dans laquelle il a été créé, sauf si vous spécifiez explicitement une autre portée.</span><span class="sxs-lookup"><span data-stu-id="ec402-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="ec402-117">Si vous créez un élément dans une étendue et que l’élément partage son nom avec un élément dans une étendue différente, l’élément d’origine peut être masqué sous le nouvel élément, mais il n’est pas substitué ou modifié.</span><span class="sxs-lookup"><span data-stu-id="ec402-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="ec402-118">Étendues PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec402-118">PowerShell Scopes</span></span>

<span data-ttu-id="ec402-119">PowerShell prend en charge les étendues suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec402-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="ec402-120">Global : portée en vigueur au démarrage de PowerShell ou lorsque vous créez une nouvelle session ou une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ec402-120">Global: The scope that is in effect when PowerShell starts or when you create a new session or runspace.</span></span> <span data-ttu-id="ec402-121">Les variables et les fonctions qui sont présentes au démarrage de PowerShell ont été créées dans la portée globale, telles que les variables automatiques et les variables de préférence.</span><span class="sxs-lookup"><span data-stu-id="ec402-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="ec402-122">Les variables, les alias et les fonctions de vos profils PowerShell sont également créés dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span> <span data-ttu-id="ec402-123">La portée globale est l’étendue parente racine dans une session.</span><span class="sxs-lookup"><span data-stu-id="ec402-123">The global scope is the root parent scope in a session.</span></span>

- <span data-ttu-id="ec402-124">Local : étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-124">Local: The current scope.</span></span> <span data-ttu-id="ec402-125">La portée locale peut être la portée globale ou toute autre étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-125">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="ec402-126">Script : étendue créée pendant l’exécution d’un fichier de script.</span><span class="sxs-lookup"><span data-stu-id="ec402-126">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="ec402-127">Seules les commandes du script s’exécutent dans l’étendue du script.</span><span class="sxs-lookup"><span data-stu-id="ec402-127">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="ec402-128">Pour les commandes dans un script, la portée de script est l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="ec402-128">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="ec402-129">**Private** n’est pas une étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-129">**Private** is not a scope.</span></span> <span data-ttu-id="ec402-130">Il s’agit d’une [option](#private-option) qui modifie la visibilité d’un élément en dehors de la portée dans laquelle l’élément est défini.</span><span class="sxs-lookup"><span data-stu-id="ec402-130">It is an [option](#private-option) that changes the visibility of an item outside of the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="ec402-131">Étendues parent et enfant</span><span class="sxs-lookup"><span data-stu-id="ec402-131">Parent and Child Scopes</span></span>

<span data-ttu-id="ec402-132">Vous pouvez créer une étendue enfant en appelant un script ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="ec402-132">You can create a new child scope by calling a script or function.</span></span> <span data-ttu-id="ec402-133">La portée d’appel est l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-133">The calling scope is the parent scope.</span></span> <span data-ttu-id="ec402-134">La fonction ou le script appelé est la portée enfant.</span><span class="sxs-lookup"><span data-stu-id="ec402-134">The called script or function is the child scope.</span></span>
<span data-ttu-id="ec402-135">Les fonctions ou les scripts que vous appelez peuvent appeler d’autres fonctions, créant ainsi une hiérarchie d’étendues enfants dont l’étendue racine est la portée globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-135">The functions or scripts you call may call other functions, creating a hierarchy of child scopes whose root scope is the global scope.</span></span>

<span data-ttu-id="ec402-136">Sauf si vous rendez explicitement les éléments privés, les éléments de l’étendue parente sont disponibles pour l’étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="ec402-136">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="ec402-137">Toutefois, les éléments que vous créez et modifiez dans l’étendue enfant n’affectent pas l’étendue parente, sauf si vous spécifiez explicitement l’étendue lors de la création des éléments.</span><span class="sxs-lookup"><span data-stu-id="ec402-137">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

> [!NOTE]
> <span data-ttu-id="ec402-138">Les fonctions d’un module ne s’exécutent pas dans une étendue enfant de la portée d’appel.</span><span class="sxs-lookup"><span data-stu-id="ec402-138">Functions from a module do not run in a child scope of the calling scope.</span></span>
> <span data-ttu-id="ec402-139">Les modules ont leur propre état de session lié à la portée globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-139">Modules have their own session state that is linked to the global scope.</span></span>
> <span data-ttu-id="ec402-140">L’ensemble du code de module s’exécute dans une hiérarchie spécifique à un module d’étendues ayant sa propre étendue racine.</span><span class="sxs-lookup"><span data-stu-id="ec402-140">All module code runs in a module-specific hierarchy of scopes that has its own root scope.</span></span>

## <a name="inheritance"></a><span data-ttu-id="ec402-141">Héritage</span><span class="sxs-lookup"><span data-stu-id="ec402-141">Inheritance</span></span>

<span data-ttu-id="ec402-142">Une étendue enfant n’hérite pas des variables, des alias et des fonctions de l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-142">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="ec402-143">À moins qu’un élément ne soit privé, l’étendue enfant peut afficher les éléments dans l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-143">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="ec402-144">De plus, il peut modifier les éléments en spécifiant explicitement l’étendue parent, mais les éléments ne font pas partie de l’étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="ec402-144">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="ec402-145">Toutefois, une étendue enfant est créée avec un ensemble d’éléments.</span><span class="sxs-lookup"><span data-stu-id="ec402-145">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="ec402-146">En règle générale, il comprend tous les alias qui ont l’option **options AllScope** .</span><span class="sxs-lookup"><span data-stu-id="ec402-146">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="ec402-147">Cette option est décrite plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="ec402-147">This option is discussed later in this article.</span></span> <span data-ttu-id="ec402-148">Elle comprend toutes les variables qui ont l’option **options AllScope** , ainsi que certaines variables automatiques.</span><span class="sxs-lookup"><span data-stu-id="ec402-148">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="ec402-149">Pour rechercher les éléments dans une étendue particulière, utilisez le paramètre scope de `Get-Variable` ou `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="ec402-149">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="ec402-150">Par exemple, pour obtenir toutes les variables dans la portée locale, tapez :</span><span class="sxs-lookup"><span data-stu-id="ec402-150">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="ec402-151">Pour récupérer toutes les variables dans la portée globale, tapez :</span><span class="sxs-lookup"><span data-stu-id="ec402-151">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="ec402-152">Modificateurs d’étendue</span><span class="sxs-lookup"><span data-stu-id="ec402-152">Scope Modifiers</span></span>

<span data-ttu-id="ec402-153">Une variable, un alias ou un nom de fonction peut inclure l’un des modificateurs d’étendue facultatifs suivants :</span><span class="sxs-lookup"><span data-stu-id="ec402-153">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="ec402-154">`global:` : Spécifie que le nom existe dans la portée **globale** .</span><span class="sxs-lookup"><span data-stu-id="ec402-154">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="ec402-155">`local:` : Spécifie que le nom existe dans l’étendue **locale** .</span><span class="sxs-lookup"><span data-stu-id="ec402-155">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="ec402-156">La portée actuelle est toujours l’étendue **locale** .</span><span class="sxs-lookup"><span data-stu-id="ec402-156">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="ec402-157">`private:` : Spécifie que le nom est **privé** et visible uniquement pour l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-157">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="ec402-158">`script:` : Spécifie que le nom existe dans l’étendue du **script** .</span><span class="sxs-lookup"><span data-stu-id="ec402-158">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="ec402-159">La portée du **script** est l’étendue du fichier de script ancêtre le plus proche ou **globale** s’il n’existe pas de fichier de script ancêtre le plus proche.</span><span class="sxs-lookup"><span data-stu-id="ec402-159">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="ec402-160">`using:` -Utilisé pour accéder aux variables définies dans une autre portée lors de l’exécution de scripts via des applets de commande telles que `Start-Job` et `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="ec402-160">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="ec402-161">`workflow:` : Spécifie que le nom existe dans un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ec402-161">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="ec402-162">Remarque : les flux de travail ne sont pas pris en charge dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="ec402-162">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="ec402-163">`<variable-namespace>` -Modificateur créé par un fournisseur de PowerShell PSDrive.</span><span class="sxs-lookup"><span data-stu-id="ec402-163">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="ec402-164">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ec402-164">For example:</span></span>

  |  <span data-ttu-id="ec402-165">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="ec402-165">Namespace</span></span>  |                    <span data-ttu-id="ec402-166">Description</span><span class="sxs-lookup"><span data-stu-id="ec402-166">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="ec402-167">Alias définis dans l’étendue actuelle</span><span class="sxs-lookup"><span data-stu-id="ec402-167">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="ec402-168">Variables d’environnement définies dans la portée actuelle</span><span class="sxs-lookup"><span data-stu-id="ec402-168">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="ec402-169">Fonctions définies dans l’étendue actuelle</span><span class="sxs-lookup"><span data-stu-id="ec402-169">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="ec402-170">Variables définies dans la portée actuelle</span><span class="sxs-lookup"><span data-stu-id="ec402-170">Variables defined in the current scope</span></span>             |

<span data-ttu-id="ec402-171">L’étendue par défaut des scripts est l’étendue du script.</span><span class="sxs-lookup"><span data-stu-id="ec402-171">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="ec402-172">L’étendue par défaut des fonctions et des alias est l’étendue locale, même si elles sont définies dans un script.</span><span class="sxs-lookup"><span data-stu-id="ec402-172">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="ec402-173">Utilisation de modificateurs d’étendue</span><span class="sxs-lookup"><span data-stu-id="ec402-173">Using scope modifiers</span></span>

<span data-ttu-id="ec402-174">Pour spécifier l’étendue d’une nouvelle variable, d’un alias ou d’une fonction, utilisez un modificateur d’étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-174">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="ec402-175">La syntaxe d’un modificateur de portée dans une variable est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-175">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="ec402-176">La syntaxe d’un modificateur de portée dans une fonction est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-176">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="ec402-177">La commande suivante, qui n’utilise pas de modificateur de portée, crée une variable dans l’étendue actuelle ou **locale** :</span><span class="sxs-lookup"><span data-stu-id="ec402-177">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="ec402-178">Pour créer la même variable dans la portée **globale** , utilisez le `global:` modificateur de portée :</span><span class="sxs-lookup"><span data-stu-id="ec402-178">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="ec402-179">Pour créer la même variable dans la portée de **script** , utilisez le `script:` modificateur de portée :</span><span class="sxs-lookup"><span data-stu-id="ec402-179">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="ec402-180">Vous pouvez également utiliser un modificateur d’étendue avec des fonctions.</span><span class="sxs-lookup"><span data-stu-id="ec402-180">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="ec402-181">La définition de fonction suivante crée une fonction dans la portée **globale** :</span><span class="sxs-lookup"><span data-stu-id="ec402-181">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="ec402-182">Vous pouvez également utiliser des modificateurs de portée pour faire référence à une variable dans une étendue différente.</span><span class="sxs-lookup"><span data-stu-id="ec402-182">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="ec402-183">La commande suivante fait référence à la `$test` variable, d’abord dans l’étendue locale, puis dans la portée globale :</span><span class="sxs-lookup"><span data-stu-id="ec402-183">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="ec402-184">`Using:`Modificateur de portée</span><span class="sxs-lookup"><span data-stu-id="ec402-184">The `Using:` scope modifier</span></span>

<span data-ttu-id="ec402-185">L’utilisation de est un modificateur d’étendue spécial qui identifie une variable locale dans une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="ec402-185">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="ec402-186">Sans modificateur, PowerShell s’attend à ce que les variables des commandes distantes soient définies dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ec402-186">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="ec402-187">Le `Using` modificateur de portée est introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ec402-187">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="ec402-188">Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder.</span><span class="sxs-lookup"><span data-stu-id="ec402-188">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="ec402-189">Le `Using` modificateur de portée est pris en charge dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="ec402-189">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="ec402-190">Commandes exécutées à distance, démarrées avec `Invoke-Command` à l’aide du paramètre **ComputerName** ou **session** (session à distance)</span><span class="sxs-lookup"><span data-stu-id="ec402-190">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** or **Session** parameter (remote session)</span></span>
- <span data-ttu-id="ec402-191">Travaux en arrière-plan, démarrés avec `Start-Job` (session hors processus)</span><span class="sxs-lookup"><span data-stu-id="ec402-191">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="ec402-192">Travaux de thread, démarrés via `Start-ThreadJob` ou `ForEach-Object -Parallel` (session de threads distincte)</span><span class="sxs-lookup"><span data-stu-id="ec402-192">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="ec402-193">Selon le contexte, les valeurs des variables incorporées sont soit des copies indépendantes des données dans la portée de l’appelant, soit des références à celles-ci.</span><span class="sxs-lookup"><span data-stu-id="ec402-193">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="ec402-194">Dans les sessions à distance et hors processus, il s’agit toujours de copies indépendantes.</span><span class="sxs-lookup"><span data-stu-id="ec402-194">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="ec402-195">Pour plus d’informations, consultez [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ec402-195">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="ec402-196">Dans les sessions de thread, elles sont passées par référence.</span><span class="sxs-lookup"><span data-stu-id="ec402-196">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="ec402-197">Cela signifie qu’il est possible de modifier les variables d’étendue d’appel dans un thread différent.</span><span class="sxs-lookup"><span data-stu-id="ec402-197">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="ec402-198">La modification en toute sécurité des variables requiert la synchronisation des threads.</span><span class="sxs-lookup"><span data-stu-id="ec402-198">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="ec402-199">Pour plus d’informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec402-199">For more information see:</span></span>

- [<span data-ttu-id="ec402-200">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="ec402-200">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="ec402-201">Sérialisation de valeurs de variables</span><span class="sxs-lookup"><span data-stu-id="ec402-201">Serialization of variable values</span></span>

<span data-ttu-id="ec402-202">Les commandes exécutées à distance et les travaux en arrière-plan s’exécutent hors processus.</span><span class="sxs-lookup"><span data-stu-id="ec402-202">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="ec402-203">Les sessions hors processus utilisent la sérialisation et la désérialisation basées sur XML pour rendre les valeurs des variables disponibles dans les limites du processus.</span><span class="sxs-lookup"><span data-stu-id="ec402-203">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="ec402-204">Le processus de sérialisation convertit des objets en **PSObject** qui contient les propriétés des objets d’origine, mais pas ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="ec402-204">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="ec402-205">Pour un ensemble limité de types, la désérialisation réalimente les objets dans le type d’origine.</span><span class="sxs-lookup"><span data-stu-id="ec402-205">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="ec402-206">L’objet réalimenté est une copie de l’instance d’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="ec402-206">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="ec402-207">Il a les propriétés et les méthodes de type.</span><span class="sxs-lookup"><span data-stu-id="ec402-207">It has the type properties and methods.</span></span> <span data-ttu-id="ec402-208">Pour les types simples, tels que **System. version** , la copie est exacte.</span><span class="sxs-lookup"><span data-stu-id="ec402-208">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="ec402-209">Pour les types complexes, la copie n’est pas parfaite.</span><span class="sxs-lookup"><span data-stu-id="ec402-209">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="ec402-210">Par exemple, les objets de certificat réalimentés n’incluent pas la clé privée.</span><span class="sxs-lookup"><span data-stu-id="ec402-210">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="ec402-211">Les instances de tous les autres types sont des instances **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="ec402-211">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="ec402-212">La propriété **PSTypeNames** contient le nom du type d’origine préfixé avec **désérialisé** , par exemple, **Deserialized.SysTEM. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="ec402-212">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="ec402-213">Option Options AllScope</span><span class="sxs-lookup"><span data-stu-id="ec402-213">The AllScope Option</span></span>

<span data-ttu-id="ec402-214">Les variables et les alias ont une propriété **option** qui peut prendre la valeur **options AllScope**.</span><span class="sxs-lookup"><span data-stu-id="ec402-214">Variables and aliases have an **Option** property that can take a value of **AllScope**.</span></span> <span data-ttu-id="ec402-215">Les éléments qui ont la propriété **options AllScope** deviennent partie intégrante des portées enfants que vous créez, bien qu’elles ne soient pas héritées rétroactivement par les étendues parentes.</span><span class="sxs-lookup"><span data-stu-id="ec402-215">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="ec402-216">Un élément qui a la propriété **options AllScope** est visible dans la portée enfant et fait partie de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-216">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="ec402-217">Les modifications apportées à l’élément dans toute portée affectent toutes les étendues dans lesquelles la variable est définie.</span><span class="sxs-lookup"><span data-stu-id="ec402-217">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="ec402-218">Gestion de l’étendue</span><span class="sxs-lookup"><span data-stu-id="ec402-218">Managing Scope</span></span>

<span data-ttu-id="ec402-219">Plusieurs applets de commande ont un paramètre d' **étendue** qui vous permet d’obtenir ou de définir (créer et modifier) des éléments dans une étendue particulière.</span><span class="sxs-lookup"><span data-stu-id="ec402-219">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="ec402-220">Utilisez la commande suivante pour rechercher toutes les applets de commande de votre session qui ont un paramètre d' **étendue** :</span><span class="sxs-lookup"><span data-stu-id="ec402-220">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="ec402-221">Pour rechercher les variables qui sont visibles dans une étendue particulière, utilisez le `Scope` paramètre de `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="ec402-221">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="ec402-222">Les variables visibles incluent des variables globales, des variables dans l’étendue parente et des variables dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-222">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="ec402-223">Par exemple, la commande suivante obtient les variables qui sont visibles dans l’étendue locale :</span><span class="sxs-lookup"><span data-stu-id="ec402-223">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="ec402-224">Pour créer une variable dans une étendue particulière, utilisez un modificateur d’étendue ou le paramètre **scope** de `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="ec402-224">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="ec402-225">La commande suivante crée une variable dans la portée globale :</span><span class="sxs-lookup"><span data-stu-id="ec402-225">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="ec402-226">Vous pouvez également utiliser le paramètre scope des `New-Alias` applets de commande, `Set-Alias` ou `Get-Alias` pour spécifier l’étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-226">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="ec402-227">La commande suivante crée un alias dans l’étendue globale :</span><span class="sxs-lookup"><span data-stu-id="ec402-227">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="ec402-228">Pour obtenir les fonctions dans une portée particulière, utilisez l' `Get-Item` applet de commande lorsque vous êtes dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-228">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="ec402-229">L' `Get-Item` applet de commande n’a pas de paramètre d' **étendue** .</span><span class="sxs-lookup"><span data-stu-id="ec402-229">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="ec402-230">Pour les applets de commande qui utilisent le paramètre **scope** , vous pouvez également faire référence aux étendues par numéro.</span><span class="sxs-lookup"><span data-stu-id="ec402-230">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="ec402-231">Le nombre décrit la position relative d’une étendue à une autre.</span><span class="sxs-lookup"><span data-stu-id="ec402-231">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="ec402-232">La portée 0 représente l’étendue actuelle, ou locale.</span><span class="sxs-lookup"><span data-stu-id="ec402-232">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="ec402-233">L’étendue 1 indique l’étendue parente immédiate.</span><span class="sxs-lookup"><span data-stu-id="ec402-233">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="ec402-234">L’étendue 2 indique le parent de l’étendue parent, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ec402-234">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="ec402-235">Les étendues numérotées sont utiles si vous avez créé de nombreuses étendues récursives.</span><span class="sxs-lookup"><span data-stu-id="ec402-235">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="ec402-236">Utilisation de la notation de source de point avec l’étendue</span><span class="sxs-lookup"><span data-stu-id="ec402-236">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="ec402-237">Les scripts et les fonctions suivent toutes les règles de portée.</span><span class="sxs-lookup"><span data-stu-id="ec402-237">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="ec402-238">Vous les créez dans une étendue particulière, et elles affectent uniquement cette étendue, sauf si vous utilisez un paramètre d’applet de commande ou un modificateur de portée pour modifier cette étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-238">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="ec402-239">Toutefois, vous pouvez ajouter un script ou une fonction à l’étendue actuelle à l’aide de la notation par point source.</span><span class="sxs-lookup"><span data-stu-id="ec402-239">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="ec402-240">Ensuite, lorsqu’un script s’exécute dans l’étendue actuelle, toutes les fonctions, tous les alias et toutes les variables créés par le script sont disponibles dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-240">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="ec402-241">Pour ajouter une fonction à l’étendue actuelle, tapez un point (.) et un espace avant le chemin d’accès et le nom de la fonction dans l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="ec402-241">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="ec402-242">Par exemple, pour exécuter le script Sample.ps1 à partir du répertoire C:\Scripts dans l’étendue du script (par défaut pour les scripts), utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-242">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="ec402-243">Pour exécuter le script de Sample.ps1 dans l’étendue locale, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-243">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="ec402-244">Lorsque vous utilisez l’opérateur d’appel (&) pour exécuter une fonction ou un script, il n’est pas ajouté à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-244">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="ec402-245">L’exemple suivant utilise l’opérateur d’appel :</span><span class="sxs-lookup"><span data-stu-id="ec402-245">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="ec402-246">Vous pouvez en savoir plus sur l’opérateur d’appel dans [about_Operators](about_operators.md).</span><span class="sxs-lookup"><span data-stu-id="ec402-246">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="ec402-247">Les alias, fonctions ou variables créés par le script de Sample.ps1 ne sont pas disponibles dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-247">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="ec402-248">Restriction sans étendue</span><span class="sxs-lookup"><span data-stu-id="ec402-248">Restricting Without Scope</span></span>

<span data-ttu-id="ec402-249">Quelques concepts de PowerShell sont similaires à l’étendue ou à l’interaction avec l’étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-249">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="ec402-250">Ces concepts peuvent être confondus avec l’étendue ou le comportement de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-250">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="ec402-251">Les sessions, les modules et les invites imbriquées sont des environnements autonomes, mais il ne s’agit pas de portées enfants de la portée globale dans la session.</span><span class="sxs-lookup"><span data-stu-id="ec402-251">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="ec402-252">Sessions</span><span class="sxs-lookup"><span data-stu-id="ec402-252">Sessions</span></span>

<span data-ttu-id="ec402-253">Une session est un environnement dans lequel PowerShell s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ec402-253">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="ec402-254">Lorsque vous créez une session sur un ordinateur distant, PowerShell établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ec402-254">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="ec402-255">La connexion persistante vous permet d’utiliser la session pour plusieurs commandes associées.</span><span class="sxs-lookup"><span data-stu-id="ec402-255">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="ec402-256">Étant donné qu’une session est un environnement contenu, elle a sa propre étendue, mais une session n’est pas une étendue enfant de la session dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="ec402-256">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="ec402-257">La session commence par sa propre étendue globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-257">The session starts with its own global scope.</span></span> <span data-ttu-id="ec402-258">Cette étendue est indépendante de l’étendue globale de la session.</span><span class="sxs-lookup"><span data-stu-id="ec402-258">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="ec402-259">Vous pouvez créer des étendues enfants dans la session.</span><span class="sxs-lookup"><span data-stu-id="ec402-259">You can create child scopes in the session.</span></span> <span data-ttu-id="ec402-260">Par exemple, vous pouvez exécuter un script pour créer une étendue enfant dans une session.</span><span class="sxs-lookup"><span data-stu-id="ec402-260">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="ec402-261">Modules</span><span class="sxs-lookup"><span data-stu-id="ec402-261">Modules</span></span>

<span data-ttu-id="ec402-262">Vous pouvez utiliser un module PowerShell pour partager et fournir des outils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec402-262">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="ec402-263">Un module est une unité qui peut contenir des applets de commande, des scripts, des fonctions, des variables, des alias et d’autres éléments utiles.</span><span class="sxs-lookup"><span data-stu-id="ec402-263">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="ec402-264">Sauf définition explicite, les éléments d’un module ne sont pas accessibles à l’extérieur du module.</span><span class="sxs-lookup"><span data-stu-id="ec402-264">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="ec402-265">Par conséquent, vous pouvez ajouter le module à votre session et utiliser les éléments publics sans vous soucier que les autres éléments peuvent remplacer les applets de commande, les scripts, les fonctions et d’autres éléments de votre session.</span><span class="sxs-lookup"><span data-stu-id="ec402-265">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="ec402-266">Par défaut, les modules sont chargés dans le niveau supérieur de l' _État de session_ actuel et non dans l' _étendue_ actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-266">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_.</span></span> <span data-ttu-id="ec402-267">L’état actuel de la session peut être un état de session de module ou l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="ec402-267">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="ec402-268">L’ajout d’un module à une session ne modifie pas l’étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-268">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="ec402-269">Si vous êtes dans la portée globale, les modules sont chargés dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="ec402-269">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="ec402-270">Toutes les exportations sont placées dans les tables globales.</span><span class="sxs-lookup"><span data-stu-id="ec402-270">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="ec402-271">Si vous chargez Module2 _à partir_ de Module1, Module2 est chargé dans l’état de session de Module1, et non dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="ec402-271">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="ec402-272">Toutes les exportations à partir de Module2 sont placées en haut de l’état de la session Module1.</span><span class="sxs-lookup"><span data-stu-id="ec402-272">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="ec402-273">Si vous utilisez `Import-Module -Scope local` , les exportations sont placées dans l’objet de portée actuel plutôt que au niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="ec402-273">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="ec402-274">Si vous êtes _dans un module_ et utilisez `Import-Module -Scope global` (ou `Import-Module -Global` ) pour charger un autre module, ce module et ses exportations sont chargés dans l’état de session global, et non dans l’état de session local du module.</span><span class="sxs-lookup"><span data-stu-id="ec402-274">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="ec402-275">Cette fonctionnalité a été conçue pour écrire un module qui manipule des modules.</span><span class="sxs-lookup"><span data-stu-id="ec402-275">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="ec402-276">Le module **WindowsCompatibility** effectue cette importation pour importer des modules de proxy dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="ec402-276">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="ec402-277">Dans l’état de session, les modules ont leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-277">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="ec402-278">Prenons le module suivant `C:\temp\mod1.psm1` :</span><span class="sxs-lookup"><span data-stu-id="ec402-278">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="ec402-279">Maintenant, nous créons une variable globale `$a` , lui attribuons une valeur et appelons la fonction **foo**.</span><span class="sxs-lookup"><span data-stu-id="ec402-279">Now we create a global variable `$a`, give it a value and call the function **foo**.</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="ec402-280">Le module déclare la variable `$a` dans la portée du module, puis la fonction **foo** génère la valeur de la variable dans les deux étendues.</span><span class="sxs-lookup"><span data-stu-id="ec402-280">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="ec402-281">Invites imbriquées</span><span class="sxs-lookup"><span data-stu-id="ec402-281">Nested Prompts</span></span>

<span data-ttu-id="ec402-282">Les invites imbriquées n’ont pas leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-282">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="ec402-283">Lorsque vous entrez une invite imbriquée, l’invite imbriquée est un sous-ensemble de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="ec402-283">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="ec402-284">Toutefois, vous restez dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="ec402-284">But, you remain within the local scope.</span></span>

<span data-ttu-id="ec402-285">Les scripts ont leur propre étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-285">Scripts do have their own scope.</span></span> <span data-ttu-id="ec402-286">Si vous déboguez un script et que vous atteignez un point d’arrêt dans le script, vous entrez la portée du script.</span><span class="sxs-lookup"><span data-stu-id="ec402-286">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="ec402-287">Option privée</span><span class="sxs-lookup"><span data-stu-id="ec402-287">Private Option</span></span>

<span data-ttu-id="ec402-288">Les alias et les variables ont une propriété **option** qui peut prendre la valeur **Private**.</span><span class="sxs-lookup"><span data-stu-id="ec402-288">Aliases and variables have an **Option** property that can take a value of **Private**.</span></span> <span data-ttu-id="ec402-289">Les éléments qui ont l’option **Private** peuvent être affichés et modifiés dans l’étendue dans laquelle ils sont créés, mais ils ne peuvent pas être affichés ou modifiés en dehors de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-289">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="ec402-290">Par exemple, si vous créez une variable qui a une option privée dans l’étendue globale, puis exécutez un script, `Get-Variable` les commandes du script n’affichent pas la variable privée.</span><span class="sxs-lookup"><span data-stu-id="ec402-290">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="ec402-291">L’utilisation du modificateur de portée globale dans cette instance n’affiche pas la variable privée.</span><span class="sxs-lookup"><span data-stu-id="ec402-291">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="ec402-292">Vous pouvez utiliser le paramètre option des applets de commande,, `New-Variable` `Set-Variable` `New-Alias` et `Set-Alias` pour définir la valeur de la propriété option sur Private.</span><span class="sxs-lookup"><span data-stu-id="ec402-292">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="ec402-293">Visibilité</span><span class="sxs-lookup"><span data-stu-id="ec402-293">Visibility</span></span>

<span data-ttu-id="ec402-294">La propriété **Visibility** d’une variable ou d’un alias détermine si vous pouvez voir l’élément en dehors du conteneur, dans lequel il a été créé.</span><span class="sxs-lookup"><span data-stu-id="ec402-294">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="ec402-295">Un conteneur peut être un module, un script ou un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="ec402-295">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="ec402-296">La visibilité est conçue pour les conteneurs de la même façon que la valeur **privée** de la propriété **option** est conçue pour les étendues.</span><span class="sxs-lookup"><span data-stu-id="ec402-296">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="ec402-297">La propriété **Visibility** prend les valeurs **publiques** et **privées** .</span><span class="sxs-lookup"><span data-stu-id="ec402-297">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="ec402-298">Les éléments qui ont une visibilité privée peuvent être affichés et modifiés uniquement dans le conteneur dans lequel ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="ec402-298">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="ec402-299">Si le conteneur est ajouté ou importé, les éléments qui ont une visibilité privée ne peuvent pas être affichés ou modifiés.</span><span class="sxs-lookup"><span data-stu-id="ec402-299">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="ec402-300">Étant donné que la visibilité est conçue pour les conteneurs, elle fonctionne différemment dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-300">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="ec402-301">Si vous créez un élément qui a une visibilité privée dans l’étendue globale, vous ne pouvez pas afficher ou modifier l’élément dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="ec402-301">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="ec402-302">Si vous essayez d’afficher ou de modifier la valeur d’une variable qui a une visibilité privée, PowerShell retourne un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ec402-302">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="ec402-303">Vous pouvez utiliser les `New-Variable` applets de commande et `Set-Variable` pour créer une variable qui a une visibilité privée.</span><span class="sxs-lookup"><span data-stu-id="ec402-303">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="ec402-304">Exemples</span><span class="sxs-lookup"><span data-stu-id="ec402-304">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="ec402-305">Exemple 1 : modifier une valeur de variable uniquement dans un script</span><span class="sxs-lookup"><span data-stu-id="ec402-305">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="ec402-306">La commande suivante modifie la valeur de la `$ConfirmPreference` variable dans un script.</span><span class="sxs-lookup"><span data-stu-id="ec402-306">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="ec402-307">La modification n’affecte pas la portée globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-307">The change does not affect the global scope.</span></span>

<span data-ttu-id="ec402-308">Tout d’abord, pour afficher la valeur de la `$ConfirmPreference` variable dans l’étendue locale, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-308">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="ec402-309">Créez un script de Scope.ps1 qui contient les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec402-309">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="ec402-310">Exécutez le script.</span><span class="sxs-lookup"><span data-stu-id="ec402-310">Run the script.</span></span> <span data-ttu-id="ec402-311">Le script modifie la valeur de la `$ConfirmPreference` variable, puis indique sa valeur dans la portée du script.</span><span class="sxs-lookup"><span data-stu-id="ec402-311">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="ec402-312">La sortie doit ressembler à la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-312">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="ec402-313">Ensuite, testez la valeur actuelle de la `$ConfirmPreference` variable dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec402-313">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="ec402-314">Cet exemple montre que les modifications apportées à la valeur d’une variable dans la portée du script n’affectent pas la valeur de la variable dans l’étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-314">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="ec402-315">Exemple 2 : afficher une valeur de variable dans différentes portées</span><span class="sxs-lookup"><span data-stu-id="ec402-315">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="ec402-316">Vous pouvez utiliser les modificateurs d’étendue pour afficher la valeur d’une variable dans la portée locale et dans une étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-316">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="ec402-317">Tout d’abord, définissez une `$test` variable dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-317">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="ec402-318">Ensuite, créez un script de Sample.ps1 qui définit la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="ec402-318">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="ec402-319">Dans le script, utilisez un modificateur de portée pour faire référence à la version globale ou locale de la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="ec402-319">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="ec402-320">Dans Sample.ps1 :</span><span class="sxs-lookup"><span data-stu-id="ec402-320">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="ec402-321">Lorsque vous exécutez Sample.ps1, la sortie doit ressembler à la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ec402-321">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="ec402-322">Une fois le script terminé, seule la valeur globale de `$test` est définie dans la session.</span><span class="sxs-lookup"><span data-stu-id="ec402-322">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="ec402-323">Exemple 3 : modifier la valeur d’une variable dans une étendue parente</span><span class="sxs-lookup"><span data-stu-id="ec402-323">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="ec402-324">Sauf si vous protégez un élément à l’aide de l’option Private ou d’une autre méthode, vous pouvez afficher et modifier la valeur d’une variable dans une étendue parente.</span><span class="sxs-lookup"><span data-stu-id="ec402-324">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="ec402-325">Tout d’abord, définissez une `$test` variable dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="ec402-325">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="ec402-326">Ensuite, créez un script de Sample.ps1 qui définit la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="ec402-326">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="ec402-327">Dans le script, utilisez un modificateur de portée pour faire référence à la version globale ou locale de la `$test` variable.</span><span class="sxs-lookup"><span data-stu-id="ec402-327">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="ec402-328">Dans Sample.ps1 :</span><span class="sxs-lookup"><span data-stu-id="ec402-328">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="ec402-329">Une fois le script terminé, la valeur globale de `$test` est modifiée.</span><span class="sxs-lookup"><span data-stu-id="ec402-329">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="ec402-330">Exemple 4 : création d’une variable privée</span><span class="sxs-lookup"><span data-stu-id="ec402-330">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="ec402-331">Une variable privée est une variable qui a une propriété **option** dont la valeur est *Private*.</span><span class="sxs-lookup"><span data-stu-id="ec402-331">A private variable is a variable that has an **Option** property that has a value of *Private*.</span></span> <span data-ttu-id="ec402-332">Les variables *privées* sont héritées par l’étendue enfant, mais elles ne peuvent être affichées ou modifiées que dans l’étendue dans laquelle elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="ec402-332">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="ec402-333">La commande suivante crée une variable privée appelée `$ptest` dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="ec402-333">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="ec402-334">Vous pouvez afficher et modifier la valeur de `$ptest` dans l’étendue locale.</span><span class="sxs-lookup"><span data-stu-id="ec402-334">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="ec402-335">Ensuite, créez un Sample.ps1 script qui contient les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ec402-335">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="ec402-336">La commande tente d’afficher et de modifier la valeur de `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="ec402-336">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="ec402-337">Dans Sample.ps1 :</span><span class="sxs-lookup"><span data-stu-id="ec402-337">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="ec402-338">La `$ptest` variable n’est pas visible dans l’étendue du script, la sortie est vide.</span><span class="sxs-lookup"><span data-stu-id="ec402-338">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="ec402-339">Exemple 5 : utilisation d’une variable locale dans une commande à distance</span><span class="sxs-lookup"><span data-stu-id="ec402-339">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="ec402-340">Pour les variables d’une commande distante créée dans la session locale, utilisez le `Using` modificateur de portée.</span><span class="sxs-lookup"><span data-stu-id="ec402-340">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="ec402-341">PowerShell suppose que les variables des commandes distantes ont été créées dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ec402-341">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="ec402-342">La syntaxe est :</span><span class="sxs-lookup"><span data-stu-id="ec402-342">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="ec402-343">Par exemple, les commandes suivantes créent une `$Cred` variable dans la session locale, puis utilisent la `$Cred` variable dans une commande distante :</span><span class="sxs-lookup"><span data-stu-id="ec402-343">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="ec402-344">L’étendue using a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ec402-344">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="ec402-345">Dans PowerShell 2,0, pour indiquer qu’une variable a été créée dans la session locale, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="ec402-345">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="ec402-346">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec402-346">See also</span></span>

[<span data-ttu-id="ec402-347">about_Variables</span><span class="sxs-lookup"><span data-stu-id="ec402-347">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="ec402-348">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="ec402-348">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="ec402-349">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ec402-349">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="ec402-350">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="ec402-350">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="ec402-351">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="ec402-351">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)
