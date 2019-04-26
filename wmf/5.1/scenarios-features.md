---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Nouveaux scénarios et fonctionnalités dans WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085428"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="52efc-103">Nouveaux scénarios et fonctionnalités dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="52efc-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="52efc-104">Remarque : Ces informations sont provisoires et sujettes à modification.</span><span class="sxs-lookup"><span data-stu-id="52efc-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="52efc-105">Éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="52efc-105">PowerShell Editions</span></span>

<span data-ttu-id="52efc-106">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="52efc-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="52efc-107">**Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="52efc-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="52efc-108">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="52efc-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="52efc-109">**En savoir plus sur l’utilisation des éditions de PowerShell**</span><span class="sxs-lookup"><span data-stu-id="52efc-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="52efc-110">Déterminer la version en cours d’exécution de PowerShell à l’aide de $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="52efc-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="52efc-111">Filtrer les résultats de Get-Module par CompatiblePSEditions à l’aide du paramètre PSEdition</span><span class="sxs-lookup"><span data-stu-id="52efc-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="52efc-112">Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell</span><span class="sxs-lookup"><span data-stu-id="52efc-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="52efc-113">Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell</span><span class="sxs-lookup"><span data-stu-id="52efc-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="52efc-114">Applets de commande de catalogue</span><span class="sxs-lookup"><span data-stu-id="52efc-114">Catalog Cmdlets</span></span>

<span data-ttu-id="52efc-115">Deux nouvelles applets de commande ont été ajoutées au module [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) pour générer et valider des fichiers catalogue Windows.</span><span class="sxs-lookup"><span data-stu-id="52efc-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="52efc-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="52efc-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="52efc-117">New-FileCatalog crée un fichier catalogue Windows pour un ensemble de dossiers et de fichiers.</span><span class="sxs-lookup"><span data-stu-id="52efc-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="52efc-118">Ce fichier catalogue contient des hachages pour tous les fichiers dans les chemins spécifiés.</span><span class="sxs-lookup"><span data-stu-id="52efc-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="52efc-119">Les utilisateurs peuvent distribuer l’ensemble des dossiers ainsi que le fichier catalogue correspondant représentant ces dossiers.</span><span class="sxs-lookup"><span data-stu-id="52efc-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="52efc-120">Ces informations sont utiles pour vérifier si des modifications ont été apportées aux dossiers depuis l’heure de création du catalogue.</span><span class="sxs-lookup"><span data-stu-id="52efc-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="52efc-121">Les versions de catalogues 1 et 2 sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="52efc-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="52efc-122">La version 1 utilise l’algorithme de hachage SHA1 pour créer des fichiers à hacher et la version 2 utilise SHA256.</span><span class="sxs-lookup"><span data-stu-id="52efc-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="52efc-123">La version de catalogue 2 n’est pas prise en charge sur *Windows Server 2008 R2* ni *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="52efc-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="52efc-124">Vous devez utiliser la version de catalogue 2 sur *Windows 8*, *Windows Server 2012* et les systèmes d’exploitation ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="52efc-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="52efc-125">Le fichier catalogue est ainsi créé.</span><span class="sxs-lookup"><span data-stu-id="52efc-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="52efc-126">Pour vérifier l’intégrité du fichier catalogue (Pester.cat dans l’exemple ci-dessus), signez-le à l’aide de l’applet de commande [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature).</span><span class="sxs-lookup"><span data-stu-id="52efc-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="52efc-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="52efc-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="52efc-128">Test-FileCatalog valide le catalogue qui représente un ensemble de dossiers.</span><span class="sxs-lookup"><span data-stu-id="52efc-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="52efc-129">Cette applet de commande compare tous les fichiers à hacher et leurs chemins relatifs qui figurent dans le *catalogue* à ceux sur le *disque*.</span><span class="sxs-lookup"><span data-stu-id="52efc-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="52efc-130">Si elle détecte une incompatibilité entre les fichiers à hacher et les chemins, elle retourne le statut *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="52efc-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="52efc-131">Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre *-Detailed*.</span><span class="sxs-lookup"><span data-stu-id="52efc-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="52efc-132">Elle affiche également le statut de signature du catalogue dans la propriété *Signature*, ce qui revient à appeler l’applet de commande [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) sur le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="52efc-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="52efc-133">Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre *-FilesToSkip*.</span><span class="sxs-lookup"><span data-stu-id="52efc-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="52efc-134">Cache d’analyse de module</span><span class="sxs-lookup"><span data-stu-id="52efc-134">Module Analysis Cache</span></span>

<span data-ttu-id="52efc-135">À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.</span><span class="sxs-lookup"><span data-stu-id="52efc-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="52efc-136">Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="52efc-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="52efc-137">Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="52efc-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="52efc-138">Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement `$env:PSModuleAnalysisCachePath` avant de démarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52efc-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="52efc-139">Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="52efc-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="52efc-140">La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.</span><span class="sxs-lookup"><span data-stu-id="52efc-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="52efc-141">Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :</span><span class="sxs-lookup"><span data-stu-id="52efc-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="52efc-142">Cela définit un appareil non valide comme chemin.</span><span class="sxs-lookup"><span data-stu-id="52efc-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="52efc-143">Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée, mais vous pouvez observer la présence d’une erreur signalée à l’aide d’un suivi :</span><span class="sxs-lookup"><span data-stu-id="52efc-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="52efc-144">Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement.</span><span class="sxs-lookup"><span data-stu-id="52efc-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="52efc-145">Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="52efc-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="52efc-146">Cette variable d’environnement prend effet immédiatement dans le processus actif.</span><span class="sxs-lookup"><span data-stu-id="52efc-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="52efc-147">Spécification de la version de module</span><span class="sxs-lookup"><span data-stu-id="52efc-147">Specifying module version</span></span>

<span data-ttu-id="52efc-148">Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52efc-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="52efc-149">Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.</span><span class="sxs-lookup"><span data-stu-id="52efc-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="52efc-150">Dans WMF 5.1 :</span><span class="sxs-lookup"><span data-stu-id="52efc-150">In WMF 5.1:</span></span>

- <span data-ttu-id="52efc-151">Vous pouvez utiliser [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="52efc-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="52efc-152">Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="52efc-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="52efc-153">**Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="52efc-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="52efc-154">S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).</span><span class="sxs-lookup"><span data-stu-id="52efc-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="52efc-155">Améliorations apportées à Pester</span><span class="sxs-lookup"><span data-stu-id="52efc-155">Improvements to Pester</span></span>

<span data-ttu-id="52efc-156">Dans WMF 5.1, la version de Pester qui est fournie avec PowerShell a été mise à jour de la version 3.3.5 vers 3.4.0, avec l’ajout de la validation https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, ce qui permet à Pester de mieux fonctionner sur Nano Server.</span><span class="sxs-lookup"><span data-stu-id="52efc-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="52efc-157">Vous pouvez examiner les modifications des versions 3.3.5 à 3.4.0 dans le fichier ChangeLog.md qui se trouve ici : https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="52efc-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
