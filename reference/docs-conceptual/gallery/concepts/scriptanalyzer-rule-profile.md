---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Profil de règle ScriptAnalyzer pour la galerie
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328470"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="2581a-103">Profil de règle ScriptAnalyzer pour la galerie</span><span class="sxs-lookup"><span data-stu-id="2581a-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="2581a-104">Pour garantir la qualité des packages publiés sur PowerShell Gallery, nous appliquons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) visant à identifier la présence de violations dans les scripts soumis.</span><span class="sxs-lookup"><span data-stu-id="2581a-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="2581a-105">Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="2581a-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="2581a-106">Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="2581a-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="2581a-107">Dans la version à venir, les résultats de ScriptAnalyzer s’afficheront sur la page de chacun des packages de la galerie.</span><span class="sxs-lookup"><span data-stu-id="2581a-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="2581a-108">Nous encourageons les propriétaires à vérifier que les packages qu’ils ont publiés ne comportent pas d’erreurs graves.</span><span class="sxs-lookup"><span data-stu-id="2581a-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
