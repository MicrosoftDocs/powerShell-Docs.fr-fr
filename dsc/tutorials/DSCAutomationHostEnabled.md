---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clé de Registre DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401191"
---
><span data-ttu-id="4f340-103">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f340-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="4f340-104">Clé de Registre DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="4f340-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="4f340-105">DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** pour activer la configuration de l’ordinateur au moment du démarrage initial.</span><span class="sxs-lookup"><span data-stu-id="4f340-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="4f340-106">DSCAutomationHostEnabled prend en charge trois modes :</span><span class="sxs-lookup"><span data-stu-id="4f340-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="4f340-107">Valeur de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="4f340-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="4f340-108">Description</span><span class="sxs-lookup"><span data-stu-id="4f340-108">Description</span></span>   |
|---|---|
<span data-ttu-id="4f340-109">0</span><span class="sxs-lookup"><span data-stu-id="4f340-109">0</span></span> | <span data-ttu-id="4f340-110">Désactive la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="4f340-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="4f340-111">1</span><span class="sxs-lookup"><span data-stu-id="4f340-111">1</span></span> | <span data-ttu-id="4f340-112">Active la configuration de la machine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="4f340-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="4f340-113">2</span><span class="sxs-lookup"><span data-stu-id="4f340-113">2</span></span> | <span data-ttu-id="4f340-114">Active la configuration de la machine uniquement si DSC est en attente ou en cours.</span><span class="sxs-lookup"><span data-stu-id="4f340-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="4f340-115">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4f340-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4f340-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f340-116">See Also</span></span>

<span data-ttu-id="4f340-117">Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="4f340-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>