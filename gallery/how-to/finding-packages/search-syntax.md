---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Syntaxe de recherche PowerShell Gallery
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742854"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="e10ce-103">Syntaxe de recherche PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e10ce-103">Gallery Search Syntax</span></span>

<span data-ttu-id="e10ce-104">Vous pouvez rechercher l’à l’aide de PowerShell Gallery le [site web de PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="e10ce-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="e10ce-105">Site web PowerShell Gallery offre un searchbox de texte où vous pouvez utiliser des mots, expressions et des mots pour affiner les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="e10ce-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="e10ce-106">Recherche par mots clés</span><span class="sxs-lookup"><span data-stu-id="e10ce-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="e10ce-107">Recherche tente de trouver des documents pertinents contenant toutes les 3 mots clés et retourner les documents correspondants.</span><span class="sxs-lookup"><span data-stu-id="e10ce-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="e10ce-108">Recherche à l’aide d’expressions et de mots clés</span><span class="sxs-lookup"><span data-stu-id="e10ce-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="e10ce-109">Si vous entrez une expression entre guillemets (« »), vous indiquez de rechercher une expression spécifique et non des mots clés distincts.</span><span class="sxs-lookup"><span data-stu-id="e10ce-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="e10ce-110">Les documents correspondants doivent généralement contenir l’expression exacte « sql azure », y compris avec des différences de casse, par exemple « SQL Azure » et également le mot « déploiement ».</span><span class="sxs-lookup"><span data-stu-id="e10ce-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="e10ce-111">Filtrage sur les champs</span><span class="sxs-lookup"><span data-stu-id="e10ce-111">Filtering on fields</span></span>

<span data-ttu-id="e10ce-112">Vous pouvez rechercher un ID (ou « Id » ou « id ») de package spécifique ou certains autres champs en ajoutant en préfixe le nom du champ au terme recherché.</span><span class="sxs-lookup"><span data-stu-id="e10ce-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="e10ce-113">Actuellement, les champs sur lesquels la recherche peut porter sont « Id », « Version », « Tags », « Author », « Owner », « Functions », « Cmdlets », « DscResources » et « PowerShellVersion ».</span><span class="sxs-lookup"><span data-stu-id="e10ce-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="e10ce-114">[Quelle est la différence entre l’ID et le titre ?</span><span class="sxs-lookup"><span data-stu-id="e10ce-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="e10ce-115">L’ID est le nom que vous utilisez dans la console.</span><span class="sxs-lookup"><span data-stu-id="e10ce-115">ID is the name you use in the console.</span></span> <span data-ttu-id="e10ce-116">Le titre est ce qui figure en haut de la page du package dans les résultats de la recherche.]</span><span class="sxs-lookup"><span data-stu-id="e10ce-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="e10ce-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="e10ce-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="e10ce-118">recherche les packages avec un ID contenant « PSReadline ».</span><span class="sxs-lookup"><span data-stu-id="e10ce-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="e10ce-119">est une autre façon de rechercher des packages avec « AzureRM.Profile » dans leur champ ID.</span><span class="sxs-lookup"><span data-stu-id="e10ce-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="e10ce-120">Le filtre Id étant une correspondance avec la sous-chaîne, si vous recherchez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e10ce-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="e10ce-121">Cela fournit des résultats qui incluent AzureRM.Profile » et « Azure.Storage ».</span><span class="sxs-lookup"><span data-stu-id="e10ce-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="e10ce-122">Vous pouvez également rechercher plusieurs mots clés dans un champ unique.</span><span class="sxs-lookup"><span data-stu-id="e10ce-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="e10ce-123">Et vous pouvez effectuer des recherches d’expressions à l’aide de guillemets doubles :</span><span class="sxs-lookup"><span data-stu-id="e10ce-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="e10ce-124">Pour rechercher tous les packages avec la balise DSC.</span><span class="sxs-lookup"><span data-stu-id="e10ce-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="e10ce-125">Pour rechercher tous les packages avec la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e10ce-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="e10ce-126">Pour rechercher tous les packages avec l’applet de commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e10ce-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="e10ce-127">Pour rechercher tous les packages avec le nom de ressource DSC spécifié.</span><span class="sxs-lookup"><span data-stu-id="e10ce-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="e10ce-128">Pour rechercher tous les packages avec la version PowerShell spécifiée</span><span class="sxs-lookup"><span data-stu-id="e10ce-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="e10ce-129">Enfin, si vous utilisez un champ non pris en charge, tel que « commandes », nous l’ignorons simplement et effectuons une recherche dans tous les champs.</span><span class="sxs-lookup"><span data-stu-id="e10ce-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="e10ce-130">Par conséquent, la requête suivante</span><span class="sxs-lookup"><span data-stu-id="e10ce-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="e10ce-131">est interprétée exactement comme cette requête :</span><span class="sxs-lookup"><span data-stu-id="e10ce-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
