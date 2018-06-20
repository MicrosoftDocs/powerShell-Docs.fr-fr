---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Éléments avec des éditions PowerShell compatibles
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189497"
---
# <a name="items-with-compatible-powershell-editions"></a>Éléments avec des éditions PowerShell compatibles

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.

- **Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>PowerShell Gallery extrait des métadonnées d’éditions PS prises en charge et vous permet de filtrer les éléments compatibles pour des éditions PowerShell spécifiques

Si des éditions PS compatibles sont spécifiées pour un élément, elles sont répertoriées dans le cadre des « Éditions PowerShell » dans la page d’affichage de l’élément et également dans les résultats des éléments.

![Page d’affichage de l’élément avec des éditions PS](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Rechercher des éléments dans l’interface utilisateur PowerShell Gallery qui fonctionnent sur PowerShellCore

Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les éléments sur PowerShell Gallery.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Plus d’informations sur la création et la recherche des éléments avec des éditions PowerShell compatibles

- [Modules avec des éditions PS](../../concepts/module-psedition-support.md)
- [Scripts avec des éditions PS](../../concepts/script-psedition-support.md)