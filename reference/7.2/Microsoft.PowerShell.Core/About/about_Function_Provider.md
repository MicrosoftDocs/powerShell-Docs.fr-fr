---
description: Fonction
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Function
ms.openlocfilehash: f72ad1e93e65848238afd9feacb38982b4986177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596744"
---
# <a name="function-provider"></a><span data-ttu-id="272ea-103">Fournisseur de fonctions</span><span class="sxs-lookup"><span data-stu-id="272ea-103">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="272ea-104">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="272ea-104">Provider name</span></span>
<span data-ttu-id="272ea-105">Fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-105">Function</span></span>

## <a name="drives"></a><span data-ttu-id="272ea-106">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="272ea-106">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="272ea-107">Fonctions</span><span class="sxs-lookup"><span data-stu-id="272ea-107">Capabilities</span></span>

<span data-ttu-id="272ea-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="272ea-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="272ea-109">Description courte</span><span class="sxs-lookup"><span data-stu-id="272ea-109">Short description</span></span>

<span data-ttu-id="272ea-110">Fournit l’accès aux fonctions définies dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="272ea-110">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="272ea-111">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="272ea-111">Detailed description</span></span>

<span data-ttu-id="272ea-112">Le fournisseur de **fonctions** PowerShell vous permet d’accéder, d’ajouter, de modifier, d’effacer et de supprimer les fonctions et les filtres dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="272ea-112">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="272ea-113">Une fonction est un bloc de code nommé qui effectue une action.</span><span class="sxs-lookup"><span data-stu-id="272ea-113">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="272ea-114">Quand vous tapez le nom de la fonction, le code de la fonction s'exécute.</span><span class="sxs-lookup"><span data-stu-id="272ea-114">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="272ea-115">Un filtre est un bloc de code nommé qui établit les conditions d'une action.</span><span class="sxs-lookup"><span data-stu-id="272ea-115">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="272ea-116">Vous pouvez taper le nom du filtre à la place de la condition, par exemple dans une `Where-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="272ea-116">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="272ea-117">La **fonction** Drive est un espace de noms plat qui contient uniquement les objets Function et Filter.</span><span class="sxs-lookup"><span data-stu-id="272ea-117">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="272ea-118">Ni les fonctions ni les filtres n'ont des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="272ea-118">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="272ea-119">Le fournisseur de **fonctions** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="272ea-119">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="272ea-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="272ea-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="272ea-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="272ea-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="272ea-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="272ea-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="272ea-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="272ea-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="272ea-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="272ea-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="272ea-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="272ea-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="272ea-126">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="272ea-126">Types exposed by this provider</span></span>

<span data-ttu-id="272ea-127">Chaque fonction est une instance de la classe [System. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) .</span><span class="sxs-lookup"><span data-stu-id="272ea-127">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="272ea-128">Chaque filtre est une instance de la classe [System. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .</span><span class="sxs-lookup"><span data-stu-id="272ea-128">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="272ea-129">Navigation dans le lecteur de fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-129">Navigating the Function drive</span></span>

<span data-ttu-id="272ea-130">Le fournisseur de **fonctions** expose son magasin de données dans le `Function:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-130">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="272ea-131">Pour utiliser des fonctions, vous pouvez modifier votre emplacement sur le `Function:` lecteur ( `Set-Location Function:` ).</span><span class="sxs-lookup"><span data-stu-id="272ea-131">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="272ea-132">Vous pouvez également travailler à partir d’un autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="272ea-132">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="272ea-133">Pour faire référence à une fonction à partir d’un autre emplacement, utilisez le nom du lecteur ( `Function:` ) dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="272ea-133">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="272ea-134">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="272ea-135">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="272ea-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="272ea-136">Vous pouvez également utiliser le fournisseur de **fonctions** à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="272ea-136">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="272ea-137">Pour faire référence à une fonction à partir d’un autre emplacement, utilisez le nom du lecteur `Function:` dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="272ea-137">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="272ea-138">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="272ea-138">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="272ea-139">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="272ea-139">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="272ea-140">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="272ea-140">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="272ea-141">Obtention de fonctions</span><span class="sxs-lookup"><span data-stu-id="272ea-141">Getting functions</span></span>

