---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour ListControl (Format)
description: TypeName, élément pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645659"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName, élément pour EntrySelectedBy pour ListControl (Format)

Spécifie un type .NET qui utilise cette entrée de la vue liste. Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de liste.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément TypeName pour EntrySelectedBy pour ListControl (format)

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
|[Élément EntrySelectedBy pour ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom complet du type .NET, tel que `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.

Pour plus d’informations sur l’utilisation de cet élément dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Élément EntrySelectedBy pour ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
