---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401132"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="06c4e-103">Utilisation de DSC sur Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="06c4e-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="06c4e-104">La configuration d’état souhaité (DSC) est prise en charge dans Microsoft Azure par le biais du [gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/extensions/dsc-overview) et d’[Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="06c4e-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="06c4e-105">Gestionnaire d’extensions de configuration d’état souhaité Azure</span><span class="sxs-lookup"><span data-stu-id="06c4e-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="06c4e-106">L’extension Azure DSC permet aux machines virtuelles hébergées dans Microsoft Azure d’être gérées avec DSC.</span><span class="sxs-lookup"><span data-stu-id="06c4e-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="06c4e-107">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="06c4e-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="06c4e-108">Gestionnaire d’extensions de configuration d’état souhaité Azure</span><span class="sxs-lookup"><span data-stu-id="06c4e-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="06c4e-109">VMSS Windows et configuration d’état souhaité avec des modèles Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="06c4e-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="06c4e-110">Transfert d’informations d’identification au gestionnaire de l’extension de configuration d’état souhaité (DSC) Azure</span><span class="sxs-lookup"><span data-stu-id="06c4e-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="06c4e-111">Historique de l’extension Configuration d’état souhaité Azure</span><span class="sxs-lookup"><span data-stu-id="06c4e-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="06c4e-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="06c4e-112">Azure Automation DSC</span></span>

<span data-ttu-id="06c4e-113">Le [service Azure Automation](https://azure.microsoft.com/en-us/services/automation/) vous permet de gérer les nœuds gérés, ressources et configurations DSC dans Azure.</span><span class="sxs-lookup"><span data-stu-id="06c4e-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="06c4e-114">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="06c4e-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="06c4e-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="06c4e-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="06c4e-116">Bien démarrer avec Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="06c4e-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="06c4e-117">Intégration d’ordinateurs en vue de leur gestion par Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="06c4e-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)