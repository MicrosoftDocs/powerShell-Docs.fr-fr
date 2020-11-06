---
ms.date: 06/12/2017
title: Utilisation de la fonctionnalité FileList dans PowerShell Gallery
description: Utilisation de la fonctionnalité FileList dans PowerShell Gallery
ms.openlocfilehash: 45e39cb3f2620228be9ad16c2bb697f23642195d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662270"
---
# <a name="filelist-feature-in-the-gallery"></a>Fonctionnalité FileList dans la galerie

Vous pouvez afficher le contenu de tous les packages publiés dans la galerie.

Cette fonctionnalité est en deux parties : lister les fichiers du package et afficher le contenu des fichiers dont le type est pris en charge. Nous prenons actuellement en charge l’affichage du contenu des extensions de fichier suivantes : .ps1, .psm1, .psd1, .ps1xml, .xml et .txt. Dans les prochaines versions, nous prendrons en charge davantage d’extensions de fichier.

## <a name="where-to-find-filelist"></a>Où trouver la fonctionnalité FileList ?

Sur la page de chaque package se trouvent une section Liste de fichiers et un lien **Afficher**.
Cliquez sur Afficher pour obtenir la liste complète des éléments contenus dans le package.

Chaque type de fichier pris en charge est affiché sous la forme d’un lien hypertexte. Cliquez sur ce lien pour accéder à une nouvelle page présentant le contenu des fichiers affiché dans la syntaxe PowerShell sélectionnée. Pour revenir à la page de détails du package, cliquez sur le titre ou la version du package en haut de l’écran.
