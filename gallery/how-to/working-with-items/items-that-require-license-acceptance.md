---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery
title: Exiger l’acceptation de la licence
ms.openlocfilehash: 69787cdb12aa47223072551c9b68fc046573f022
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218397"
---
# <a name="require-license-acceptance"></a>Exiger l’acceptation de la licence

Le texte d’acceptation de la licence s’affiche sur la page des détails de l’article pour les modules qui nécessitent l’acceptation de la licence. La licence pour le module peut être affichée en cliquant sur le lien « View License.txt ».

![Exiger l’acceptation de la licence](../../Images/RequireLicenseAcceptance.png)

Les utilisateurs seront invités à accepter la licence lors de l’installation, de l’enregistrement ou de la mise à jour du module via PowerShellGet, ou lors du déploiement sur Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exiger l’acceptation de la licence lors du déploiement sur Azure Automation

Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence. En cliquant sur OK, vous acceptez les termes du contrat de licence. »

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Plus d’informations

[Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
[Site web Azure Automation](/azure/automation)