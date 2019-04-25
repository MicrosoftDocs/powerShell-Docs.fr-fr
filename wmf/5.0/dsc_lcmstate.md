---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085794"
---
# <a name="detailed-information-about-lcm-state"></a>Informations détaillées sur l’état du gestionnaire de configuration local

Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local. Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.
