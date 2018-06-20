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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="41ed8-102">Informations détaillées sur l’état du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="41ed8-102">Detailed information about LCM state</span></span>

<span data-ttu-id="41ed8-103">Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="41ed8-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="41ed8-104">Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="41ed8-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="41ed8-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="41ed8-105">**Idle**</span></span>
* <span data-ttu-id="41ed8-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="41ed8-106">**Busy**</span></span>
* <span data-ttu-id="41ed8-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="41ed8-107">**PendingReboot**</span></span>
* <span data-ttu-id="41ed8-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="41ed8-108">**PendingConfiguration**</span></span>

<span data-ttu-id="41ed8-109">Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.</span><span class="sxs-lookup"><span data-stu-id="41ed8-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
