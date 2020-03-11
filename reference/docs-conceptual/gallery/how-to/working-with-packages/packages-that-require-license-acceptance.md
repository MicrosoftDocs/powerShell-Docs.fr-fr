---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery
title: Exiger l’acceptation de la licence
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278644"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="ba6ae-103">Exiger l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ba6ae-103">Require license acceptance</span></span>

<span data-ttu-id="ba6ae-104">Le texte d’acceptation de la licence s’affiche sur la page des détails de l’article pour les modules qui nécessitent l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="ba6ae-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="ba6ae-105">La licence pour le module peut être affichée en cliquant sur le lien « View License.txt ».</span><span class="sxs-lookup"><span data-stu-id="ba6ae-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Exiger l’acceptation de la licence](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="ba6ae-107">Les utilisateurs seront invités à accepter la licence lors de l’installation, de l’enregistrement ou de la mise à jour du module via PowerShellGet, ou lors du déploiement sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="ba6ae-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="ba6ae-108">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="ba6ae-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="ba6ae-109">Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="ba6ae-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="ba6ae-110">En cliquant sur OK, vous acceptez les termes du contrat de licence. »</span><span class="sxs-lookup"><span data-stu-id="ba6ae-110">By clicking OK, you are accepting license terms.'</span></span>

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="ba6ae-112">Détails supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ba6ae-112">More details</span></span>

<span data-ttu-id="ba6ae-113">[Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
[Site web Azure Automation](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="ba6ae-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
