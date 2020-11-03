---
description: La variable d’environnement PSModulePath contient une liste d’emplacements de dossiers dans lesquels rechercher les modules et les ressources.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: b904b01cc3fc63f32151885d040fe7b0e618f6d5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208113"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="d5aa9-104">À propos de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="d5aa9-104">About PSModulePath</span></span>

<span data-ttu-id="d5aa9-105">La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="d5aa9-106">Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-106">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="d5aa9-107">Emplacements à l’ensemble du système : ces dossiers contiennent des modules fournis avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-107">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="d5aa9-108">Ces modules sont stockés dans le `$PSHOME\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-108">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="d5aa9-109">Il s’agit également de l’emplacement d’installation des modules de gestion Windows.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-109">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="d5aa9-110">Modules installés par l’utilisateur : il s’agit de modules installés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-110">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="d5aa9-111">`Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-111">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="d5aa9-112">Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="d5aa9-112">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="d5aa9-113">Sur Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME\Documents\PowerShell\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-113">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="d5aa9-114">L’emplacement de l’étendue **ALLUSERS** est `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-114">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="d5aa9-115">Sur les systèmes non-Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME/.local/share/powershell/Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-115">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="d5aa9-116">L’emplacement de l’étendue **ALLUSERS** est `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-116">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="d5aa9-117">En outre, les programmes d’installation qui installent des modules dans d’autres répertoires, tels que le répertoire Program Files, peuvent ajouter leurs emplacements à la valeur de `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-117">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="d5aa9-118">Sur Windows, l’emplacement spécifique à l’utilisateur est le `PowerShell\Modules` dossier situé dans le dossier **documents** de votre profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-118">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="d5aa9-119">Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-119">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="d5aa9-120">Microsoft OneDrive peut également modifier l’emplacement de votre dossier **documents** .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-120">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="d5aa9-121">Vous pouvez vérifier l’emplacement de votre dossier **documents** à l’aide de la commande suivante : `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-121">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="d5aa9-122">Modification de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="d5aa9-122">Modifying PSModulePath</span></span>

