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
# <a name="require-license-acceptance"></a><span data-ttu-id="69fa7-103">Exiger l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="69fa7-103">Require license acceptance</span></span>

<span data-ttu-id="69fa7-104">Le texte d’acceptation de la licence s’affiche sur la page des détails de l’article pour les modules qui nécessitent l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="69fa7-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="69fa7-105">La licence pour le module peut être affichée en cliquant sur le lien **View License.txt**.</span><span class="sxs-lookup"><span data-stu-id="69fa7-105">License for module can be viewed by clicking on **View License.txt** link.</span></span>

![Exiger l’acceptation de la licence](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="69fa7-107">Les utilisateurs seront invités à accepter la licence lors de l’installation, de l’enregistrement ou de la mise à jour du module via PowerShellGet, ou lors du déploiement sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="69fa7-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="69fa7-108">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="69fa7-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="69fa7-109">Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="69fa7-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="69fa7-110">En cliquant sur OK, vous acceptez les termes du contrat de licence. »</span><span class="sxs-lookup"><span data-stu-id="69fa7-110">By clicking OK, you are accepting license terms.'</span></span>

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="69fa7-112">Détails supplémentaires</span><span class="sxs-lookup"><span data-stu-id="69fa7-112">More details</span></span>

<span data-ttu-id="69fa7-113">[Exiger l’acceptation de la licence dans PowerShellGet](../../concepts/module-license-acceptance.md)
[Site web Azure Automation](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="69fa7-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
