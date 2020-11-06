---
ms.date: 06/12/2017
title: Déployer sur Azure Automation
description: Cet article explique comment utiliser PowerShell Gallery pour déployer un package sur Azure Automation.
ms.openlocfilehash: e9de079ee6cc950c8a268423b9eabd515959b718
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662368"
---
# <a name="deploy-to-azure-automation"></a>Déployer sur Azure Automation

Le bouton Déployer sur Azure Automation de la page de détails du package a pour effet de déployer le package de PowerShell Gallery sur Azure Automation.

![Bouton Déployer sur Azure Automation](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

Quand vous cliquez dessus, vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure. Si le package comporte des dépendances, elles sont toutes déployées sur Azure Automation par la même occasion.

> [!WARNING]
> Si le même package et la même version existent déjà dans le compte Automation, un nouveau déploiement à partir de PowerShell Gallery a pour effet de remplacer le package dans le compte.

Si vous déployez un module, il apparaît dans la section Modules d’Azure Automation. Si vous déployez un script, il apparaît dans la section Runbooks d’Azure Automation.

Pour désactiver le bouton Déployer sur Azure Automation, ajoutez la balise AzureAutomationNotSupported aux métadonnées du package.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exiger l’acceptation de la licence lors du déploiement sur Azure Automation

Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence. En cliquant sur OK, vous acceptez les termes du contrat de licence. »

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Détails supplémentaires

- [Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
- [Exiger l’acceptation de la licence dans PowerShell Gallery](packages-that-require-license-acceptance.md)
- [Site web Azure Automation](https://azure.microsoft.com/services/automation/)
