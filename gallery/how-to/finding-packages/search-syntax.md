---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Syntaxe de recherche PowerShell Gallery
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003702"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="11ba6-103">Syntaxe de recherche PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="11ba6-103">Gallery Search Syntax</span></span>

<span data-ttu-id="11ba6-104">PowerShell Gallery offre une zone de recherche de texte où vous pouvez utiliser des mots, des expressions et des mots clés pour limiter les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="11ba6-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="11ba6-105">Recherche par mots clés</span><span class="sxs-lookup"><span data-stu-id="11ba6-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="11ba6-106">La recherche fera de son mieux pour trouver des documents pertinents contenant les 3 mots clés et retourner les documents correspondants.</span><span class="sxs-lookup"><span data-stu-id="11ba6-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="11ba6-107">Recherche à l’aide d’expressions et de mots clés</span><span class="sxs-lookup"><span data-stu-id="11ba6-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="11ba6-108">Si vous entrez une expression entre guillemets (« »), vous indiquez de rechercher une expression spécifique et non des mots clés distincts.</span><span class="sxs-lookup"><span data-stu-id="11ba6-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="11ba6-109">Les documents correspondants doivent généralement contenir l’expression exacte « sql azure », y compris avec des différences de casse, par exemple « SQL Azure » et également le mot « déploiement ».</span><span class="sxs-lookup"><span data-stu-id="11ba6-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="11ba6-110">Filtrage sur les champs</span><span class="sxs-lookup"><span data-stu-id="11ba6-110">Filtering on fields</span></span>

<span data-ttu-id="11ba6-111">Vous pouvez rechercher un ID (ou « Id » ou « id ») de package spécifique ou certains autres champs en ajoutant en préfixe le nom du champ au terme recherché.</span><span class="sxs-lookup"><span data-stu-id="11ba6-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="11ba6-112">Actuellement, les champs sur lesquels la recherche peut porter sont « Id », « Version », « Tags », « Author », « Owner », « Functions », « Cmdlets », « DscResources » et « PowerShellVersion ».</span><span class="sxs-lookup"><span data-stu-id="11ba6-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="11ba6-113">[Quelle est la différence entre l’ID et le titre ?</span><span class="sxs-lookup"><span data-stu-id="11ba6-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="11ba6-114">L’ID est le nom que vous utilisez dans la console.</span><span class="sxs-lookup"><span data-stu-id="11ba6-114">ID is the name you use in the console.</span></span> <span data-ttu-id="11ba6-115">Le titre est ce qui figure en haut de la page du package dans les résultats de la recherche.]</span><span class="sxs-lookup"><span data-stu-id="11ba6-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="11ba6-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="11ba6-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="11ba6-117">recherche des packages avec « PSReadline » ou « AzureRM.Profile » dans leur champ ID, respectivement.</span><span class="sxs-lookup"><span data-stu-id="11ba6-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="11ba6-118">est une autre façon de rechercher des packages avec « AzureRM.Profile » dans leur champ ID.</span><span class="sxs-lookup"><span data-stu-id="11ba6-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="11ba6-119">Le filtre Id étant une correspondance avec la sous-chaîne, si vous recherchez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="11ba6-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="11ba6-120">Vous obtiendrez des résultats comme « AzureRM.Profile » et « Azure.Storage ».</span><span class="sxs-lookup"><span data-stu-id="11ba6-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="11ba6-121">Vous pouvez également rechercher plusieurs mots clés dans un champ unique.</span><span class="sxs-lookup"><span data-stu-id="11ba6-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="11ba6-122">Vous pouvez aussi combiner et associer des champs.</span><span class="sxs-lookup"><span data-stu-id="11ba6-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="11ba6-123">Vous pouvez effectuer des recherches d’expressions :</span><span class="sxs-lookup"><span data-stu-id="11ba6-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="11ba6-124">Pour rechercher tous les packages avec la balise DSC.</span><span class="sxs-lookup"><span data-stu-id="11ba6-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="11ba6-125">Pour rechercher tous les packages avec la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="11ba6-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="11ba6-126">Pour rechercher tous les packages avec l’applet de commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="11ba6-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="11ba6-127">Pour rechercher tous les packages avec le nom de ressource DSC spécifié.</span><span class="sxs-lookup"><span data-stu-id="11ba6-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="11ba6-128">Pour rechercher tous les packages avec la version PowerShell spécifiée</span><span class="sxs-lookup"><span data-stu-id="11ba6-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="11ba6-129">Enfin, si vous utilisez un champ non pris en charge, tel que « commandes », nous l’ignorons simplement et effectuons une recherche dans tous les champs.</span><span class="sxs-lookup"><span data-stu-id="11ba6-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="11ba6-130">Par conséquent, la requête suivante</span><span class="sxs-lookup"><span data-stu-id="11ba6-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="11ba6-131">est interprétée exactement comme cette requête :</span><span class="sxs-lookup"><span data-stu-id="11ba6-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
