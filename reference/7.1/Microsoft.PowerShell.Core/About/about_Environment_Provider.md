---
description: Environnement
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Environment
ms.openlocfilehash: 44f2f123da3066bc08e2b1ef0ec25c24b18799bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207334"
---
# <a name="environment-provider"></a><span data-ttu-id="9a3de-104">Fournisseur d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-104">Environment provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="9a3de-105">Nom du fournisseur</span><span class="sxs-lookup"><span data-stu-id="9a3de-105">Provider name</span></span>
<span data-ttu-id="9a3de-106">Environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-106">Environment</span></span>

## <a name="drives"></a><span data-ttu-id="9a3de-107">Lecteurs</span><span class="sxs-lookup"><span data-stu-id="9a3de-107">Drives</span></span>

`Env:`

## <a name="capabilities"></a><span data-ttu-id="9a3de-108">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="9a3de-108">Capabilities</span></span>

<span data-ttu-id="9a3de-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="9a3de-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="9a3de-110">Description courte</span><span class="sxs-lookup"><span data-stu-id="9a3de-110">Short description</span></span>

<span data-ttu-id="9a3de-111">Fournit l'accès aux variables d'environnement Windows.</span><span class="sxs-lookup"><span data-stu-id="9a3de-111">Provides access to the Windows environment variables.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="9a3de-112">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="9a3de-112">Detailed description</span></span>

<span data-ttu-id="9a3de-113">Le fournisseur d' **environnement** PowerShell vous permet d’extraire, d’ajouter, de modifier, d’effacer et de supprimer des variables d’environnement et des valeurs dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a3de-113">The PowerShell **Environment** provider lets you get, add, change, clear, and delete environment variables and values in PowerShell.</span></span>

<span data-ttu-id="9a3de-114">Les variables d' **environnement** sont des variables nommées dynamiquement qui décrivent l’environnement dans lequel vos programmes s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="9a3de-114">**Environment** variables are dynamically named variables that describe the environment in which your programs run.</span></span> <span data-ttu-id="9a3de-115">Windows et PowerShell utilisent des variables d’environnement pour stocker des informations persistantes qui affectent l’exécution du système et des processus.</span><span class="sxs-lookup"><span data-stu-id="9a3de-115">Windows and PowerShell use environment variables to store persistent information that affect system and process execution.</span></span> <span data-ttu-id="9a3de-116">Contrairement aux variables PowerShell, les variables d’environnement ne sont pas soumises aux contraintes de portée.</span><span class="sxs-lookup"><span data-stu-id="9a3de-116">Unlike PowerShell variables, environment variables are not subject to scope constraints.</span></span>

<span data-ttu-id="9a3de-117">Le lecteur d' **environnement** est un espace de noms plat contenant les variables d’environnement spécifiques à la session de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9a3de-117">The **Environment** drive is a flat namespace containing the environment variables specific to the current user's session.</span></span> <span data-ttu-id="9a3de-118">Les variables d’environnement n’ont pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="9a3de-118">The environment variables have no child items.</span></span>

<span data-ttu-id="9a3de-119">Le fournisseur d' **environnement** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="9a3de-119">The **Environment** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="9a3de-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="9a3de-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="9a3de-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="9a3de-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="9a3de-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9a3de-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="9a3de-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="9a3de-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="9a3de-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9a3de-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="9a3de-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9a3de-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="9a3de-126">Types exposés par ce fournisseur</span><span class="sxs-lookup"><span data-stu-id="9a3de-126">Types exposed by this provider</span></span>

<span data-ttu-id="9a3de-127">Chaque variable d’environnement est une instance de la classe [System. Collections. DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) .</span><span class="sxs-lookup"><span data-stu-id="9a3de-127">Each environment variable is an instance of the [System.Collections.DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) class.</span></span> <span data-ttu-id="9a3de-128">Le nom de la variable est la clé du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="9a3de-128">The name of the variable is the dictionary key.</span></span> <span data-ttu-id="9a3de-129">La valeur de la variable d'environnement est la valeur du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="9a3de-129">The value of the environment variable is the dictionary value.</span></span>

## <a name="navigating-the-environment-drive"></a><span data-ttu-id="9a3de-130">Navigation dans le lecteur de l’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-130">Navigating the Environment drive</span></span>

