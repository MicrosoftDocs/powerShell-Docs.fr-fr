---
title: Guide pratique pour créer et charger des fichiers CAB
ms.date: 09/13/2016
ms.openlocfilehash: 247ed70ba206d70be01155653efbe887bf603f53
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893031"
---
# <a name="how-to-create-and-upload-cab-files"></a>Guide pratique pour créer et charger des fichiers CAB

Cette rubrique explique comment créer des fichiers CAB d’aide pouvant être mis à jour et les télécharger à l’emplacement où les applets de commande d’aide pouvant être mises à jour peuvent les trouver.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Comment créer et télécharger des fichiers CAB d’aide actualisables

Vous pouvez utiliser la fonctionnalité d’aide actualisable pour remettre des fichiers d’aide nouveaux ou mis à jour pour un module dans plusieurs langues et cultures. Un package d’aide pouvant être mis à jour pour un module se compose d’un fichier XML HelpInfo et d’un ou plusieurs fichiers Cabinet ( `.CAB` ). Chaque fichier CAB contient des fichiers d’aide pour le module dans une culture d’interface utilisateur. Utilisez la procédure suivante pour créer des fichiers CAB pour l’aide actualisable.

1. Organisez les fichiers d’aide pour le module par culture d’interface utilisateur. Chaque fichier CAB d’aide actualisable contient les fichiers d’aide d’un module dans une culture d’interface utilisateur. Vous pouvez fournir plusieurs fichiers CAB d’aide pour le module, chacun pour une culture d’interface utilisateur différente.

1. Vérifiez que les fichiers d’aide incluent uniquement les types de fichiers autorisés pour l’aide actualisable et validez-les par rapport à un schéma de fichier d’aide. Si l' `Update-Help` applet de commande rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, elle n’installe pas le fichier non valide et arrête l’installation des fichiers à partir du fichier CAB. Pour obtenir la liste des types de fichiers autorisés, consultez [types de fichiers autorisés dans un fichier CAB de l’aide actualisable](./file-types-permitted-in-an-updatable-help-cab-file.md).

1. Signez numériquement les fichiers d’aide. Les signatures numériques ne sont pas requises, mais elles constituent une bonne pratique.

1. Inclure tous les fichiers d’aide pour le module dans la culture de l’interface utilisateur, non seulement les fichiers qui sont nouveaux ou ont été modifiés. Si le fichier CAB est incomplet, les utilisateurs qui téléchargent les fichiers d’aide pour la première fois ou ne téléchargent pas chaque mise à jour ne disposent pas de tous les fichiers d’aide du module.

1. Utilisez un utilitaire qui crée des fichiers CAB, tels que `MakeCab.exe` . PowerShell n’inclut pas les applets de commande qui créent des fichiers CAB.

1. Nommez les fichiers CAB. Pour plus d’informations, consultez [Comment nommer un fichier cab d’aide pouvant être mis à jour](./how-to-name-an-updatable-help-cab-file.md).

1. Téléchargez les fichiers CAB du module à l’emplacement spécifié par l’élément **HelpContentUri** dans le fichier XML HelpInfo du module. Téléchargez ensuite le fichier XML HelpInfo à l’emplacement spécifié par la clé **HelpInfoUri** du manifeste de module. **HelpContentUri** et **HelpInfoUri** peuvent pointer vers le même emplacement.

> [!CAUTION]
> La valeur de la clé **HelpInfoUri** et de l’élément **HelpContentUri** doit commencer par `http` ou `https` . La valeur doit indiquer un emplacement Internet et ne doit pas inclure un nom de fichier.
