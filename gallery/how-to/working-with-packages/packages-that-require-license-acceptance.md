---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery
title: Exiger l’acceptation de la licence
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003710"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="e1c8b-103">Exiger l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="e1c8b-103">Require license acceptance</span></span>

<span data-ttu-id="e1c8b-104">Le texte d’acceptation de la licence s’affiche sur la page des détails de l’article pour les modules qui nécessitent l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="e1c8b-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="e1c8b-105">La licence pour le module peut être affichée en cliquant sur le lien « View License.txt ».</span><span class="sxs-lookup"><span data-stu-id="e1c8b-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Exiger l’acceptation de la licence](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="e1c8b-107">Les utilisateurs seront invités à accepter la licence lors de l’installation, de l’enregistrement ou de la mise à jour du module via PowerShellGet, ou lors du déploiement sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="e1c8b-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="e1c8b-108">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="e1c8b-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="e1c8b-109">Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="e1c8b-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="e1c8b-110">En cliquant sur OK, vous acceptez les termes du contrat de licence. »</span><span class="sxs-lookup"><span data-stu-id="e1c8b-110">By clicking OK, you are accepting license terms.'</span></span>

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="e1c8b-112">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="e1c8b-112">More details</span></span>

<span data-ttu-id="e1c8b-113">[Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
[Site web Azure Automation](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="e1c8b-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
