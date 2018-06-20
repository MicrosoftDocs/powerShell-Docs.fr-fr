---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Déployer sur Azure Automation
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219332"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="76fd3-103">Déployer sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="76fd3-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="76fd3-104">Le bouton Déployer sur Azure Automation dans la page de détails de l’élément déploie l’élément de PowerShell Gallery sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="76fd3-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Bouton Déployer sur Azure Automation](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="76fd3-106">Quand vous cliquez dessus, vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure.</span><span class="sxs-lookup"><span data-stu-id="76fd3-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="76fd3-107">Si l’élément contient des dépendances, toutes les dépendances sont également déployées sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="76fd3-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="76fd3-108">Si le même élément et la même version existent déjà dans votre compte Automation, un nouveau déploiement à partir de PowerShell Gallery remplace l’élément dans votre compte Automation.</span><span class="sxs-lookup"><span data-stu-id="76fd3-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="76fd3-109">Si vous déployez un module, il apparaît dans la section Modules d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="76fd3-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="76fd3-110">Si vous déployez un script, il apparaît dans la section Runbooks d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="76fd3-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="76fd3-111">Le bouton Déployer sur Azure Automation peut être désactivé en ajoutant la balise AzureAutomationNotSupported aux métadonnées de l’élément.</span><span class="sxs-lookup"><span data-stu-id="76fd3-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="76fd3-112">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="76fd3-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="76fd3-113">Si le module en cours de déploiement sur Azure Automation exige l’acceptation de la licence, l’avertissement suivant s’affiche sur l’interface utilisateur du portail : « Ce module exige l’acceptation de la licence.</span><span class="sxs-lookup"><span data-stu-id="76fd3-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="76fd3-114">En cliquant sur OK, vous acceptez les termes du contrat de licence. »</span><span class="sxs-lookup"><span data-stu-id="76fd3-114">By clicking OK, you are accepting license terms.'</span></span>

![Le déploiement sur Azure Automation nécessite l’acceptation de la licence.](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="76fd3-116">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="76fd3-116">More details</span></span>

- [<span data-ttu-id="76fd3-117">Exiger l’acceptation de la licence dans PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="76fd3-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="76fd3-118">Exiger l’acceptation de la licence dans PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="76fd3-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="76fd3-119">Site web Azure Automation</span><span class="sxs-lookup"><span data-stu-id="76fd3-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
