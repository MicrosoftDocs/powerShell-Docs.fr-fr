---
title: Écriture de l’aide des applets de commande PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083159"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Aide d’écriture pour les applets de commande PowerShell

Applets de commande PowerShell peut être utile, mais à moins que vos rubriques d’aide expliquer clairement ce que fait l’applet de commande et comment l’utiliser, l’applet de commande ne peut pas utilisé ou, pire encore, il peut nuire aux utilisateurs.
Le format de fichier d’aide applet de commande basé sur XML améliore la cohérence, mais une aide précieuse nécessite beaucoup plus.

Si vous n’avez jamais écrit aide de l’applet de commande, passez en revue les instructions suivantes.
Le schéma XML requis pour créer la rubrique d’aide de l’applet de commande est décrite dans la section suivante.
Démarrer avec [création du fichier d’aide de l’applet de commande](./how-to-create-the-cmdlet-help-file.md).
Cette rubrique inclut une description des nœuds XML de niveau supérieur.

## <a name="writing-guidelines-for-cmdlet-help"></a>Guides de l’aide de l’applet de commande

### <a name="write-well"></a>Écrire
Rien ne remplace une rubrique bien écrite.
Si vous n’êtes pas un rédacteur professionnel, trouver un enregistreur ou un éditeur pour vous aider à.
Une autre solution consiste à copier votre texte d’aide dans Microsoft Word et à utiliser la grammaire et orthographe vérifie pour améliorer votre travail.

### <a name="write-simply"></a>Écrire simplement
Utiliser des expressions et les mots simples.
Éviter le jargon.
Prendre en compte que de nombreux lecteurs sont équipés uniquement un dictionnaire de langue étrangère et votre rubrique d’aide.

### <a name="write-consistently"></a>Écrire de manière cohérente
L’aide d’applets de commande associées doivent être similaires (par exemple, x-get et set-x).
Utiliser les descriptions standards pour les paramètres standard, comme **Force** et **InputObject**.
(Les copier à partir de l’aide pour les applets de commande core.) Utilisez des termes standards.
Par exemple, utilisez « paramètre », pas « argument », utilisez « cmdlet » pas « commande » ou « applet de commande. »

### <a name="start-the-synopsis-with-a-verb"></a>Démarrer le synopsis avec un verbe
Le champ synopsis informe l’utilisateur quel l’applet de commande ne, il est ni son fonctionnement.
Verbes créez une instruction basé sur des tâches qui informe les utilisateurs si cette applet de commande répond à leurs besoins.
Utiliser des verbes simples comme « get », « créer » et « modifier ».
Évitez de « set », ce qui peut être vagues et fantaisistes mots comme « modifier ».

### <a name="focus-on-objects"></a>Vous concentrer sur des objets
La plupart « get » complet d’applets de commande quelque chose, mais leur fonction principale consiste à obtenir un objet.
Dans votre aide, de vous concentrer sur l’objet, afin que les utilisateurs comprennent que l’affichage par défaut est un des nombreux et qu’ils peuvent utiliser les méthodes et propriétés de l’objet que vous avez récupérées pour eux de différentes façons.

### <a name="write-detailed-descriptions"></a>Écrire une description détaillée
Mentionner rapidement tout ce que l’applet de commande peut faire dans la description détaillée.
Si la fonction principale consiste à modifier une propriété, mais l’applet de commande peut modifier toutes les propriétés, liste cela dans la description détaillée.

### <a name="use-conventional-syntax"></a>Utilisez la syntaxe classique
Utilisez le format Backus-Naur standard, ce qui est courant pour Windows et de l’aide en ligne de commande UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Utiliser des types Microsoft .NET Framework pour les valeurs de paramètre
Les espaces réservés pour les valeurs de paramètre (dans les descriptions de syntaxe et les paramètres) affichent les types .NET Framework des objets qui accepte le paramètre.
L’équipe PowerShell développé cette convention pour aider à apprendre aux utilisateurs sur le .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Écrire des descriptions de paramètre complet
Descriptions de paramètres doivent informer les utilisateurs de deux choses : le paramètre ne (son effet) et ils doivent taper les valeurs des paramètres.

### <a name="write-practical-examples"></a>Écrire des exemples concrets
Les exemples doivent afficher l’utilisation de tous les paramètres, mais le plus important est de montrer comment utiliser l’applet de commande dans les tâches réelles.
Démarrez avec un exemple simple et écrire des exemples de plus en plus complexes.
Dans l’exemple final, montrent comment utiliser l’applet de commande dans un pipeline.

### <a name="use-the-notes-field"></a>Utilisez le champ Notes
Utilisez le champ Notes pour expliquer les concepts que les utilisateurs doivent comprendre l’applet de commande.
Vous pouvez également utiliser des notes pour aider les utilisateurs à éviter les erreurs courantes.
Évitez d’URL comme elles changent.
Au lieu de cela, fournissez de termes à rechercher les utilisateurs.

### <a name="test-your-help"></a>Tester votre aide
L’aide de test comme vous tester votre code.
Avez des amis et collègues lire votre contenu d’aide et de fournissent des commentaires.
Vous pouvez également recueillir les commentaires des groupes de discussion.

## <a name="see-also"></a>Voir aussi

 [Comment créer le fichier d’aide de l’applet de commande](./how-to-create-the-cmdlet-help-file.md)

 [Comment ajouter le nom de l’applet de commande et le Synopsis à une rubrique d’aide applet de commande](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Comment ajouter la Description détaillée à une rubrique d’aide applet de commande](./how-to-add-a-cmdlet-description.md)

 [Comment ajouter la syntaxe pour une rubrique d’aide applet de commande](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Comment ajouter des paramètres à une rubrique d’aide applet de commande](./how-to-add-parameter-information.md)

 [Comment ajouter des Types d’entrée à une rubrique d’aide applet de commande](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Comment ajouter des valeurs de retour à une rubrique d’aide applet de commande](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Comment ajouter des Notes à une rubrique d’aide applet de commande](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Comment ajouter des exemples à une rubrique d’aide applet de commande](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Comment ajouter des liens connexes à une rubrique d’aide applet de commande](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)