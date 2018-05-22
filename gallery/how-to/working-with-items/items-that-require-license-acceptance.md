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
---
# <a name="require-license-acceptance"></a><span data-ttu-id="e8cae-103">Exiger l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="e8cae-103">Require license acceptance</span></span>

<span data-ttu-id="e8cae-104">Le texte d’acceptation de la licence s’affiche sur la page des détails de l’article pour les modules qui nécessitent l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="e8cae-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="e8cae-105">La licence pour le module peut être affichée en cliquant sur le lien « View License.txt ».</span><span class="sxs-lookup"><span data-stu-id="e8cae-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Exiger l’acceptation de la licence](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="e8cae-107">Les utilisateurs seront invités à accepter la licence lors de l’installation, de l’enregistrement ou de la mise à jour du module via PowerShellGet, ou lors du déploiement sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="e8cae-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="e8cae-108">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="e8cae-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="e8cae-109">Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="e8cae-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="e8cae-110">En cliquant sur OK, vous acceptez les termes du contrat de licence. »</span><span class="sxs-lookup"><span data-stu-id="e8cae-110">By clicking OK, you are accepting license terms.'</span></span>

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="e8cae-112">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="e8cae-112">More details</span></span>

<span data-ttu-id="e8cae-113">[Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
[Site web Azure Automation](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="e8cae-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>