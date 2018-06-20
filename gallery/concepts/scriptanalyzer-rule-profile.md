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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="36e21-103">Profil de règle ScriptAnalyzer pour la galerie</span><span class="sxs-lookup"><span data-stu-id="36e21-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="36e21-104">Pour garantir la qualité des éléments publiés dans PowerShell Gallery, nous exécutons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) pour déterminer s’il existe des violations dans les scripts soumis.</span><span class="sxs-lookup"><span data-stu-id="36e21-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="36e21-105">Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="36e21-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="36e21-106">Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="36e21-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="36e21-107">Dans la version à venir, les résultats de ScriptAnalyzer seront affichés sur chaque page de chaque élément dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="36e21-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="36e21-108">Nous encourageons les propriétaires d’éléments à vérifier leurs éléments pour s’assurer qu’il n’existe pas d’erreurs graves dans les éléments publiés.</span><span class="sxs-lookup"><span data-stu-id="36e21-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
