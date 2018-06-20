---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Microsoft Azure
ms.openlocfilehash: d35488c3f66895e930eaa84360f3d3ec9d74e9c7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221882"
---
# <a name="using-dsc-on-microsoft-azure"></a>Utilisation de DSC sur Microsoft Azure

La configuration d’état souhaité (DSC) est prise en charge dans Microsoft Azure par le biais du [gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) et d’[Azure Automation DSC](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Gestionnaire d’extensions de configuration d’état souhaité Azure

L’extension Azure DSC permet aux machines virtuelles hébergées dans Microsoft Azure d’être gérées avec DSC.
Pour plus d'informations, voir les rubriques suivantes :

- [Gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [VMSS Windows et configuration d’état souhaité avec des modèles Azure Resource Manager](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Transfert d’informations d’identification au gestionnaire de l’extension de configuration d’état souhaité (DSC) Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Historique de l’extension Configuration d’état souhaité Azure](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

Le [service Azure Automation](https://azure.microsoft.com/services/automation/) vous permet de gérer les nœuds gérés, ressources et configurations DSC dans Azure. Pour plus d'informations, voir les rubriques suivantes :

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Bien démarrer avec Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Intégration d’ordinateurs en vue de leur gestion par Azure Automation DSC](/azure/automation/automation-dsc-onboarding)