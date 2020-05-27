---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Clé de Registre DSCAutomationHostEnabled
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808331"
---
# <a name="dscautomationhostenabled-registry-key"></a>Clé de Registre DSCAutomationHostEnabled

> S’applique à : Windows PowerShell 5.0

DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** pour activer la configuration de l’ordinateur au moment du démarrage initial.
**DSCAutomationHostEnabled** gère trois modes :

|  Valeur de DSCAutomationHostEnabled  |  Description   |
|---|---|
0 | Désactive la configuration de la machine au démarrage. |
1 | Active la configuration de la machine au démarrage. |
2 | Active la configuration de la machine uniquement si DSC est en attente ou en cours. Il s’agit de la valeur par défaut. |

## <a name="see-also"></a>Voir aussi

Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).
