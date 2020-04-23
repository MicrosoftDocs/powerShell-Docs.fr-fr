---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: Préversions de module
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328140"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="babb9-103">Préversions de module</span><span class="sxs-lookup"><span data-stu-id="babb9-103">Prerelease Module Versions</span></span>

<span data-ttu-id="babb9-104">À compter de la version 1.6.0, PowerShellGet et PowerShell Gallery prennent en charge l’identification des versions supérieures à 1.0.0 comme des préversions.</span><span class="sxs-lookup"><span data-stu-id="babb9-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="babb9-105">Avant cette fonctionnalité, les packages en préversion devaient avoir un numéro de version commençant par 0.</span><span class="sxs-lookup"><span data-stu-id="babb9-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="babb9-106">L’objectif de ces fonctionnalités est de fournir une meilleure prise en charge de la convention de gestion des versions [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) sans perdre la compatibilité descendante avec les versions 3 et supérieures de PowerShell, ou les versions existantes de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="babb9-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="babb9-107">Cette rubrique étudie les fonctionnalités propres aux modules.</span><span class="sxs-lookup"><span data-stu-id="babb9-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="babb9-108">Les fonctionnalités équivalentes des scripts sont décrites dans la rubrique [Préversions de script](script-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="babb9-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="babb9-109">À l’aide de ces fonctionnalités, les éditeurs peuvent identifier un module ou un script avec une version 2.5.0-alpha et publier plus tard une version 2.5.0 prête pour la production qui remplace la préversion.</span><span class="sxs-lookup"><span data-stu-id="babb9-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="babb9-110">Voici globalement en quoi consistent les fonctionnalités de module en préversion :</span><span class="sxs-lookup"><span data-stu-id="babb9-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="babb9-111">L’ajout d’une chaîne de préversion à la section PSData du manifeste du module identifie le module comme une préversion.</span><span class="sxs-lookup"><span data-stu-id="babb9-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="babb9-112">Lors de la publication du module sur PowerShell Gallery, ces données sont extraites du manifeste et utilisées pour identifier les packages en préversion.</span><span class="sxs-lookup"><span data-stu-id="babb9-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="babb9-113">Il est nécessaire d’ajouter l’indicateur `-AllowPrerelease` aux commandes PowerShellGet `Find-Module`, `Install-Module`, `Update-Module` et `Save-Module` pour pouvoir acquérir des packages en préversion.</span><span class="sxs-lookup"><span data-stu-id="babb9-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="babb9-114">Sans cet indicateur, les packages en préversion ne s’affichent pas.</span><span class="sxs-lookup"><span data-stu-id="babb9-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="babb9-115">Les versions de module affichées par `Find-Module` et `Get-InstalledModule`, ainsi que celles qui se trouvent dans PowerShell Gallery, sont affichées sous forme de chaîne unique suivie de la chaîne de préversion, par exemple 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="babb9-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="babb9-116">Les détails des fonctionnalités sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="babb9-116">Details for the features are included below.</span></span>

<span data-ttu-id="babb9-117">Ces changements n’affectent pas la prise en charge des versions de module intégrée à PowerShell, et sont compatibles avec PowerShell 3.0, 4.0 et 5.</span><span class="sxs-lookup"><span data-stu-id="babb9-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="babb9-118">Identification d’une version de module comme préversion</span><span class="sxs-lookup"><span data-stu-id="babb9-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="babb9-119">La prise en charge des préversions par PowerShellGet nécessite l’utilisation de deux champs dans le manifeste du module :</span><span class="sxs-lookup"><span data-stu-id="babb9-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="babb9-120">La valeur ModuleVersion incluse dans le manifeste de module doit être une version en 3 parties si une préversion est utilisée, et doit être compatible avec la gestion de versions PowerShell existante.</span><span class="sxs-lookup"><span data-stu-id="babb9-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="babb9-121">Le format de version est A.B.C, où A, B et C sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="babb9-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="babb9-122">La chaîne de préversion est spécifiée dans le manifeste de module, dans la section PSData de PrivateData.</span><span class="sxs-lookup"><span data-stu-id="babb9-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="babb9-123">Les exigences détaillées de la chaîne de préversion sont décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="babb9-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="babb9-124">Voici à quoi ressemble un exemple de section d’un manifeste de module qui définit un module comme préversion :</span><span class="sxs-lookup"><span data-stu-id="babb9-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="babb9-125">Les exigences détaillées de la chaîne de préversion sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="babb9-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="babb9-126">Une chaîne de préversion peut être spécifiée uniquement quand la valeur ModuleVersion comprend 3 segments : Majeure.Mineure.Build.</span><span class="sxs-lookup"><span data-stu-id="babb9-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="babb9-127">Ce format est compatible avec SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="babb9-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="babb9-128">Un trait d’union sépare le numéro de build et la chaîne de préversion.</span><span class="sxs-lookup"><span data-stu-id="babb9-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="babb9-129">Un trait d’union peut être inclus dans la chaîne de préversion uniquement en première position.</span><span class="sxs-lookup"><span data-stu-id="babb9-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="babb9-130">La chaîne de préversion peut contenir uniquement des caractères alphanumériques ASCII [0-9A-Za-z-].</span><span class="sxs-lookup"><span data-stu-id="babb9-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="babb9-131">Il est recommandé de commencer la chaîne de préversion par un caractère alphabétique, pour qu’elle soit plus facile à identifier comme préversion au moment d’analyser une liste de packages.</span><span class="sxs-lookup"><span data-stu-id="babb9-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="babb9-132">Seules les chaînes de préversion SemVer v1.0.0 sont prises en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="babb9-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="babb9-133">La chaîne de préversion **ne doit pas** contenir de point ou le signe + [.+], lesquels sont autorisé dans SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="babb9-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="babb9-134">Exemples de chaînes de préversion prises en charge : -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="babb9-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="babb9-135">Impact de la gestion de versions des préversions sur l’ordre de tri et les dossiers d’installation</span><span class="sxs-lookup"><span data-stu-id="babb9-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="babb9-136">L’ordre de tri change quand vous utilisez une préversion, ce qui est important quand vous publiez dans PowerShell Gallery et quand vous installez des modules à l’aide des commandes PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="babb9-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="babb9-137">Si la chaîne de préversion est spécifiée pour deux modules, l’ordre de tri est basé sur la partie de chaîne qui suit le trait d’union.</span><span class="sxs-lookup"><span data-stu-id="babb9-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="babb9-138">Par conséquent, 2.5.0-alpha est inférieur à 2.5.0-bêta, qui est inférieur à 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="babb9-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="babb9-139">Si deux modules ont la même valeur ModuleVersion et qu’un seul a une chaîne de préversion, le module sans chaîne de préversion est assimilé à la version prête pour la production et classé comme une version supérieure à la préversion (qui inclut la chaîne de préversion).</span><span class="sxs-lookup"><span data-stu-id="babb9-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="babb9-140">Par exemple, entre les versions 2.5.0 et 2.5.0-bêta, la version 2.5.0 est considérée comme supérieure.</span><span class="sxs-lookup"><span data-stu-id="babb9-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="babb9-141">Quand vous publiez dans PowerShell Gallery, par défaut, la version du module qui est publié doit avoir une version supérieure à n’importe quelle version déjà publiée qui se trouve dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="babb9-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="babb9-142">Rechercher et acquérir des packages en préversion avec les commandes PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="babb9-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="babb9-143">Pour pouvoir gérer des packages en préversion avec les commandes PowerShellGet Find-Module, Install-Module, Update-Module et Save-Module, il est nécessaire d’ajouter l’indicateur -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="babb9-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="babb9-144">Si l’indicateur -AllowPrerelease est spécifié, les packages en préversion présents sont inclus.</span><span class="sxs-lookup"><span data-stu-id="babb9-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="babb9-145">S’il n’est pas spécifié, les packages en préversion ne s’affichent pas.</span><span class="sxs-lookup"><span data-stu-id="babb9-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="babb9-146">Les seules exceptions dans les commandes de module PowerShellGet sont Get-InstalledModule et certains cas avec Uninstall-Module.</span><span class="sxs-lookup"><span data-stu-id="babb9-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="babb9-147">Get-InstalledModule affiche toujours automatiquement les informations de préversion dans la chaîne de version des modules.</span><span class="sxs-lookup"><span data-stu-id="babb9-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="babb9-148">Uninstall-Module désinstalle par défaut la version la plus récente d’un module, si __aucune version__ n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="babb9-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="babb9-149">Ce comportement n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="babb9-149">That behavior has not changed.</span></span> <span data-ttu-id="babb9-150">Toutefois, si une préversion est spécifiée à l’aide de -RequiredVersion, -AllowPrerelease est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="babb9-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="babb9-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="babb9-151">Examples</span></span>

<span data-ttu-id="babb9-152">Supposons que PowerShell Gallery dispose du module TestPackage dans les versions 1.8.0 et 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="babb9-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="babb9-153">Si `-AllowPrerelease` n’est pas spécifié, seule la version 1.8.0 est retournée.</span><span class="sxs-lookup"><span data-stu-id="babb9-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="babb9-154">Pour installer une préversion, spécifiez toujours -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="babb9-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="babb9-155">La spécification d’une chaîne de version de préversion n’est pas suffisante.</span><span class="sxs-lookup"><span data-stu-id="babb9-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="babb9-156">Échec de la commande précédente, car -AllowPrerelease n’a pas été spécifié.</span><span class="sxs-lookup"><span data-stu-id="babb9-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="babb9-157">L’ajout de `-AllowPrerelease` permet à l’opération de réussir.</span><span class="sxs-lookup"><span data-stu-id="babb9-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="babb9-158">L’installation côte à côte de versions d’un module qui diffèrent uniquement par la préversion spécifiée n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="babb9-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="babb9-159">Quand vous installez un module à l’aide de PowerShellGet, différentes versions du même module sont installées côte à côte en créant un nom de dossier qui utilise la valeur ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="babb9-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="babb9-160">La valeur ModuleVersion, sans la chaîne de préversion, est utilisée comme nom du dossier.</span><span class="sxs-lookup"><span data-stu-id="babb9-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="babb9-161">Si un utilisateur installe MyModule version 2.5.0-alpha, il est installé dans le dossier `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="babb9-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="babb9-162">Si l’utilisateur installe ensuite la version 2.5.0-bêta, celle-ci **remplace** le contenu du dossier `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="babb9-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="babb9-163">L’avantage de cette approche est qu’il est inutile de désinstaller la préversion après l’installation de la version prête pour la production.</span><span class="sxs-lookup"><span data-stu-id="babb9-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="babb9-164">L’exemple ci-dessous correspond à ce que vous devez obtenir :</span><span class="sxs-lookup"><span data-stu-id="babb9-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="babb9-165">Uninstall-Module supprime la dernière version d’un module quand -RequiredVersion n’est pas fourni.</span><span class="sxs-lookup"><span data-stu-id="babb9-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="babb9-166">Si -RequiredVersion est spécifié et qu’il s’agit d’une préversion, -AllowPrerelease doit être ajouté à la commande.</span><span class="sxs-lookup"><span data-stu-id="babb9-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="babb9-167">Détails supplémentaires</span><span class="sxs-lookup"><span data-stu-id="babb9-167">More details</span></span>

- [<span data-ttu-id="babb9-168">Préversions de script</span><span class="sxs-lookup"><span data-stu-id="babb9-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="babb9-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="babb9-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="babb9-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="babb9-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="babb9-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="babb9-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="babb9-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="babb9-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="babb9-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="babb9-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="babb9-174">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="babb9-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
