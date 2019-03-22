---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Profil de règle ScriptAnalyzer pour la galerie
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059590"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Profil de règle ScriptAnalyzer pour la galerie

Pour garantir la qualité des packages publiés sur PowerShell Gallery, nous appliquons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) visant à identifier la présence de violations dans les scripts soumis.

Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.
Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalyzer.

Dans la version à venir, les résultats de ScriptAnalyzer s’afficheront sur la page de chacun des packages de la galerie. Nous encourageons les propriétaires à vérifier que les packages qu’ils ont publiés ne comportent pas d’erreurs graves.
