---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079878"
---
# <a name="using-dsc-on-microsoft-azure"></a>Utilisation de DSC sur Microsoft Azure

La configuration d’état souhaité (DSC) est prise en charge dans Microsoft Azure par le biais du [gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/extensions/dsc-overview) et d’[Azure Automation DSC](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Gestionnaire d’extensions de configuration d’état souhaité Azure

L’extension Azure DSC permet aux machines virtuelles hébergées dans Microsoft Azure d’être gérées avec DSC.
Pour plus d'informations, voir les rubriques suivantes :

- [Gestionnaire d’extensions de configuration d’état souhaité Azure](/azure/virtual-machines/extensions/dsc-overview)
- [VMSS Windows et configuration d’état souhaité avec des modèles Azure Resource Manager](/azure/virtual-machines/extensions/dsc-template)
- [Transfert d’informations d’identification au gestionnaire de l’extension de configuration d’état souhaité (DSC) Azure](/azure/virtual-machines/extensions/dsc-credentials)
- [Historique de l’extension Configuration d’état souhaité Azure](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

Le [service Azure Automation](https://azure.microsoft.com/en-us/services/automation/) vous permet de gérer les nœuds gérés, ressources et configurations DSC dans Azure. Pour plus d'informations, voir les rubriques suivantes :

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Bien démarrer avec Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Intégration d’ordinateurs en vue de leur gestion par Azure Automation DSC](/azure/automation/automation-dsc-onboarding)