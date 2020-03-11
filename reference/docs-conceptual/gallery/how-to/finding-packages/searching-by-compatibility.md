---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,applet de commande,psgallery
title: Packages avec un système d’exploitation ou des éditions PowerShell compatibles
ms.openlocfilehash: b414ce2c2b189e9da150cbe612e0bb2572d39e76
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278355"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="0d94c-103">Packages avec des systèmes d’exploitation ou des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="0d94c-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="0d94c-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent les compatibilités de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="0d94c-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="0d94c-105">Recherche par édition de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d94c-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="0d94c-106">Les deux éditions de PowerShell sont :</span><span class="sxs-lookup"><span data-stu-id="0d94c-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="0d94c-107">**Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="0d94c-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="0d94c-108">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="0d94c-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="0d94c-109">PowerShell Gallery vous permet de filtrer les packages compatibles pour des éditions spécifiques de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d94c-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="0d94c-110">Si des éditions PS compatibles sont spécifiées pour un package, elles sont répertoriées dans le cadre des « Éditions PowerShell » dans la page d’affichage du package et également dans les résultats des packages.</span><span class="sxs-lookup"><span data-stu-id="0d94c-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="0d94c-111">Vous pouvez également rechercher les packages compatibles à l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d94c-111">You can also search for compatible packages using PowerShell.</span></span>

![Page d’affichage de l’élément avec des éditions PS](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="0d94c-113">Rechercher des packages dans l’interface utilisateur PowerShell Gallery qui fonctionnent sur PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="0d94c-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="0d94c-114">Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les packages sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0d94c-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="0d94c-115">Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="0d94c-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="0d94c-117">Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="0d94c-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="0d94c-119">Rechercher des packages pour trouver des éditions compatibles à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d94c-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="0d94c-120">Vous pouvez spécifier des balises pour filtrer l’édition de PowerShell et le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0d94c-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="0d94c-121">Vous utilisez l’applet de commande `Find-Package` en spécifiant le paramètre `-Tag` afin de spécifier l’édition (et le système d’exploitation) ciblée.</span><span class="sxs-lookup"><span data-stu-id="0d94c-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="0d94c-122">Comme ceci :</span><span class="sxs-lookup"><span data-stu-id="0d94c-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="0d94c-123">Recherche par système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="0d94c-123">Searching by Operating System</span></span>

<span data-ttu-id="0d94c-124">PowerShell Core étant disponible pour Windows, Linux et MacOS, les packages dans la galerie peuvent être conçus pour n’importe quelle combinaison de ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0d94c-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="0d94c-125">Dans l’interface utilisateur de la galerie, utilisez les balises de recherche suivantes pour trouver des packages balisés par système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="0d94c-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="0d94c-126">Balises : « Windows »</span><span class="sxs-lookup"><span data-stu-id="0d94c-126">Tags: "Windows"</span></span>
- <span data-ttu-id="0d94c-127">Balises : « Linux »</span><span class="sxs-lookup"><span data-stu-id="0d94c-127">Tags: "Linux"</span></span>
- <span data-ttu-id="0d94c-128">Balises : « MacOS »</span><span class="sxs-lookup"><span data-stu-id="0d94c-128">Tags: "MacOS"</span></span>

<span data-ttu-id="0d94c-129">Vous pouvez spécifier ces balises sur `Find-Module` (et autres applets de commande dans le module PowerShellGet), comme suit :</span><span class="sxs-lookup"><span data-stu-id="0d94c-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="0d94c-130">Recherche de compatibilités multiples</span><span class="sxs-lookup"><span data-stu-id="0d94c-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="0d94c-131">Vous pouvez rechercher un package qui a plusieurs compatibilités à l’aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="0d94c-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="0d94c-132">Balises : « Compatibility1 » « Compatibility2 »</span><span class="sxs-lookup"><span data-stu-id="0d94c-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="0d94c-133">Par exemple, si vous recherchez un package avec compatibilité PowerShell Core qui s’exécute sur des ordinateurs Windows et Linux, utilisez ces balises de recherche :</span><span class="sxs-lookup"><span data-stu-id="0d94c-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="0d94c-134">Balises : « PSEdition_Core » « Windows », « Linux »</span><span class="sxs-lookup"><span data-stu-id="0d94c-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="0d94c-135">Pour effectuer une recherche à l’aide de PowerShell, vous pouvez utiliser `Find-Module` (et les autres applets de commande dans le module PowerShellGet), comme suit :</span><span class="sxs-lookup"><span data-stu-id="0d94c-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="0d94c-136">Plus d’informations sur la création et la recherche des packages avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="0d94c-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="0d94c-137">Modules avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="0d94c-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="0d94c-138">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="0d94c-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
