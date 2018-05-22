---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Gestion des propriétaires d’éléments
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="a976e-103">Gestion des propriétaires d’éléments</span><span class="sxs-lookup"><span data-stu-id="a976e-103">Managing item owners</span></span>

<span data-ttu-id="a976e-104">La propriété d’un élément dans PowerShell Gallery est définie par la personne qui a publié l’élément dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="a976e-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="a976e-105">Ces métadonnées doivent parfois être gérées au-delà de la publication initiale de l’élément, ce qui signifie que les métadonnées du propriétaire doivent être mutables alors que l’élément lui-même ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="a976e-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="a976e-106">Tous les propriétaires d’éléments sont des homologues.</span><span class="sxs-lookup"><span data-stu-id="a976e-106">All item owners are peers.</span></span>
<span data-ttu-id="a976e-107">Cela signifie que tout propriétaire d’élément peut publier une nouvelle version d’un élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="a976e-108">Cela signifie également que tout propriétaire d’élément peut supprimer n’importe quel autre propriétaire d’élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="a976e-109">Aucun propriétaire n’a plus d’autorité qu’un autre.</span><span class="sxs-lookup"><span data-stu-id="a976e-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="a976e-110">Définition du propriétaire initial d’un élément</span><span class="sxs-lookup"><span data-stu-id="a976e-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="a976e-111">Quand un nouvel élément est publié dans PowerShell Gallery, le propriétaire initial est défini par l’utilisateur qui a publié l’élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="a976e-112">Cela est déterminé par l’utilisateur dont la clé API a été utilisée dans l’applet de commande Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="a976e-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="a976e-113">Ajout de propriétaires</span><span class="sxs-lookup"><span data-stu-id="a976e-113">Adding Owners</span></span>

