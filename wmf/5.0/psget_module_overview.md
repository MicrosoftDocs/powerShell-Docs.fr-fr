---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222171"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="c6c0e-102">Découverte de module PowerShell, installer et inventorier avec PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c6c0e-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="c6c0e-103">PowerShellGet est fourni avec cette version de WMF :</span><span class="sxs-lookup"><span data-stu-id="c6c0e-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="c6c0e-104">Find-Module peut filtrer les métadonnées de modules avec le paramètre -Tag</span><span class="sxs-lookup"><span data-stu-id="c6c0e-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="c6c0e-105">Find-Module peut filtrer le langage de recherche propre au dépôt avec le paramètre -Filter</span><span class="sxs-lookup"><span data-stu-id="c6c0e-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="c6c0e-106">Find-Module peut filtrer le contenu de module avec les paramètres -Command, -DscResource et -Includes.</span><span class="sxs-lookup"><span data-stu-id="c6c0e-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="c6c0e-107">Find-DscResource autorise la découverte des ressources DSC individuelles dans les dépôts</span><span class="sxs-lookup"><span data-stu-id="c6c0e-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="c6c0e-108">Prise en charge de l’installation à partir de partages de fichiers et de la publication vers des partages de fichiers avec NuGet</span><span class="sxs-lookup"><span data-stu-id="c6c0e-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="c6c0e-109">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="c6c0e-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="c6c0e-110">Nouvelles fonctionnalités de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c6c0e-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="c6c0e-111">Prise en charge des versions côte à côte dans Windows PowerShell 5.0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="c6c0e-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="c6c0e-112">Prise en charge de l’installation de dépendances de modules</span><span class="sxs-lookup"><span data-stu-id="c6c0e-112">Module dependency installation support</span></span>
-   <span data-ttu-id="c6c0e-113">Trois nouvelles applets de commande</span><span class="sxs-lookup"><span data-stu-id="c6c0e-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="c6c0e-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="c6c0e-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="c6c0e-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="c6c0e-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="c6c0e-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="c6c0e-116">Save-Module</span></span>
