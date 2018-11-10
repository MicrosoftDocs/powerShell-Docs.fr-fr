---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Profil de règle ScriptAnalyzer pour la galerie
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002494"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="42242-103">Profil de règle ScriptAnalyzer pour la galerie</span><span class="sxs-lookup"><span data-stu-id="42242-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="42242-104">Pour garantir la qualité des packages publiés sur PowerShell Gallery, nous appliquons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) visant à identifier la présence de violations dans les scripts soumis.</span><span class="sxs-lookup"><span data-stu-id="42242-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="42242-105">Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="42242-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="42242-106">Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="42242-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="42242-107">Dans la version à venir, les résultats de ScriptAnalyzer s’afficheront sur la page de chacun des packages de la galerie.</span><span class="sxs-lookup"><span data-stu-id="42242-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="42242-108">Nous encourageons les propriétaires à vérifier que les packages qu’ils ont publiés ne comportent pas d’erreurs graves.</span><span class="sxs-lookup"><span data-stu-id="42242-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
