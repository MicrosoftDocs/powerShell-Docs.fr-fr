---
title: Écriture de l’aide pour les scripts et fonctions PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848106"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Écriture de l’aide pour les scripts et fonctions PowerShell

Les scripts et les fonctions PowerShell doivent être entièrement documentés chaque fois qu’ils sont partagés avec d’autres utilisateurs.
L' `Get-Help` applet de commande affiche les rubriques d’aide script et fonction dans le même format que celui dans lequel elle affiche l’aide pour `Get-Help` les applets de commande, et tous les paramètres fonctionnent sur des rubriques d’aide sur les scripts et les fonctions.

Les scripts PowerShell peuvent inclure une rubrique d’aide sur le script et des rubriques d’aide sur chaque fonction dans le script.
Les fonctions partagées indépendamment des scripts peuvent inclure leurs propres rubriques d’aide.

Ce document explique le format et le positionnement correct des rubriques d’aide, et propose des instructions pour le contenu.

## <a name="types-of-script-and-function-help"></a>Types d’aide sur les scripts et les fonctions

### <a name="comment-based-help"></a>Aide sur les commentaires
La rubrique d’aide qui décrit un script ou une fonction peut être implémentée sous la forme d’un ensemble de commentaires dans le script ou la fonction.
Quand vous écrivez une aide basée sur des commentaires pour un script et des fonctions dans un script, faites attention aux règles de placement de l’aide basée sur les commentaires.
Le positionnement détermine si l' `Get-Help` applet de commande associe la rubrique d’aide au script ou à une fonction.
Pour plus d’informations sur l’écriture de rubriques d’aide basées sur des commentaires, consultez [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Aide sur les commandes basées sur XML
La rubrique d’aide qui décrit un script ou une fonction peut être implémentée dans un fichier XML qui utilise le schéma de l’aide de la commande.
Pour associer le script ou la fonction au fichier XML, utilisez le `ExternalHelp` mot clé comment, suivi du chemin d’accès et du nom du fichier XML.

Lorsque le `ExternalHelp` mot clé comment est présent, il est prioritaire par rapport à l’aide basée sur `Get-Help` les commentaires, même si ne trouve pas un fichier d' `ExternalHelp` aide qui correspond à la valeur du mot clé.

### <a name="online-help"></a>Aide en ligne
Vous pouvez poster vos rubriques d’aide sur Internet, puis vous `Get-Help` diriger vers pour ouvrir les rubriques.
Pour plus d’informations sur l’écriture de rubriques d’aide basées sur des commentaires, consultez [prise en charge de l’aide en ligne](../module/supporting-online-help.md).

Il n’existe aucune méthode établie pour écrire des rubriques conceptuelles (« à propos de ») pour les scripts et les fonctions.
Toutefois, vous pouvez poster des rubriques conceptuelles sur Internet Lister les rubriques et leurs URL dans la section Liens connexes d’une rubrique d’aide de la commande.

## <a name="content-considerations-for-script-and-function-help"></a>Considérations sur le contenu pour l’aide sur les scripts et les fonctions

- Si vous écrivez une très brève rubrique d’aide avec seulement quelques-unes des sections de l’aide sur les commandes disponibles, veillez à inclure des descriptions claires des paramètres du script ou de la fonction. Incluez également un ou deux exemples de commandes dans la section exemples, même si vous décidez d’omettre les exemples de descriptions.

- Dans toutes les descriptions, reportez-vous à la commande sous la forme d’un script ou d’une fonction. Ces informations permettent à l’utilisateur de comprendre et de gérer la commande.

  Par exemple, la description détaillée suivante indique que la commande New-topic est un script. Cela rappelle aux utilisateurs qu’ils doivent spécifier le chemin d’accès et le nom complet lorsqu’ils l’exécutent.

  > « Le script New-topic crée une rubrique conceptuelle vide pour chaque nom de rubrique dans le fichier d’entrée... »

  La description détaillée suivante indique qu' `Disable-PSRemoting` il s’agit d’une fonction. Ces informations sont particulièrement utiles aux utilisateurs lorsque la session comprend plusieurs commandes portant le même nom, dont certaines peuvent être masquées par une commande avec une priorité plus élevée.

  > La `Disable-PSRemoting` fonction désactive toutes les configurations de session sur l’ordinateur local...

- Dans une rubrique d’aide sur les scripts, explique comment utiliser le script dans son ensemble. Si vous écrivez également des rubriques d’aide pour les fonctions dans le script, mentionnez les fonctions dans la rubrique d’aide de votre script et incluez des références aux rubriques d’aide de la fonction dans la section Liens connexes de la rubrique d’aide de script. À l’inverse, lorsqu’une fonction fait partie d’un script, expliquez dans la rubrique d’aide de la fonction le rôle joué par la fonction dans le script et la manière dont elle peut être utilisée de manière indépendante. Ensuite, répertoriez la rubrique d’aide sur les scripts dans la section Liens connexes de la rubrique d’aide de la fonction.

- Lorsque vous écrivez des exemples pour une rubrique d’aide sur un script, veillez à inclure le chemin d’accès au fichier de script dans l’exemple de commande. Cela rappelle aux utilisateurs qu’ils doivent spécifier le chemin d’accès explicitement, même si le script se trouve dans le répertoire actif.

- Dans une rubrique d’aide sur une fonction, Rappelez aux utilisateurs que la fonction existe uniquement dans la session active et, pour l’utiliser dans d’autres sessions, elle doit l’ajouter ou l’ajouter à un profil PowerShell.

- `Get-Help`affiche la rubrique d’aide d’un script ou d’une fonction uniquement lorsque le fichier de script et les fichiers de rubrique d’aide sont enregistrés dans les emplacements appropriés. Par conséquent, il n’est pas utile d’inclure des instructions pour l’installation de PowerShell ou l’enregistrement ou l’installation du script ou de la fonction dans une rubrique d’aide sur un script ou une fonction. Au lieu de cela, incluez toutes les instructions d’installation dans le document que vous utilisez pour distribuer le script ou la fonction.

## <a name="see-also"></a>Voir aussi

[Écriture de rubriques d’aide basées sur des commentaires](./writing-comment-based-help-topics.md)
