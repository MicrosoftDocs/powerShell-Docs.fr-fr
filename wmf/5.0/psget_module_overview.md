---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057466"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Découverte de module PowerShell, installer et inventorier avec PowerShellGet

PowerShellGet est fourni avec cette version de WMF :
-   Find-Module peut filtrer les métadonnées de modules avec le paramètre -Tag
-   Find-Module peut filtrer le langage de recherche propre au dépôt avec le paramètre -Filter
-   Find-Module peut filtrer le contenu de module avec les paramètres -Command, -DscResource et -Includes.
-   Find-DscResource autorise la découverte des ressources DSC individuelles dans les dépôts
-   Prise en charge de l’installation à partir de partages de fichiers et de la publication vers des partages de fichiers avec NuGet

## <a name="example-commands"></a>Exemples de commandes
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Nouvelles fonctionnalités de PowerShellGet
-   Prise en charge des versions côte à côte dans Windows PowerShell 5.0 ou version ultérieure
-   Prise en charge de l’installation de dépendances de modules
-   Trois nouvelles applets de commande
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
