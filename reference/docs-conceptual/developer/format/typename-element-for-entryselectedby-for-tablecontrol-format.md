---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour TableControl (Format)
description: TypeName, élément pour EntrySelectedBy pour TableControl (Format)
ms.openlocfilehash: 5a9f5cda1810d461d19ffb48a1cfa2d41f87ca96
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651431"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName, élément pour EntrySelectedBy pour TableControl (Format)

Spécifie un type .NET qui utilise cette entrée de la vue table. Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de table.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) EntrySelectedBy élément (format) TypeName, élément pour EntrySelectedBy (format)

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
|[Élément EntrySelectedBy (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom du type .NET.

## <a name="remarks"></a>Notes

Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[Élément EntrySelectedBy (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
