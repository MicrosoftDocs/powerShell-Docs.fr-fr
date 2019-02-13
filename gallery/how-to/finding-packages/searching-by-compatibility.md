---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,applet de commande,psgallery
title: Packages avec le système d’exploitation ou des éditions PowerShell compatibles
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678429"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="c86f8-103">Packages avec des systèmes d’exploitation ou des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="c86f8-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="c86f8-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent les compatibilités de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c86f8-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="c86f8-105">Recherche par édition de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c86f8-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="c86f8-106">Les deux éditions de Powershell sont :</span><span class="sxs-lookup"><span data-stu-id="c86f8-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="c86f8-107">**Édition Desktop :** repose sur .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="c86f8-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="c86f8-108">**Core Edition :** Basée sur .NET Core et assure la compatibilité avec les scripts et modules qui ciblent des versions de PowerShell exécutées sur des éditions à encombrement réduit de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="c86f8-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="c86f8-109">PowerShell Gallery permet de vous permettent de filtrer les packages compatibles pour les éditions PowerShell spécifiques</span><span class="sxs-lookup"><span data-stu-id="c86f8-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="c86f8-110">Si un package a compatible PSEditions spécifié, ils sont répertoriés dans le cadre des « Éditions PowerShell » dans la page d’affichage de package, ainsi que dans les résultats de packages.</span><span class="sxs-lookup"><span data-stu-id="c86f8-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="c86f8-111">Vous pouvez également rechercher des packages compatibles à l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c86f8-111">You can also search for compatible packages using PowerShell.</span></span>

![Page d’affichage de l’élément avec des éditions PS](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="c86f8-113">Rechercher des packages dans la galerie d’interface utilisateur qui fonctionnent sur PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c86f8-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="c86f8-114">Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les packages sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c86f8-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="c86f8-115">Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c86f8-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="c86f8-117">Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="c86f8-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="c86f8-119">Rechercher des packages à trouver des éditions compatibles à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c86f8-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="c86f8-120">Vous pouvez spécifier des balises pour filtrer pour l’édition de PowerShell et le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c86f8-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="c86f8-121">Vous utilisez le `Find-Package` applet de commande en spécifiant le `-Tag` paramètre pour spécifier l’édition (et le système d’exploitation) que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="c86f8-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="c86f8-122">Comme ça :</span><span class="sxs-lookup"><span data-stu-id="c86f8-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="c86f8-123">Recherche par système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c86f8-123">Searching by Operating System</span></span> 

<span data-ttu-id="c86f8-124">Dans la mesure où PowerShell Core est disponible pour Windows, Linux et MacOS, les packages dans la galerie peuvent être conçues pour n’importe quelle combinaison de ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c86f8-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="c86f8-125">Dans la galerie d’interface utilisateur utiliser les balises de recherches suivantes pour rechercher des packages marqués par le système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="c86f8-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="c86f8-126">Balises : « Windows »</span><span class="sxs-lookup"><span data-stu-id="c86f8-126">Tags: "Windows"</span></span>
- <span data-ttu-id="c86f8-127">Balises : « Linux »</span><span class="sxs-lookup"><span data-stu-id="c86f8-127">Tags: "Linux"</span></span>
- <span data-ttu-id="c86f8-128">Balises : « MacOS »</span><span class="sxs-lookup"><span data-stu-id="c86f8-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="c86f8-129">Vous pouvez spécifier ces balises sur `Find-Module` (et autres applets de commande dans le module PowerShellGet), comme suit :</span><span class="sxs-lookup"><span data-stu-id="c86f8-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="c86f8-130">Recherche de compatibilités plusieurs</span><span class="sxs-lookup"><span data-stu-id="c86f8-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="c86f8-131">Vous pouvez rechercher un package qui a plusieurs les compatibilités en utilisant la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="c86f8-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="c86f8-132">Balises : « Compatibility1 » « Compatibility2 »</span><span class="sxs-lookup"><span data-stu-id="c86f8-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="c86f8-133">Par exemple, si vous recherchez un package avec PowerShell Core compatibilité qui s’exécute sur des ordinateurs à la fois mon Windows et Linux, utilisez les balises de recherche :</span><span class="sxs-lookup"><span data-stu-id="c86f8-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="c86f8-134">Balises : « PSEdition_Core » « Windows », « Linux »</span><span class="sxs-lookup"><span data-stu-id="c86f8-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="c86f8-135">Pour effectuer une recherche à l’aide de PowerShell, vous pouvez utiliser la `Find-Module` (et les autres applets de commande dans le module PowerShellGet), comme suit :</span><span class="sxs-lookup"><span data-stu-id="c86f8-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="c86f8-136">Plus d’informations sur la création et la recherche des packages avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="c86f8-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="c86f8-137">Modules avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="c86f8-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="c86f8-138">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="c86f8-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
