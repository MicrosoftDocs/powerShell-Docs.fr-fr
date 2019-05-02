---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Syntaxe de recherche PowerShell Gallery
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084298"
---
# <a name="gallery-search-syntax"></a>Syntaxe de recherche PowerShell Gallery

Pour faire une recherche dans PowerShell Gallery, vous pouvez utiliser le [site web de PowerShell Gallery](https://www.powershellgallery.com/).
Il propose une zone de recherche de texte qui accepte des mots, des expressions et des mots clés pour limiter les résultats de la recherche.

## <a name="search-by-keywords"></a>Recherche par mots clés

    dsc azure sql

Sont recherchés et retournés les documents contenant les trois mots clés.

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
    
Sont recherchés les packages dont l’ID contient « PSReadline ».

    Id:"AzureRM.Profile"

est une autre façon de rechercher des packages avec « AzureRM.Profile » dans leur champ ID.

Le filtre Id étant une correspondance avec la sous-chaîne, si vous recherchez ce qui suit :

    Id:"azure"

Les résultats retournés comportent « AzureRM.Profile » et « Azure.Storage ».

Vous pouvez également rechercher plusieurs mots clés dans un champ unique. 

    id:azure tags:intellisense

Il est aussi possible d’effectuer des recherches d’expressions entre guillemets doubles :

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
