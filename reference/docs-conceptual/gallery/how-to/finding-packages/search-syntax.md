---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Syntaxe de recherche PowerShell Gallery
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328450"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="220c4-103">Syntaxe de recherche PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="220c4-103">Gallery Search Syntax</span></span>

<span data-ttu-id="220c4-104">Pour faire une recherche dans PowerShell Gallery, vous pouvez utiliser le [site web de PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="220c4-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="220c4-105">Il propose une zone de recherche de texte qui accepte des mots, des expressions et des mots clés pour limiter les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="220c4-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="220c4-106">Recherche par mots clés</span><span class="sxs-lookup"><span data-stu-id="220c4-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="220c4-107">Sont recherchés et retournés les documents contenant les trois mots clés.</span><span class="sxs-lookup"><span data-stu-id="220c4-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="220c4-108">Recherche à l’aide d’expressions et de mots clés</span><span class="sxs-lookup"><span data-stu-id="220c4-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="220c4-109">Si vous entrez une expression entre guillemets (« »), vous indiquez de rechercher une expression spécifique et non des mots clés distincts.</span><span class="sxs-lookup"><span data-stu-id="220c4-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="220c4-110">Les documents correspondants doivent généralement contenir l’expression exacte « sql azure », y compris avec des différences de casse, par exemple « SQL Azure » et également le mot « déploiement ».</span><span class="sxs-lookup"><span data-stu-id="220c4-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="220c4-111">Filtrage sur les champs</span><span class="sxs-lookup"><span data-stu-id="220c4-111">Filtering on fields</span></span>

<span data-ttu-id="220c4-112">Vous pouvez rechercher un ID (ou « Id » ou « id ») de package spécifique ou certains autres champs en ajoutant en préfixe le nom du champ au terme recherché.</span><span class="sxs-lookup"><span data-stu-id="220c4-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="220c4-113">Actuellement, les champs sur lesquels la recherche peut porter sont « Id », « Version », « Tags », « Author », « Owner », « Functions », « Cmdlets », « DscResources » et « PowerShellVersion ».</span><span class="sxs-lookup"><span data-stu-id="220c4-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="220c4-114">[Quelle est la différence entre l’ID et le titre ?</span><span class="sxs-lookup"><span data-stu-id="220c4-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="220c4-115">L’ID est le nom que vous utilisez dans la console.</span><span class="sxs-lookup"><span data-stu-id="220c4-115">ID is the name you use in the console.</span></span> <span data-ttu-id="220c4-116">Le titre est ce qui figure en haut de la page du package dans les résultats de la recherche.]</span><span class="sxs-lookup"><span data-stu-id="220c4-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="220c4-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="220c4-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="220c4-118">Sont recherchés les packages dont l’ID contient « PSReadline ».</span><span class="sxs-lookup"><span data-stu-id="220c4-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="220c4-119">est une autre façon de rechercher des packages avec « AzureRM.Profile » dans leur champ ID.</span><span class="sxs-lookup"><span data-stu-id="220c4-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="220c4-120">Le filtre Id étant une correspondance avec la sous-chaîne, si vous recherchez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="220c4-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="220c4-121">Les résultats retournés comportent « AzureRM.Profile » et « Azure.Storage ».</span><span class="sxs-lookup"><span data-stu-id="220c4-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="220c4-122">Vous pouvez également rechercher plusieurs mots clés dans un champ unique.</span><span class="sxs-lookup"><span data-stu-id="220c4-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="220c4-123">Il est aussi possible d’effectuer des recherches d’expressions entre guillemets doubles :</span><span class="sxs-lookup"><span data-stu-id="220c4-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="220c4-124">Pour rechercher tous les packages avec la balise DSC.</span><span class="sxs-lookup"><span data-stu-id="220c4-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="220c4-125">Pour rechercher tous les packages avec la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="220c4-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="220c4-126">Pour rechercher tous les packages avec l’applet de commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="220c4-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="220c4-127">Pour rechercher tous les packages avec le nom de ressource DSC spécifié.</span><span class="sxs-lookup"><span data-stu-id="220c4-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="220c4-128">Pour rechercher tous les packages avec la version PowerShell spécifiée</span><span class="sxs-lookup"><span data-stu-id="220c4-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="220c4-129">Enfin, si vous utilisez un champ non pris en charge, tel que « commandes », nous l’ignorons simplement et effectuons une recherche dans tous les champs.</span><span class="sxs-lookup"><span data-stu-id="220c4-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="220c4-130">Par conséquent, la requête suivante</span><span class="sxs-lookup"><span data-stu-id="220c4-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="220c4-131">est interprétée exactement comme cette requête :</span><span class="sxs-lookup"><span data-stu-id="220c4-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage