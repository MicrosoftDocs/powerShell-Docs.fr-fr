---
title: Élément EntrySelectedBy pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 75a0f42e7722b54791a873200a35c8fcbbd665b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774131"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)

Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que cette définition soit utilisée.|
|[SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.|
|[TypeName, élément pour EntrySelectedBy pour GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Notes

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` . Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[TypeName, élément pour EntrySelectedBy pour GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[CustomEntry, élément pour CustomEntries pour Controls pour View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
