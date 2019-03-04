---
title: Comment créer un fichier XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853265"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Guide pratique pour créer un fichier XML HelpInfo

Les rubriques de cette section explique comment créer et remplir un fichier d’informations d’aide, communément appelé un « fichier XML HelpInfo, » pour la fonctionnalité de Windows PowerShell de l’aide actualisable.

## <a name="helpinfo-xml-file-overview"></a>Vue d’ensemble du fichier XML HelpInfo

Le fichier XML HelpInfo est la principale source d’informations sur l’aide actualisable pour le module. Il inclut l’emplacement des fichiers d’aide pour les modules, les cultures d’interface utilisateur pris en charge et les numéros de version de l’aide actualisable utilise pour déterminer si l’utilisateur dispose des derniers fichiers d’aide.

Chaque module possède qu’un seul fichier XML HelpInfo, même si le module inclut plusieurs fichiers d’aide pour plusieurs cultures d’interface utilisateur. L’auteur du module crée le fichier XML HelpInfo et le place dans l’emplacement Internet spécifié par le **HelpInfoUri** clés dans le manifeste de module. Lorsque les fichiers d’aide de module sont mis à jour et téléchargés, l’auteur du module met à jour le fichier XML HelpInfo et remplace le fichier XML HelpInfo d’origine par la nouvelle version.

Il est essentiel que le fichier XML HelpInfo est maintenu avec soin. Si vous chargez de nouveaux fichiers, mais que vous oubliez incrémenter les numéros de version, de l’aide actualisable pas téléchargera les nouveaux fichiers dans les ordinateurs des utilisateurs. Si vous ajoutez des fichiers d’aide pour une nouvelle culture d’interface utilisateur, mais ne mettre à jour le fichier XML HelpInfo ou placez-le à l’emplacement approprié, de l’aide actualisable télécharge pas les nouveaux fichiers.

## <a name="in-this-section"></a>Dans cette section

Cette section comprend les rubriques suivantes.

- [Schéma XML de HelpInfo](./helpinfo-xml-schema.md)

- [Exemple de fichier XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Le nom d’un fichier XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Comment définir des numéros de Version HelpInfo XML](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge d’aide actualisable](./supporting-updatable-help.md)