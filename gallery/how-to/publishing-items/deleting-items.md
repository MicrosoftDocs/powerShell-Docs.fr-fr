---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Suppression d’éléments
ms.openlocfilehash: 454cd404437bf1c31b9a1b81cd9dd0ac81e6b0f6
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893091"
---
# <a name="deleting-items"></a><span data-ttu-id="935a7-103">Suppression d’éléments</span><span class="sxs-lookup"><span data-stu-id="935a7-103">Deleting items</span></span>

<span data-ttu-id="935a7-104">PowerShell Gallery ne prend pas en charge la suppression définitive d’éléments, car cela empêcherait toute personne qui en dépend de rester disponible.</span><span class="sxs-lookup"><span data-stu-id="935a7-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="935a7-105">Au lieu de cela, PowerShell Gallery prend en charge un moyen de retirer de la liste un élément. Cette opération peut être effectuée dans la page de gestion des éléments sur le site web.</span><span class="sxs-lookup"><span data-stu-id="935a7-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="935a7-106">Quand un élément est retiré de la liste, il ne s’affiche plus dans la recherche et dans les listes d’éléments, aussi bien dans PowerShell Gallery et lors de l’utilisation de commandes PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="935a7-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="935a7-107">Toutefois, il reste téléchargeable en spécifiant sa version exacte, ce qui permet aux scripts automatisés de continuer à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="935a7-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="935a7-108">Si vous rencontrez une situation exceptionnelle où si vous pensez que l’un de vos éléments doit être supprimé, l’équipe PowerShell Gallery peut s’en charger manuellement.</span><span class="sxs-lookup"><span data-stu-id="935a7-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="935a7-109">Par exemple, la violation des droits d’auteur ou un contenu potentiellement dangereux peuvent constituer une raison valable de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="935a7-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="935a7-110">Dans ce cas, vous devez soumettre une demande de support par le biais de [PowerShell Gallery](http://www.PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="935a7-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>