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
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="25aea-104">Clé de Registre DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="25aea-104">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="25aea-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25aea-105">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="25aea-106">DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** pour activer la configuration de l’ordinateur au moment du démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="25aea-106">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span> <span data-ttu-id="25aea-107">**DSCAutomationHostEnabled** gère trois modes :</span><span class="sxs-lookup"><span data-stu-id="25aea-107">**DSCAutomationHostEnabled** supports three modes:</span></span>

| <span data-ttu-id="25aea-108">Valeur de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="25aea-108">DSCAutomationHostEnabled Value</span></span> |                                              <span data-ttu-id="25aea-109">Description</span><span class="sxs-lookup"><span data-stu-id="25aea-109">Description</span></span>                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="25aea-110">0</span><span class="sxs-lookup"><span data-stu-id="25aea-110">0</span></span>                              | <span data-ttu-id="25aea-111">Désactive la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="25aea-111">Disable configuring the machine at boot-up.</span></span>                                                           |
| <span data-ttu-id="25aea-112">1</span><span class="sxs-lookup"><span data-stu-id="25aea-112">1</span></span>                              | <span data-ttu-id="25aea-113">Active la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="25aea-113">Enable configuring the machine at boot-up.</span></span>                                                            |
| <span data-ttu-id="25aea-114">2</span><span class="sxs-lookup"><span data-stu-id="25aea-114">2</span></span>                              | <span data-ttu-id="25aea-115">Active la configuration de la machine uniquement si DSC est en attente ou en cours.</span><span class="sxs-lookup"><span data-stu-id="25aea-115">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="25aea-116">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="25aea-116">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="25aea-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25aea-117">See Also</span></span>

<span data-ttu-id="25aea-118">Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="25aea-118">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
