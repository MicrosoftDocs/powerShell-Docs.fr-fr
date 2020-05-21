---
title: Définition des jeux de sélection | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 95eeb037b3b9190fec1212a68029624993f3fd9f
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692284"
---
# <a name="defining-selection-sets"></a>Définition de jeux de sélections

Lorsque vous créez plusieurs vues et contrôles, vous pouvez définir des ensembles d’objets appelés jeux de sélection. Un jeu de sélection vous permet de définir les objets une seule fois, sans avoir à les définir à plusieurs reprises pour chaque vue ou contrôle. En règle générale, les jeux de sélection sont utilisés lorsque vous avez un ensemble d’objets .NET associés. Par exemple, le `FileSystem` fichier de mise en forme (FileSystem. format. ps1xml) définit un jeu de sélection des types de système de fichiers utilisés par plusieurs vues.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Où les jeux de sélection sont définis et référencés

Vous définissez des jeux de sélection dans le cadre des données communes qui peuvent être utilisées par toutes les vues et tous les contrôles définis dans le fichier de mise en forme. L’exemple suivant montre comment définir trois jeux de sélection.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Vous pouvez référencer un jeu de sélection des manières suivantes :

- Chaque vue a un `ViewSelectedBy` élément qui définit les objets qui sont affichés à l’aide de la vue. L' `ViewSelectedBy` élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection utilisé par toutes les définitions de la vue. Il n’existe aucune restriction sur le nombre de jeux de sélection que vous pouvez référencer à partir d’une vue.

- Dans chaque définition d’une vue ou d’un contrôle, l' `EntrySelectedBy` élément définit les objets qui sont affichés à l’aide de cette définition. En général, une vue ou un contrôle n’a qu’une seule définition, de sorte que les objets sont définis par l' `ViewSelectedBy` élément. L' `EntrySelectedBy` élément de la définition a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection. Si vous spécifiez le jeu de sélection pour une définition, vous ne pouvez pas spécifier d’autres éléments enfants de l' `EntrySelectedBy` élément.

- Dans chaque définition d’une vue ou d’un contrôle, l' `SelectionCondition` élément peut être utilisé pour spécifier une condition lorsque la définition est utilisée. L' `SelectionCondition` élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection qui déclenche la condition. La condition est déclenchée lorsque l’un des objets définis dans le jeu de sélection est affiché. Pour plus d’informations sur la façon de définir ces conditions, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Exemple de jeu de sélection

L’exemple suivant montre un jeu de sélection provenant directement du fichier de `FileSystem` mise en forme fourni par Windows PowerShell. Pour plus d’informations sur les autres fichiers de mise en forme Windows PowerShell, consultez [fichiers de mise en forme Windows PowerShell](./powershell-formatting-files.md).

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

Le jeu de sélection précédent est référencé dans l' `ViewSelectedBy` élément d’une vue de table.

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

- L’élément [SelectionSets](./selectionsets-element-format.md) définit les jeux d’objets .net référencés par les vues et les contrôles du fichier de mise en forme.

- L’élément [SelectionSet](./selectionset-element-format.md) définit un ensemble unique d’objets .net.

- L’élément [Name](./name-element-for-selectionset-format.md) spécifie le nom utilisé pour référencer le jeu de sélection.

- L’élément [types](./types-element-for-selectionset-format.md) spécifie les types .net des objets du jeu de sélection. (Dans les fichiers de mise en forme, les objets sont spécifiés par leur type .NET.)

 Les éléments XML suivants sont utilisés pour spécifier un jeu de sélection.

- L’élément suivant spécifie le jeu de sélection à utiliser dans toutes les définitions de la vue :

  - [SelectionSetName, élément pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

  - [SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé par une définition de vue unique :

  - [SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé par les définitions courantes et de contrôle d’affichage :

  - [SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé lorsque vous définissez l’objet à développer :

  - [SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Les éléments suivants spécifient le jeu de sélection utilisé par les conditions de sélection.

  - [SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Voir aussi

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nom](./name-element-for-selectionset-format.md)

[Types](./types-element-for-selectionset-format.md)

[Fichiers de mise en forme PowerShell](./powershell-formatting-files.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme et de types PowerShell](./writing-a-powershell-formatting-file.md)
