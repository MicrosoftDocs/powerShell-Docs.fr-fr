---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Filtrage des résultats de la recherche
ms.openlocfilehash: 51f8d243cb9b1f4ff7413eec8839697299e8dd52
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691464"
---
# <a name="filtering-search-results"></a><span data-ttu-id="cd818-103">Filtrage des résultats de la recherche</span><span class="sxs-lookup"><span data-stu-id="cd818-103">Filtering search results</span></span>

<span data-ttu-id="cd818-104">[L’onglet Packages](https://www.powershellgallery.com/packages) affiche tous les packages disponibles sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="cd818-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="cd818-105">Il existe plusieurs moyens de filtrer, de trier et de parcourir les packages.</span><span class="sxs-lookup"><span data-stu-id="cd818-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="cd818-106">Pour afficher des informations sur un package en particulier, cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="cd818-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="cd818-107">Filtrer par</span><span class="sxs-lookup"><span data-stu-id="cd818-107">Filter By</span></span>

<span data-ttu-id="cd818-108">La liste déroulante sous « Filtrer par » permet aux utilisateurs de filtrer les résultats selon :</span><span class="sxs-lookup"><span data-stu-id="cd818-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>

- <span data-ttu-id="cd818-109">Inclure la préversion</span><span class="sxs-lookup"><span data-stu-id="cd818-109">Include Prerelease</span></span>
- <span data-ttu-id="cd818-110">Stable uniquement</span><span class="sxs-lookup"><span data-stu-id="cd818-110">Stable Only</span></span>

<span data-ttu-id="cd818-111">Pour plus d’informations sur « Préversion » et « Stable », consultez [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Gestion des préversions ajoutée à PowerShellGet et à PowerShell Gallery) dans le blog de l’équipe PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd818-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="cd818-112">Les cases à cocher sous la liste déroulante permettent aux utilisateurs de filtrer les résultats par :</span><span class="sxs-lookup"><span data-stu-id="cd818-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>

- <span data-ttu-id="cd818-113">Types de packages</span><span class="sxs-lookup"><span data-stu-id="cd818-113">Package Types</span></span>
  - <span data-ttu-id="cd818-114">Module</span><span class="sxs-lookup"><span data-stu-id="cd818-114">Module</span></span>
  - <span data-ttu-id="cd818-115">Script</span><span class="sxs-lookup"><span data-stu-id="cd818-115">Script</span></span>
- <span data-ttu-id="cd818-116">Catégories</span><span class="sxs-lookup"><span data-stu-id="cd818-116">Categories</span></span>
  - <span data-ttu-id="cd818-117">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="cd818-117">Cmdlet</span></span>
  - <span data-ttu-id="cd818-118">Ressource DSC</span><span class="sxs-lookup"><span data-stu-id="cd818-118">DSC Resource</span></span>
  - <span data-ttu-id="cd818-119">Fonction</span><span class="sxs-lookup"><span data-stu-id="cd818-119">Function</span></span>
  - <span data-ttu-id="cd818-120">Fonctionnalité Rôle</span><span class="sxs-lookup"><span data-stu-id="cd818-120">Role Capability</span></span>
  - <span data-ttu-id="cd818-121">Workflow</span><span class="sxs-lookup"><span data-stu-id="cd818-121">Workflow</span></span>

<span data-ttu-id="cd818-122">Pour afficher uniquement les modules de PowerShell Gallery, cochez Module dans Types de packages.</span><span class="sxs-lookup"><span data-stu-id="cd818-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="cd818-123">De même, pour afficher uniquement les scripts de PowerShell Gallery, cochez Script dans Types de packages.</span><span class="sxs-lookup"><span data-stu-id="cd818-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="cd818-124">Les filtres sont inclusifs.</span><span class="sxs-lookup"><span data-stu-id="cd818-124">Filters are inclusive.</span></span>
> <span data-ttu-id="cd818-125">Exemple : un package contenant à la fois des cmdlets et des fonctions s’affiche si la case Cmdlet ou la case Function (ou les deux) sont cochées.</span><span class="sxs-lookup"><span data-stu-id="cd818-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="cd818-126">Si aucune des deux n’est sélectionnée, le package n’apparaît pas.</span><span class="sxs-lookup"><span data-stu-id="cd818-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="cd818-127">De même, si toutes les catégories sont sélectionnées, seuls les packages contenant l’une de ces catégories s’affichent.</span><span class="sxs-lookup"><span data-stu-id="cd818-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="cd818-128">**Les packages qui n’appartiennent à aucune de ces catégories n’apparaissent pas.**</span><span class="sxs-lookup"><span data-stu-id="cd818-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="cd818-129">Trier par</span><span class="sxs-lookup"><span data-stu-id="cd818-129">Sort By</span></span>

<span data-ttu-id="cd818-130">La liste déroulante Trier par permet aux utilisateurs de trier les résultats par :</span><span class="sxs-lookup"><span data-stu-id="cd818-130">The Sort By drop-down allows users to sort the results by:</span></span>

- <span data-ttu-id="cd818-131">Popularité : la popularité est déterminée par le nombre de téléchargements</span><span class="sxs-lookup"><span data-stu-id="cd818-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="cd818-132">A à Z : par ordre alphabétique de nom de package</span><span class="sxs-lookup"><span data-stu-id="cd818-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="cd818-133">Récent : par date de publication des packages</span><span class="sxs-lookup"><span data-stu-id="cd818-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="cd818-134">Zone de recherche</span><span class="sxs-lookup"><span data-stu-id="cd818-134">Search Box</span></span>

<span data-ttu-id="cd818-135">La zone de recherche permet aux utilisateurs de rechercher des packages par mots clés.</span><span class="sxs-lookup"><span data-stu-id="cd818-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="cd818-136">Pour plus d’informations, consultez [Syntaxe de recherche dans la galerie](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="cd818-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
