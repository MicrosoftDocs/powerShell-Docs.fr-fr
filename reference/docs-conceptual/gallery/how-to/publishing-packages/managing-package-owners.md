---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Gestion des propriétaires de package
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328260"
---
# <a name="managing-package-owners"></a>Gestion des propriétaires de package

La propriété d’un package dans PowerShell Gallery est définie par la personne qui a publié le package dans la galerie.
Ces métadonnées doivent parfois être gérées au-delà de la publication initiale du package, ce qui signifie que les métadonnées du propriétaire doivent être mutables alors que le package lui-même ne l’est pas.

Tous les propriétaires de package sont des homologues.
Cela signifie que tout propriétaire de package peut publier une nouvelle version d’un package. Cela signifie également que tout propriétaire de package peut supprimer n’importe quel autre propriétaire de package.
Aucun propriétaire n’a plus d’autorité qu’un autre.

## <a name="setting-a-packages-initial-owner"></a>Définition du propriétaire initial d’un package

Quand un nouveau package est publié dans PowerShell Gallery, le propriétaire initial est défini par l’utilisateur qui a publié le package. Cela est déterminé par l’utilisateur dont la clé API a été utilisée dans l’applet de commande Publish-Module.

## <a name="adding-owners"></a>Ajout de propriétaires

Une fois qu’un package a été publié dans PowerShell Gallery, il est facile d’inviter d’autres utilisateurs à devenir propriétaires d’un package.

1. [Connectez-vous](https://powershellgallery.com/users/account/LogOn) à PowerShell Gallery avec le compte qui est le propriétaire actuel d’un package.
2. Accédez à la page d’un package via l’onglet « Éléments » en recherchant votre nom d’utilisateur ou en cliquant dessus, puis sur [**Gérer mes packages**](https://www.powershellgallery.com/account/Packages).
3. Une fois que vous êtes connecté comme propriétaire d’un package, un lien « Gérer les propriétaires » sur lequel vous pouvez cliquer est affiché sur le côté gauche.
4. Entrez le nom d’utilisateur de la personne à ajouter comme propriétaire, puis cliquez sur « Ajouter ».
5. Un e-mail est alors envoyé au nouveau copropriétaire pour inviter celui-ci à devenir le propriétaire d’un package.
6. Une fois que l’utilisateur clique sur le lien, il est copropriétaire à part entière avec contrôle total sur un package, ce qui inclut la possibilité de supprimer d’autres utilisateurs comme propriétaires.

**REMARQUE** : Tant que le nouveau propriétaire n’a pas confirmé être propriétaire, il n’est *pas* répertorié comme propriétaire d’un package.
Quand vous consultez la page **Gérer les propriétaires**, vous voyez une entrée « en attente d’approbation » dans les propriétaires actuels.
Cette invitation peut être supprimée, de la même manière que peuvent l’être les autres propriétaires.
Ce système d’invitation empêche les utilisateurs d’ajouter de façon factice d’autres utilisateurs comme propriétaires de leurs packages.

Notez que les métadonnées des « Auteurs » sont purement du texte libre. Seuls les « Propriétaires » sont contrôlés.


## <a name="removing-owners"></a>Suppression de propriétaires

Quand un package a plusieurs propriétaires et que l’un d’eux doit être supprimé, le processus est simple :

1. [Connectez-vous](https://powershellgallery.com/users/account/LogOn) à PowerShell Gallery avec le compte qui est le propriétaire actuel d’un package.
2. Accédez à la page d’un élément via l’onglet « Packahes » en recherchant votre nom d’utilisateur ou en cliquant dessus, puis sur [**Gérer mes éléments**](https://www.powershellgallery.com/account/Packages).
3. Une fois que vous êtes connecté comme propriétaire d’un package, un lien « Gérer les propriétaires » sur lequel vous pouvez cliquer est affiché sur le côté gauche.
4. Cliquez sur le lien « supprimer » en regard du propriétaire à supprimer.



## <a name="transferring-package-ownership"></a>Transfert de propriété de package

Nous recevons parfois des demandes de support pour transférer la propriété d’un package d’un utilisateur à un autre, mais vous pouvez presque toujours le faire vous-même.
Le transfert de la propriété d’un utilisateur à un autre est juste une combinaison des deux fonctionnalités ci-dessus.

1. Le propriétaire actuel invite le nouvel utilisateur à devenir copropriétaire et le nouvel utilisateur accepte l’invitation.
2. Le nouvel utilisateur supprime l’ancien utilisateur de la liste des propriétaires.

Cette demande se présente sous deux formes, mais le processus fonctionne de la même façon.

- La propriété d’un package passe d’un développeur à un autre
- Le package a été publié accidentellement à l’aide du mauvais compte


## <a name="orphaned-packages"></a>Packages orphelins

Un dernier scénario, toutefois peu fréquent, se produit.
Des packages sont devenus orphelins et le compte des propriétaires des packages ne peut pas être utilisé pour ajouter de nouveaux propriétaires.
Voici quelques exemples de ce scénario :

- Le compte du propriétaire est associé à une adresse e-mail qui n’existe plus et l’utilisateur a oublié son mot de passe
- Le propriétaire inscrit a quitté la société qui produit le package et n’est pas joignable pour mettre à jour la propriété du package
- En raison d’un bogue qui a affecté uniquement un petit nombre de packages, le package est, d’une certaine manière, sans propriétaire dans la galerie

Les administrateurs PowerShell Gallery peuvent accéder au lien « Gérer les propriétaires » de n’importe quel package.
Si vous êtes le propriétaire légitime d’un package et que vous ne pouvez pas joindre le propriétaire actuel pour obtenir des autorisations de propriété, utilisez le lien « Signaler un abus » dans la galerie pour joindre les administrateurs PowerShell Gallery.
Nous suivons alors un processus pour vérifier votre propriété du package.
Si nous déterminons que vous devez être un propriétaire du package, nous utilisons alors nous-mêmes le lien « Gérer les propriétaires » du package et nous vous envoyons l’invitation pour devenir propriétaire.
Nous n’effectuons cette opération qu’après avoir vérifié que vous devez être un propriétaire. Ce processus varie selon les circonstances.
Nous utilisons souvent l’URL du projet du package pour trouver un moyen de contacter le propriétaire du projet, mais nous pouvons aussi utiliser Twitter, l’e-mail ou d’autres moyens.
