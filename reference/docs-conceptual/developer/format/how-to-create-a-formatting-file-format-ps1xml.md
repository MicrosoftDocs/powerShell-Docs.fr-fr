---
title: Comment créer un fichier de mise en forme (.format.ps1XML) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: abdbd4e15b0c4cb1dafcde087d24ed5792c86c3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781254"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Guide pratique pour créer un fichier de mise en forme (.format.ps1xml)

Cette rubrique explique comment créer un fichier de mise en forme (.format.ps1XML).

> [!NOTE]
> Vous pouvez également créer un fichier de mise en forme en effectuant une copie de l’un des fichiers fournis par Windows PowerShell. Si vous effectuez une copie d’un fichier existant, supprimez la signature numérique existante et ajoutez votre propre signature au nouveau fichier.

### <a name="to-create-a-formatps1xml-file"></a>Pour créer un fichier .format.ps1XML.

1. Créez un fichier texte (. txt) à l’aide d’un éditeur de texte tel que le bloc-notes.

2. Copiez les lignes suivantes dans le fichier de mise en forme.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Les `<Configuration></Configuration>` balises définissent le `Configuration` nœud racine. Toutes les balises XML supplémentaires seront incluses dans ce nœud.

   - Les `<ViewDefinitions></ViewDefinitions>` balises définissent le `ViewDefinitions` nœud. Tous les affichages sont définis dans ce nœud.

3. Enregistrez le fichier dans le dossier d’installation de Windows PowerShell, dans le dossier de votre module ou dans un sous-dossier du dossier du module. Lorsque vous enregistrez le fichier, utilisez le format de nom suivant : `MyFile.format.ps1xml` . La mise en forme des fichiers doit utiliser l' `.format.ps1xml` extension.

   Vous êtes maintenant prêt à ajouter des vues au fichier de mise en forme. Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme. Vous pouvez ajouter une vue unique pour chaque objet, plusieurs vues pour le même objet ou une vue unique utilisée par plusieurs objets.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