<span data-ttu-id="9a3de-131">Le fournisseur d' **environnement** expose son magasin de données dans le `Env:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="9a3de-131">The **Environment** provider exposes its data store in the `Env:` drive.</span></span> <span data-ttu-id="9a3de-132">Pour utiliser des variables d’environnement, modifiez votre emplacement sur le `Env:` lecteur ( `Set-Location Env:` ) ou utilisez un autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a3de-132">To work with environment variables, change your location to the `Env:` drive (`Set-Location Env:`), or work from another PowerShell drive.</span></span> <span data-ttu-id="9a3de-133">Pour référencer une variable d’environnement à partir d’un autre emplacement, utilisez le `Env:` nom du lecteur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9a3de-133">To reference an environment variable from another location, use the `Env:` drive name in the path.</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="9a3de-134">Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="9a3de-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="9a3de-135">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="9a3de-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="9a3de-136">Vous pouvez également utiliser le fournisseur de l' **environnement** à partir de n’importe quel autre lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a3de-136">You can also work with the **Environment** provider from any other PowerShell drive.</span></span> <span data-ttu-id="9a3de-137">Pour référencer une variable d’environnement à partir d’un autre emplacement, utilisez le nom du lecteur `Env:` dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9a3de-137">To reference an environment variable from another location, use the drive name `Env:` in the path.</span></span>

<span data-ttu-id="9a3de-138">Le fournisseur d' **environnement** expose également les variables d’environnement à l’aide d’un préfixe variable de `$env:` .</span><span class="sxs-lookup"><span data-stu-id="9a3de-138">The **Environment** provider also exposes environment variables using a variable prefix of `$env:`.</span></span>  <span data-ttu-id="9a3de-139">La commande suivante affiche le contenu de la variable d’environnement **ProgramFiles** .</span><span class="sxs-lookup"><span data-stu-id="9a3de-139">The following command views the contents of the **ProgramFiles** environment variable.</span></span> <span data-ttu-id="9a3de-140">Le `$env:` préfixe de variable peut être utilisé à partir de n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a3de-140">The `$env:` variable prefix can be used from any PowerShell drive.</span></span>

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

<span data-ttu-id="9a3de-141">Vous pouvez également modifier la valeur d’une variable d’environnement à l’aide du `$env:` préfixe de variable.</span><span class="sxs-lookup"><span data-stu-id="9a3de-141">You can also change the value of an environment variable using the `$env:` variable prefix.</span></span>  <span data-ttu-id="9a3de-142">Toutes les modifications apportées se rapportent uniquement à la session PowerShell active tant qu’elle est active.</span><span class="sxs-lookup"><span data-stu-id="9a3de-142">Any changes made only pertain to the current PowerShell session for as long as it is active.</span></span>

> [!NOTE]
> <span data-ttu-id="9a3de-143">PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="9a3de-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="9a3de-144">Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="9a3de-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="9a3de-145">et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="9a3de-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-environment-variables"></a><span data-ttu-id="9a3de-146">Obtention de variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-146">Getting environment variables</span></span>

<span data-ttu-id="9a3de-147">Cette commande répertorie toutes les variables d’environnement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="9a3de-147">This command lists all the environment variables in the current session.</span></span>

```powershell
Get-Item -Path Env:
```

<span data-ttu-id="9a3de-148">Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a3de-148">You can use this command from any PowerShell drive.</span></span>

<span data-ttu-id="9a3de-149">Le fournisseur d’environnement n’a pas de conteneurs, donc la commande ci-dessus a le même effet lorsqu’elle est utilisée avec `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="9a3de-149">The Environment provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a><span data-ttu-id="9a3de-150">Obtenir une variable d’environnement sélectionnée</span><span class="sxs-lookup"><span data-stu-id="9a3de-150">Get a selected environment variable</span></span>

<span data-ttu-id="9a3de-151">Cette commande obtient la `WINDIR` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="9a3de-151">This command gets the `WINDIR` environment Variable.</span></span>

```powershell
Get-ChildItem -Path Env:windir
```

<span data-ttu-id="9a3de-152">Vous pouvez également utiliser le format de préfixe de variable.</span><span class="sxs-lookup"><span data-stu-id="9a3de-152">You can also use the variable prefix format as well.</span></span>

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a><span data-ttu-id="9a3de-153">Créer une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-153">Create an environment variable</span></span>

<span data-ttu-id="9a3de-154">Cette commande crée la `USERMODE` variable d’environnement avec la valeur « non-admin ».</span><span class="sxs-lookup"><span data-stu-id="9a3de-154">This command creates the `USERMODE` environment variable with a value of "Non-Admin".</span></span> <span data-ttu-id="9a3de-155">La `-Path` valeur du paramètre crée le nouvel élément dans le `Env:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="9a3de-155">The `-Path` parameter value creates the new item in the `Env:` drive.</span></span> <span data-ttu-id="9a3de-156">La nouvelle variable d’environnement est utilisable uniquement dans la session PowerShell active tant qu’elle est active.</span><span class="sxs-lookup"><span data-stu-id="9a3de-156">The new environment variable is only usable in the current PowerShell session for as long as it is active.</span></span>

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a><span data-ttu-id="9a3de-157">Modification d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-157">Changing an environment variable</span></span>

