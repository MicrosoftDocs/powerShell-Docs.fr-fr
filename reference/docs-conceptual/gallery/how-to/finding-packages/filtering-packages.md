---
ms.date: 06/12/2017
title: Filtrage des résultats de la recherche
description: Cet article décrit l’interface utilisateur utilisée pour filtrer le contenu dans PowerShell Gallery.
ms.openlocfilehash: cc375f3ddb35c95ed134776500bd326bc3db6b1a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661401"
---
# <a name="filtering-search-results"></a>Filtrage des résultats de la recherche

[L’onglet Packages](https://www.powershellgallery.com/packages) affiche tous les packages disponibles sur PowerShell Gallery.

Il existe plusieurs moyens de filtrer, de trier et de parcourir les packages. Pour afficher des informations sur un package en particulier, cliquez dessus.

## <a name="filter-by"></a>Filtrer par

La liste déroulante sous « Filtrer par » permet aux utilisateurs de filtrer les résultats selon :

- Inclure la préversion
- Stable uniquement

Pour plus d’informations sur « Préversion » et « Stable », consultez [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Gestion des préversions ajoutée à PowerShellGet et à PowerShell Gallery) dans le blog de l’équipe PowerShell.

Les cases à cocher sous la liste déroulante permettent aux utilisateurs de filtrer les résultats par :

- Types de packages
  - Module
  - Script
- Catégories
  - Applet de commande
  - Ressource DSC
  - Fonction
  - Fonctionnalité Rôle
  - Workflow

Pour afficher uniquement les modules de PowerShell Gallery, cochez Module dans Types de packages. De même, pour afficher uniquement les scripts de PowerShell Gallery, cochez Script dans Types de packages.

> [!NOTE]
> Les filtres sont inclusifs. Exemple : un package contenant à la fois des cmdlets et des fonctions s’affiche si la case Cmdlet ou la case Function (ou les deux) sont cochées. Si aucune des deux n’est sélectionnée, le package n’apparaît pas. De même, si toutes les catégories sont sélectionnées, seuls les packages contenant l’une de ces catégories s’affichent. **Les packages qui n’appartiennent à aucune de ces catégories n’apparaissent pas.**

## <a name="sort-by"></a>Trier par

La liste déroulante Trier par permet aux utilisateurs de trier les résultats par :

- Popularité : la popularité est déterminée par le nombre de téléchargements
- A à Z : par ordre alphabétique de nom de package
- Récent : par date de publication des packages

## <a name="search-box"></a>Zone de recherche

La zone de recherche permet aux utilisateurs de rechercher des packages par mots clés.
Pour plus d’informations, consultez [Syntaxe de recherche dans la galerie](search-syntax.md).
