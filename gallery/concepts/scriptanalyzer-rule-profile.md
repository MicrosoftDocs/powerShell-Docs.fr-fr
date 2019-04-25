---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Profil de règle ScriptAnalyzer pour la galerie
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084587"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Profil de règle ScriptAnalyzer pour la galerie

Pour garantir la qualité des packages publiés sur PowerShell Gallery, nous appliquons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) visant à identifier la présence de violations dans les scripts soumis.

Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.
Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalyzer.

Dans la version à venir, les résultats de ScriptAnalyzer s’afficheront sur la page de chacun des packages de la galerie. Nous encourageons les propriétaires à vérifier que les packages qu’ils ont publiés ne comportent pas d’erreurs graves.
