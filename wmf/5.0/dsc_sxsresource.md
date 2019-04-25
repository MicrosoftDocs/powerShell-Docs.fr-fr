---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057923"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Prise en charge du contrôle de version de modules côte à côte pour les ressources DSC

Les modules contenant des ressources DSC peuvent être installés côte à côte, et les configurations DSC peuvent utiliser une version spécifique de la ressource installée sur le système.

Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problèmes connus

Voici une liste des problèmes connus avec l’installation côte à côte dans cette version :

-   L’utilisation de deux versions différentes de la ressource DSC dans la même configuration n’est pas prise en charge.
