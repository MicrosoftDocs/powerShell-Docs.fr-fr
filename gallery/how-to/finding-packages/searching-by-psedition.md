---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Packages avec des éditions PowerShell compatibles
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003706"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="616e1-103">Packages avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="616e1-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="616e1-104">À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="616e1-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="616e1-105">**Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="616e1-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="616e1-106">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="616e1-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="616e1-107">PowerShell Gallery extrait des métadonnées d’éditions PS prises en charge et vous permet de filtrer les packages compatibles pour des éditions PowerShell spécifiques</span><span class="sxs-lookup"><span data-stu-id="616e1-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="616e1-108">Si des éditions PS compatibles sont spécifiées pour un package, elles sont répertoriées dans le cadre des « Éditions PowerShell » dans la page d’affichage du package et également dans les résultats des packages.</span><span class="sxs-lookup"><span data-stu-id="616e1-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Page d’affichage de l’élément avec des éditions PS](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="616e1-110">Rechercher des packages dans l’interface utilisateur PowerShell Gallery qui fonctionnent sur PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="616e1-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="616e1-111">Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les packages sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="616e1-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="616e1-112">Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="616e1-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="616e1-114">Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="616e1-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="616e1-116">Plus d’informations sur la création et la recherche des packages avec des éditions PowerShell compatibles</span><span class="sxs-lookup"><span data-stu-id="616e1-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="616e1-117">Modules avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="616e1-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="616e1-118">Scripts avec des éditions PS</span><span class="sxs-lookup"><span data-stu-id="616e1-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
