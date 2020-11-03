---
description: Variable
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Variable
ms.openlocfilehash: cae9a100b9e0a8fd044ec87d1541e1fe2bf440c8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207485"
---
# <a name="variable-provider"></a><span data-ttu-id="67e75-104">Fournisseur de variables</span><span class="sxs-lookup"><span data-stu-id="67e75-104">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="67e75-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="67e75-105">Provider name</span></span>
<span data-ttu-id="67e75-106">Variable</span><span class="sxs-lookup"><span data-stu-id="67e75-106">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="67e75-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="67e75-107">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="67e75-108">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="67e75-108">Capabilities</span></span>

<span data-ttu-id="67e75-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="67e75-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="67e75-110">Description courte</span><span class="sxs-lookup"><span data-stu-id="67e75-110">Short description</span></span>

<span data-ttu-id="67e75-111">Fournit l’accès aux variables PowerShell et à leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="67e75-111">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="67e75-112">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="67e75-112">Detailed description</span></span>

<span data-ttu-id="67e75-113">Le fournisseur de **variables** PowerShell vous permet d’afficher, d’ajouter, de modifier, d’effacer et de supprimer des variables PowerShell dans la console active.</span><span class="sxs-lookup"><span data-stu-id="67e75-113">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="67e75-114">Le fournisseur **de variables PowerShell** prend en charge les variables créées par PowerShell, y compris les variables automatiques, les variables de préférence et les variables que vous créez.</span><span class="sxs-lookup"><span data-stu-id="67e75-114">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="67e75-115">La **variable** Drive est un espace de noms plat qui contient uniquement les objets variables.</span><span class="sxs-lookup"><span data-stu-id="67e75-115">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="67e75-116">Les variables n'ont pas d'éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="67e75-116">The variables have no child items.</span></span>

<span data-ttu-id="67e75-117">Le fournisseur **variable** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="67e75-117">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="67e75-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="67e75-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="67e75-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="67e75-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="67e75-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="67e75-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="67e75-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="67e75-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="67e75-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="67e75-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="67e75-123">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="67e75-123">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="67e75-124">PowerShell comprend également un ensemble d’applets de commande spécialement conçues pour afficher et modifier des variables.</span><span class="sxs-lookup"><span data-stu-id="67e75-124">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="67e75-125">Lorsque vous utilisez des applets de commande de **variables** , vous n’avez pas besoin de spécifier le `Variable:` lecteur dans le nom.</span><span class="sxs-lookup"><span data-stu-id="67e75-125">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="67e75-126">Cet article ne traite pas de l’utilisation des applets de commande **variables** .</span><span class="sxs-lookup"><span data-stu-id="67e75-126">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="67e75-127">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="67e75-127">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="67e75-128">New-Variable</span><span class="sxs-lookup"><span data-stu-id="67e75-128">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="67e75-129">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="67e75-129">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="67e75-130">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="67e75-130">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="67e75-131">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="67e75-131">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="67e75-132">Vous pouvez également utiliser l’analyseur d’expression PowerShell pour créer, afficher et modifier les valeurs des variables sans utiliser les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="67e75-132">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="67e75-133">Lorsque vous travaillez avec des variables directement, utilisez un signe dollar ( `$` ) pour identifier le nom en tant que variable et l’opérateur d’assignation ( `=` ) pour établir et modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="67e75-133">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="67e75-134">Par exemple, `$p = Get-Process` crée la `p` variable et stocke les résultats d’une `Get-Process` commande dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="67e75-134">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="67e75-135">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="67e75-135">Types exposed by this provider</span></span>

<span data-ttu-id="67e75-136">Les variables peuvent être de plusieurs types différents.</span><span class="sxs-lookup"><span data-stu-id="67e75-136">Variables can be one of several different types.</span></span> <span data-ttu-id="67e75-137">La plupart des variables sont des instances de la `PSVariable` classe.</span><span class="sxs-lookup"><span data-stu-id="67e75-137">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="67e75-138">D’autres variables et leurs types sont répertoriés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="67e75-138">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="67e75-139">La `?` variable est une instance de la `QuestionMarkVariable` classe.</span><span class="sxs-lookup"><span data-stu-id="67e75-139">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="67e75-140">La `null` variable est une instance de la `NullVariable` classe.</span><span class="sxs-lookup"><span data-stu-id="67e75-140">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="67e75-141">Les variables de nombre maximal sont des instances de la `SessionStateCapacityVariable` classe.</span><span class="sxs-lookup"><span data-stu-id="67e75-141">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="67e75-142">`LocalVariable` les instances de contiennent des informations sur l’exécution actuelle, telles que :</span><span class="sxs-lookup"><span data-stu-id="67e75-142">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="67e75-143">Navigation dans les lecteurs de variables</span><span class="sxs-lookup"><span data-stu-id="67e75-143">Navigating the Variable drives</span></span>

