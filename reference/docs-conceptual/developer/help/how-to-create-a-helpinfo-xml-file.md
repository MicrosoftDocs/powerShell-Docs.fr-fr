---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour créer un fichier XML HelpInfo
description: Guide pratique pour créer un fichier XML HelpInfo
ms.openlocfilehash: d5a24306aa6488fdefad0b7b1ea9e2978a93a7b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647713"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Guide pratique pour créer un fichier XML HelpInfo

Les rubriques de cette section expliquent comment créer et remplir un fichier d’informations d’aide, communément appelé « fichier XML HelpInfo », pour la fonctionnalité d’aide actualisable PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Vue d’ensemble du fichier XML HelpInfo

Le fichier XML HelpInfo est la principale source d’informations sur l’aide actualisable du module. Il inclut l’emplacement des fichiers d’aide pour les modules, les cultures d’interface utilisateur prises en charge et les numéros de version que l’aide actualisable utilise pour déterminer si l’utilisateur dispose des fichiers d’aide les plus récents.

Chaque module a un seul fichier XML HelpInfo, même si le module inclut plusieurs fichiers d’aide pour plusieurs cultures d’interface utilisateur. L’auteur du module crée le fichier XML HelpInfo et le place dans l’emplacement Internet spécifié par la clé **HelpInfoUri** dans le manifeste du module. Lorsque les fichiers d’aide du module sont mis à jour et téléchargés, le créateur du module met à jour le fichier XML HelpInfo et remplace le fichier XML HelpInfo d’origine par la nouvelle version.

Il est essentiel que le fichier XML HelpInfo soit soigneusement géré. Si vous téléchargez de nouveaux fichiers, mais oubliez d’incrémenter les numéros de version, l’aide actualisable ne téléchargera pas les nouveaux fichiers sur les ordinateurs des utilisateurs. Si vous ajoutez des fichiers d’aide pour une nouvelle culture d’interface utilisateur, mais que vous ne mettez pas à jour le fichier XML HelpInfo ou que vous le placez à l’emplacement approprié, l’aide actualisable ne télécharge pas les nouveaux fichiers.

## <a name="in-this-section"></a>Dans cette section

Cette section comprend les rubriques suivantes.

- [Schéma XML HelpInfo](./helpinfo-xml-schema.md)

- [Exemple de fichier XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Guide pratique pour nommer un fichier XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Guide pratique pour définir les numéros de version XML HelpInfo](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’aide actualisable](./supporting-updatable-help.md)
