---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clé de Registre DSCAutomationHostEnabled
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
><span data-ttu-id="615ac-103">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="615ac-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="615ac-104">Clé de Registre DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="615ac-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="615ac-105">DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** pour activer la configuration de l’ordinateur au moment du démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="615ac-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="615ac-106">DSCAutomationHostEnabled prend en charge trois modes :</span><span class="sxs-lookup"><span data-stu-id="615ac-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="615ac-107">Valeur de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="615ac-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="615ac-108">Description</span><span class="sxs-lookup"><span data-stu-id="615ac-108">Description</span></span>   |
|---|---|
<span data-ttu-id="615ac-109">0</span><span class="sxs-lookup"><span data-stu-id="615ac-109">0</span></span> | <span data-ttu-id="615ac-110">Désactive la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="615ac-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="615ac-111">1</span><span class="sxs-lookup"><span data-stu-id="615ac-111">1</span></span> | <span data-ttu-id="615ac-112">Active la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="615ac-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="615ac-113">2</span><span class="sxs-lookup"><span data-stu-id="615ac-113">2</span></span> | <span data-ttu-id="615ac-114">Active la configuration de la machine uniquement si DSC est en attente ou en cours.</span><span class="sxs-lookup"><span data-stu-id="615ac-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="615ac-115">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="615ac-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="615ac-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="615ac-116">See Also</span></span>

<span data-ttu-id="615ac-117">Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="615ac-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>