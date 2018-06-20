---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Envoi de feedback via les médias sociaux ou les commentaires
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188137"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="0ae3e-103">Envoi de feedback via les médias sociaux ou les commentaires</span><span class="sxs-lookup"><span data-stu-id="0ae3e-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="0ae3e-104">Powershell Gallery prend en charge les deux approches pour les utilisateurs qui souhaitent fournir des commentaires publics sur un élément :</span><span class="sxs-lookup"><span data-stu-id="0ae3e-104">The Powershell Gallery supports two approaches for users to provide public feedback on an item:</span></span>

- <span data-ttu-id="0ae3e-105">Utiliser les liens sur le côté gauche pour « partager » un élément sur les réseaux sociaux Facebook, LinkedIn et Twitter ;</span><span class="sxs-lookup"><span data-stu-id="0ae3e-105">Use the links on the left edge to "share" an item in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="0ae3e-106">utiliser la fonctionnalité Commenter pour publier des commentaires sur un élément et permettre aux auteurs de suivre les commentaires sur les éléments qu’ils publient.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-106">Use the Comment feature to post comments on an item, and to allow Authors to watch for comments on items they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="0ae3e-107">Commentaires sur les réseaux sociaux</span><span class="sxs-lookup"><span data-stu-id="0ae3e-107">Social Media Feedback</span></span>

<span data-ttu-id="0ae3e-108">Sur le côté gauche de la page pour chaque élément dans PowerShell Gallery, vous trouverez des liens pour Facebook, LinkedIn et Twitter.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-108">On the left side of the page for each item in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="0ae3e-109">En cliquant sur ces liens, vous ouvrez le réseau social et pouvez rapidement partager un lien vers l’élément.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the item.</span></span>

<span data-ttu-id="0ae3e-110">Les utilisateurs doivent se connecter au site qu'ils ont choisi afin de partager l’élément PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery item.</span></span>

<span data-ttu-id="0ae3e-111">Les utilisateurs sont invités à procéder ainsi s’ils souhaitent recommander un élément à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-111">Users are encouraged to do this if they find that an item is something they would recommend to others.</span></span>
<span data-ttu-id="0ae3e-112">PowerShell Gallery vérifie chaque réseau social à la recherche de « partages » de l’élément et un affiche le nombre de fois que l’élément a été partagé sur chacun des réseaux sociaux.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-112">The PowerShell Gallery will check each social media site for "shares" of the item, and display how many times that item has been shared in each of the social media sites.</span></span>
<span data-ttu-id="0ae3e-113">Étant donné que cela n'indique que le nombre de fois où un élément a été partagé, cela sera interprété comme si d’autres utilisateurs cliquaient sur « J’aime » pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the item.</span></span>


## <a name="comments"></a><span data-ttu-id="0ae3e-114">Commentaires</span><span class="sxs-lookup"><span data-stu-id="0ae3e-114">Comments</span></span>

<span data-ttu-id="0ae3e-115">PowerShell Gallery utilise le service LiveFyre pour permettre aux utilisateurs de commenter sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on items.</span></span>
<span data-ttu-id="0ae3e-116">Les utilisateurs qui ont des recommandations ou des commentaires peuvent utiliser cette fonctionnalité pour fournir des commentaires qui sont visibles par toute personne qui consulte la page de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the item page.</span></span>
<span data-ttu-id="0ae3e-117">Les propriétaires d’élément peuvent suivre ces commentaires et être avertis lorsqu’un utilisateur publie un commentaire.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-117">Item owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="0ae3e-118">Le système de commentaires est basé sur LiveFyre, un service distinct qui n’est pas géré par Microsoft et nécessite une authentification séparée.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="0ae3e-119">La première fois que vous souhaitez laisser un commentaire ou suivez des commentaires sur l’un de vos éléments, vous devrez créer un compte LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-119">The first time you choose to leave a comment or Follow comments on one of your items, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="0ae3e-120">Si vous avez créé un compte LiveFyre et vous êtes connecté, vous pouvez préparer un commentaire avec des retours sur l’élément. Cliquez alors sur « Publier le commentaire... » Le commentaire ne sera pas être visible immédiatement.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the item, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="0ae3e-121">Les commentaires pour les éléments de PowerShell Gallery sont modérés par des administrateurs, et toutes les publications sont vérifiées par ces derniers avant d’être publiées et visibles pour d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-121">Comments for gallery items are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="0ae3e-122">Notre objectif avec la modération des commentaires est de vous assurer qu’ils sont en conformité avec les [conditions d’utilisation](https://www.powershellgallery.com/policies/Terms) de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="0ae3e-123">Les propriétaires d’éléments sont encouragés à suivre les commentaires qui sont publiés sur LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-123">Item owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="0ae3e-124">Un compte LiveFyre est requis, et il est recommandé d’utiliser l’adresse de messagerie que vous utilisez pour la publication de votre élément dans LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your item in LiveFyre.</span></span>
<span data-ttu-id="0ae3e-125">Pour suivre les commentaires, connectez-vous à LiveFyre et accédez à n’importe quel élément pour lequel vous êtes répertorié comme propriétaire.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-125">To Follow comments, log into LiveFyre, and navigate to any item where you are listed as an Owner.</span></span>
<span data-ttu-id="0ae3e-126">Sous la zone de commentaires en bas de chaque élément, vous pouvez voir un lien « + S’abonner ».</span><span class="sxs-lookup"><span data-stu-id="0ae3e-126">Below the Comment box at the bottom of each item you will see "+Follow".</span></span>
<span data-ttu-id="0ae3e-127">Une fois que vous cliquez dessus, LiveFyre envoie un courrier électronique à l’adresse de messagerie inscrite chaque fois que de nouveaux commentaires sont écrits pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="0ae3e-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the item.</span></span>