<span data-ttu-id="67e75-144">Le fournisseur **variable** expose son magasin de données dans le `Variable:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="67e75-144">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="67e75-145">Pour utiliser des variables, vous pouvez modifier votre emplacement sur le `Variable:` lecteur ( `Set-Location Variable:` ) ou vous pouvez utiliser n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67e75-145">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="67e75-146">Pour faire référence à une variable à partir d’un autre emplacement, utilisez le nom du lecteur ( `Variable:` ) dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="67e75-146">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="67e75-147">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="67e75-147">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="67e75-148">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="67e75-148">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="67e75-149">Vous pouvez également utiliser le fournisseur de **variables** à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67e75-149">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="67e75-150">Pour faire référence à une variable à partir d’un autre emplacement, utilisez le nom du lecteur `Variable:` dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="67e75-150">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="67e75-151">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="67e75-151">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="67e75-152">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="67e75-152">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="67e75-153">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="67e75-153">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="67e75-154">Affichage de la valeur des variables</span><span class="sxs-lookup"><span data-stu-id="67e75-154">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="67e75-155">Obtient toutes les variables dans la session active</span><span class="sxs-lookup"><span data-stu-id="67e75-155">Get all variables in the current session</span></span>

<span data-ttu-id="67e75-156">Cette commande obtient la liste de toutes les variables et de leur valeur dans la session active.</span><span class="sxs-lookup"><span data-stu-id="67e75-156">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="67e75-157">Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67e75-157">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="67e75-158">Obtenir une variable à l’aide du chemin d’accès au fournisseur</span><span class="sxs-lookup"><span data-stu-id="67e75-158">Get a variable using its provider path</span></span>

<span data-ttu-id="67e75-159">Cette commande récupère une valeur de variables en utilisant son chemin d’accès de fournisseur préfixé par le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="67e75-159">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="67e75-160">Cela a le même effet que le préfixe du nom des variables avec le signe dollar ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="67e75-160">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="67e75-161">Récupérer des variables à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="67e75-161">Get variables using wildcards</span></span>

<span data-ttu-id="67e75-162">Cette commande obtient les variables dont le nom commence par « max ».</span><span class="sxs-lookup"><span data-stu-id="67e75-162">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="67e75-163">Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67e75-163">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="67e75-164">Obtient la valeur de l' ?</span><span class="sxs-lookup"><span data-stu-id="67e75-164">Get the value of the ?</span></span> <span data-ttu-id="67e75-165">variable</span><span class="sxs-lookup"><span data-stu-id="67e75-165">variable</span></span>

<span data-ttu-id="67e75-166">Cette commande utilise le `-LiteralPath` paramètre de la commande [« obtient-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem) pour récupérer la valeur de la `?` variable dans le `Variable:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="67e75-166">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="67e75-167">`?`Est un caractère générique dans les chemins d’accès, mais `Get-ChildItem` ne tente pas de résoudre les caractères génériques dans les valeurs du `-LiteralPath` paramètre.</span><span class="sxs-lookup"><span data-stu-id="67e75-167">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="67e75-168">Obtient les variables ReadOnly et constantes</span><span class="sxs-lookup"><span data-stu-id="67e75-168">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="67e75-169">Cette commande obtient les variables qui ont les valeurs de `ReadOnly` ou `Constant` pour leur propriété **options** .</span><span class="sxs-lookup"><span data-stu-id="67e75-169">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="67e75-170">Création de variables</span><span class="sxs-lookup"><span data-stu-id="67e75-170">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="67e75-171">Créer une variable</span><span class="sxs-lookup"><span data-stu-id="67e75-171">Create a new variable</span></span>