<span data-ttu-id="d5aa9-123">Pour modifier les répertoires de module par défaut de la session active, utilisez le format de commande suivant pour modifier la valeur de la `PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-123">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="d5aa9-124">Par exemple, pour ajouter le `C:\Program Files\Fabrikam\Modules` répertoire à la valeur de la variable d’environnement PSModulePath, tapez :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-124">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="d5aa9-125">Le point-virgule ( `;` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-125">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="d5aa9-126">Sur les plateformes non-Windows, le signe deux-points ( `:` ) sépare les emplacements de chemin d’accès dans la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-126">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="d5aa9-127">Pour modifier la valeur de `PSModulePath` dans chaque session, ajoutez la commande précédente à votre profil PowerShell ou utilisez la méthode **SetEnvironmentVariable ne contient** de la classe d' **environnement** .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-127">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="d5aa9-128">La commande suivante utilise la méthode **GetEnvironmentVariable** pour récupérer le paramètre de l’ordinateur de `PSModulePath` et la méthode **SetEnvironmentVariable ne contient** pour ajouter le `C:\Program Files\Fabrikam\Modules` chemin d’accès à la valeur.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-128">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="d5aa9-129">Pour ajouter un chemin d’accès au paramètre utilisateur, remplacez la valeur cible par **utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-129">To add a path to the user setting, change the target value to **User** .</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="d5aa9-130">Pour plus d’informations sur les méthodes de la classe **System. Environment** , consultez [méthodes d’environnement](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="d5aa9-130">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="d5aa9-131">Construction de PSModulePath PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5aa9-131">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="d5aa9-132">La valeur de `$env:PSModulePath` est construite à chaque démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-132">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="d5aa9-133">La valeur varie en fonction de la version de PowerShell et de son mode de lancement.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-133">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="d5aa9-134">Démarrage de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5aa9-134">Windows PowerShell startup</span></span>

<span data-ttu-id="d5aa9-135">Windows PowerShell utilise la logique suivante pour construire au `PSModulePath` démarrage :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-135">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="d5aa9-136">Si `PSModulePath` n’existe pas, combinez **CurrentUser** , **ALLUSERS** et les `$PSHOME` chemins des modules</span><span class="sxs-lookup"><span data-stu-id="d5aa9-136">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="d5aa9-137">Si `PSModulePath` existe :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-137">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="d5aa9-138">Si `PSModulePath` contient le `$PSHOME` chemin des modules :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-138">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="d5aa9-139">Le chemin des modules **ALLUSERS** est inséré avant le `$PSHOME` chemin des modules</span><span class="sxs-lookup"><span data-stu-id="d5aa9-139">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="d5aa9-140">tierce</span><span class="sxs-lookup"><span data-stu-id="d5aa9-140">else:</span></span>
    - <span data-ttu-id="d5aa9-141">Utilisez simplement `PSModulePath` comme défini, car l’utilisateur a délibérément supprimé l' `$PSHOME` emplacement</span><span class="sxs-lookup"><span data-stu-id="d5aa9-141">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="d5aa9-142">Le chemin d’accès du module **CurrentUser** est préfixé uniquement si l’étendue de l’utilisateur `$env:PSModulePath` n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-142">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="d5aa9-143">Dans le cas contraire, l’étendue de l’utilisateur `$env:PSModulePath` est utilisée comme définie.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-143">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="d5aa9-144">Démarrage de PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="d5aa9-144">PowerShell Core 6 startup</span></span>

<span data-ttu-id="d5aa9-145">PowerShell Core 6 n’utilise pas le contenu de `$env:PSModulePath` s’il détecte qu’il a été démarré à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-145">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="d5aa9-146">Il le remplace par :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-146">It overwrites it with:</span></span>

- <span data-ttu-id="d5aa9-147">**CurrentUser** modules chemin + **ALLUSERS** modules chemin + `$PSHOME` modules chemin + modules Windows PowerShell `$PSHOME` chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-147">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="d5aa9-148">Démarrage de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="d5aa9-148">PowerShell 7 startup</span></span>

<span data-ttu-id="d5aa9-149">Dans Windows, pour la plupart des variables d’environnement, si la variable de portée utilisateur existe, un nouveau processus utilise cette valeur uniquement s’il existe une variable de portée ordinateur portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-149">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="d5aa9-150">Dans PowerShell 7, `PSModulePath` est traité de façon similaire à la façon dont la `Path` variable d’environnement est traitée sur Windows.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-150">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="d5aa9-151">Sur Windows, `Path` est traité différemment des autres variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-151">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="d5aa9-152">Quand un processus est démarré, Windows combine l’étendue de l’utilisateur `Path` avec l’étendue de l’ordinateur `Path` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-152">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="d5aa9-153">Récupérer l’étendue de l’utilisateur `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="d5aa9-153">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="d5aa9-154">Comparer pour traiter la `PSModulePath` variable d’environnement héritée</span><span class="sxs-lookup"><span data-stu-id="d5aa9-154">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="d5aa9-155">Si le même :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-155">If the same:</span></span>
    - <span data-ttu-id="d5aa9-156">Ajoutez le **ALLUSERS** `PSModulePath` à la fin suivant la sémantique de la `Path` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-156">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="d5aa9-157">Le `System32` chemin d’accès Windows provient de l’ordinateur défini `PSModulePath` , il n’est donc pas nécessaire de l’ajouter explicitement</span><span class="sxs-lookup"><span data-stu-id="d5aa9-157">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="d5aa9-158">Si différent, Treat comme si l’utilisateur l’avait explicitement modifié et n’ajoute pas **ALLUSERS**`PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="d5aa9-158">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="d5aa9-159">Préfixe avec utilisateur, système et `$PSHOME` chemins d’accès PS7 dans cet ordre</span><span class="sxs-lookup"><span data-stu-id="d5aa9-159">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="d5aa9-160">Si `powershell.config.json` contient une étendue d’utilisateur `PSModulePath` , utilisez-le à la place de la valeur par défaut pour l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="d5aa9-160">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="d5aa9-161">Si `powershell.config.json` contient une portée système `PSModulePath` , utilisez-le à la place de la valeur par défaut pour le système.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-161">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="d5aa9-162">Les systèmes UNIX n’ont pas de séparation entre les variables d’environnement utilisateur et système.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-162">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="d5aa9-163">`PSModulePath` est hérité et les chemins d’accès spécifiques à PS7 sont préfixés s’ils ne sont pas déjà définis.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-163">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="d5aa9-164">Démarrage de Windows PowerShell à partir de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="d5aa9-164">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="d5aa9-165">Pour cette discussion, _Windows PowerShell_ signifie à la fois `powershell.exe` et `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-165">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="d5aa9-166">La valeur de `$env:PSModulePath` est copiée vers `WinPSModulePath` avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5aa9-166">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="d5aa9-167">Supprimer PS7 le chemin d’accès au module utilisateur</span><span class="sxs-lookup"><span data-stu-id="d5aa9-167">Remove PS7 the User module path</span></span>
- <span data-ttu-id="d5aa9-168">Supprimer PS7 le chemin d’accès au module système</span><span class="sxs-lookup"><span data-stu-id="d5aa9-168">Remove PS7 the System module path</span></span>
- <span data-ttu-id="d5aa9-169">Supprimer PS7 le `$PSHOME` chemin d’accès au module</span><span class="sxs-lookup"><span data-stu-id="d5aa9-169">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="d5aa9-170">Les chemins d’accès PS7 sont supprimés afin que les modules PS7 ne soient pas chargés dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-170">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="d5aa9-171">La `WinPSModulePath` valeur est utilisée lors du démarrage de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-171">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="d5aa9-172">Démarrage de PowerShell 7 à partir de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5aa9-172">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="d5aa9-173">Le démarrage de PowerShell 7 se poursuit comme avec l’ajout de chemins d’accès hérités ajoutés par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-173">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="d5aa9-174">Étant donné que les chemins d’accès spécifiques à PS7 sont préfixés, il n’y a aucun problème fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-174">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="d5aa9-175">Démarrage de PowerShell 6 à partir de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="d5aa9-175">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="d5aa9-176">PowerShell Core 6 remplace `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="d5aa9-176">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="d5aa9-177">Aucune modification n’est apportée.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-177">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="d5aa9-178">Démarrage de PowerShell 7 à partir de PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="d5aa9-178">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="d5aa9-179">Le démarrage de PowerShell 7 se poursuit comme avec l’ajout de chemins d’accès hérités que PowerShell Core 6 a ajoutés.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-179">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="d5aa9-180">Étant donné que les chemins d’accès spécifiques à PS7 sont préfixés, il n’y a aucun problème fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="d5aa9-180">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5aa9-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5aa9-181">See also</span></span>

- [<span data-ttu-id="d5aa9-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="d5aa9-182">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="d5aa9-183">Méthodes d’environnement</span><span class="sxs-lookup"><span data-stu-id="d5aa9-183">Environment Methods</span></span>](/dotnet/api/system.environment)