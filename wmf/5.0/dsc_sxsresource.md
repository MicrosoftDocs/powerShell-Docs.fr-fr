---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218431"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="80f4d-102">Prise en charge du contrôle de version de modules côte à côte pour les ressources DSC</span><span class="sxs-lookup"><span data-stu-id="80f4d-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="80f4d-103">Les modules contenant des ressources DSC peuvent être installés côte à côte, et les configurations DSC peuvent utiliser une version spécifique de la ressource installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="80f4d-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="80f4d-104">Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="80f4d-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="80f4d-105">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="80f4d-105">Known issues</span></span>

<span data-ttu-id="80f4d-106">Voici une liste des problèmes connus avec l’installation côte à côte dans cette version :</span><span class="sxs-lookup"><span data-stu-id="80f4d-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="80f4d-107">L’utilisation de deux versions différentes de la ressource DSC dans la même configuration n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="80f4d-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
