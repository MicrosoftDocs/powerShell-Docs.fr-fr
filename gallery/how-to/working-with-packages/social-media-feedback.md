---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Envoi de feedback via les médias sociaux ou les commentaires
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076070"
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Envoi de feedback via les médias sociaux ou les commentaires

PowerShell Gallery prend en charge les deux approches pour les utilisateurs qui souhaitent fournir des commentaires publics sur un package :

- Utiliser les liens sur le côté gauche pour « partager » un package sur les réseaux sociaux Facebook, LinkedIn et Twitter ;
- utiliser la fonctionnalité Commenter pour publier des commentaires sur un package et permettre aux auteurs de suivre les commentaires sur les packages qu’ils publient.

## <a name="social-media-feedback"></a>Commentaires sur les réseaux sociaux

Sur le côté gauche de la page pour chaque package dans PowerShell Gallery, vous trouverez des liens pour Facebook, LinkedIn et Twitter.
En cliquant sur ces liens, vous ouvrez le réseau social et pouvez rapidement partager un lien vers le package.

Les utilisateurs doivent se connecter au site qu'ils ont choisi afin de partager le package PowerShell Gallery.

Les utilisateurs sont invités à procéder ainsi s’ils souhaitent recommander un package à d’autres personnes.
PowerShell Gallery vérifie chaque réseau social à la recherche de « partages » du package et un affiche le nombre de fois que le package a été partagé sur chacun des réseaux sociaux.
Étant donné que cela n’indique que le nombre de fois où un élément a été partagé, cela sera interprété comme si d’autres utilisateurs cliquaient sur « J’aime » pour le package.

## <a name="comments"></a>Commentaires

> [!IMPORTANT]
> Le système de gestion des commentaires Livefyre est fourni par un fournisseur tiers et n’est plus pris en charge.
> Le système Livefyre ne sera plus disponible sur PowerShell Gallery à compter du 01/05/2019. 

PowerShell Gallery utilise le service LiveFyre pour permettre aux utilisateurs de commenter sur les packages.
Les utilisateurs qui ont des recommandations ou des commentaires peuvent utiliser cette fonctionnalité pour fournir des commentaires qui sont visibles par toute personne qui consulte la page du package.
Les propriétaires de package peuvent suivre ces commentaires et être avertis lorsqu’un utilisateur publie un commentaire.

Le système de commentaires est basé sur LiveFyre, un service distinct qui n’est pas géré par Microsoft et nécessite une authentification séparée.
La première fois que vous souhaitez laisser un commentaire ou suivez des commentaires sur l’un de vos packages, vous devrez créer un compte LiveFyre.

Si vous avez créé un compte LiveFyre et vous êtes connecté, vous pouvez préparer un commentaire avec des retours sur le package. Cliquez alors sur « Publier le commentaire... » Le commentaire ne sera pas être visible immédiatement.
Les commentaires pour les packages de PowerShell Gallery sont modérés par des administrateurs, et toutes les publications sont vérifiées par ces derniers avant d’être publiées et visibles pour d’autres personnes.
Notre objectif avec la modération des commentaires est de vous assurer qu’ils sont en conformité avec les [conditions d’utilisation](https://www.powershellgallery.com/policies/Terms) de PowerShell Gallery.

Les propriétaires de packages sont encouragés à suivre les commentaires qui sont publiés sur LiveFyre.
Un compte LiveFyre est requis, et il est recommandé d’utiliser l’adresse de messagerie que vous utilisez pour la publication de votre package dans LiveFyre.
Pour suivre les commentaires, connectez-vous à LiveFyre et accédez à n’importe quel package pour lequel vous êtes répertorié comme propriétaire.
Sous la zone de commentaires en bas de chaque package, vous pouvez voir un lien « + S’abonner ».
Une fois que vous cliquez dessus, LiveFyre envoie un courrier électronique à l’adresse de messagerie inscrite chaque fois que de nouveaux commentaires sont écrits pour le package.
