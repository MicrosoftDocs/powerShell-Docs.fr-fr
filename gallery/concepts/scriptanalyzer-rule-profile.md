---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Profil de règle ScriptAnalyzer pour la galerie
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225740"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Profil de règle ScriptAnalyzer pour la galerie

Pour garantir la qualité des éléments publiés dans PowerShell Gallery, nous exécutons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) pour déterminer s’il existe des violations dans les scripts soumis.

Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.
Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalzyer.

Dans la version à venir, les résultats de ScriptAnalyzer seront affichés sur chaque page de chaque élément dans la galerie. Nous encourageons les propriétaires d’éléments à vérifier leurs éléments pour s’assurer qu’il n’existe pas d’erreurs graves dans les éléments publiés.
