---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Gestion des propriétaires de package
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003749"
---
# <a name="managing-package-owners"></a><span data-ttu-id="54d57-103">Gestion des propriétaires de package</span><span class="sxs-lookup"><span data-stu-id="54d57-103">Managing package owners</span></span>

<span data-ttu-id="54d57-104">La propriété d’un package dans PowerShell Gallery est définie par la personne qui a publié le package dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="54d57-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="54d57-105">Ces métadonnées doivent parfois être gérées au-delà de la publication initiale du package, ce qui signifie que les métadonnées du propriétaire doivent être mutables alors que le package lui-même ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="54d57-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="54d57-106">Tous les propriétaires de package sont des homologues.</span><span class="sxs-lookup"><span data-stu-id="54d57-106">All package owners are peers.</span></span>
<span data-ttu-id="54d57-107">Cela signifie que tout propriétaire de package peut publier une nouvelle version d’un package.</span><span class="sxs-lookup"><span data-stu-id="54d57-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="54d57-108">Cela signifie également que tout propriétaire de package peut supprimer n’importe quel autre propriétaire de package.</span><span class="sxs-lookup"><span data-stu-id="54d57-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="54d57-109">Aucun propriétaire n’a plus d’autorité qu’un autre.</span><span class="sxs-lookup"><span data-stu-id="54d57-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="54d57-110">Définition du propriétaire initial d’un package</span><span class="sxs-lookup"><span data-stu-id="54d57-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="54d57-111">Quand un nouveau package est publié dans PowerShell Gallery, le propriétaire initial est défini par l’utilisateur qui a publié le package.</span><span class="sxs-lookup"><span data-stu-id="54d57-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="54d57-112">Cela est déterminé par l’utilisateur dont la clé API a été utilisée dans l’applet de commande Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="54d57-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="54d57-113">Ajout de propriétaires</span><span class="sxs-lookup"><span data-stu-id="54d57-113">Adding Owners</span></span>