### <a name="rename-an-environment-variable"></a><span data-ttu-id="9a3de-158">Renommer une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-158">Rename an environment variable</span></span>

<span data-ttu-id="9a3de-159">Cette commande utilise l' `Rename-Item` applet de commande pour modifier le nom de la `USERMODE` variable d’environnement que vous avez créée `USERROLE` .</span><span class="sxs-lookup"><span data-stu-id="9a3de-159">This command uses the `Rename-Item` cmdlet to change the name of the `USERMODE` environment variable that you created to `USERROLE`.</span></span> <span data-ttu-id="9a3de-160">Ne changez pas le nom d'une variable d'environnement utilisée par le système.</span><span class="sxs-lookup"><span data-stu-id="9a3de-160">Do not change the name of an environment variable that the system uses.</span></span> <span data-ttu-id="9a3de-161">Bien que ces modifications affectent uniquement la session active, elles peuvent provoquer un fonctionnement incorrect du système ou d'un programme.</span><span class="sxs-lookup"><span data-stu-id="9a3de-161">Although these changes affect only the current session, they might cause the system or a program to operate incorrectly.</span></span>

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a><span data-ttu-id="9a3de-162">Modifier une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-162">Change an environment variable</span></span>

<span data-ttu-id="9a3de-163">Cette commande utilise l' `Set-Item` applet de commande pour modifier la valeur de la `USERROLE` variable d’environnement en « Administrator ».</span><span class="sxs-lookup"><span data-stu-id="9a3de-163">This command uses the `Set-Item` cmdlet to change the value of the `USERROLE` environment variable to "Administrator".</span></span>

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a><span data-ttu-id="9a3de-164">Copier une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-164">Copy an environment variable</span></span>

<span data-ttu-id="9a3de-165">Cette commande copie la valeur de la `USERROLE` variable d’environnement dans la `USERROLE2` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="9a3de-165">This command copies the value of the `USERROLE` environment variable to the `USERROLE2` environment Variable.</span></span>

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a><span data-ttu-id="9a3de-166">Supprimer une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="9a3de-166">Remove an environment variable</span></span>

<span data-ttu-id="9a3de-167">Cette commande supprime la `USERROLE2` variable d’environnement de la session active.</span><span class="sxs-lookup"><span data-stu-id="9a3de-167">This command deletes the `USERROLE2` environment variable from the current session.</span></span>

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a><span data-ttu-id="9a3de-168">Supprimer une variable d’environnement avec Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9a3de-168">Remove an environment variable with Clear-Item</span></span>

<span data-ttu-id="9a3de-169">Cette commande supprime la `USERROLE` variable d’environnement en effaçant sa valeur.</span><span class="sxs-lookup"><span data-stu-id="9a3de-169">This command deletes the `USERROLE` environment variable by clearing its value.</span></span>

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a><span data-ttu-id="9a3de-170">Utilisation du pipeline</span><span class="sxs-lookup"><span data-stu-id="9a3de-170">Using the pipeline</span></span>

<span data-ttu-id="9a3de-171">Les applets de commande du fournisseur acceptent l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="9a3de-171">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="9a3de-172">Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="9a3de-172">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="9a3de-173">Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.</span><span class="sxs-lookup"><span data-stu-id="9a3de-173">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="9a3de-174">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="9a3de-174">Getting help</span></span>

<span data-ttu-id="9a3de-175">Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9a3de-175">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="9a3de-176">Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9a3de-176">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a><span data-ttu-id="9a3de-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a3de-177">See also</span></span>

[<span data-ttu-id="9a3de-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9a3de-178">about_Providers</span></span>](../About/about_Providers.md)

