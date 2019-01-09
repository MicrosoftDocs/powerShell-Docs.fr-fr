---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,applet de commande,psgallery
title: Packages avec le système d’exploitation ou des éditions PowerShell compatibles
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747702"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Packages avec des systèmes d’exploitation ou des éditions PowerShell compatibles

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent les compatibilités de la plateforme et les différents ensembles de fonctionnalités.

## <a name="searching-by-powershell-edition"></a>Recherche par édition de PowerShell 
Les deux éditions de Powershell sont :
- **Édition Desktop :** repose sur .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.
- **Core Edition :** Basée sur .NET Core et assure la compatibilité avec les scripts et modules qui ciblent des versions de PowerShell exécutées sur des éditions à encombrement réduit de Windows telles que Nano Server et Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell Gallery permet de vous permettent de filtrer les packages compatibles pour les éditions PowerShell spécifiques

Si un package a compatible PSEditions spécifié, ils sont répertoriés dans le cadre des « Éditions PowerShell » dans la page d’affichage de package, ainsi que dans les résultats de packages.
Vous pouvez également rechercher des packages compatibles à l’aide de PowerShell.

![Page d’affichage de l’élément avec des éditions PS](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Rechercher des packages dans la galerie d’interface utilisateur qui fonctionnent sur PowerShell Core

Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les packages sur PowerShell Gallery.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.

![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Rechercher des packages à trouver des éditions compatibles à l’aide de PowerShell
Vous pouvez spécifier des balises pour filtrer pour l’édition de PowerShell et le système d’exploitation. Vous utilisez le `Find-Package` applet de commande en spécifiant le `-Tag` paramètre pour spécifier l’édition (et le système d’exploitation) que vous ciblez.
Comme ça :

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Recherche par système d’exploitation 

Dans la mesure où PowerShell Core est disponible pour Windows, Linux et MacOS, les packages dans la galerie peuvent être conçues pour n’importe quelle combinaison de ces systèmes d’exploitation. Dans la galerie d’interface utilisateur utiliser les balises de recherches suivantes pour rechercher des packages marqués par le système d’exploitation :

- Balises : « Windows »
- Balises : « Linux »
- Balises : « MacOS » 

Vous pouvez spécifier ces balises sur `Find-Module` (et autres applets de commande dans le module PowerShellGet), comme suit :

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Recherche de compatibilités plusieurs

Vous pouvez rechercher un package qui a plusieurs les compatibilités en utilisant la syntaxe : 

Balises « Compatibility1 » « Compatibility2 » 

Par exemple, si vous recherchez un package avec PowerShell Core compatibilité qui s’exécute sur des ordinateurs à la fois mon Windows et Linux, utilisez les balises de recherche :

Balises « PSEdition_Core » « Windows », « Linux » 

Pour effectuer une recherche à l’aide de PowerShell, vous pouvez utiliser la `Find-Module` (et les autres applets de commande dans le module PowerShellGet), comme suit :

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Plus d’informations sur la création et la recherche des packages avec des éditions PowerShell compatibles

- [Modules avec des éditions PS](../../concepts/module-psedition-support.md)
- [Scripts avec des éditions PS](../../concepts/script-psedition-support.md)
