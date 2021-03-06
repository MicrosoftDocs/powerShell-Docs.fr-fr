---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntries, élément pour TableControl (Format)
description: TableRowEntries, élément pour TableControl (Format)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651458"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries, élément pour TableControl (Format)

Définit les lignes de la table.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format)

## <a name="syntax"></a>Syntaxe

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableRowEntries` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[TableRowEntry, élément pour TableRowEntries pour TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les données affichées dans une ligne de la table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TableControl, élément (Format)](./tablecontrol-element-format.md)|Définit un format de table pour une vue.|

## <a name="remarks"></a>Notes

Vous devez spécifier un ou plusieurs `TableRowEntry` éléments pour la vue de la table. Il n’existe pas de limite maximale pour le nombre d' `TableRowEntry` éléments qui peuvent être ajoutés ou dont l’ordre est significatif.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableRowEntries` élément qui définit une ligne qui affiche les valeurs de deux propriétés de l' [objet System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[TableControl, élément (Format)](./tablecontrol-element-format.md)

[Élément TableRowEntry (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
