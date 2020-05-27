---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,applet de commande,psgallery
title: Packages avec un système d’exploitation ou des éditions PowerShell compatibles
ms.openlocfilehash: fce1383fa604a555a40b050ce92c5cc45ca7054c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691449"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Packages avec des systèmes d’exploitation ou des éditions PowerShell compatibles

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent les compatibilités de la plateforme et les différents ensembles de fonctionnalités.

## <a name="searching-by-powershell-edition"></a>Recherche par édition de PowerShell

Les deux éditions de PowerShell sont :

- **Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et Bureau Windows.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell Gallery vous permet de filtrer les packages compatibles pour des éditions spécifiques de PowerShell

Si des éditions PS compatibles sont spécifiées pour un package, elles sont répertoriées dans le cadre des « Éditions PowerShell » dans la page d’affichage du package et également dans les résultats des packages.
Vous pouvez également rechercher les packages compatibles à l’aide de PowerShell.

![Page d’affichage de l’élément avec des éditions PS](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Rechercher des packages dans l’interface utilisateur PowerShell Gallery qui fonctionnent sur PowerShellCore

Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les packages sur PowerShell Gallery.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Rechercher des packages pour trouver des éditions compatibles à l’aide de PowerShell
Vous pouvez spécifier des balises pour filtrer l’édition de PowerShell et le système d’exploitation.
Vous utilisez l’applet de commande `Find-Package` en spécifiant le paramètre `-Tag` afin de spécifier l’édition (et le système d’exploitation) ciblée.
Comme ceci :

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Recherche par système d’exploitation

PowerShell Core étant disponible pour Windows, Linux et MacOS, les packages dans la galerie peuvent être conçus pour n’importe quelle combinaison de ces systèmes d’exploitation. Dans l’interface utilisateur de la galerie, utilisez les balises de recherche suivantes pour trouver des packages balisés par système d’exploitation :

- Balises : « Windows »
- Balises : « Linux »
- Balises : « MacOS »

Vous pouvez spécifier ces balises sur `Find-Module` (et autres applets de commande dans le module PowerShellGet), comme suit :

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Recherche de compatibilités multiples

Vous pouvez rechercher un package qui a plusieurs compatibilités à l’aide de la syntaxe suivante :

Balises : « Compatibility1 » « Compatibility2 »

Par exemple, si vous recherchez un package avec compatibilité PowerShell Core qui s’exécute sur des ordinateurs Windows et Linux, utilisez ces balises de recherche :

Balises : « PSEdition_Core » « Windows », « Linux »

Pour effectuer une recherche à l’aide de PowerShell, vous pouvez utiliser `Find-Module` (et les autres applets de commande dans le module PowerShellGet), comme suit :

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Plus d’informations sur la création et la recherche des packages avec des éditions PowerShell compatibles

- [Modules avec des éditions PS](../../concepts/module-psedition-support.md)
- [Scripts avec des éditions PS](../../concepts/script-psedition-support.md)
