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
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="5c7a5-103">Clé de Registre DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="5c7a5-103">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="5c7a5-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5c7a5-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5c7a5-105">DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** pour activer la configuration de l’ordinateur au moment du démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="5c7a5-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="5c7a5-106">**DSCAutomationHostEnabled** gère trois modes :</span><span class="sxs-lookup"><span data-stu-id="5c7a5-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="5c7a5-107">Valeur de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="5c7a5-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="5c7a5-108">Description</span><span class="sxs-lookup"><span data-stu-id="5c7a5-108">Description</span></span>   |
|---|---|
<span data-ttu-id="5c7a5-109">0</span><span class="sxs-lookup"><span data-stu-id="5c7a5-109">0</span></span> | <span data-ttu-id="5c7a5-110">Désactive la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="5c7a5-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="5c7a5-111">1</span><span class="sxs-lookup"><span data-stu-id="5c7a5-111">1</span></span> | <span data-ttu-id="5c7a5-112">Active la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="5c7a5-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="5c7a5-113">2</span><span class="sxs-lookup"><span data-stu-id="5c7a5-113">2</span></span> | <span data-ttu-id="5c7a5-114">Active la configuration de la machine uniquement si DSC est en attente ou en cours.</span><span class="sxs-lookup"><span data-stu-id="5c7a5-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="5c7a5-115">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5c7a5-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="5c7a5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c7a5-116">See Also</span></span>

<span data-ttu-id="5c7a5-117">Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="5c7a5-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
