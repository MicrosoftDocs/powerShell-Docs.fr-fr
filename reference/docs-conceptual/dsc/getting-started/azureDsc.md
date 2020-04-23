---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,installation
title: Utilisation de DSC sur Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870827"
---
# <a name="using-dsc-on-microsoft-azure"></a>Utilisation de DSC sur Microsoft Azure

La configuration d’état souhaité (DSC) est prise en charge dans Microsoft Azure par le biais du [gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/extensions/dsc-overview) et d’[Azure Automation DSC](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Gestionnaire d’extensions de configuration d’état souhaité Azure

L’extension Azure DSC permet aux machines virtuelles hébergées dans Microsoft Azure d’être gérées avec DSC. Pour plus d'informations, voir les rubriques suivantes :

- [Gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/extensions/dsc-overview)
- [VMSS Windows et configuration d’état souhaité avec des modèles Azure Resource Manager](/azure/virtual-machines/extensions/dsc-template)
- [Transfert d’informations d’identification au gestionnaire de l’extension de configuration d’état souhaité (DSC) Azure](/azure/virtual-machines/extensions/dsc-credentials)
- [Historique de l’extension Configuration d’état souhaité Azure](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

Le [service Azure Automation](https://azure.microsoft.com/services/automation/) vous permet de gérer les nœuds gérés, ressources et configurations DSC dans Azure. Pour plus d'informations, voir les rubriques suivantes :

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Bien démarrer avec Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Gestion de machines avec Azure Automation DSC](/azure/automation/automation-dsc-onboarding)