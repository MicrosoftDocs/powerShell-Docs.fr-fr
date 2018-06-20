---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219859"
---
# <a name="detailed-information-about-lcm-state"></a>Informations détaillées sur l’état du gestionnaire de configuration local

Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local. Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.
