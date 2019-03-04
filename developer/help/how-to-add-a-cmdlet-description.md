---
title: Comment ajouter une Description de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862595"
---
# <a name="how-to-add-a-cmdlet-description"></a>Guide pratique pour ajouter une description de l’applet de commande

Cette section décrit comment ajouter du contenu qui s’affiche dans la section DESCRIPTION de l’aide de l’applet de commande. Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell. Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.

### <a name="to-add-a-description"></a>Pour ajouter une Description

- Commencez par expliquer les fonctionnalités de base de l’applet de commande plus en détail. Dans de nombreux cas, vous pouvez expliquer les termes utilisés dans le nom de l’applet de commande et illustrer les concepts êtes pas familiarisés avec un exemple. Par exemple, si l’applet de commande ajoute des données à un fichier, expliquez qu’il ajoute des données à la fin d’un fichier existant.

- Pour rechercher toutes les fonctionnalités de l’applet de commande, passez en revue la liste de paramètres. Décrire la fonction principale de l’applet de commande et ensuite inclure les autres fonctions et fonctionnalités. Par exemple, si la fonction principale de l’applet de commande consiste à modifier une propriété, mais l’applet de commande peut modifier toutes les propriétés, par exemple, dans la description détaillée. Si les paramètres de l’applet de commande permettent aux utilisateurs de solliciter des informations de différentes façons, expliquer.

- Inclure des informations sur les méthodes que les utilisateurs peuvent utiliser l’applet de commande, outre les utilisations évident. Par exemple, vous pouvez utiliser l’objet qui le `Get-Host` récupère d’applet de commande pour modifier la couleur du texte dans la fenêtre de commande Windows PowerShell.

  Exemple :  « Le `Get-Acl` applet de commande Obtient les objets qui représentent le descripteur de sécurité d’un fichier ou d’une ressource. Le descripteur de sécurité contient les listes de contrôle d'accès (ACL) de la ressource. La liste ACL spécifie les autorisations dont disposent les utilisateurs et groupes d’utilisateurs à accéder à la ressource. »

- La description détaillée doit décrire l’applet de commande, mais elle ne doit pas décrire les concepts qui utilise l’applet de commande. Placez les définitions de concept dans les remarques supplémentaires.

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