<span data-ttu-id="54d57-114">Une fois qu’un package a été publié dans PowerShell Gallery, il est facile d’inviter d’autres utilisateurs à devenir propriétaires d’un package.</span><span class="sxs-lookup"><span data-stu-id="54d57-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="54d57-115">[Connectez-vous](https://powershellgallery.com/users/account/LogOn) à PowerShell Gallery avec le compte qui est le propriétaire actuel d’un package.</span><span class="sxs-lookup"><span data-stu-id="54d57-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="54d57-116">Accédez à la page d’un package via l’onglet « Éléments » en recherchant votre nom d’utilisateur ou en cliquant dessus, puis sur [**Gérer mes packages**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="54d57-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="54d57-117">Une fois que vous êtes connecté comme propriétaire d’un package, un lien « Gérer les propriétaires » sur lequel vous pouvez cliquer est affiché sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="54d57-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="54d57-118">Entrez le nom d’utilisateur de la personne à ajouter comme propriétaire, puis cliquez sur « Ajouter ».</span><span class="sxs-lookup"><span data-stu-id="54d57-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="54d57-119">Un e-mail est alors envoyé au nouveau copropriétaire pour inviter celui-ci à devenir le propriétaire d’un package.</span><span class="sxs-lookup"><span data-stu-id="54d57-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="54d57-120">Une fois que l’utilisateur clique sur le lien, il est copropriétaire à part entière avec contrôle total sur un package, ce qui inclut la possibilité de supprimer d’autres utilisateurs comme propriétaires.</span><span class="sxs-lookup"><span data-stu-id="54d57-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="54d57-121">**REMARQUE** : Tant que le nouveau propriétaire n’a pas confirmé être propriétaire, il n’est *pas* répertorié comme propriétaire d’un package.</span><span class="sxs-lookup"><span data-stu-id="54d57-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="54d57-122">Quand vous consultez la page **Gérer les propriétaires**, vous voyez une entrée « en attente d’approbation » dans les propriétaires actuels.</span><span class="sxs-lookup"><span data-stu-id="54d57-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="54d57-123">Cette invitation peut être supprimée, de la même manière que peuvent l’être les autres propriétaires.</span><span class="sxs-lookup"><span data-stu-id="54d57-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="54d57-124">Ce système d’invitation empêche les utilisateurs d’ajouter de façon factice d’autres utilisateurs comme propriétaires de leurs packages.</span><span class="sxs-lookup"><span data-stu-id="54d57-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="54d57-125">Notez que les métadonnées des « Auteurs » sont purement du texte libre. Seuls les « Propriétaires » sont contrôlés.</span><span class="sxs-lookup"><span data-stu-id="54d57-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="54d57-126">Suppression de propriétaires</span><span class="sxs-lookup"><span data-stu-id="54d57-126">Removing Owners</span></span>

<span data-ttu-id="54d57-127">Quand un package a plusieurs propriétaires et que l’un d’eux doit être supprimé, le processus est simple :</span><span class="sxs-lookup"><span data-stu-id="54d57-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="54d57-128">[Connectez-vous](https://powershellgallery.com/users/account/LogOn) à PowerShell Gallery avec le compte qui est le propriétaire actuel d’un package.</span><span class="sxs-lookup"><span data-stu-id="54d57-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="54d57-129">Accédez à la page d’un élément via l’onglet « Packahes » en recherchant votre nom d’utilisateur ou en cliquant dessus, puis sur [**Gérer mes éléments**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="54d57-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="54d57-130">Une fois que vous êtes connecté comme propriétaire d’un package, un lien « Gérer les propriétaires » sur lequel vous pouvez cliquer est affiché sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="54d57-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="54d57-131">Cliquez sur le lien « supprimer » en regard du propriétaire à supprimer.</span><span class="sxs-lookup"><span data-stu-id="54d57-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="54d57-132">Transfert de propriété de package</span><span class="sxs-lookup"><span data-stu-id="54d57-132">Transferring Package Ownership</span></span>

<span data-ttu-id="54d57-133">Nous recevons parfois des demandes de support pour transférer la propriété d’un package d’un utilisateur à un autre, mais vous pouvez presque toujours le faire vous-même.</span><span class="sxs-lookup"><span data-stu-id="54d57-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="54d57-134">Le transfert de la propriété d’un utilisateur à un autre est juste une combinaison des deux fonctionnalités ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="54d57-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="54d57-135">Le propriétaire actuel invite le nouvel utilisateur à devenir copropriétaire et le nouvel utilisateur accepte l’invitation.</span><span class="sxs-lookup"><span data-stu-id="54d57-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="54d57-136">Le nouvel utilisateur supprime l’ancien utilisateur de la liste des propriétaires.</span><span class="sxs-lookup"><span data-stu-id="54d57-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="54d57-137">Cette demande se présente sous deux formes, mais le processus fonctionne de la même façon.</span><span class="sxs-lookup"><span data-stu-id="54d57-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="54d57-138">La propriété d’un package passe d’un développeur à un autre</span><span class="sxs-lookup"><span data-stu-id="54d57-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="54d57-139">Le package a été publié accidentellement à l’aide du mauvais compte</span><span class="sxs-lookup"><span data-stu-id="54d57-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="54d57-140">Packages orphelins</span><span class="sxs-lookup"><span data-stu-id="54d57-140">Orphaned Packages</span></span>

<span data-ttu-id="54d57-141">Un dernier scénario, toutefois peu fréquent, se produit.</span><span class="sxs-lookup"><span data-stu-id="54d57-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="54d57-142">Des packages sont devenus orphelins et le compte des propriétaires des packages ne peut pas être utilisé pour ajouter de nouveaux propriétaires.</span><span class="sxs-lookup"><span data-stu-id="54d57-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="54d57-143">Voici quelques exemples de ce scénario :</span><span class="sxs-lookup"><span data-stu-id="54d57-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="54d57-144">Le compte du propriétaire est associé à une adresse e-mail qui n’existe plus et l’utilisateur a oublié son mot de passe</span><span class="sxs-lookup"><span data-stu-id="54d57-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="54d57-145">Le propriétaire inscrit a quitté la société qui produit le package et n’est pas joignable pour mettre à jour la propriété du package</span><span class="sxs-lookup"><span data-stu-id="54d57-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="54d57-146">En raison d’un bogue qui a affecté uniquement un petit nombre de packages, le package est, d’une certaine manière, sans propriétaire dans la galerie</span><span class="sxs-lookup"><span data-stu-id="54d57-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="54d57-147">Les administrateurs PowerShell Gallery peuvent accéder au lien « Gérer les propriétaires » de n’importe quel package.</span><span class="sxs-lookup"><span data-stu-id="54d57-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="54d57-148">Si vous êtes le propriétaire légitime d’un package et que vous ne pouvez pas joindre le propriétaire actuel pour obtenir des autorisations de propriété, utilisez le lien « Signaler un abus » dans la galerie pour joindre les administrateurs PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="54d57-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="54d57-149">Nous suivons alors un processus pour vérifier votre propriété du package.</span><span class="sxs-lookup"><span data-stu-id="54d57-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="54d57-150">Si nous déterminons que vous devez être un propriétaire du package, nous utilisons alors nous-mêmes le lien « Gérer les propriétaires » du package et nous vous envoyons l’invitation pour devenir propriétaire.</span><span class="sxs-lookup"><span data-stu-id="54d57-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="54d57-151">Nous n’effectuons cette opération qu’après avoir vérifié que vous devez être un propriétaire. Ce processus varie selon les circonstances.</span><span class="sxs-lookup"><span data-stu-id="54d57-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="54d57-152">Nous utilisons souvent l’URL du projet du package pour trouver un moyen de contacter le propriétaire du projet, mais nous pouvons aussi utiliser Twitter, l’e-mail ou d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="54d57-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
