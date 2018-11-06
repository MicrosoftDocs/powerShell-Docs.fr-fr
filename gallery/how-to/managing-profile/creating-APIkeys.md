---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Gestion des clés API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002511"
---
# <a name="managing-api-keys"></a>Gestion des clés API

PowerShell Gallery permet la création de plusieurs clés API de façon à prendre en charge diverses contraintes de publication. Une clé API peut s’appliquer à un ou plusieurs packages, accorde des privilèges spécifiques et présente une date d’expiration.

> [!IMPORTANT]
> Les utilisateurs qui ont publié dans PowerShell Gallery avant l’introduction des clés API étendues ont une « clé API d’accès total ». Les clés d’accès total n’intègrent pas les améliorations de sécurité inhérentes aux clés API étendues. Les clés d’accès total n’expirent jamais et s’appliquent à tous les éléments qui appartiennent à l’utilisateur. Si vous supprimez cette clé, elle ne peut pas être recréée.

L’illustration suivante montre les options disponibles pendant la création d’une clé API étendue.

![Création de clés API](../../Images/PSGallery_KeyScoped.png)

Dans cet exemple, nous avons créé une clé API nommée **AzureRMDataFactory**. La valeur de cette clé peut être utilisée pour envoyer (push) des packages avec des noms qui commencent par « AzureRM.DataFactory » et qui sont valides pendant 365 jours. Il s’agit d’un scénario classique quand différentes équipes au sein d’une même entreprise travaillent sur différents packages. Les membres d’une équipe disposent d’une clé qui leur accorde des privilèges pour le package sur lequel ils travaillent.
La valeur d’expiration évite que des clés obsolètes ou oubliées soient utilisées.

## <a name="using-glob-patterns"></a>Utilisation de modèles Glob

Si vous travaillez sur plusieurs packages, vous pouvez utiliser des modèles Glob pour établir des correspondances avec eux en tant que groupe. Les autorisations d’une clé API s’appliquent à tous les nouveaux packages présentant une correspondance avec le modèle Glob. Ainsi, dans l’exemple précédent, le **modèle Glob** a la valeur « AzureRM.DataFactory* ». Vous pouvez envoyer (push) un package nommé « AzureRm.DataFactoryV2.Netcore » en utilisant cette clé dans la mesure où le package correspond au modèle Glob.

## <a name="create-api-keys-securely"></a>Créer des clés API en toute sécurité

Par mesure de sécurité, une valeur de clé qui vient d’être créée n’est jamais affichée à l’écran et n’est accessible qu’à partir du bouton Copier, comme illustré ci-dessous.

![Obtention de la nouvelle valeur de clé API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Vous ne pouvez copier la valeur d’une clé API que de suite après l’avoir créée ou actualisée. Elle ne s’affiche pas et n’est plus accessible une fois que la page a été actualisée. Si vous perdez la valeur de la clé, vous devez cliquer sur Regénérer et copier la clé une fois qu’elle a été regénérée.

## <a name="key-permissions-and-expiration"></a>Autorisations et expiration des clés

Les clés API étendues peuvent attribuer l’une des autorisations suivantes :

- Envoi (push) de nouveaux packages
- Envoi (push) de nouveaux packages ou de packages de mises à jour
- Retrait de packages de la liste

Chaque nouvelle clé est assortie d’un délai d’expiration. La valeur du délai d’expiration est exprimée en jours. Les valeurs possibles du délai d’expiration sont les suivantes :

- 1 jour
- 90 jours
- 180 jours
- 270 jours
- 365 jours (valeur par défaut)

Ces paramètres ne peuvent pas être modifiés une fois que la clé est créée. Vous ne pouvez pas créer une clé qui n’expire jamais.

## <a name="editing-and-deleting-existing-api-keys"></a>Modification et suppression de clés API existantes

Vous pouvez modifier certains paramètres d’une clé existante. Comme indiqué précédemment, vous ne pouvez ni modifier l’étendue de sécurité d’une clé API existante, ni modifier son délai d’expiration. Les options que vous pouvez modifier figurent dans la capture d’écran suivante :

![Obtention d’une nouvelle valeur de clé API](../../Images/PSGallery_EditAPIKey.png)

Pour modifier les packages contrôlés par une clé, vous pouvez choisir individuellement les packages dans la liste ou modifier le modèle Glob.

En cliquant sur **Regénérer**, vous créez une nouvelle valeur de clé. Comme à l’étape initiale de création de la clé, vous devez **Copier** la valeur de la clé de suite après l’avoir mise à jour. L’option **Copier** n’est plus disponible une fois que vous quittez cette page.

Quand vous cliquez sur **Supprimer**, un message de confirmation s’affiche. Dès lors qu’une clé est supprimée, elle ne peut plus être utilisée.

## <a name="key-expiration"></a>Expiration des clés

Dix jours avant la date d’expiration, PowerShell Gallery envoie un e-mail d’avertissement au titulaire du compte de la clé API. Une fois arrivée à expiration, la clé est inutilisable. Un message d’avertissement s’affiche en haut de la page de gestion des clés API en répertoriant les clés qui ne sont plus valides. Vous pouvez générer une nouvelle valeur de clé.
