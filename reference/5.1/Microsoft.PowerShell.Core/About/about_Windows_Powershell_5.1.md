---
description: Décrit les nouvelles fonctionnalités incluses dans Windows PowerShell 5,1.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208741"
---
# <a name="about_windows_powershell_51"></a><span data-ttu-id="d379c-104">about_Windows_PowerShell_5.1</span><span class="sxs-lookup"><span data-stu-id="d379c-104">about_Windows_PowerShell_5.1</span></span>

## <a name="short-description"></a><span data-ttu-id="d379c-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="d379c-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d379c-106">Décrit les nouvelles fonctionnalités incluses dans Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="d379c-106">Describes new features that are included in Windows PowerShell 5.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="d379c-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="d379c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d379c-108">Windows PowerShell 5,1 comprend de nouvelles fonctionnalités importantes qui étendent son utilisation, améliorent sa convivialité et vous permettent de contrôler et de gérer des environnements Windows plus facilement et de manière plus complète.</span><span class="sxs-lookup"><span data-stu-id="d379c-108">Windows PowerShell 5.1 includes significant new features that extend its use, improve its usability, and allow you to control and manage Windows-based environments more easily and comprehensively.</span></span>

<span data-ttu-id="d379c-109">Windows PowerShell 5,1 est à compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="d379c-109">Windows PowerShell 5.1 is backward-compatible.</span></span> <span data-ttu-id="d379c-110">Les applets de commande, fournisseurs, modules, composants logiciels enfichables, scripts, fonctions et profils conçus pour Windows PowerShell 4,0, Windows PowerShell 3,0 et Windows PowerShell 2,0 fonctionnent généralement dans Windows PowerShell 5,1 sans aucune modification.</span><span class="sxs-lookup"><span data-stu-id="d379c-110">Cmdlets, providers, modules, snap-ins, scripts, functions, and profiles that were designed for Windows PowerShell 4.0, Windows PowerShell 3.0, and Windows PowerShell 2.0 generally work in Windows PowerShell 5.1 without changes.</span></span>

- <span data-ttu-id="d379c-111">Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="d379c-111">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="d379c-112">Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA</span><span class="sxs-lookup"><span data-stu-id="d379c-112">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="d379c-113">Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB</span><span class="sxs-lookup"><span data-stu-id="d379c-113">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="d379c-114">Améliorations du débogage pour les classes DSC et PowerShell</span><span class="sxs-lookup"><span data-stu-id="d379c-114">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="d379c-115">Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d379c-115">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="d379c-116">Réponses à plusieurs demandes et problèmes des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d379c-116">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="d379c-117">Windows PowerShell 5,1 est installé par défaut sur Windows Server 2016 et Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d379c-117">Windows PowerShell 5.1 is installed by default on Windows Server 2016 and Windows 10.</span></span> <span data-ttu-id="d379c-118">Pour installer Windows PowerShell 5,1 sur Windows Server 2012 R2, Windows 8.1 Enterprise ou Windows 8.1 Pro, consultez [installer et configurer WMF 5,1](/powershell/scripting/wmf/setup/install-configure).</span><span class="sxs-lookup"><span data-stu-id="d379c-118">To install Windows PowerShell 5.1 on Windows Server 2012 R2, Windows 8.1 Enterprise, or Windows 8.1 Pro, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>
<span data-ttu-id="d379c-119">Veillez à lire les détails du téléchargement et à respecter la configuration requise avant d’installer Windows Management Framework 5,1.</span><span class="sxs-lookup"><span data-stu-id="d379c-119">Be sure to read the download details, and meet all system requirements, before you install Windows Management Framework 5.1.</span></span>

