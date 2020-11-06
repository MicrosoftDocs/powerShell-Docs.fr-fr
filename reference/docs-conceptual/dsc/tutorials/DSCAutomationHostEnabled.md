---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Clé de Registre DSCAutomationHostEnabled
description: Cet article définit les valeurs qui peuvent être définies dans la clé de Registre DSCAutomationHostEnabled
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656183"
---
# <a name="dscautomationhostenabled-registry-key"></a>Clé de Registre DSCAutomationHostEnabled

> S’applique à : Windows PowerShell 5.0

DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** pour activer la configuration de l’ordinateur au moment du démarrage initial. **DSCAutomationHostEnabled** gère trois modes :

| Valeur de DSCAutomationHostEnabled |                                              Description                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 0                              | Désactive la configuration de la machine au démarrage.                                                           |
| 1                              | Active la configuration de la machine au démarrage.                                                            |
| 2                              | Active la configuration de la machine uniquement si DSC est en attente ou en cours. Il s’agit de la valeur par défaut. |

## <a name="see-also"></a>Voir aussi

Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).
