---
title: Comment créer un fichier de mise en forme (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065495"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Guide pratique pour créer un fichier de mise en forme (.format.ps1xml)

Cette rubrique décrit comment créer un fichier de mise en forme (. format.ps1xml).

> [!NOTE]
> Vous pouvez également créer un fichier de mise en forme en effectuant une copie d’un des fichiers fournis par Windows PowerShell. Si vous effectuez une copie d’un fichier existant, supprimez la signature numérique existante et ajouter votre propre signature dans le nouveau fichier.

### <a name="to-create-a-formatps1xml-file"></a>Pour créer un. fichier format.ps1xml.

1. Créer un fichier texte (.txt) à l’aide d’un texte éditeur tel que le bloc-notes.

2. Copiez les lignes suivantes dans le fichier de mise en forme.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Le \<Configuration >\</Configuration > balises définissent la racine `Configuration` nœud. Toutes les balises XML supplémentaires seront placées dans ce nœud.

   - Le <ViewDefinitions> </ViewDefinitions> balises définissent le `ViewDefinitions` nœud. Toutes les vues sont définies au sein de ce nœud.

3. Enregistrez le fichier dans le dossier d’installation de Windows PowerShell, dans votre dossier de module ou dans un sous-dossier du dossier du module. Utilisez le format de nom suivant lorsque vous enregistrez le fichier : `MyFile.format.ps1xml`. Fichiers de mise en forme doivent utiliser le `.format.ps1xml` extension.

   Vous êtes maintenant prêt à ajouter des affichages dans le fichier de mise en forme. Il n’existe aucune limite au nombre de vues qui peuvent être définies dans un fichier de mise en forme. Vous pouvez ajouter une vue unique pour chaque objet, plusieurs vues pour le même objet ou une vue unique qui est utilisée par plusieurs objets.

## <a name="see-also"></a>Voir aussi

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