<span data-ttu-id="d379c-120">Vous pouvez également en savoir plus sur les modifications apportées à Windows PowerShell 5,1 dans [Nouveautés de Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).</span><span class="sxs-lookup"><span data-stu-id="d379c-120">You can also read about changes to Windows PowerShell 5.1 in [What's New in Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).</span></span>

## <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="d379c-121">Nouveaux scénarios et fonctionnalités dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d379c-121">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="d379c-122">Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.</span><span class="sxs-lookup"><span data-stu-id="d379c-122">Note: This information is preliminary and subject to change.</span></span>

### <a name="powershell-editions"></a><span data-ttu-id="d379c-123">Éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d379c-123">PowerShell Editions</span></span>
<span data-ttu-id="d379c-124">À compter de la version 5.1, PowerShell est disponible dans plusieurs éditions, dont les ensembles de fonctionnalités et la compatibilité de plateforme diffèrent.</span><span class="sxs-lookup"><span data-stu-id="d379c-124">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="d379c-125">**Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="d379c-125">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="d379c-126">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="d379c-126">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="d379c-127">**En savoir plus sur l’utilisation des éditions de PowerShell**</span><span class="sxs-lookup"><span data-stu-id="d379c-127">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="d379c-128">Déterminer la version en cours d’exécution de PowerShell à l’aide de $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="d379c-128">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="d379c-129">Filtrer les résultats de Get-Module par CompatiblePSEditions à l’aide du paramètre PSEdition</span><span class="sxs-lookup"><span data-stu-id="d379c-129">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="d379c-130">Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d379c-130">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="d379c-131">Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d379c-131">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a><span data-ttu-id="d379c-132">Applets de commande de catalogue</span><span class="sxs-lookup"><span data-stu-id="d379c-132">Catalog Cmdlets</span></span>

<span data-ttu-id="d379c-133">Deux nouvelles applets de commande ont été ajoutées au module [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) pour générer et valider des fichiers catalogue Windows.</span><span class="sxs-lookup"><span data-stu-id="d379c-133">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) module; these generate and validate Windows catalog files.</span></span>

#### <a name="new-filecatalog"></a><span data-ttu-id="d379c-134">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="d379c-134">New-FileCatalog</span></span>

<span data-ttu-id="d379c-135">New-FileCatalog crée un fichier catalogue Windows pour un ensemble de dossiers et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d379c-135">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="d379c-136">Ce fichier catalogue contient des hachages pour tous les fichiers dans les chemins spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d379c-136">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="d379c-137">Les utilisateurs peuvent distribuer l’ensemble des dossiers ainsi que le fichier catalogue correspondant représentant ces dossiers.</span><span class="sxs-lookup"><span data-stu-id="d379c-137">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="d379c-138">Ces informations sont utiles pour vérifier si des modifications ont été apportées aux dossiers depuis l’heure de création du catalogue.</span><span class="sxs-lookup"><span data-stu-id="d379c-138">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="d379c-139">Les versions de catalogues 1 et 2 sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="d379c-139">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="d379c-140">La version 1 utilise l’algorithme de hachage SHA1 pour créer des fichiers à hacher et la version 2 utilise SHA256.</span><span class="sxs-lookup"><span data-stu-id="d379c-140">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="d379c-141">La version de catalogue 2 n’est pas prise en charge sur *Windows Server 2008 R2* ni *Windows 7* .</span><span class="sxs-lookup"><span data-stu-id="d379c-141">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7* .</span></span> <span data-ttu-id="d379c-142">Vous devez utiliser la version de catalogue 2 sur *Windows 8* , *Windows Server 2012* et les systèmes d’exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="d379c-142">You should use catalog version 2 on *Windows 8* , *Windows Server 2012* , and later operating systems.</span></span>

<span data-ttu-id="d379c-143">Pour vérifier l’intégrité du fichier catalogue (Pester.cat dans l’exemple ci-dessus), signez-le à l’aide de l’applet de commande [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature).</span><span class="sxs-lookup"><span data-stu-id="d379c-143">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) cmdlet.</span></span>

#### <a name="test-filecatalog"></a><span data-ttu-id="d379c-144">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="d379c-144">Test-FileCatalog</span></span>

<span data-ttu-id="d379c-145">Test-FileCatalog valide le catalogue qui représente un ensemble de dossiers.</span><span class="sxs-lookup"><span data-stu-id="d379c-145">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="d379c-146">Cette applet de commande compare tous les fichiers à hacher et leurs chemins relatifs qui figurent dans le *catalogue* à ceux sur le *disque* .</span><span class="sxs-lookup"><span data-stu-id="d379c-146">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk* .</span></span> <span data-ttu-id="d379c-147">Si elle détecte une incompatibilité entre les fichiers à hacher et les chemins, elle retourne le statut *ValidationFailed* .</span><span class="sxs-lookup"><span data-stu-id="d379c-147">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed* .</span></span> <span data-ttu-id="d379c-148">Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre *-Detailed* .</span><span class="sxs-lookup"><span data-stu-id="d379c-148">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="d379c-149">Elle affiche également le statut de signature du catalogue dans la propriété *Signature* , ce qui revient à appeler l’applet de commande [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) sur le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="d379c-149">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) cmdlet on the catalog file.</span></span> <span data-ttu-id="d379c-150">Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre *-FilesToSkip* .</span><span class="sxs-lookup"><span data-stu-id="d379c-150">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

