---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Syntaxe de recherche PowerShell Gallery
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="gallery-search-syntax"></a>Syntaxe de recherche PowerShell Gallery

PowerShell Gallery offre une zone de recherche de texte où vous pouvez utiliser des mots, des expressions et des mots clés pour limiter les résultats de la recherche.

## <a name="search-by-keywords"></a>Recherche par mots clés

    dsc azure sql

La recherche fera de son mieux pour trouver des documents pertinents contenant les 3 mots clés et retourner les documents correspondants.

## <a name="search-using-phrases-and-keywords"></a>Recherche à l’aide d’expressions et de mots clés

    "azure sql" deployment

Si vous entrez une expression entre guillemets (« »), vous indiquez de rechercher une expression spécifique et non des mots clés distincts.
Les documents correspondants doivent généralement contenir l’expression exacte « sql azure », y compris avec des différences de casse, par exemple « SQL Azure » et également le mot « déploiement ».

## <a name="filtering-on-fields"></a>Filtrage sur les champs

Vous pouvez rechercher un ID (ou « Id » ou « id ») d’élément spécifique ou certains autres champs en ajoutant en préfixe le nom du champ au terme recherché.

Actuellement, les champs sur lesquels la recherche peut porter sont « Id », « Version », « Tags », « Author », « Owner », « Functions », « Cmdlets », « DscResources » et « PowerShellVersion ».

[Quelle est la différence entre l’ID et le titre ? L’ID est le nom que vous utilisez dans la console. Le titre est ce qui figure en haut de la page de l’élément dans les résultats de la recherche.]

## <a name="examples"></a>Exemples

    ID:"PSReadline"
    id:"AzureRM.Profile"

recherche des éléments avec « PSReadline » ou « AzureRM.Profile » dans leur champ ID, respectivement.

    Id:"AzureRM.Profile"

est une autre façon de rechercher des éléments avec « AzureRM.Profile » dans leur champ ID.

Le filtre Id étant une correspondance avec la sous-chaîne, si vous recherchez ce qui suit :

    Id:"azure"

Vous obtiendrez des résultats comme « AzureRM.Profile » et « Azure.Storage ».

Vous pouvez également rechercher plusieurs mots clés dans un champ unique. Vous pouvez aussi combiner et associer des champs.

    id:azure tags:intellisense
    id:azure id:storage

Vous pouvez effectuer des recherches d’expressions :

    id:"azure.storage"


Pour rechercher tous les éléments avec la balise DSC.

    Tags:"DSC"

Pour rechercher tous les éléments avec la fonction spécifiée.

    Functions:"Update-AzureRM"

Pour rechercher tous les éléments avec l’applet de commande spécifiée.

    Cmdlets:"Get-AzureRmEnvironment"

Pour rechercher tous les éléments avec le nom de ressource DSC spécifié.

    DscResources:"xArchive"

Pour rechercher tous les éléments avec la version PowerShell spécifiée

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Enfin, si vous utilisez un champ non pris en charge, tel que « commandes », nous l’ignorons simplement et effectuons une recherche dans tous les champs. Par conséquent, la requête suivante

    commands:blobs storage

est interprétée exactement comme cette requête :

    blobs storage