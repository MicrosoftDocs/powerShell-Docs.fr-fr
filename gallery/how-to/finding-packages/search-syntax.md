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
# <a name="gallery-search-syntax"></a>Syntaxe de recherche PowerShell Gallery

Vous pouvez rechercher l’à l’aide de PowerShell Gallery le [site web de PowerShell Gallery](https://www.powershellgallery.com/).
Site web PowerShell Gallery offre un searchbox de texte où vous pouvez utiliser des mots, expressions et des mots pour affiner les résultats de recherche.

## <a name="search-by-keywords"></a>Recherche par mots clés

    dsc azure sql

Recherche tente de trouver des documents pertinents contenant toutes les 3 mots clés et retourner les documents correspondants.

## <a name="search-using-phrases-and-keywords"></a>Recherche à l’aide d’expressions et de mots clés

    "azure sql" deployment

Si vous entrez une expression entre guillemets (« »), vous indiquez de rechercher une expression spécifique et non des mots clés distincts.
Les documents correspondants doivent généralement contenir l’expression exacte « sql azure », y compris avec des différences de casse, par exemple « SQL Azure » et également le mot « déploiement ».

## <a name="filtering-on-fields"></a>Filtrage sur les champs

Vous pouvez rechercher un ID (ou « Id » ou « id ») de package spécifique ou certains autres champs en ajoutant en préfixe le nom du champ au terme recherché.

Actuellement, les champs sur lesquels la recherche peut porter sont « Id », « Version », « Tags », « Author », « Owner », « Functions », « Cmdlets », « DscResources » et « PowerShellVersion ».

[Quelle est la différence entre l’ID et le titre ? L’ID est le nom que vous utilisez dans la console. Le titre est ce qui figure en haut de la page du package dans les résultats de la recherche.]

## <a name="examples"></a>Exemples

    ID:PSReadline
    
recherche les packages avec un ID contenant « PSReadline ».

    Id:"AzureRM.Profile"

est une autre façon de rechercher des packages avec « AzureRM.Profile » dans leur champ ID.

Le filtre Id étant une correspondance avec la sous-chaîne, si vous recherchez ce qui suit :

    Id:"azure"

Cela fournit des résultats qui incluent AzureRM.Profile » et « Azure.Storage ».

Vous pouvez également rechercher plusieurs mots clés dans un champ unique. 

    id:azure tags:intellisense

Et vous pouvez effectuer des recherches d’expressions à l’aide de guillemets doubles :

    id:"azure.storage"

Pour rechercher tous les packages avec la balise DSC.

    Tags:DSC

Pour rechercher tous les packages avec la fonction spécifiée.

    Functions:Get-TreeSize

Pour rechercher tous les packages avec l’applet de commande spécifiée.

    Cmdlets:Get-AzureRmEnvironment

Pour rechercher tous les packages avec le nom de ressource DSC spécifié.

    DscResources:xArchive

Pour rechercher tous les packages avec la version PowerShell spécifiée

    PowerShellVersion:2.0

Enfin, si vous utilisez un champ non pris en charge, tel que « commandes », nous l’ignorons simplement et effectuons une recherche dans tous les champs. Par conséquent, la requête suivante

    commands:blobs storage

est interprétée exactement comme cette requête :

    blobs storage