### <a name="module-analysis-cache"></a><span data-ttu-id="d379c-151">Cache d’analyse de module</span><span class="sxs-lookup"><span data-stu-id="d379c-151">Module Analysis Cache</span></span>

<span data-ttu-id="d379c-152">À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.</span><span class="sxs-lookup"><span data-stu-id="d379c-152">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="d379c-153">Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="d379c-153">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="d379c-154">Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="d379c-154">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="d379c-155">Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement `$env:PSModuleAnalysisCachePath` avant de démarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d379c-155">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="d379c-156">Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="d379c-156">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="d379c-157">La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.</span><span class="sxs-lookup"><span data-stu-id="d379c-157">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="d379c-158">Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :</span><span class="sxs-lookup"><span data-stu-id="d379c-158">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="d379c-159">Cela définit un appareil non valide comme chemin.</span><span class="sxs-lookup"><span data-stu-id="d379c-159">This sets the path to an invalid device.</span></span> <span data-ttu-id="d379c-160">Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée, mais vous pouvez observer la présence d’une erreur signalée à l’aide d’un suivi :</span><span class="sxs-lookup"><span data-stu-id="d379c-160">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

<span data-ttu-id="d379c-161">Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement.</span><span class="sxs-lookup"><span data-stu-id="d379c-161">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="d379c-162">Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d379c-162">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="d379c-163">Cette variable d’environnement prend effet immédiatement dans le processus actif.</span><span class="sxs-lookup"><span data-stu-id="d379c-163">Setting this environment variable will take effect immediately in the current process.</span></span>

### <a name="specifying-module-version"></a><span data-ttu-id="d379c-164">Spécification de la version de module</span><span class="sxs-lookup"><span data-stu-id="d379c-164">Specifying module version</span></span>

<span data-ttu-id="d379c-165">Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d379c-165">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="d379c-166">Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.</span><span class="sxs-lookup"><span data-stu-id="d379c-166">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="d379c-167">Dans WMF 5.1 :</span><span class="sxs-lookup"><span data-stu-id="d379c-167">In WMF 5.1:</span></span>

* <span data-ttu-id="d379c-168">Vous pouvez utiliser [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).</span><span class="sxs-lookup"><span data-stu-id="d379c-168">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).</span></span>
  <span data-ttu-id="d379c-169">Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="d379c-169">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="d379c-170">**Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="d379c-170">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="d379c-171">S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).</span><span class="sxs-lookup"><span data-stu-id="d379c-171">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

### <a name="improvements-to-pester"></a><span data-ttu-id="d379c-172">Améliorations apportées à Pester</span><span class="sxs-lookup"><span data-stu-id="d379c-172">Improvements to Pester</span></span>

<span data-ttu-id="d379c-173">Dans WMF 5,1, la version de pester fournie avec PowerShell a été mise à jour de 3.3.5 à 3.4.0, avec l’ajout de GitHub [PR # 484](https://github.com/pester/Pester/pull/484), ce qui permet un meilleur comportement pour pester sur nano Server.</span><span class="sxs-lookup"><span data-stu-id="d379c-173">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of GitHub [PR# 484](https://github.com/pester/Pester/pull/484), which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="d379c-174">Vous pouvez examiner les modifications des versions 3.3.5 à 3.4.0 dans le fichier ChangeLog.md qui se trouve ici : https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="d379c-174">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

## <a name="keywords"></a><span data-ttu-id="d379c-175">MOT</span><span class="sxs-lookup"><span data-stu-id="d379c-175">KEYWORDS</span></span>

<span data-ttu-id="d379c-176">Nouveautés de Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="d379c-176">What's New in Windows PowerShell 5.1</span></span>
