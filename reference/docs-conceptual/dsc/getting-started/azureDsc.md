---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,installation
title: Utilisation de DSC sur Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870827"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="ff89b-103">Utilisation de DSC sur Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="ff89b-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="ff89b-104">La configuration d’état souhaité (DSC) est prise en charge dans Microsoft Azure par le biais du [gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/extensions/dsc-overview) et d’[Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="ff89b-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="ff89b-105">Gestionnaire d’extensions de configuration d’état souhaité Azure</span><span class="sxs-lookup"><span data-stu-id="ff89b-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="ff89b-106">L’extension Azure DSC permet aux machines virtuelles hébergées dans Microsoft Azure d’être gérées avec DSC.</span><span class="sxs-lookup"><span data-stu-id="ff89b-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="ff89b-107">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ff89b-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="ff89b-108">Gestionnaire d’extensions de configuration d’état souhaité Azure</span><span class="sxs-lookup"><span data-stu-id="ff89b-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="ff89b-109">VMSS Windows et configuration d’état souhaité avec des modèles Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="ff89b-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="ff89b-110">Transfert d’informations d’identification au gestionnaire de l’extension de configuration d’état souhaité (DSC) Azure</span><span class="sxs-lookup"><span data-stu-id="ff89b-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="ff89b-111">Historique de l’extension Configuration d’état souhaité Azure</span><span class="sxs-lookup"><span data-stu-id="ff89b-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="ff89b-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="ff89b-112">Azure Automation DSC</span></span>

<span data-ttu-id="ff89b-113">Le [service Azure Automation](https://azure.microsoft.com/services/automation/) vous permet de gérer les nœuds gérés, ressources et configurations DSC dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ff89b-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="ff89b-114">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ff89b-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="ff89b-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="ff89b-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="ff89b-116">Bien démarrer avec Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="ff89b-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="ff89b-117">Gestion de machines avec Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="ff89b-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)