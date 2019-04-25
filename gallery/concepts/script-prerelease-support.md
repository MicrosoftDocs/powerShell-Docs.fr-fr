---
ms.date: 10/17/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Préversions des scripts
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084638"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="314a4-103">Préversions des scripts</span><span class="sxs-lookup"><span data-stu-id="314a4-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="314a4-104">À compter de la version 1.6.0, PowerShellGet et PowerShell Gallery prennent en charge l’identification des versions supérieures à 1.0.0 comme des préversions.</span><span class="sxs-lookup"><span data-stu-id="314a4-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="314a4-105">Avant cette fonctionnalité, les packages en préversion devaient avoir un numéro de version commençant par 0.</span><span class="sxs-lookup"><span data-stu-id="314a4-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="314a4-106">L’objectif de ces fonctionnalités est de fournir une meilleure prise en charge de la convention de gestion des versions [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sans perdre la compatibilité descendante avec les versions 3 et supérieures de PowerShell, ou les versions existantes de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="314a4-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="314a4-107">Cette rubrique étudie les fonctionnalités propres aux scripts.</span><span class="sxs-lookup"><span data-stu-id="314a4-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="314a4-108">Les fonctionnalités équivalentes des modules sont décrites dans la rubrique [Préversions de module](module-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="314a4-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="314a4-109">À l’aide de ces fonctionnalités, les éditeurs peuvent identifier un script avec une version 2.5.0-alpha et publier plus tard une version 2.5.0 prête pour la production qui remplace la préversion.</span><span class="sxs-lookup"><span data-stu-id="314a4-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="314a4-110">Voici des exemples de fonctionnalités de script en préversion, à un niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="314a4-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="314a4-111">Ajout d’un suffixe PrereleaseString à la chaîne de version dans le manifeste de script.</span><span class="sxs-lookup"><span data-stu-id="314a4-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="314a4-112">Quand le script est publié dans PowerShell Gallery, ces données sont extraites du manifeste et utilisées pour identifier les packages en préversion.</span><span class="sxs-lookup"><span data-stu-id="314a4-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="314a4-113">L’acquisition de packages en préversion nécessite d’ajouter l’indicateur -AllowPrerelease aux commandes PowerShellGet Find-Script, Install-Script, Update-Script et Save-Script.</span><span class="sxs-lookup"><span data-stu-id="314a4-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="314a4-114">Sans cet indicateur, les packages en préversion ne s’affichent pas.</span><span class="sxs-lookup"><span data-stu-id="314a4-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="314a4-115">Les versions de script affichées par Find-Script, Get-InstalledScript et celles qui se trouvent dans PowerShell Gallery sont affichées avec le suffixe PrereleaseString, par exemple 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="314a4-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="314a4-116">Les détails des fonctionnalités sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="314a4-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="314a4-117">Identification d’une version de script comme préversion</span><span class="sxs-lookup"><span data-stu-id="314a4-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="314a4-118">La prise en charge des préversions par PowerShellGet est plus facile pour les scripts que pour les modules.</span><span class="sxs-lookup"><span data-stu-id="314a4-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="314a4-119">La gestion des versions de script est prise en charge uniquement par PowerShellGet, il n’y a donc aucun problème de compatibilité quand vous ajoutez la chaîne de préversion.</span><span class="sxs-lookup"><span data-stu-id="314a4-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="314a4-120">Pour identifier un script dans PowerShell Gallery comme préversion, ajoutez un suffixe de préversion à une chaîne de version correctement mise en forme dans les métadonnées de script.</span><span class="sxs-lookup"><span data-stu-id="314a4-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="314a4-121">Voici à quoi ressemble un exemple de section d’un manifeste de script avec une préversion :</span><span class="sxs-lookup"><span data-stu-id="314a4-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="314a4-122">Pour utiliser un suffixe de préversion, la chaîne de version doit remplir les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="314a4-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="314a4-123">Un suffixe de préversion peut être spécifié uniquement quand le numéro de version comprend 3 segments : Majeure.Mineure.Build.</span><span class="sxs-lookup"><span data-stu-id="314a4-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="314a4-124">Ce format est compatible avec SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="314a4-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="314a4-125">Le suffixe de préversion est une chaîne qui commence par un trait d’union et peut contenir des caractères alphanumériques ASCII [0-9A-Za-z-]</span><span class="sxs-lookup"><span data-stu-id="314a4-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="314a4-126">Seules les chaînes de préversion SemVer v1.0.0 sont prises en charge pour l’instant. Par conséquent, le suffixe de préversion **ne doit pas** contenir de point ou de signe + [.+], lesquels sont autorisés dans SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="314a4-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="314a4-127">Exemples de chaînes PrereleaseString prises en charge : -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="314a4-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="314a4-128">Impact de la gestion de versions des préversions sur l’ordre de tri et les dossiers d’installation</span><span class="sxs-lookup"><span data-stu-id="314a4-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="314a4-129">L’ordre de tri change quand vous utilisez une préversion, ce qui est important quand vous publiez dans PowerShell Gallery et quand vous installez des scripts à l’aide des commandes PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="314a4-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="314a4-130">Si deux versions de script existent avec le numéro de version, l’ordre de tri est basé sur la partie de la chaîne qui suit le trait d’union.</span><span class="sxs-lookup"><span data-stu-id="314a4-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="314a4-131">Par conséquent, 2.5.0-alpha est inférieur à 2.5.0-bêta, qui est inférieur à 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="314a4-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="314a4-132">Si deux scripts ont le même numéro de version et qu’un seul a un suffixe PrereleaseString, le script **sans** suffixe de préversion est assimilé à la version prête pour la production et trié comme une version supérieure à la préversion.</span><span class="sxs-lookup"><span data-stu-id="314a4-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="314a4-133">Par exemple, entre les versions 2.5.0 et 2.5.0-bêta, la version 2.5.0 est considérée comme supérieure.</span><span class="sxs-lookup"><span data-stu-id="314a4-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="314a4-134">Quand vous publiez dans PowerShell Gallery, par défaut, la version du script qui est publié doit être supérieure à n’importe quelle version déjà publiée qui se trouve dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="314a4-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="314a4-135">Un éditeur peut mettre à jour la version 2.5.0-alpha vers 2.5.0-bêta ou 2.5.0 (sans suffixe de préversion).</span><span class="sxs-lookup"><span data-stu-id="314a4-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="314a4-136">Rechercher et acquérir des packages en préversion avec les commandes PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="314a4-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="314a4-137">Le traitement de packages en préversion à l’aide des commandes PowerShellGet Find-Script, Install-Script, Update-Script et Save-Script nécessite l’ajout de l’indicateur -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="314a4-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="314a4-138">Si -AllowPrerelease est spécifié, les packages en préversion présents sont inclus.</span><span class="sxs-lookup"><span data-stu-id="314a4-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="314a4-139">S’il n’est pas spécifié, les packages en préversion ne s’affichent pas.</span><span class="sxs-lookup"><span data-stu-id="314a4-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="314a4-140">Les seules exceptions dans les commandes de script PowerShellGet sont Get-InstalledScript et certains cas avec Uninstall-Script.</span><span class="sxs-lookup"><span data-stu-id="314a4-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="314a4-141">Get-InstalledScript affiche toujours automatiquement les informations de préversion dans la chaîne de version, si elles sont présentes.</span><span class="sxs-lookup"><span data-stu-id="314a4-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="314a4-142">Uninstall-Script désinstalle par défaut la version la plus récente d’un script, si **aucune version** n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="314a4-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="314a4-143">Ce comportement n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="314a4-143">That behavior has not changed.</span></span> <span data-ttu-id="314a4-144">Toutefois, si une préversion est spécifiée à l’aide de `-RequiredVersion`, `-AllowPrerelease` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="314a4-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="314a4-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="314a4-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha

PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="314a4-146">Uninstall-Script supprime la version actuelle d’un script quand -RequiredVersion n’est pas fourni.</span><span class="sxs-lookup"><span data-stu-id="314a4-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="314a4-147">Si -RequiredVersion est spécifié et qu’il s’agit d’une préversion, -AllowPrerelease doit être ajouté à la commande.</span><span class="sxs-lookup"><span data-stu-id="314a4-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="314a4-148">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="314a4-148">More details</span></span>

- [<span data-ttu-id="314a4-149">Préversions de module</span><span class="sxs-lookup"><span data-stu-id="314a4-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="314a4-150">Find-Script</span><span class="sxs-lookup"><span data-stu-id="314a4-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="314a4-151">Install-Script</span><span class="sxs-lookup"><span data-stu-id="314a4-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="314a4-152">Save-Script</span><span class="sxs-lookup"><span data-stu-id="314a4-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="314a4-153">Update-Script</span><span class="sxs-lookup"><span data-stu-id="314a4-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="314a4-154">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="314a4-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="314a4-155">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="314a4-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
