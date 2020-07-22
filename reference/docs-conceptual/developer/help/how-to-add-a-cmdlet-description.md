---
title: Guide pratique pour ajouter une description de l’applet de commande
ms.date: 09/13/2016
ms.openlocfilehash: 2b98c4cefc3a55eccfeb7eba5a290e7d93a6088b
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893235"
---
# <a name="how-to-add-a-cmdlet-description"></a>Guide pratique pour ajouter une description de l’applet de commande

Cette section décrit comment ajouter du contenu qui s’affiche dans la section **Description** de l’aide de l’applet de commande. Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de **commande** .

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des `dll-Help.xml` fichiers situés dans le répertoire d’installation de PowerShell. Par exemple, le `Microsoft.PowerShell.Commands.Management.dll-Help.xml` fichier contient du contenu pour plusieurs des applets de commande PowerShell.

### <a name="to-add-a-description"></a>Pour ajouter une description

- Commencez par expliquer plus en détail les fonctionnalités de base de l’applet de commande. Dans de nombreux cas, vous pouvez expliquer les termes utilisés dans le nom de l’applet de commande et illustrer des concepts inconnus à l’aide d’un exemple. Par exemple, si l’applet de commande ajoute des données à un fichier, Expliquez qu’elle ajoute des données à la fin d’un fichier existant.

- Pour rechercher toutes les fonctionnalités de l’applet de commande, consultez la liste des paramètres. Décrivez la fonction principale de l’applet de commande, puis incluez d’autres fonctions et fonctionnalités. Par exemple, si la fonction principale de l’applet de commande consiste à modifier une propriété, mais que l’applet de commande peut modifier toutes les propriétés, par exemple, dans la description détaillée. Si les paramètres de l’applet de commande permettent aux utilisateurs de solliciter des informations de différentes façons, expliquez-les.

- Incluez des informations sur la façon dont les utilisateurs peuvent utiliser l’applet de commande, en plus des utilisations évidentes. Par exemple, vous pouvez utiliser l’objet que l' `Get-Host` applet de commande récupère pour modifier la couleur du texte dans la fenêtre de commande Windows PowerShell.

  Exemple : «l' `Get-Acl` applet de commande obtient les objets qui représentent le descripteur de sécurité d’un fichier ou d’une ressource. Le descripteur de sécurité contient les listes de contrôle d'accès (ACL) de la ressource. La liste de contrôle d’accès spécifie les autorisations dont disposent les utilisateurs et les groupes d’utilisateurs pour accéder à la ressource.»

- La description détaillée doit décrire l’applet de commande, mais elle ne doit pas décrire les concepts utilisés par l’applet de commande. Placez les définitions de concept dans des remarques supplémentaires.

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
