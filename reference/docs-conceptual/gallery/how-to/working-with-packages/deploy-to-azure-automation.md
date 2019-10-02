---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Déployer sur Azure Automation
ms.openlocfilehash: 707691e24a77647064e60da0d9a31ad5eece1c59
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327910"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="2108a-103">Déployer sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2108a-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="2108a-104">Le bouton Déployer sur Azure Automation de la page de détails du package a pour effet de déployer le package de PowerShell Gallery sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="2108a-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Bouton Déployer sur Azure Automation](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="2108a-106">Quand vous cliquez dessus, vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure.</span><span class="sxs-lookup"><span data-stu-id="2108a-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="2108a-107">Si le package comporte des dépendances, elles sont toutes déployées sur Azure Automation par la même occasion.</span><span class="sxs-lookup"><span data-stu-id="2108a-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="2108a-108">Si le même package et la même version existent déjà dans le compte Automation, un nouveau déploiement à partir de PowerShell Gallery a pour effet de remplacer le package dans le compte.</span><span class="sxs-lookup"><span data-stu-id="2108a-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="2108a-109">Si vous déployez un module, il apparaît dans la section Modules d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="2108a-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="2108a-110">Si vous déployez un script, il apparaît dans la section Runbooks d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="2108a-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="2108a-111">Pour désactiver le bouton Déployer sur Azure Automation, ajoutez la balise AzureAutomationNotSupported aux métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="2108a-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="2108a-112">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2108a-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="2108a-113">Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="2108a-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="2108a-114">En cliquant sur OK, vous acceptez les termes du contrat de licence. »</span><span class="sxs-lookup"><span data-stu-id="2108a-114">By clicking OK, you are accepting license terms.'</span></span>

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="2108a-116">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="2108a-116">More details</span></span>

- [<span data-ttu-id="2108a-117">Exiger l’acceptation de la licence dans PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2108a-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="2108a-118">Exiger l’acceptation de la licence dans PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="2108a-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="2108a-119">Site web Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2108a-119">Azure Automation website</span></span>](https://azure.microsoft.com/services/automation/)
