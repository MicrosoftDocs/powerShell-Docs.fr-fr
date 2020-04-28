---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Retirer des packages de la liste
ms.openlocfilehash: b7404420db531ac5d97debd46e1b84c6fdd49d9a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978268"
---
# <a name="unlisting-packages"></a><span data-ttu-id="b8e4e-103">Retirer des packages de la liste</span><span class="sxs-lookup"><span data-stu-id="b8e4e-103">Unlisting Packages</span></span>

<span data-ttu-id="b8e4e-104">**Pourquoi la suppression d’un package de PowerShell Gallery n’est-elle pas proposée en option ?**</span><span class="sxs-lookup"><span data-stu-id="b8e4e-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="b8e4e-105">PowerShell Gallery ne gère pas la suppression définitive de packages par des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="b8e4e-106">Cela permet à d’autres utilisateurs d’ajouter des dépendances vis-à-vis de vos packages sans avoir à se soucier de risques d’arrêts.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="b8e4e-107">Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, les utilisateurs ne peuvent plus utiliser le module Pester.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="b8e4e-108">Au lieu de supprimer un package, vous pouvez ne plus le répertorier.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-108">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="b8e4e-109">**À quoi sert le retrait d’un package sur PowerShell Gallery ?**</span><span class="sxs-lookup"><span data-stu-id="b8e4e-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="b8e4e-110">Lorsqu’un package, comme un module ou un script, est retiré de la liste sur PowerShell Gallery, il est supprimé de l’onglet Packages. Par ailleurs, il n’est plus détectable à l’aide de la barre de recherche.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-110">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="b8e4e-111">La seule façon de le télécharger consiste à spécifier son nom et sa version exacts.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="b8e4e-112">Le retrait d’un package de la liste ne provoque donc pas l’arrêt des modules ou des scripts qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-112">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="b8e4e-113">Pour retirer votre package de la liste, accédez à la page des détails du package, puis sélectionnez « Supprimer le module ».</span><span class="sxs-lookup"><span data-stu-id="b8e4e-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="b8e4e-114">Décochez la case « Répertorié », puis sélectionnez « Enregistrer ».</span><span class="sxs-lookup"><span data-stu-id="b8e4e-114">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="b8e4e-115">**Comment supprimer un package ?**</span><span class="sxs-lookup"><span data-stu-id="b8e4e-115">**How can I remove a package?**</span></span>

<span data-ttu-id="b8e4e-116">Si vous vous trouvez dans une situation nécessitant la suppression d’un package, contactez les administrateurs PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="b8e4e-117">Les scénarios de suppression valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="b8e4e-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="b8e4e-118">Problèmes de violation des droits d’auteur.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="b8e4e-119">Contenu potentiellement dangereux.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="b8e4e-120">Package contenant des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-120">Package contains sensitive data.</span></span>

<span data-ttu-id="b8e4e-121">Pour soumettre une demande de suppression de package aux administrateurs PowerShell Gallery, accédez à la page des détails de votre package, puis sélectionnez Contacter le support.</span><span class="sxs-lookup"><span data-stu-id="b8e4e-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
