---
title: Élément EntrySelectedBy pour CustomEntry pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4d4900cefb0d499397fc9dff7e037ce0a541f72f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783685"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)

Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de l’affichage de contrôle.|
|[Élément TypeName pour EntrySelectedBy pour CustomEntry (format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Définit les contrôles utilisés par des objets .NET spécifiques.|

## <a name="remarks"></a>Notes

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une entrée. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour l’entrée à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` . Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [vue de contrôle personnalisé](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Élément TypeName pour EntrySelectedBy pour CustomEntry (format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Affichage de contrôle personnalisé](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
