---
title: Migration de Windows PowerShell 5.1 vers PowerShell 7
description: Mise à jour de PowerShell 5.1 vers PowerShell 7 pour vos plateformes Windows.
ms.date: 03/25/2020
ms.openlocfilehash: e3881b1758f50119444969ad39541aec694cebe5
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500500"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="f1b33-103">Migration de Windows PowerShell 5.1 vers PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="f1b33-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="f1b33-104">Conçu pour les environnements cloud, locaux et hybrides, PowerShell 7 intègre de nombreuses améliorations et [nouvelles fonctionnalités](What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="f1b33-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="f1b33-105">S’installe et s’exécute côte à côte avec Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1b33-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="f1b33-106">Meilleure compatibilité avec les modules Windows PowerShell existants</span><span class="sxs-lookup"><span data-stu-id="f1b33-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="f1b33-107">Nouvelles fonctionnalités de langage, notamment les opérateurs ternaires et `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="f1b33-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="f1b33-108">performances améliorées</span><span class="sxs-lookup"><span data-stu-id="f1b33-108">Improved performance</span></span>
- <span data-ttu-id="f1b33-109">Communication à distance basée sur SSH</span><span class="sxs-lookup"><span data-stu-id="f1b33-109">SSH-based remoting</span></span>
- <span data-ttu-id="f1b33-110">Interopérabilité multiplateforme</span><span class="sxs-lookup"><span data-stu-id="f1b33-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="f1b33-111">Prise en charge des conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="f1b33-111">Support for Docker containers</span></span>

<span data-ttu-id="f1b33-112">PowerShell 7 fonctionne côte à côte avec Windows PowerShell, ce qui vous permet de tester et de comparer facilement différentes versions avant le déploiement.</span><span class="sxs-lookup"><span data-stu-id="f1b33-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="f1b33-113">La migration est simple, rapide et sécurisée.</span><span class="sxs-lookup"><span data-stu-id="f1b33-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="f1b33-114">échec.</span><span class="sxs-lookup"><span data-stu-id="f1b33-114">failure.</span></span>

<span data-ttu-id="f1b33-115">PowerShell 7 est pris en charge sur les systèmes d'exploitation Windows suivants :</span><span class="sxs-lookup"><span data-stu-id="f1b33-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="f1b33-116">Windows 8.1 et 10</span><span class="sxs-lookup"><span data-stu-id="f1b33-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="f1b33-117">Windows Server 2012, 2012 R2, 2016 et 2019</span><span class="sxs-lookup"><span data-stu-id="f1b33-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="f1b33-118">PowerShell 7 s’exécute également sur macOS et plusieurs distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="f1b33-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="f1b33-119">Pour obtenir une liste des systèmes d’exploitation pris en charge et des informations sur le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="f1b33-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="f1b33-120">Installation de PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="f1b33-120">Installing PowerShell 7</span></span>

<span data-ttu-id="f1b33-121">Pour offrir plus de flexibilité et répondre aux besoins du service informatique, des ingénieurs DevOps et des développeurs, plusieurs options d’installation de PowerShell 7 sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="f1b33-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="f1b33-122">Dans la plupart des cas, les options d’installation peuvent se limiter aux méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1b33-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="f1b33-123">Déployer PowerShell à l’aide du [package MSI](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="f1b33-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="f1b33-124">Déployer PowerShell à l’aide du [package ZIP](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="f1b33-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="f1b33-125">Le package MSI peut être déployé et mis à jour avec des produits de gestion, notamment [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span><span class="sxs-lookup"><span data-stu-id="f1b33-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="f1b33-126">Téléchargez les packages à partir de la [page de mise en production GitHub](https://github.com/PowerShell/PowerShell/releases).</span><span class="sxs-lookup"><span data-stu-id="f1b33-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="f1b33-127">Le déploiement du package MSI nécessite une autorisation d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f1b33-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="f1b33-128">Le package ZIP peut être déployé par n’importe quel utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1b33-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="f1b33-129">Le package ZIP constitue le moyen le plus simple d’installer PowerShell 7 à des fins de test, avant de procéder à une installation complète.</span><span class="sxs-lookup"><span data-stu-id="f1b33-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="f1b33-130">Utilisation de PowerShell 7 côte à côte avec Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f1b33-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="f1b33-131">PowerShell 7 est conçu pour coexister avec Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="f1b33-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="f1b33-132">Les fonctionnalités suivantes protègent votre investissement dans PowerShell et simplifient la migration vers PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="f1b33-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="f1b33-133">Chemins d’installation et noms d’exécutables distincts</span><span class="sxs-lookup"><span data-stu-id="f1b33-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="f1b33-134">PSModulePath distinct</span><span class="sxs-lookup"><span data-stu-id="f1b33-134">Separate PSModulePath</span></span>
- <span data-ttu-id="f1b33-135">Profils distincts pour chaque version</span><span class="sxs-lookup"><span data-stu-id="f1b33-135">Separate profiles for each version</span></span>
- <span data-ttu-id="f1b33-136">Compatibilité améliorée des modules</span><span class="sxs-lookup"><span data-stu-id="f1b33-136">Improved module compatibility</span></span>
- <span data-ttu-id="f1b33-137">Nouveaux points de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="f1b33-137">New remoting endpoints</span></span>
- <span data-ttu-id="f1b33-138">Prise en charge de la stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="f1b33-138">Group policy support</span></span>
- <span data-ttu-id="f1b33-139">Journaux d’événements distincts</span><span class="sxs-lookup"><span data-stu-id="f1b33-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="f1b33-140">Chemins d’installation et noms d’exécutables distincts</span><span class="sxs-lookup"><span data-stu-id="f1b33-140">Separate installation path and executable name</span></span>

<span data-ttu-id="f1b33-141">PowerShell 7 s’installe dans un nouveau répertoire, permettant une exécution côte à côte avec Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="f1b33-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="f1b33-142">Emplacements d’installation par version :</span><span class="sxs-lookup"><span data-stu-id="f1b33-142">Install locations by version:</span></span>

- <span data-ttu-id="f1b33-143">Windows PowerShell 5.1 : `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="f1b33-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="f1b33-144">PowerShell Core 6.x : `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="f1b33-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="f1b33-145">PowerShell 7 : `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="f1b33-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="f1b33-146">Le nouvel emplacement est ajouté à votre chemin d’accès, ce qui vous permet d’exécuter à la fois Windows PowerShell 5.1 et PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="f1b33-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="f1b33-147">Si vous effectuez une migration de PowerShell Core 6.x vers PowerShell 7, PowerShell 6 est supprimé et le chemin d’accès remplacé.</span><span class="sxs-lookup"><span data-stu-id="f1b33-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="f1b33-148">Dans Windows PowerShell, l’exécutable PowerShell est nommé `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="f1b33-149">Dans la version 6 et versions ultérieures, l’exécutable est nommé `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="f1b33-150">Le nouveau nom facilite la prise en charge de l’exécution côte à côte des deux versions.</span><span class="sxs-lookup"><span data-stu-id="f1b33-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="f1b33-151">PSModulePath distinct</span><span class="sxs-lookup"><span data-stu-id="f1b33-151">Separate PSModulePath</span></span>

<span data-ttu-id="f1b33-152">Par défaut, Windows PowerShell et PowerShell 7 stockent les modules à différents emplacements.</span><span class="sxs-lookup"><span data-stu-id="f1b33-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="f1b33-153">PowerShell 7 combine ces emplacements dans la variable d’environnement `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="f1b33-154">Lors de l’importation d’un module par nom, PowerShell vérifie l’emplacement spécifié par `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="f1b33-155">Cela permet à PowerShell 7 de charger à la fois les modules de base et de bureau.</span><span class="sxs-lookup"><span data-stu-id="f1b33-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="f1b33-156">Étendue Install</span><span class="sxs-lookup"><span data-stu-id="f1b33-156">Install Scope</span></span>            |                <span data-ttu-id="f1b33-157">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f1b33-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="f1b33-158">PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="f1b33-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="f1b33-159">Modules PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1b33-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="f1b33-160">Installé par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="f1b33-160">User installed</span></span><br><span data-ttu-id="f1b33-161">Étendue AllUsers</span><span class="sxs-lookup"><span data-stu-id="f1b33-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="f1b33-162">Installé par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="f1b33-162">User installed</span></span><br><span data-ttu-id="f1b33-163">Étendue CurrentUser</span><span class="sxs-lookup"><span data-stu-id="f1b33-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="f1b33-164">Les exemples suivants montrent les valeurs par défaut de `$Env:PSModulePath` pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="f1b33-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="f1b33-165">Pour Windows PowerShell 5.1 :</span><span class="sxs-lookup"><span data-stu-id="f1b33-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="f1b33-166">Pour PowerShell 7 :</span><span class="sxs-lookup"><span data-stu-id="f1b33-166">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="f1b33-167">Notez que PowerShell 7 inclut les chemins d’accès Windows PowerShell et les chemins d’accès PowerShell 7 pour garantir le chargement automatique des modules.</span><span class="sxs-lookup"><span data-stu-id="f1b33-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="f1b33-168">Des chemins d’accès supplémentaires peuvent exister si vous avez modifié la variable d’environnement PSModulePath ou si vous avez installé des modules ou des applications personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f1b33-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="f1b33-169">Pour plus d’informations, consultez `PSModulePath` dans [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span><span class="sxs-lookup"><span data-stu-id="f1b33-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="f1b33-170">Pour plus d'informations sur les modules, consultez [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span><span class="sxs-lookup"><span data-stu-id="f1b33-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="f1b33-171">Profils distincts</span><span class="sxs-lookup"><span data-stu-id="f1b33-171">Separate profiles</span></span>

<span data-ttu-id="f1b33-172">Un profil PowerShell est un script qui s’exécute au démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1b33-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="f1b33-173">Ce script personnalise votre environnement en ajoutant des commandes, des alias, des fonctions, des variables, des modules et des lecteurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1b33-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="f1b33-174">Le script de profil rend ces personnalisations disponibles dans chaque session, sans avoir à les recréer manuellement.</span><span class="sxs-lookup"><span data-stu-id="f1b33-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="f1b33-175">Le chemin d’accès vers l’emplacement du profil a changé dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="f1b33-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="f1b33-176">Dans Windows PowerShell 5,1, l’emplacement du profil est `$HOME\Documents\WindowsPowerShell`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="f1b33-177">Dans PowerShell 7, l’emplacement du profil est `$HOME\Documents\PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="f1b33-178">Les noms des fichiers de profil ont également changé :</span><span class="sxs-lookup"><span data-stu-id="f1b33-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="f1b33-179">Pour plus d'informations, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="f1b33-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="f1b33-180">Compatibilité de PowerShell 7 avec les modules Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f1b33-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="f1b33-181">La plupart des modules que vous utilisez dans Windows PowerShell 5.1 fonctionnent déjà avec PowerShell 7, y compris Azure PowerShell et Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f1b33-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="f1b33-182">Nous continuons à collaborer avec d’autres équipes afin d’ajouter une prise en charge native de PowerShell 7 pour d’autres modules, notamment Microsoft Graph, Office 365, entre autres.</span><span class="sxs-lookup"><span data-stu-id="f1b33-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="f1b33-183">Pour obtenir la liste actuelle des modules pris en charge, consultez [Compatibilité des modules PowerShell 7](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="f1b33-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="f1b33-184">Sur Windows, nous avons également ajouté un commutateur **UseWindowsPowerShell** vers `Import-Module` afin de faciliter la transition vers PowerShell 7 pour ceux qui utilisent des modules incompatibles.</span><span class="sxs-lookup"><span data-stu-id="f1b33-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="f1b33-185">Pour plus d’informations sur cette fonctionnalité, consultez [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span><span class="sxs-lookup"><span data-stu-id="f1b33-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="f1b33-186">Communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1b33-186">PowerShell Remoting</span></span>

<span data-ttu-id="f1b33-187">La communication à distance PowerShell, vous permet d'exécuter n'importe quelle commande PowerShell sur un ou plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f1b33-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="f1b33-188">Vous pouvez établir des connexions persistantes, démarrer des sessions interactives et exécuter des scripts sur ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f1b33-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="f1b33-189">Communication à distance WS-Management</span><span class="sxs-lookup"><span data-stu-id="f1b33-189">WS-Management remoting</span></span>

<span data-ttu-id="f1b33-190">Windows PowerShell 5.1 et les versions antérieures utilisent le protocole WS-Management (WSMAN) pour la négociation de connexion et le transport de données.</span><span class="sxs-lookup"><span data-stu-id="f1b33-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="f1b33-191">Windows Remote Management (WinRM) utilise le protocole WSMAN.</span><span class="sxs-lookup"><span data-stu-id="f1b33-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="f1b33-192">Si WinRM a été activé, PowerShell 7 utilise le point de terminaison Windows PowerShell 5.1 existant, nommé `Microsoft.PowerShell`, pour les connexions de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="f1b33-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="f1b33-193">Pour mettre à jour PowerShell 7 afin d’inclure son propre point de terminaison, exécutez l’applet de commande `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="f1b33-194">Pour plus d’informations sur la connexion à des points de terminaison spécifiques, consultez [Communication à distance WS-Management dans PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="f1b33-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="f1b33-195">Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="f1b33-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="f1b33-196">Pour obtenir plus d’informations, notamment des instructions, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="f1b33-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="f1b33-197">Pour plus d'informations sur l’utilisation de la communication à distance, consultez [À propos de la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote)</span><span class="sxs-lookup"><span data-stu-id="f1b33-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="f1b33-198">Communication à distance basée sur SSH</span><span class="sxs-lookup"><span data-stu-id="f1b33-198">SSH-based remoting</span></span>

<span data-ttu-id="f1b33-199">La communication à distance basée sur SSH a été ajoutée dans PowerShell Core 6.x pour prendre en charge d’autres systèmes d’exploitation qui ne peuvent pas utiliser des composants natifs Windows comme **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="f1b33-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="f1b33-200">La communication à distance SSH crée un processus hôte PowerShell sur l’ordinateur cible en tant que sous-système SSH.</span><span class="sxs-lookup"><span data-stu-id="f1b33-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="f1b33-201">Pour obtenir des informations et des exemples sur la configuration de la communication à distance basée sur SSH sur Windows ou Linux, consultez : [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="f1b33-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="f1b33-202">PowerShell Gallery (PSGallery) contient un module et une applet de commande qui configure automatiquement la communication à distance basée sur SSH.</span><span class="sxs-lookup"><span data-stu-id="f1b33-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="f1b33-203">Installez le module `Microsoft.PowerShell.RemotingTools` à partir de [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0), puis exécutez l’applet de commande `Enable-SSH`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="f1b33-204">Les applets de commande `New-PSSession`, `Enter-PSSession` et `Invoke-Command` intègrent de nouveaux jeux de paramètres pour prendre en charge les connexions SSH.</span><span class="sxs-lookup"><span data-stu-id="f1b33-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="f1b33-205">Pour créer une session distante, spécifiez l’ordinateur cible avec le paramètre **HostName** et indiquez le nom d’utilisateur avec **UserName**.</span><span class="sxs-lookup"><span data-stu-id="f1b33-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="f1b33-206">Lors de l’exécution des cmdlets de manière interactive, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f1b33-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="f1b33-207">Si vous utilisez le paramètre **HostName**, vous pouvez également fournir les informations de nom d’utilisateur en y ajoutant le signe arobase (@) et le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1b33-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign ('@'), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="f1b33-208">Vous pouvez configurer l’authentification par clé SSH à l’aide d’un fichier de clé privée avec le paramètre **KeyFilePath**.</span><span class="sxs-lookup"><span data-stu-id="f1b33-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="f1b33-209">Pour plus d’informations, consultez [Gestion des clés OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="f1b33-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="f1b33-210">Stratégie de groupe prise en charge</span><span class="sxs-lookup"><span data-stu-id="f1b33-210">Group Policy supported</span></span>

<span data-ttu-id="f1b33-211">PowerShell inclut des paramètres de stratégie de groupe qui vous aident à définir des valeurs d’option cohérentes pour les serveurs d’un environnement d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f1b33-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="f1b33-212">Ces paramètres comprennent ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f1b33-212">These settings include:</span></span>

- <span data-ttu-id="f1b33-213">Configuration de session de console : définit un point de terminaison de configuration dans lequel PowerShell est exécuté.</span><span class="sxs-lookup"><span data-stu-id="f1b33-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="f1b33-214">Activer la journalisation des modules : définit la propriété LogPipelineExecutionDetails des modules.</span><span class="sxs-lookup"><span data-stu-id="f1b33-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="f1b33-215">Activer la journalisation de blocs de scripts PowerShell : active la journalisation détaillée de tous les scripts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1b33-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="f1b33-216">Activer l’exécution des scripts : définit la stratégie d'exécution de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1b33-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="f1b33-217">Activer la transcription PowerShell : active la capture d’entrée et de sortie de commandes PowerShell dans des transcriptions textuelles.</span><span class="sxs-lookup"><span data-stu-id="f1b33-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="f1b33-218">Définir le chemin source par défaut pour Update-Help : définit la source de l’aide actualisable sur un répertoire, et non sur Internet.</span><span class="sxs-lookup"><span data-stu-id="f1b33-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="f1b33-219">Pour plus d’informations, consultez [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span><span class="sxs-lookup"><span data-stu-id="f1b33-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="f1b33-220">PowerShell 7 comprend des modèles de stratégie de groupe et un script d’installation dans `$PSHOME`.</span><span class="sxs-lookup"><span data-stu-id="f1b33-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="f1b33-221">Les outils de stratégie de groupe utilisent des fichiers de modèles d’administration (`.admx`, `.adml`) pour remplir les paramètres de stratégie dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1b33-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="f1b33-222">Cela permet aux administrateurs de gérer les paramètres de stratégie basés sur le registre.</span><span class="sxs-lookup"><span data-stu-id="f1b33-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="f1b33-223">Le script `InstallPSCorePolicyDefinitions.ps1` installe les modèles d’administration PowerShell Core sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f1b33-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="f1b33-224">Journaux d’événements distincts</span><span class="sxs-lookup"><span data-stu-id="f1b33-224">Separate Event Logs</span></span>

<span data-ttu-id="f1b33-225">Windows PowerShell et PowerShell 7 journalisent les événements dans des journaux d’événements distincts.</span><span class="sxs-lookup"><span data-stu-id="f1b33-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="f1b33-226">Utilisez la commande suivante pour obtenir la liste des journaux PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1b33-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="f1b33-227">Pour plus d’informations, consultez [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span><span class="sxs-lookup"><span data-stu-id="f1b33-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="f1b33-228">Amélioration de l’expérience de modification avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f1b33-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="f1b33-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) avec l’extension [PowerShell](https://code.visualstudio.com/docs/languages/powershell) est l’environnement de script pris en charge pour PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="f1b33-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="f1b33-230">Windows PowerShell Integrated Scripting Environment (ISE) prend uniquement en charge Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1b33-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="f1b33-231">L’extension PowerShell mise à jour comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f1b33-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="f1b33-232">Nouveau mode de compatibilité ISE</span><span class="sxs-lookup"><span data-stu-id="f1b33-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="f1b33-233">PSReadLine dans la console intégrée, notamment la mise en surbrillance de la syntaxe, la modification sur plusieurs lignes et la recherche en arrière</span><span class="sxs-lookup"><span data-stu-id="f1b33-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="f1b33-234">Améliorations en matière de stabilité et de performances</span><span class="sxs-lookup"><span data-stu-id="f1b33-234">Stability and performance improvements</span></span>
- <span data-ttu-id="f1b33-235">Nouvelle intégration CodeLens</span><span class="sxs-lookup"><span data-stu-id="f1b33-235">New CodeLens integration</span></span>
- <span data-ttu-id="f1b33-236">Amélioration de la saisie semi-automatique du chemin</span><span class="sxs-lookup"><span data-stu-id="f1b33-236">Improved path auto-completion</span></span>

<span data-ttu-id="f1b33-237">Pour faciliter la transition vers Visual Studio Code, utilisez la fonction **Activer le mode ISE**, disponible dans la **palette de commandes**.</span><span class="sxs-lookup"><span data-stu-id="f1b33-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="f1b33-238">Cette fonction bascule VSCode dans une disposition de style ISE.</span><span class="sxs-lookup"><span data-stu-id="f1b33-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="f1b33-239">La disposition de style ISE vous offre toutes les nouvelles fonctionnalités et capacités de PowerShell dans une expérience utilisateur familière.</span><span class="sxs-lookup"><span data-stu-id="f1b33-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="f1b33-240">Pour basculer vers la nouvelle disposition ISE, appuyez sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> pour ouvrir la **de la palette de commandes**, tapez `PowerShell` et sélectionnez **PowerShell : Activez le mode ISE**.</span><span class="sxs-lookup"><span data-stu-id="f1b33-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="f1b33-241">Pour revenir à la disposition d’origine, ouvrez la **palette de commandes**, puis sélectionnez **PowerShell : Désactiver le mode ISE (restaurer les valeurs par défaut)** .</span><span class="sxs-lookup"><span data-stu-id="f1b33-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="f1b33-242">Pour plus d’informations sur la personnalisation de la disposition VSCode pour ISE, consultez [Guide pratique de réplication de l’expérience ISE dans Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span><span class="sxs-lookup"><span data-stu-id="f1b33-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="f1b33-243">Aucune mise à jour de l’environnement ISE avec de nouvelles fonctionnalités n’est prévue.</span><span class="sxs-lookup"><span data-stu-id="f1b33-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="f1b33-244">L’environnement ISE est désormais une fonctionnalité qui n’est pas installée par l’utilisateur dans les dernières versions de Windows 10 et Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f1b33-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="f1b33-245">Il n’est pas prévu de supprimer définitivement l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="f1b33-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="f1b33-246">L’équipe PowerShell et ses partenaires se concentrent actuellement sur l’amélioration de l’expérience de script dans l’extension PowerShell pour Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f1b33-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f1b33-247">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f1b33-247">Next Steps</span></span>

<span data-ttu-id="f1b33-248">Maintenant que vous possédez les connaissances requises pour réussir votre migration, [installez PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) !</span><span class="sxs-lookup"><span data-stu-id="f1b33-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
