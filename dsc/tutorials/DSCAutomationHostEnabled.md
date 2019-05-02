---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clé de Registre DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076474"
---
>S'applique à : Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Clé de Registre DSCAutomationHostEnabled

DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** pour activer la configuration de l’ordinateur au moment du démarrage initial.
**DSCAutomationHostEnabled** gère trois modes :

|  Valeur de DSCAutomationHostEnabled  |  Description   |
|---|---|
0 | Désactive la configuration de la machine au démarrage. |
1 | Active la configuration de la machine au démarrage. |
2 | Active la configuration de la machine uniquement si DSC est en attente ou en cours. Il s'agit de la valeur par défaut. |

## <a name="see-also"></a>Voir aussi

Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).
