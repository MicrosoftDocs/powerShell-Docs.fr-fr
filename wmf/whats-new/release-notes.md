---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Notes de publication de WMF 5.x
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855764"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="9813a-103">Notes de publication de Windows Management Framework (WMF) 5.x</span><span class="sxs-lookup"><span data-stu-id="9813a-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="9813a-104">Modifications de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="9813a-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="9813a-105">Ajout d’un nouveau flux **d’informations** structuré dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9813a-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="9813a-106">Amélioration de DSC, notamment quatre nouvelles ressources DSC :</span><span class="sxs-lookup"><span data-stu-id="9813a-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="9813a-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9813a-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="9813a-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9813a-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="9813a-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="9813a-109">ServiceSet</span></span>
  - <span data-ttu-id="9813a-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="9813a-110">ProcessSet</span></span>
- <span data-ttu-id="9813a-111">Ajout de Just Enough Administration pour permettre une administration basée sur des rôles par la communication à distance PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="9813a-112">Extension du langage aux énumérations et aux classes définies par l’utilisateur dans PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9813a-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="9813a-113">Amélioration des fonctionnalités de débogage dans PowerShell ISE et ajout du débogage à distance</span><span class="sxs-lookup"><span data-stu-id="9813a-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="9813a-114">Ajout des modules PowerShellGet et PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9813a-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="9813a-115">Amélioration de la transcription et de la journalisation des scripts PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="9813a-116">Ajout des cmdlets CMS (Cryptographic Message Syntax)</span><span class="sxs-lookup"><span data-stu-id="9813a-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="9813a-117">Ajout du module NetworkSwitchManager pour Windows dans WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="9813a-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="9813a-118">Ajout du module Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="9813a-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="9813a-119">Ajout de la prise en charge de la Journalisation de l’inventaire logiciel (SIL)</span><span class="sxs-lookup"><span data-stu-id="9813a-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="9813a-120">Plusieurs ajouts ou mises à jour de cmdlets en réponse aux problèmes et demandes des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="9813a-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="9813a-121">Modifications de WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="9813a-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="9813a-122">WMF 5.1 comprend les composants PowerShell, WMI, WinRM et SIL (Journalisation de l’inventaire logiciel) qui ont été publiés avec Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="9813a-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="9813a-123">WMF 5.1, qui peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, comporte plusieurs améliorations par rapport à WMF 5.0 :</span><span class="sxs-lookup"><span data-stu-id="9813a-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="9813a-124">Nouvelles applets de commande</span><span class="sxs-lookup"><span data-stu-id="9813a-124">New cmdlets</span></span>
- <span data-ttu-id="9813a-125">Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA</span><span class="sxs-lookup"><span data-stu-id="9813a-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="9813a-126">Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB</span><span class="sxs-lookup"><span data-stu-id="9813a-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="9813a-127">Améliorations du débogage pour les classes DSC et PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="9813a-128">Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="9813a-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="9813a-129">Réponses à plusieurs demandes et problèmes des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="9813a-129">Responses to a number of user requests and issues</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="9813a-130">Éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-130">PowerShell Editions</span></span>

<span data-ttu-id="9813a-131">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui affichent une compatibilité distincte avec les plateformes et des ensembles de fonctionnalités variables.</span><span class="sxs-lookup"><span data-stu-id="9813a-131">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="9813a-132">**Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="9813a-132">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="9813a-133">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="9813a-133">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="9813a-134">En savoir plus sur l’utilisation des éditions de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-134">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="9813a-135">Déterminer la version en cours d’exécution de PowerShell à l’aide de $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="9813a-135">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="9813a-136">Filtrer les résultats de Get-Module par CompatiblePSEditions à l’aide du paramètre PSEdition</span><span class="sxs-lookup"><span data-stu-id="9813a-136">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="9813a-137">Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-137">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="9813a-138">Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9813a-138">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="9813a-139">Cache d’analyse de module</span><span class="sxs-lookup"><span data-stu-id="9813a-139">Module Analysis Cache</span></span>

<span data-ttu-id="9813a-140">À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.</span><span class="sxs-lookup"><span data-stu-id="9813a-140">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="9813a-141">Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="9813a-141">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="9813a-142">Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="9813a-142">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="9813a-143">Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement `$env:PSModuleAnalysisCachePath` avant de démarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9813a-143">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="9813a-144">Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.</span><span class="sxs-lookup"><span data-stu-id="9813a-144">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="9813a-145">La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.</span><span class="sxs-lookup"><span data-stu-id="9813a-145">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="9813a-146">Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9813a-146">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="9813a-147">Cela définit un appareil non valide comme chemin.</span><span class="sxs-lookup"><span data-stu-id="9813a-147">This sets the path to an invalid device.</span></span> <span data-ttu-id="9813a-148">Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée, mais vous pouvez observer la présence d’une erreur signalée à l’aide d’un suivi :</span><span class="sxs-lookup"><span data-stu-id="9813a-148">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="9813a-149">Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement.</span><span class="sxs-lookup"><span data-stu-id="9813a-149">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="9813a-150">Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9813a-150">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="9813a-151">Cette variable d’environnement prend effet immédiatement dans le processus actif.</span><span class="sxs-lookup"><span data-stu-id="9813a-151">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="9813a-152">Spécification de la version de module</span><span class="sxs-lookup"><span data-stu-id="9813a-152">Specifying module version</span></span>

<span data-ttu-id="9813a-153">Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9813a-153">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="9813a-154">Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.</span><span class="sxs-lookup"><span data-stu-id="9813a-154">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="9813a-155">Dans WMF 5.1 :</span><span class="sxs-lookup"><span data-stu-id="9813a-155">In WMF 5.1:</span></span>

- <span data-ttu-id="9813a-156">Vous pouvez utiliser [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="9813a-156">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
  <span data-ttu-id="9813a-157">Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="9813a-157">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="9813a-158">**Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="9813a-158">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="9813a-159">S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).</span><span class="sxs-lookup"><span data-stu-id="9813a-159">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="9813a-160">Améliorations apportées à Pester</span><span class="sxs-lookup"><span data-stu-id="9813a-160">Improvements to Pester</span></span>

<span data-ttu-id="9813a-161">Dans WMF 5.1, la version de Pester fournie avec PowerShell a été mise à jour de la version 3.3.5 à la version 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="9813a-161">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="9813a-162">Cette mise à jour améliore le comportement de Pester sur Nano Server.</span><span class="sxs-lookup"><span data-stu-id="9813a-162">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="9813a-163">Pour voir les modifications apportées à Pester, consultez le [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) dans le référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="9813a-163">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>