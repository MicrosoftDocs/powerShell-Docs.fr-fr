---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Retirer des packages de la liste
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003721"
---
# <a name="unlisting-packages"></a><span data-ttu-id="f62e5-103">Retirer des packages de la liste</span><span class="sxs-lookup"><span data-stu-id="f62e5-103">Unlisting Packages</span></span>

<span data-ttu-id="f62e5-104">**Pourquoi la suppression d’un package de PowerShell Gallery n’est-elle pas proposée en option ?**</span><span class="sxs-lookup"><span data-stu-id="f62e5-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="f62e5-105">PowerShell Gallery ne gère pas la suppression définitive de packages par des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f62e5-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="f62e5-106">Cela permet à d’autres utilisateurs d’ajouter des dépendances vis-à-vis de vos packages sans avoir à se soucier de risques d’arrêts.</span><span class="sxs-lookup"><span data-stu-id="f62e5-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="f62e5-107">Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, l’utilisateur ne peut plus utiliser le module Pester.</span><span class="sxs-lookup"><span data-stu-id="f62e5-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="f62e5-108">Toutefois, plutôt que de supprimer un package, vous pouvez le retirer de la liste.</span><span class="sxs-lookup"><span data-stu-id="f62e5-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="f62e5-109">**À quoi sert le retrait d’un package sur PowerShell Gallery ?**</span><span class="sxs-lookup"><span data-stu-id="f62e5-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="f62e5-110">Lorsqu’un package, comme un module ou un script, est retiré de la liste sur PowerShell Gallery, il est supprimé de l’onglet Packages. Par ailleurs, il n’est plus détectable à l’aide de la barre de recherche.</span><span class="sxs-lookup"><span data-stu-id="f62e5-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="f62e5-111">La seule façon de le télécharger consiste à spécifier son nom et sa version exacts.</span><span class="sxs-lookup"><span data-stu-id="f62e5-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="f62e5-112">Le retrait d’un package de la liste ne provoque donc pas l’arrêt des modules ou des scripts qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="f62e5-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="f62e5-113">Pour retirer votre package de la liste, accédez à la page des détails du package, puis sélectionnez « Supprimer le module ».</span><span class="sxs-lookup"><span data-stu-id="f62e5-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="f62e5-114">Décochez la case « Répertorié », puis cliquez sur Enregistrer.</span><span class="sxs-lookup"><span data-stu-id="f62e5-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="f62e5-115">**Comment supprimer un package ?**</span><span class="sxs-lookup"><span data-stu-id="f62e5-115">**How can I remove an package?**</span></span>

<span data-ttu-id="f62e5-116">Si vous vous trouvez dans une situation nécessitant la suppression d’un package, contactez les administrateurs PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f62e5-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="f62e5-117">Les scénarios de suppression valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f62e5-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="f62e5-118">Problèmes de violation des droits d’auteur.</span><span class="sxs-lookup"><span data-stu-id="f62e5-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="f62e5-119">Contenu potentiellement dangereux.</span><span class="sxs-lookup"><span data-stu-id="f62e5-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="f62e5-120">Package contenant des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="f62e5-120">Package contains sensitive data.</span></span>

<span data-ttu-id="f62e5-121">Pour soumettre une demande de suppression de package aux administrateurs PowerShell Gallery, accédez à la page des détails de votre package, puis sélectionnez Contacter le support.</span><span class="sxs-lookup"><span data-stu-id="f62e5-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
