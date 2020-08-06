---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bc58d630e65b316f9223bf3c529f928358e38ebc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787373"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)

Spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, l’entrée de liste est utilisée.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) élément EntrySelectedBy pour ListEntry pour ListControl (format) SelectionCondition élément pour EntrySelectedBy pour ListControl (format) TypeName, élément pour SelectionCondition pour pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
