---
title: Écriture de l’aide pour les applets de commande PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361068"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Écriture de l’aide pour les applets de commande PowerShell

Les applets de commande PowerShell peuvent être utiles, mais à moins que vos rubriques d’aide n’expliquent clairement ce que fait l’applet de commande et comment l’utiliser, l’applet de commande peut ne pas être utilisée ou, pire encore, elle risque de nuire aux utilisateurs.
Le format de fichier d’aide sur les applets de commande XML améliore la cohérence, mais une grande partie de l’aide est nécessaire.

Si vous n’avez jamais écrit l’aide sur les applets de commande, passez en revue les instructions suivantes.
Le schéma XML requis pour créer la rubrique d’aide de l’applet de commande est décrit dans la section suivante.
Commencez par [créer le fichier d’aide de l’applet](./how-to-create-the-cmdlet-help-file.md)de commande.
Cette rubrique contient une description des nœuds XML de niveau supérieur.

## <a name="writing-guidelines-for-cmdlet-help"></a>Écriture des instructions pour l’aide sur les applets de commande

### <a name="write-well"></a>Écrire correctement
Rien ne remplace un sujet bien écrit.
Si vous n’êtes pas un éditeur professionnel, recherchez un enregistreur ou un éditeur pour vous aider.
Une autre solution consiste à copier votre texte d’aide dans Microsoft Word et à utiliser la grammaire et l’orthographe pour améliorer votre travail.

### <a name="write-simply"></a>Écrire simplement
Utilisez des mots et des expressions simples.
Évitez le jargon.
Supposons que de nombreux lecteurs disposent uniquement d’un dictionnaire de langue étrangère et de votre rubrique d’aide.

### <a name="write-consistently"></a>Écrire de manière cohérente
L’aide sur les applets de commande associées doit être similaire (par exemple, obtenir-x et Set-x).
Utilisez les descriptions standard pour les paramètres standard, par exemple **force** et **InputObject**.
(Copiez-les à partir de l’aide pour les applets de commande de base.) Utilisez les termes standard.
Par exemple, utilisez « Parameter », et non « argument », et utilisez « applet de commande » et non « Command » ou « Command-Let ».

### <a name="start-the-synopsis-with-a-verb"></a>Démarrer le synopsis avec un verbe
Le champ Synopsis informe l’utilisateur de ce que fait l’applet de commande, et non de son fonctionnement.
Les verbes créent une instruction basée sur les tâches qui informe les utilisateurs si cette applet de commande répond à leurs exigences.
Utilisez des verbes simples tels que « obten », « Create » et « change ».
Évitez « Set », qui peut être vague et fantaisie comme « Modify ».

### <a name="focus-on-objects"></a>Focus sur les objets
La plupart des applets de commande « obtenir » affichent un objet, mais leur fonction principale consiste à obtenir un objet.
Dans votre aide, concentrez-vous sur l’objet afin que les utilisateurs sachent que l’affichage par défaut est l’un des nombreux et qu’ils peuvent utiliser les méthodes et propriétés de l’objet que vous avez récupéré pour eux de différentes façons.

### <a name="write-detailed-descriptions"></a>Écrire des descriptions détaillées
Répertoriez brièvement tout ce que l’applet de commande peut faire dans la description détaillée.
Si la fonction principale consiste à modifier une propriété, mais que l’applet de commande peut modifier toutes les propriétés, répertoriez-la dans la description détaillée.

### <a name="use-conventional-syntax"></a>Utiliser la syntaxe conventionnelle
Utilisez le format Backus-Naur standard qui est courant pour l’aide de la ligne de commande Windows et UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Utiliser des types de Microsoft .NET Framework pour les valeurs de paramètres
Les espaces réservés pour les valeurs de paramètres (dans la syntaxe et les descriptions de paramètres) affichent les types de .NET Framework des objets que le paramètre acceptera.
L’équipe PowerShell a développé cette Convention pour aider les utilisateurs à se familiariser avec les .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Écrire les descriptions des paramètres complets
Les descriptions des paramètres doivent informer les utilisateurs de deux choses : ce que fait le paramètre (son effet) et ce qu’il doit taper pour les valeurs de paramètres.

### <a name="write-practical-examples"></a>Écrire des exemples pratiques
Les exemples doivent montrer comment utiliser tous les paramètres, mais l’élément le plus important consiste à montrer comment utiliser l’applet de commande dans des tâches réelles.
Commencez par un exemple simple et écrivez des exemples de plus en plus complexes.
Dans l’exemple final, montrez comment utiliser l’applet de commande dans un pipeline.

### <a name="use-the-notes-field"></a>Utiliser le champ Remarques
Utilisez le champ Remarques pour expliquer les concepts dont les utilisateurs ont besoin pour comprendre l’applet de commande.
Vous pouvez également utiliser des notes pour aider les utilisateurs à éviter les erreurs courantes.
Évitez les URL au fur et à mesure qu’elles changent.
Au lieu de cela, indiquez aux utilisateurs les termes à rechercher.

### <a name="test-your-help"></a>Tester votre aide
Testez l’aide de la même façon que vous testez votre code.
Demander aux amis et collègues de lire le contenu de l’aide et de fournir des commentaires.
Vous pouvez également solliciter des commentaires à partir de groupes de discussion.

## <a name="see-also"></a>Voir aussi

 [Comment créer le fichier d’aide de l’applet de commande](./how-to-create-the-cmdlet-help-file.md)

 [Comment ajouter le nom de l’applet de commande et synopsis à une rubrique d’aide sur une applet de commande](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Comment ajouter la description détaillée à une rubrique d’aide sur une applet de commande](./how-to-add-a-cmdlet-description.md)

 [Guide pratique pour ajouter une syntaxe à une rubrique d’aide sur une applet de commande](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Comment ajouter des paramètres à une rubrique d’aide sur une applet de commande](./how-to-add-parameter-information.md)

 [Comment ajouter des types d’entrée à une rubrique d’aide sur une applet de commande](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Comment ajouter des valeurs de retour à une rubrique d’aide sur une applet de commande](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Comment ajouter des notes à une rubrique d’aide sur une applet de commande](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Comment ajouter des exemples à une rubrique d’aide sur une applet de commande](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Comment ajouter des liens connexes à une rubrique d’aide sur une applet de commande](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)