<span data-ttu-id="272ea-142">Cette commande obtient la liste de toutes les fonctions dans la session active.</span><span class="sxs-lookup"><span data-stu-id="272ea-142">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="272ea-143">Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="272ea-143">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="272ea-144">Le fournisseur de fonctions n’a pas de conteneur, donc la commande ci-dessus a le même effet lorsqu’elle est utilisée avec `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="272ea-144">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="272ea-145">Vous pouvez récupérer la définition d’une fonction en accédant à la propriété de **définition** , comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="272ea-145">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="272ea-146">Vous pouvez également récupérer la définition d’une fonction à l’aide de son chemin d’accès de fournisseur préfixé par le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="272ea-146">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="272ea-147">Obtention des fonctions sélectionnées</span><span class="sxs-lookup"><span data-stu-id="272ea-147">Getting selected functions</span></span>

<span data-ttu-id="272ea-148">Cette commande obtient la `man` fonction à partir du `Function:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-148">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="272ea-149">Elle utilise l' `Get-Item` applet de commande pour récupérer la fonction.</span><span class="sxs-lookup"><span data-stu-id="272ea-149">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="272ea-150">L’opérateur de pipeline ( `|` ) envoie le résultat à `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="272ea-150">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="272ea-151">Le `-Wrap` paramètre dirige le texte qui ne tient pas sur la ligne sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="272ea-151">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="272ea-152">Le `-Autosize` paramètre redimensionne les colonnes de la table pour s’adapter au texte.</span><span class="sxs-lookup"><span data-stu-id="272ea-152">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="272ea-153">Utilisation des chemins d’accès des fournisseurs de fonctions</span><span class="sxs-lookup"><span data-stu-id="272ea-153">Working with Function provider paths</span></span>

<span data-ttu-id="272ea-154">Ces commandes obtiennent toutes les deux la fonction nommée `c:` .</span><span class="sxs-lookup"><span data-stu-id="272ea-154">These commands both get the function named `c:`.</span></span> <span data-ttu-id="272ea-155">La première commande peut être utilisée dans n'importe quel lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-155">The first command can be used in any drive.</span></span> <span data-ttu-id="272ea-156">La deuxième commande est utilisée dans le `Function:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-156">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="272ea-157">Comme le nom se termine par un signe deux-points, qui est la syntaxe pour un lecteur, vous devez qualifier le chemin d'accès avec le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-157">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="272ea-158">Dans le `Function:` lecteur, vous pouvez utiliser l’un ou l’autre format.</span><span class="sxs-lookup"><span data-stu-id="272ea-158">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="272ea-159">Dans la deuxième commande, le point ( `.` ) représente l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="272ea-159">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="272ea-160">Création d’une fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-160">Creating a function</span></span>

<span data-ttu-id="272ea-161">Cette commande utilise l' `New-Item` applet de commande pour créer une fonction appelée `Win32:` .</span><span class="sxs-lookup"><span data-stu-id="272ea-161">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="272ea-162">L'expression entre accolades est le bloc de script qui est représenté par le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="272ea-162">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="272ea-163">Vous pouvez également créer une fonction en la tapant à la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="272ea-163">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="272ea-164">Par exemple, éditeur `Function:Win32: {Set-Location C:\Windows\System32}` .</span><span class="sxs-lookup"><span data-stu-id="272ea-164">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="272ea-165">Si vous êtes dans le `Function:` lecteur, vous pouvez omettre le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="272ea-165">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="272ea-166">Suppression d’une fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-166">Deleting a function</span></span>

<span data-ttu-id="272ea-167">Cette commande supprime la `more:` fonction de la session active.</span><span class="sxs-lookup"><span data-stu-id="272ea-167">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="272ea-168">Modification d’une fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-168">Changing a function</span></span>

<span data-ttu-id="272ea-169">Cette commande utilise l' `Set-Item` applet de commande pour modifier la `prompt` fonction afin qu’elle affiche l’heure avant le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="272ea-169">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="272ea-170">Renommer une fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-170">Rename a function</span></span>

