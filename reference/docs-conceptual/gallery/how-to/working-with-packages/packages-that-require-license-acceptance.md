---
ms.date: 06/12/2017
title: Exiger l’acceptation de la licence
description: Procédure d’affichage de la licence de package sur la page des détails de l’élément
ms.openlocfilehash: 0d8a9ed671f7993726bc3fa41d11159b366e5a28
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662308"
---
# <a name="require-license-acceptance"></a>Exiger l’acceptation de la licence

Le texte d’acceptation de la licence s’affiche sur la page des détails de l’article pour les modules qui nécessitent l’acceptation de la licence. La licence pour le module peut être affichée en cliquant sur le lien **View License.txt**.

![Exiger l’acceptation de la licence](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

Les utilisateurs seront invités à accepter la licence lors de l’installation, de l’enregistrement ou de la mise à jour du module via PowerShellGet, ou lors du déploiement sur Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exiger l’acceptation de la licence lors du déploiement sur Azure Automation

Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence. En cliquant sur OK, vous acceptez les termes du contrat de licence. »

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Détails supplémentaires

[Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
[Site web Azure Automation](/azure/automation)