<span data-ttu-id="a976e-114">Une fois qu’un élément a été publié dans PowerShell Gallery, il est facile d’inviter d’autres utilisateurs à devenir propriétaires d’un élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="a976e-115">[Connectez-vous](https://powershellgallery.com/users/account/LogOn) à PowerShell Gallery avec le compte qui est le propriétaire actuel d’un élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="a976e-116">Accédez à la page d’un élément via l’onglet « Éléments » en recherchant votre nom d’utilisateur ou en cliquant dessus, puis sur [**Gérer mes éléments**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="a976e-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="a976e-117">Une fois que vous êtes connecté comme propriétaire d’un élément, un lien « Gérer les propriétaires » sur lequel vous pouvez cliquer est affiché sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="a976e-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="a976e-118">Entrez le nom d’utilisateur de la personne à ajouter comme propriétaire, puis cliquez sur « Ajouter ».</span><span class="sxs-lookup"><span data-stu-id="a976e-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="a976e-119">Un e-mail est alors envoyé au nouveau copropriétaire pour inviter celui-ci à devenir le propriétaire d’un élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="a976e-120">Une fois que l’utilisateur clique sur le lien, il est copropriétaire à part entière avec contrôle total sur un élément, ce qui inclut la possibilité de supprimer d’autres utilisateurs comme propriétaires.</span><span class="sxs-lookup"><span data-stu-id="a976e-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="a976e-121">**REMARQUE** : Tant que le nouveau propriétaire n’a pas confirmé être propriétaire, il n’est *pas* répertorié comme propriétaire d’un élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="a976e-122">Quand vous consultez la page **Gérer les propriétaires**, vous voyez une entrée « en attente d’approbation » dans les propriétaires actuels.</span><span class="sxs-lookup"><span data-stu-id="a976e-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="a976e-123">Cette invitation peut être supprimée, de la même manière que peuvent l’être les autres propriétaires.</span><span class="sxs-lookup"><span data-stu-id="a976e-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="a976e-124">Ce système d’invitation empêche les utilisateurs d’ajouter de façon factice d’autres utilisateurs comme propriétaires.</span><span class="sxs-lookup"><span data-stu-id="a976e-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="a976e-125">Notez que les métadonnées des « Auteurs » sont purement du texte libre. Seuls les « Propriétaires » sont contrôlés.</span><span class="sxs-lookup"><span data-stu-id="a976e-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="a976e-126">Suppression de propriétaires</span><span class="sxs-lookup"><span data-stu-id="a976e-126">Removing Owners</span></span>

<span data-ttu-id="a976e-127">Quand un élément a plusieurs propriétaires et que l’un d’eux doit être supprimé, le processus est simple :</span><span class="sxs-lookup"><span data-stu-id="a976e-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="a976e-128">[Connectez-vous](https://powershellgallery.com/users/account/LogOn) à PowerShell Gallery avec le compte qui est le propriétaire actuel d’un élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="a976e-129">Accédez à la page d’un élément via l’onglet Éléments en recherchant votre nom d’utilisateur ou en cliquant dessus, puis sur [**Gérer mes éléments**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="a976e-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="a976e-130">Une fois que vous êtes connecté comme propriétaire d’un élément, un lien « Gérer les propriétaires » sur lequel vous pouvez cliquer est affiché sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="a976e-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="a976e-131">Cliquez sur le lien « supprimer » en regard du propriétaire à supprimer.</span><span class="sxs-lookup"><span data-stu-id="a976e-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="a976e-132">Transfert de la propriété d’un élément</span><span class="sxs-lookup"><span data-stu-id="a976e-132">Transferring Item Ownership</span></span>

<span data-ttu-id="a976e-133">Nous recevons parfois des demandes de support pour transférer la propriété d’un élément d’un utilisateur à un autre, mais vous pouvez presque toujours le faire vous-même.</span><span class="sxs-lookup"><span data-stu-id="a976e-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="a976e-134">Le transfert de la propriété d’un utilisateur à un autre est juste une combinaison des deux fonctionnalités ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="a976e-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="a976e-135">Le propriétaire actuel invite le nouvel utilisateur à devenir copropriétaire et le nouvel utilisateur accepte l’invitation.</span><span class="sxs-lookup"><span data-stu-id="a976e-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="a976e-136">Le nouvel utilisateur supprime l’ancien utilisateur de la liste des propriétaires.</span><span class="sxs-lookup"><span data-stu-id="a976e-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="a976e-137">Cette demande se présente sous deux formes, mais le processus fonctionne de la même façon.</span><span class="sxs-lookup"><span data-stu-id="a976e-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="a976e-138">La propriété d’un élément passe d’un développeur à un autre</span><span class="sxs-lookup"><span data-stu-id="a976e-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="a976e-139">L’élément a été publié accidentellement à l’aide du mauvais compte</span><span class="sxs-lookup"><span data-stu-id="a976e-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="a976e-140">Éléments orphelins</span><span class="sxs-lookup"><span data-stu-id="a976e-140">Orphaned Items</span></span>

<span data-ttu-id="a976e-141">Un dernier scénario, toutefois peu fréquent, se produit.</span><span class="sxs-lookup"><span data-stu-id="a976e-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="a976e-142">Des éléments sont devenus orphelins et le compte des propriétaires d’éléments ne peut pas être utilisé pour ajouter de nouveaux propriétaires.</span><span class="sxs-lookup"><span data-stu-id="a976e-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="a976e-143">Voici quelques exemples de ce scénario :</span><span class="sxs-lookup"><span data-stu-id="a976e-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="a976e-144">Le compte du propriétaire est associé à une adresse e-mail qui n’existe plus et l’utilisateur a oublié son mot de passe</span><span class="sxs-lookup"><span data-stu-id="a976e-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="a976e-145">Le propriétaire inscrit a quitté la société qui produit l’élément et n’est pas joignable pour mettre à jour la propriété de l’élément</span><span class="sxs-lookup"><span data-stu-id="a976e-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="a976e-146">En raison d’un bogue qui a affecté uniquement un petit nombre d’éléments, l’élément est, d’une certaine manière, sans propriétaire dans la galerie</span><span class="sxs-lookup"><span data-stu-id="a976e-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="a976e-147">Les administrateurs PowerShell Gallery peuvent accéder au lien « Gérer les propriétaires » de n’importe quel élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="a976e-148">Si vous êtes le propriétaire légitime d’un élément et que vous ne pouvez pas joindre le propriétaire actuel pour obtenir des autorisations de propriété, utilisez le lien « Signaler un abus » dans la galerie pour joindre les administrateurs PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a976e-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="a976e-149">Nous suivons alors un processus pour vérifier votre propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="a976e-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="a976e-150">Si nous déterminons que vous devez être un propriétaire de l’élément, nous utilisons alors nous-mêmes le lien « Gérer les propriétaires » de l’élément et nous vous envoyons l’invitation pour devenir propriétaire.</span><span class="sxs-lookup"><span data-stu-id="a976e-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="a976e-151">Nous n’effectuons cette opération qu’après avoir vérifié que vous devez être un propriétaire. Ce processus varie selon les circonstances.</span><span class="sxs-lookup"><span data-stu-id="a976e-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="a976e-152">Nous utilisons souvent l’URL du projet de l’élément pour trouver un moyen de contacter le propriétaire du projet, mais nous pouvons aussi utiliser Twitter, l’e-mail ou d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="a976e-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>