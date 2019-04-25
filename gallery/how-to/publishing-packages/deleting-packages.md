---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Supprimer des packages
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084162"
---
# <a name="deleting-packages"></a><span data-ttu-id="a3165-103">Supprimer des packages</span><span class="sxs-lookup"><span data-stu-id="a3165-103">Deleting Packages</span></span>

<span data-ttu-id="a3165-104">PowerShell Gallery ne prend pas en charge la suppression définitive de packages, car cela provoquerait l’arrêt de tous les éléments qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="a3165-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="a3165-105">Il est en revanche possible de retirer un package de la liste sur la page de gestion des packages du site web.</span><span class="sxs-lookup"><span data-stu-id="a3165-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="a3165-106">Quand un package est retiré de la liste, il ne s’affiche plus ni dans la recherche ni dans la liste des packages, aussi bien sur PowerShell Gallery qu’avec les commandes PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a3165-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="a3165-107">Toutefois, il reste téléchargeable en spécifiant sa version exacte, ce qui permet aux scripts automatisés de continuer à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a3165-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="a3165-108">Si vous pensez vous trouver dans une situation exceptionnelle nécessitant la suppression d’un de vos packages, l’équipe PowerShell Gallery peut s’en charger manuellement.</span><span class="sxs-lookup"><span data-stu-id="a3165-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="a3165-109">Par exemple, la violation des droits d’auteur ou un contenu potentiellement dangereux peuvent constituer une raison valable de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="a3165-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="a3165-110">Dans ce cas, vous devez soumettre une demande de support par le biais de [PowerShell Gallery](http://www.PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="a3165-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
