---
title: Définition de jeux de sélection | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858925"
---
# <a name="defining-selection-sets"></a>Définition de jeux de sélections

Lorsque vous créez plusieurs vues et les contrôles, vous pouvez définir des ensembles d’objets qui portent le nom sous forme de jeux de sélection. Un jeu de sélection vous permet de définir les objets d’une seule fois, sans avoir à les définir à plusieurs reprises pour chaque vue ou d’un contrôle. En règle générale, les jeux de sélection sont utilisés lorsque vous avez un ensemble d’objets .NET connexes. Par exemple, le `FileSystem` le fichier de mise en forme (FileSystem.format.ps1xml) définit un ensemble de la sélection des types de système de fichiers qui utilisent plusieurs vues.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Où les jeux de sélection sont définis et référencés

Vous définissez des jeux de sélection dans le cadre des données courants qui peuvent être utilisées par toutes les vues et les contrôles définis dans le fichier de mise en forme. L’exemple suivant montre comment définir les trois jeux de sélection.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Vous pouvez référencer une sélection définit comme suit :

- Chaque vue possède un `ViewSelectedBy` élément qui définit les objets qui sont affichés à l’aide de la vue. Le `ViewSelectedBy` élément a un `SelectionSetName` l’élément enfant qui spécifie la sélection qui a défini toutes les définitions de l’utilisation de la vue. Il n’existe aucune restriction sur le nombre de jeux de sélection que vous pouvez référencer à partir d’une vue.

- Dans chaque définition d’une vue ou d’un contrôle, le `EntrySelectedBy` élément définit les objets qui sont affichés à l’aide de cette définition. Un contrôle ou un affichage a généralement qu’une seule définition pour les objets sont définis par le `ViewSelectedBy` élément. Le `EntrySelectedBy` de la définition de l’élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection. Si vous spécifiez la jeu de sélection pour une définition, vous ne pouvez pas spécifier un des éléments enfants de le `EntrySelectedBy` élément.

- Dans chaque définition d’une vue ou d’un contrôle, le `SelectionCondition` élément peut être utilisé pour spécifier une condition pour lorsque la définition est utilisée. Le `SelectionCondition` élément a un `SelectionSetName` élément enfant qui spécifie la sélection définie qui déclenche la condition. La condition est déclenchée lorsqu’un des objets définis dans le jeu de sélection s’affiche. Pour plus d’informations sur la définition de ces conditions, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Exemple de jeu de sélection

L’exemple suivant montre un ensemble de sélection est effectuée directement à partir du `FileSystem` mise en forme de fichier fourni par Windows PowerShell. Pour plus d’informations sur les autres PowerShell de Windows mise en forme de fichiers, consultez [fichiers de mise en forme Windows PowerShell](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

Le jeu de sélection précédente est référencé dans le `ViewSelectedBy` élément d’une vue de table.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>Éléments XML

 Il n’existe aucune limite au nombre de jeux de sélection que vous pouvez définir. Les éléments XML suivants sont utilisés pour créer un jeu de sélection.

- Le [SelectionSets](./selectionsets-element-format.md) élément définit les ensembles d’objets .NET qui sont référencés par les vues et les contrôles du fichier de mise en forme.

- Le [SelectionSet](./selectionset-element-format.md) élément définit un ensemble unique d’objets .NET.

- Le [nom](./name-element-for-selectionset-format.md) élément spécifie le nom qui est utilisé pour référencer le jeu de sélection.

- Le [Types](./types-element-for-selectionset-format.md) élément spécifie les types .NET des objets de l’ensemble de la sélection. (Au sein de la mise en forme de fichiers, les objets sont spécifiés par leur type .NET).

 Les éléments XML suivants sont utilisés pour spécifier un jeu de sélection.

- L’élément suivant spécifie la sélection du jeu à utiliser dans toutes les définitions de la vue :

    - [Élément SelectionSetName pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Élément SelectionSetName pour EntrySelectedBy pour GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé par une définition de vue unique :

    - [Élément SelectionSetName pour EntrySelectedBy pour ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Élément SelectionSetName pour EntrySelectedBy pour la table (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Élément SelectionSetName pour EntrySelectedBy pour WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Élément SelectionSetName pour EntrySelectedBy pour CustomControl de vue (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé en commun et afficher les définitions de contrôle :

    - [Élément SelectionSetName pour EntrySelectedBy pour les contrôles de vue (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Élément SelectionSetName pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé lorsque vous définissez un objet qui pour développer :

    - [Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé par les conditions de sélection.

    - [Élément SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour CustomControl de vue (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour la table (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Élément SelectionSetName pour SelectionCondition pour GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Voir aussi

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nom](./name-element-for-selectionset-format.md)

[Types](./types-element-for-selectionset-format.md)

[Fichiers de mise en forme de PowerShell](./powershell-formatting-files.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Écriture d’une mise en forme de PowerShell et le fichier de Types](./writing-a-powershell-formatting-file.md)