<span data-ttu-id="67e75-172">Cette commande crée la `services` variable et stocke les résultats d’une `Get-Service` commande dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="67e75-172">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="67e75-173">Étant donné que l’emplacement actuel se trouve dans le `Variable:` lecteur, la valeur du `-Path` paramètre est un point ( `.` ), qui représente l’emplacement actuel.</span><span class="sxs-lookup"><span data-stu-id="67e75-173">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="67e75-174">Les parenthèses entourant la `Get-Service` commande vérifient que la commande est exécutée avant la création de la variable.</span><span class="sxs-lookup"><span data-stu-id="67e75-174">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="67e75-175">Sans les parenthèses, la valeur de la nouvelle variable serait une chaîne « Get-Service ».</span><span class="sxs-lookup"><span data-stu-id="67e75-175">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="67e75-176">Créer une variable à l’aide d’un chemin d’accès absolu</span><span class="sxs-lookup"><span data-stu-id="67e75-176">Create a variable using an absolute path</span></span>

<span data-ttu-id="67e75-177">Cette commande crée une `services` variable et stocke le résultat d’une `Get-Service` commande dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="67e75-177">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="67e75-178">Pour créer une variable sans valeur, omettez l'opérateur d'affectation.</span><span class="sxs-lookup"><span data-stu-id="67e75-178">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="67e75-179">Modification de variables</span><span class="sxs-lookup"><span data-stu-id="67e75-179">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="67e75-180">Renommer une variable</span><span class="sxs-lookup"><span data-stu-id="67e75-180">Rename a variable</span></span>

<span data-ttu-id="67e75-181">Cette commande utilise l' `Rename-Item` applet de commande pour modifier le nom de la `a` variable en `processes` .</span><span class="sxs-lookup"><span data-stu-id="67e75-181">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="67e75-182">Modifier la valeur d’une variable</span><span class="sxs-lookup"><span data-stu-id="67e75-182">Change the value of a variable</span></span>

<span data-ttu-id="67e75-183">Cette commande utilise l' `Set-Item` applet de commande pour modifier la valeur de la `ErrorActionPreference` variable en « stop ».</span><span class="sxs-lookup"><span data-stu-id="67e75-183">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="67e75-184">Copier une variable</span><span class="sxs-lookup"><span data-stu-id="67e75-184">Copy a variable</span></span>

<span data-ttu-id="67e75-185">Cette commande utilise la `Copy-Item` cmdlet pour copier la `processes` variable dans `old_processes` .</span><span class="sxs-lookup"><span data-stu-id="67e75-185">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="67e75-186">Cela crée une variable nommée `old_processes` qui a la même valeur que la `processes` variable.</span><span class="sxs-lookup"><span data-stu-id="67e75-186">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="67e75-187">Supprimer une variable</span><span class="sxs-lookup"><span data-stu-id="67e75-187">Delete a variable</span></span>

<span data-ttu-id="67e75-188">Cette commande supprime la `serv` variable de la session active.</span><span class="sxs-lookup"><span data-stu-id="67e75-188">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="67e75-189">Vous pouvez utiliser cette commande dans n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67e75-189">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="67e75-190">Supprimer des variables à l’aide du paramètre-force</span><span class="sxs-lookup"><span data-stu-id="67e75-190">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="67e75-191">Cette commande supprime toutes les variables de la session active, à l’exception des variables dont la propriété **options** a la valeur `Constant` .</span><span class="sxs-lookup"><span data-stu-id="67e75-191">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="67e75-192">Sans le `-Force` paramètre, la commande ne supprime pas les variables dont la propriété **options** a la valeur `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="67e75-192">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="67e75-193">Définition de la valeur d’une variable sur NULL</span><span class="sxs-lookup"><span data-stu-id="67e75-193">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="67e75-194">Cette commande utilise l' `Clear-Item` applet de commande pour remplacer la valeur de la `processes` variable par null.</span><span class="sxs-lookup"><span data-stu-id="67e75-194">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="67e75-195">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="67e75-195">Using the pipeline</span></span>

<span data-ttu-id="67e75-196">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="67e75-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="67e75-197">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="67e75-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="67e75-198">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="67e75-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="67e75-199">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="67e75-199">Getting help</span></span>

<span data-ttu-id="67e75-200">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="67e75-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="67e75-201">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="67e75-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="67e75-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67e75-202">See also</span></span>

[<span data-ttu-id="67e75-203">about_Variables</span><span class="sxs-lookup"><span data-stu-id="67e75-203">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="67e75-204">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="67e75-204">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="67e75-205">about_Providers</span><span class="sxs-lookup"><span data-stu-id="67e75-205">about_Providers</span></span>](../About/about_Providers.md)
