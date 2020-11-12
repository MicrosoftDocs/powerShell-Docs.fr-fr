---
description: La variable d’environnement PSModulePath contient une liste d’emplacements de dossiers dans lesquels rechercher les modules et les ressources.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 6e0307996bf619bc887b076a1f8c0faa619964fe
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524461"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="cf2b7-104">À propos de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="cf2b7-104">About PSModulePath</span></span>

<span data-ttu-id="cf2b7-105">La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span> <span data-ttu-id="cf2b7-106">PowerShell recherche de manière récursive chaque dossier pour les fichiers de module ( `.psd1` ou `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="cf2b7-106">PowerShell recursively searches each folder for module (`.psd1` or `.psm1`) files.</span></span>

<span data-ttu-id="cf2b7-107">Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-107">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="cf2b7-108">Emplacements à l’ensemble du système : ces dossiers contiennent des modules fournis avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-108">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="cf2b7-109">Ces modules sont stockés dans le `$PSHOME\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-109">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="cf2b7-110">Il s’agit également de l’emplacement d’installation des modules de gestion Windows.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-110">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="cf2b7-111">Modules installés par l’utilisateur : il s’agit de modules installés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-111">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="cf2b7-112">`Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-112">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="cf2b7-113">Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="cf2b7-113">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="cf2b7-114">Sur Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME\Documents\PowerShell\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-114">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="cf2b7-115">L’emplacement de l’étendue **ALLUSERS** est `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-115">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="cf2b7-116">Sur les systèmes non-Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME/.local/share/powershell/Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-116">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="cf2b7-117">L’emplacement de l’étendue **ALLUSERS** est `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-117">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="cf2b7-118">En outre, les programmes d’installation qui installent des modules dans d’autres répertoires, tels que le répertoire Program Files, peuvent ajouter leurs emplacements à la valeur de `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-118">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="cf2b7-119">Sur Windows, l’emplacement spécifique à l’utilisateur est le `PowerShell\Modules` dossier situé dans le dossier **documents** de votre profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-119">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="cf2b7-120">Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-120">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="cf2b7-121">Microsoft OneDrive peut également modifier l’emplacement de votre dossier **documents** .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-121">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="cf2b7-122">Vous pouvez vérifier l’emplacement de votre dossier **documents** à l’aide de la commande suivante : `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-122">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="cf2b7-123">Modification de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="cf2b7-123">Modifying PSModulePath</span></span>

<span data-ttu-id="cf2b7-124">Pour modifier les répertoires de module par défaut de la session active, utilisez le format de commande suivant pour modifier la valeur de la `PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-124">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="cf2b7-125">Par exemple, pour ajouter le `C:\Program Files\Fabrikam\Modules` répertoire à la valeur de la variable d’environnement PSModulePath, tapez :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-125">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="cf2b7-126">Le point-virgule ( `;` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-126">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="cf2b7-127">Sur les plateformes non-Windows, le signe deux-points ( `:` ) sépare les emplacements de chemin d’accès dans la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-127">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="cf2b7-128">Pour modifier la valeur de `PSModulePath` dans chaque session, ajoutez la commande précédente à votre profil PowerShell ou utilisez la méthode **SetEnvironmentVariable ne contient** de la classe d' **environnement** .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-128">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="cf2b7-129">La commande suivante utilise la méthode **GetEnvironmentVariable** pour récupérer le paramètre de l’ordinateur de `PSModulePath` et la méthode **SetEnvironmentVariable ne contient** pour ajouter le `C:\Program Files\Fabrikam\Modules` chemin d’accès à la valeur.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-129">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="cf2b7-130">Pour ajouter un chemin d’accès au paramètre utilisateur, remplacez la valeur cible par **utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-130">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="cf2b7-131">Pour plus d’informations sur les méthodes de la classe **System. Environment** , consultez [méthodes d’environnement](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="cf2b7-131">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="cf2b7-132">Construction de PSModulePath PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf2b7-132">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="cf2b7-133">La valeur de `$env:PSModulePath` est construite à chaque démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-133">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="cf2b7-134">La valeur varie en fonction de la version de PowerShell et de son mode de lancement.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-134">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="cf2b7-135">Démarrage de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf2b7-135">Windows PowerShell startup</span></span>

<span data-ttu-id="cf2b7-136">Windows PowerShell utilise la logique suivante pour construire au `PSModulePath` démarrage :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-136">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="cf2b7-137">Si `PSModulePath` n’existe pas, combinez **CurrentUser** , **ALLUSERS** et les `$PSHOME` chemins des modules</span><span class="sxs-lookup"><span data-stu-id="cf2b7-137">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="cf2b7-138">Si `PSModulePath` existe :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-138">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="cf2b7-139">Si `PSModulePath` contient le `$PSHOME` chemin des modules :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-139">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="cf2b7-140">Le chemin des modules **ALLUSERS** est inséré avant le `$PSHOME` chemin des modules</span><span class="sxs-lookup"><span data-stu-id="cf2b7-140">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="cf2b7-141">tierce</span><span class="sxs-lookup"><span data-stu-id="cf2b7-141">else:</span></span>
    - <span data-ttu-id="cf2b7-142">Utilisez simplement `PSModulePath` comme défini, car l’utilisateur a délibérément supprimé l' `$PSHOME` emplacement</span><span class="sxs-lookup"><span data-stu-id="cf2b7-142">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="cf2b7-143">Le chemin d’accès du module **CurrentUser** est préfixé uniquement si l’étendue de l’utilisateur `$env:PSModulePath` n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-143">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="cf2b7-144">Dans le cas contraire, l’étendue de l’utilisateur `$env:PSModulePath` est utilisée comme définie.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-144">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="cf2b7-145">Démarrage de PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="cf2b7-145">PowerShell Core 6 startup</span></span>

<span data-ttu-id="cf2b7-146">PowerShell Core 6 n’utilise pas le contenu de `$env:PSModulePath` s’il détecte qu’il a été démarré à partir de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-146">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="cf2b7-147">Il le remplace par :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-147">It overwrites it with:</span></span>

- <span data-ttu-id="cf2b7-148">**CurrentUser** modules chemin + **ALLUSERS** modules chemin + `$PSHOME` modules chemin + modules Windows PowerShell `$PSHOME` chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-148">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="cf2b7-149">Démarrage de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cf2b7-149">PowerShell 7 startup</span></span>

<span data-ttu-id="cf2b7-150">Dans Windows, pour la plupart des variables d’environnement, si la variable de portée utilisateur existe, un nouveau processus utilise cette valeur uniquement s’il existe une variable de portée ordinateur portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-150">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="cf2b7-151">Dans PowerShell 7, `PSModulePath` est traité de façon similaire à la façon dont la `Path` variable d’environnement est traitée sur Windows.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-151">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="cf2b7-152">Sur Windows, `Path` est traité différemment des autres variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-152">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="cf2b7-153">Quand un processus est démarré, Windows combine l’étendue de l’utilisateur `Path` avec l’étendue de l’ordinateur `Path` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-153">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="cf2b7-154">Récupérer l’étendue de l’utilisateur `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="cf2b7-154">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="cf2b7-155">Comparer pour traiter la `PSModulePath` variable d’environnement héritée</span><span class="sxs-lookup"><span data-stu-id="cf2b7-155">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="cf2b7-156">Si le même :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-156">If the same:</span></span>
    - <span data-ttu-id="cf2b7-157">Ajoutez le **ALLUSERS** `PSModulePath` à la fin suivant la sémantique de la `Path` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-157">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="cf2b7-158">Le `System32` chemin d’accès Windows provient de l’ordinateur défini `PSModulePath` , il n’est donc pas nécessaire de l’ajouter explicitement</span><span class="sxs-lookup"><span data-stu-id="cf2b7-158">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="cf2b7-159">Si différent, Treat comme si l’utilisateur l’avait explicitement modifié et n’ajoute pas **ALLUSERS**`PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="cf2b7-159">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="cf2b7-160">Préfixe avec utilisateur, système et `$PSHOME` chemins d’accès PS7 dans cet ordre</span><span class="sxs-lookup"><span data-stu-id="cf2b7-160">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="cf2b7-161">Si `powershell.config.json` contient une étendue d’utilisateur `PSModulePath` , utilisez-le à la place de la valeur par défaut pour l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="cf2b7-161">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="cf2b7-162">Si `powershell.config.json` contient une portée système `PSModulePath` , utilisez-le à la place de la valeur par défaut pour le système.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-162">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="cf2b7-163">Les systèmes UNIX n’ont pas de séparation entre les variables d’environnement utilisateur et système.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-163">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="cf2b7-164">`PSModulePath` est hérité et les chemins d’accès spécifiques à PS7 sont préfixés s’ils ne sont pas déjà définis.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-164">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="cf2b7-165">Démarrage de Windows PowerShell à partir de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cf2b7-165">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="cf2b7-166">Pour cette discussion, _Windows PowerShell_ signifie à la fois `powershell.exe` et `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-166">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="cf2b7-167">La valeur de `$env:PSModulePath` est copiée vers `WinPSModulePath` avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-167">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="cf2b7-168">Supprimer PS7 le chemin d’accès au module utilisateur</span><span class="sxs-lookup"><span data-stu-id="cf2b7-168">Remove PS7 the User module path</span></span>
- <span data-ttu-id="cf2b7-169">Supprimer PS7 le chemin d’accès au module système</span><span class="sxs-lookup"><span data-stu-id="cf2b7-169">Remove PS7 the System module path</span></span>
- <span data-ttu-id="cf2b7-170">Supprimer PS7 le `$PSHOME` chemin d’accès au module</span><span class="sxs-lookup"><span data-stu-id="cf2b7-170">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="cf2b7-171">Les chemins d’accès PS7 sont supprimés afin que les modules PS7 ne soient pas chargés dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-171">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="cf2b7-172">La `WinPSModulePath` valeur est utilisée lors du démarrage de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-172">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="cf2b7-173">Démarrage de PowerShell 7 à partir de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf2b7-173">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="cf2b7-174">Le démarrage de PowerShell 7 se poursuit comme avec l’ajout de chemins d’accès hérités ajoutés par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-174">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="cf2b7-175">Étant donné que les chemins d’accès spécifiques à PS7 sont préfixés, il n’y a aucun problème fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-175">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="cf2b7-176">Démarrage de PowerShell 6 à partir de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cf2b7-176">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="cf2b7-177">PowerShell Core 6 remplace `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-177">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="cf2b7-178">Aucune modification n’est apportée.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-178">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="cf2b7-179">Démarrage de PowerShell 7 à partir de PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="cf2b7-179">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="cf2b7-180">Le démarrage de PowerShell 7 se poursuit comme avec l’ajout de chemins d’accès hérités que PowerShell Core 6 a ajoutés.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-180">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="cf2b7-181">Étant donné que les chemins d’accès spécifiques à PS7 sont préfixés, il n’y a aucun problème fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-181">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="module-search-behavior"></a><span data-ttu-id="cf2b7-182">Comportement de recherche de module</span><span class="sxs-lookup"><span data-stu-id="cf2b7-182">Module search behavior</span></span>

<span data-ttu-id="cf2b7-183">PowerShell effectue une recherche récursive dans chaque dossier du **PSModulePath** pour les fichiers de module ( `.psd1` ou `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="cf2b7-183">PowerShell recursively searches each folder in the **PSModulePath** for module (`.psd1` or `.psm1`) files.</span></span> <span data-ttu-id="cf2b7-184">Ce modèle de recherche permet d’installer plusieurs versions du même module dans des dossiers différents.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-184">This search pattern allows multiple versions of the same module to be installed in different folders.</span></span> <span data-ttu-id="cf2b7-185">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf2b7-185">For example:</span></span>

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

<span data-ttu-id="cf2b7-186">Par défaut, PowerShell charge le numéro de version le plus élevé d’un module lorsque plusieurs versions sont trouvées.</span><span class="sxs-lookup"><span data-stu-id="cf2b7-186">By default, PowerShell loads the highest version number of a module when multiple versions are found.</span></span> <span data-ttu-id="cf2b7-187">Pour charger une version spécifique, utilisez `Import-Module` avec le paramètre **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="cf2b7-187">To load a specific version, use `Import-Module` with the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="cf2b7-188">Pour plus d’informations, voir [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span><span class="sxs-lookup"><span data-stu-id="cf2b7-188">For more information, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf2b7-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf2b7-189">See also</span></span>

- [<span data-ttu-id="cf2b7-190">about_Modules</span><span class="sxs-lookup"><span data-stu-id="cf2b7-190">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="cf2b7-191">Méthodes d’environnement</span><span class="sxs-lookup"><span data-stu-id="cf2b7-191">Environment Methods</span></span>](/dotnet/api/system.environment)
