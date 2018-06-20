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
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Prise en charge du contrôle de version de modules côte à côte pour les ressources DSC

Les modules contenant des ressources DSC peuvent être installés côte à côte, et les configurations DSC peuvent utiliser une version spécifique de la ressource installée sur le système.

Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problèmes connus

Voici une liste des problèmes connus avec l’installation côte à côte dans cette version :

-   L’utilisation de deux versions différentes de la ressource DSC dans la même configuration n’est pas prise en charge.