<span data-ttu-id="272ea-171">Cette commande utilise l' `Rename-Item` applet de commande pour modifier le nom de la `help` fonction en `gh` .</span><span class="sxs-lookup"><span data-stu-id="272ea-171">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="272ea-172">Copie d’une fonction</span><span class="sxs-lookup"><span data-stu-id="272ea-172">Copying a function</span></span>

<span data-ttu-id="272ea-173">Cette commande copie la `prompt` fonction dans `oldPrompt` , en créant en fait un nouveau nom pour le bloc de script associé à la fonction prompt.</span><span class="sxs-lookup"><span data-stu-id="272ea-173">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="272ea-174">Vous pouvez utiliser ceci pour enregistrer la fonction prompt d'origine si vous projetez de la changer.</span><span class="sxs-lookup"><span data-stu-id="272ea-174">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="272ea-175">La propriété **options** de la nouvelle fonction a la valeur `None` .</span><span class="sxs-lookup"><span data-stu-id="272ea-175">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="272ea-176">Pour modifier la valeur de la propriété **options** , utilisez `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="272ea-176">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="272ea-177">Paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="272ea-177">Dynamic parameters</span></span>

<span data-ttu-id="272ea-178">Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="272ea-178">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="272ea-179">Options < [System. Management. Automation. ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="272ea-179">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="272ea-180">Détermine la valeur de la propriété **options** d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="272ea-180">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="272ea-181">`None`: Aucune option.</span><span class="sxs-lookup"><span data-stu-id="272ea-181">`None`: No options.</span></span> <span data-ttu-id="272ea-182">`None` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="272ea-182">`None` is the default.</span></span>
- <span data-ttu-id="272ea-183">`Constant`: La fonction ne peut pas être supprimée et ses propriétés ne peuvent pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="272ea-183">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="272ea-184">`Constant` est disponible uniquement lorsque vous créez une fonction.</span><span class="sxs-lookup"><span data-stu-id="272ea-184">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="272ea-185">Vous ne pouvez pas modifier l’option d’une fonction existante en `Constant` .</span><span class="sxs-lookup"><span data-stu-id="272ea-185">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="272ea-186">`Private`: La fonction est visible uniquement dans la portée actuelle</span><span class="sxs-lookup"><span data-stu-id="272ea-186">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="272ea-187">(pas dans les portées enfants).</span><span class="sxs-lookup"><span data-stu-id="272ea-187">(not in child scopes).</span></span>
- <span data-ttu-id="272ea-188">`ReadOnly`: Les propriétés de la fonction ne peuvent pas être modifiées, sauf en utilisant le `-Force` paramètre.</span><span class="sxs-lookup"><span data-stu-id="272ea-188">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="272ea-189">Vous pouvez utiliser `Remove-Item` pour supprimer la fonction.</span><span class="sxs-lookup"><span data-stu-id="272ea-189">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="272ea-190">`AllScope`: La fonction est copiée vers toutes les nouvelles étendues créées.</span><span class="sxs-lookup"><span data-stu-id="272ea-190">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="272ea-191">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="272ea-191">Cmdlets supported</span></span>

- [<span data-ttu-id="272ea-192">New-Item</span><span class="sxs-lookup"><span data-stu-id="272ea-192">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="272ea-193">Set-Item</span><span class="sxs-lookup"><span data-stu-id="272ea-193">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="272ea-194">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="272ea-194">Using the pipeline</span></span>

<span data-ttu-id="272ea-195">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="272ea-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="272ea-196">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="272ea-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="272ea-197">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="272ea-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="272ea-198">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="272ea-198">Getting help</span></span>

<span data-ttu-id="272ea-199">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="272ea-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="272ea-200">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="272ea-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="272ea-201">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="272ea-201">See also</span></span>

[<span data-ttu-id="272ea-202">about_Functions</span><span class="sxs-lookup"><span data-stu-id="272ea-202">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="272ea-203">about_Providers</span><span class="sxs-lookup"><span data-stu-id="272ea-203">about_Providers</span></span>](../About/about_Providers.md)

