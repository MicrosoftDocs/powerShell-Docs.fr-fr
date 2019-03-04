---
title: Écriture de l’aide pour les fonctions et les Scripts PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857475"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Écriture de l’aide de Scripts PowerShell et de fonctions

Fonctions et scripts PowerShell doivent être entièrement documentées chaque fois qu’ils sont partagés avec d’autres utilisateurs.
Le `Get-Help` applet de commande affiche les rubriques d’aide de script et de fonction dans le même format qu’il affiche l’aide des applets de commande, tous les le `Get-Help` paramètres fonctionnent sur les rubriques d’aide de script et de la fonction.

Scripts PowerShell peuvent inclure une rubrique d’aide sur le script et les rubriques d’aide sur les fonctions de chaque dans le script.
Les fonctions qui sont partagées indépendamment des scripts peuvent inclure leurs propres rubriques d’aide.

Ce document explique le format et le positionnement correct des rubriques d’aide, et il suggère des indications pour le contenu.

## <a name="types-of-script-and-function-help"></a>Types de Script et l’aide de la fonction

### <a name="comment-based-help"></a>Aide basée sur le commentaire
La rubrique d’aide qui décrit un script ou une fonction peut être implémentée comme un ensemble de commentaires dans le script ou la fonction.
Lors de l’écriture de l’aide basée sur un commentaire pour un script et pour les fonctions dans un script, soyez très attentif aux règles de placement de l’aide en fonction du commentaire.
La sélection élective détermine si le `Get-Help` applet de commande associe la rubrique d’aide avec le script ou une fonction.
Pour plus d’informations sur l’écriture de rubriques d’aide en fonction du commentaire, consultez [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Aide de commande basé sur XML
La rubrique d’aide qui décrit un script ou une fonction peut être implémentée dans un fichier XML qui utilise le schéma d’aide de commande.
Pour associer le script ou la fonction avec le fichier XML, utilisez la `ExternalHelp` commenter le mot clé suivi par le chemin d’accès et le nom du fichier XML.

Lorsque le `ExternalHelp` commenter le mot clé est présente, elle est prioritaire sur l’aide basée sur le commentaire, même si `Get-Help` Impossible de trouver un fichier d’aide qui correspond à la valeur de la `ExternalHelp` mot clé.

### <a name="online-help"></a>Aide en ligne
Vous pouvez publier vos rubriques d’aide sur Internet et puis de diriger `Get-Help` pour ouvrir les rubriques.
Pour plus d’informations sur l’écriture de rubriques d’aide en fonction du commentaire, consultez [Supporting Online Help](../module/supporting-online-help.md).

Il n’existe aucune méthode établie pour l’écriture rubriques conceptuelle (« About ») pour les scripts et fonctions.
Toutefois, vous pouvez publier des rubriques conceptuelles sur la liste Internet les rubriques et leurs URL dans la section liens connexes d’une rubrique d’aide de commande.

## <a name="content-considerations-for-script-and-function-help"></a>Considérations sur le contenu pour le Script et de la fonction aide

- Si vous écrivez une rubrique d’aide très courte avec seulement quelques-unes des sections d’aide de commande disponibles, veillez à inclure des descriptions claires des paramètres de script ou la fonction. Également inclure un ou deux exemples de commandes dans la section exemples, même si vous décidez d’omettre les descriptions de l’exemple.

- Dans toutes les descriptions, reportez-vous à la commande en tant que script ou fonction. Ces informations aident l’utilisateur à comprendre et à gérer la commande.

  Par exemple, la description détaillée suivante stipule que la commande New-rubrique est un script. Cela permet de rappeler aux utilisateurs dont ils ont besoin pour spécifier le chemin d’accès et le nom complet lorsqu’ils l’exécutent.

  > « Le script New-rubrique crée une rubrique conceptuelle vide pour chaque nom de la rubrique dans le fichier d’entrée... »

  La description détaillée suivante stipule que `Disable-PSRemoting` est une fonction. Ces informations sont particulièrement utiles pour les utilisateurs lors de la session comprend plusieurs commandes portant le même nom, certains d'entre eux peuvent être masquée par une commande avec une priorité plus élevée.

  > Le `Disable-PSRemoting` fonction désactive toutes les configurations de session sur l’ordinateur local...

- Dans une rubrique d’aide de script, expliquent comment utiliser le script dans sa globalité. Si vous écrivez également les rubriques d’aide pour les fonctions dans le script, mentionnez les fonctions dans la rubrique d’aide de votre script et inclure des références à des rubriques d’aide de la fonction dans la section liens connexes de la rubrique d’aide de script. À l’inverse, lorsqu’une fonction fait partie d’un script, expliquez dans la rubrique d’aide (fonction) le rôle joué par la fonction dans le script et comment elle peut être utilisée indépendamment. Puis répertorier la rubrique d’aide de script dans la section liens connexes de la rubrique d’aide (fonction).

- Lorsque vous écrivez des exemples pour une rubrique d’aide de script, veillez à inclure le chemin d’accès au fichier de script dans l’exemple de commande. Cela rappelle aux utilisateurs qu’ils doivent spécifier le chemin d’accès explicitement, même lorsque le script est dans le répertoire actif.

- Dans une rubrique d’aide (fonction), rappeler aux utilisateurs que la fonction existe uniquement dans la session active et, pour l’utiliser dans d’autres sessions, dont ils ont besoin pour l’ajouter, ou ajoutez-le à un profil de PowerShell.

- `Get-Help` Affiche la rubrique d’aide pour une fonction ou un script uniquement lorsque le fichier de script et les fichiers de la rubrique d’aide sont enregistrées dans les emplacements corrects. Par conséquent, il n’est pas utile d’inclure des instructions d’installation de PowerShell, ou d’enregistrement ou de l’installation du script ou une fonction dans une rubrique d’aide de script ou la fonction. Incluez plutôt les instructions d’installation dans le document qui vous permet de distribuer le script ou la fonction.

## <a name="see-also"></a>Voir aussi

 [Écriture de rubriques d’aide basé sur XML pour les Scripts et fonctions](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Écriture de rubriques d’aide basé sur XML pour les commandes](./writing-xml-based-help-topics-for-commands.md)

 [Écriture de rubriques d’aide en fonction du commentaire](./writing-comment-based-help-topics.md)
