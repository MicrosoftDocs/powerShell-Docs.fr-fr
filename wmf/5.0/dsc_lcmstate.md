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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="20979-102">Informations détaillées sur l’état du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="20979-102">Detailed information about LCM state</span></span>

<span data-ttu-id="20979-103">Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="20979-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="20979-104">Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="20979-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="20979-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="20979-105">**Idle**</span></span>
* <span data-ttu-id="20979-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="20979-106">**Busy**</span></span>
* <span data-ttu-id="20979-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="20979-107">**PendingReboot**</span></span>
* <span data-ttu-id="20979-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="20979-108">**PendingConfiguration**</span></span>

<span data-ttu-id="20979-109">Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.</span><span class="sxs-lookup"><span data-stu-id="20979-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
