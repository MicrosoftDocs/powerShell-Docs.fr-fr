---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Envoi de feedback via les médias sociaux ou les commentaires
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327880"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="9fca0-103">Envoi de feedback via les médias sociaux ou les commentaires</span><span class="sxs-lookup"><span data-stu-id="9fca0-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="9fca0-104">PowerShell Gallery prend en charge les deux approches pour les utilisateurs qui souhaitent fournir des commentaires publics sur un package :</span><span class="sxs-lookup"><span data-stu-id="9fca0-104">The PowerShell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="9fca0-105">Utiliser les liens sur le côté gauche pour « partager » un package sur les réseaux sociaux Facebook, LinkedIn et Twitter ;</span><span class="sxs-lookup"><span data-stu-id="9fca0-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="9fca0-106">utiliser la fonctionnalité Commenter pour publier des commentaires sur un package et permettre aux auteurs de suivre les commentaires sur les packages qu’ils publient.</span><span class="sxs-lookup"><span data-stu-id="9fca0-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="9fca0-107">Commentaires sur les réseaux sociaux</span><span class="sxs-lookup"><span data-stu-id="9fca0-107">Social Media Feedback</span></span>

<span data-ttu-id="9fca0-108">Sur le côté gauche de la page pour chaque package dans PowerShell Gallery, vous trouverez des liens pour Facebook, LinkedIn et Twitter.</span><span class="sxs-lookup"><span data-stu-id="9fca0-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="9fca0-109">En cliquant sur ces liens, vous ouvrez le réseau social et pouvez rapidement partager un lien vers le package.</span><span class="sxs-lookup"><span data-stu-id="9fca0-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="9fca0-110">Les utilisateurs doivent se connecter au site qu'ils ont choisi afin de partager le package PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9fca0-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="9fca0-111">Les utilisateurs sont invités à procéder ainsi s’ils souhaitent recommander un package à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="9fca0-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="9fca0-112">PowerShell Gallery vérifie chaque réseau social à la recherche de « partages » du package et un affiche le nombre de fois que le package a été partagé sur chacun des réseaux sociaux.</span><span class="sxs-lookup"><span data-stu-id="9fca0-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="9fca0-113">Étant donné que cela n’indique que le nombre de fois où un élément a été partagé, cela sera interprété comme si d’autres utilisateurs cliquaient sur « J’aime » pour le package.</span><span class="sxs-lookup"><span data-stu-id="9fca0-113">Since this shows only the count of times something has been shared, it will be interpreted other users as "liking" the package.</span></span>

## <a name="comments"></a><span data-ttu-id="9fca0-114">Commentaires</span><span class="sxs-lookup"><span data-stu-id="9fca0-114">Comments</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fca0-115">Le système de gestion des commentaires Livefyre est fourni par un fournisseur tiers et n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9fca0-115">Livefyre commenting is provided by a third-party vendor and is no longer supported.</span></span>
> <span data-ttu-id="9fca0-116">Le système Livefyre ne sera plus disponible sur PowerShell Gallery à compter du 01/05/2019.</span><span class="sxs-lookup"><span data-stu-id="9fca0-116">Livefyre commenting will no longer be available on the PowerShell Gallery starting 05/01/2019.</span></span> 

<span data-ttu-id="9fca0-117">PowerShell Gallery utilise le service LiveFyre pour permettre aux utilisateurs de commenter sur les packages.</span><span class="sxs-lookup"><span data-stu-id="9fca0-117">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="9fca0-118">Les utilisateurs qui ont des recommandations ou des commentaires peuvent utiliser cette fonctionnalité pour fournir des commentaires qui sont visibles par toute personne qui consulte la page du package.</span><span class="sxs-lookup"><span data-stu-id="9fca0-118">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="9fca0-119">Les propriétaires de package peuvent suivre ces commentaires et être avertis lorsqu’un utilisateur publie un commentaire.</span><span class="sxs-lookup"><span data-stu-id="9fca0-119">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="9fca0-120">Le système de commentaires est basé sur LiveFyre, un service distinct qui n’est pas géré par Microsoft et nécessite une authentification séparée.</span><span class="sxs-lookup"><span data-stu-id="9fca0-120">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="9fca0-121">La première fois que vous souhaitez laisser un commentaire ou suivez des commentaires sur l’un de vos packages, vous devrez créer un compte LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9fca0-121">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="9fca0-122">Si vous avez créé un compte LiveFyre et vous êtes connecté, vous pouvez préparer un commentaire avec des retours sur le package. Cliquez alors sur « Publier le commentaire... » Le commentaire ne sera pas être visible immédiatement.</span><span class="sxs-lookup"><span data-stu-id="9fca0-122">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="9fca0-123">Les commentaires pour les packages de PowerShell Gallery sont modérés par des administrateurs, et toutes les publications sont vérifiées par ces derniers avant d’être publiées et visibles pour d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="9fca0-123">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="9fca0-124">Notre objectif avec la modération des commentaires est de vous assurer qu’ils sont en conformité avec les [conditions d’utilisation](https://www.powershellgallery.com/policies/Terms) de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9fca0-124">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="9fca0-125">Les propriétaires de packages sont encouragés à suivre les commentaires qui sont publiés sur LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9fca0-125">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="9fca0-126">Un compte LiveFyre est requis, et il est recommandé d’utiliser l’adresse de messagerie que vous utilisez pour la publication de votre package dans LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9fca0-126">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="9fca0-127">Pour suivre les commentaires, connectez-vous à LiveFyre et accédez à n’importe quel package pour lequel vous êtes répertorié comme propriétaire.</span><span class="sxs-lookup"><span data-stu-id="9fca0-127">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="9fca0-128">Sous la zone de commentaires en bas de chaque package, vous pouvez voir un lien « + S’abonner ».</span><span class="sxs-lookup"><span data-stu-id="9fca0-128">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="9fca0-129">Une fois que vous cliquez dessus, LiveFyre envoie un courrier électronique à l’adresse de messagerie inscrite chaque fois que de nouveaux commentaires sont écrits pour le package.</span><span class="sxs-lookup"><span data-stu-id="9fca0-129">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>
