---
title: Élément TableRowEntry pour TableRowEntries pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 83076ae5b2c48992ce5e621c65fc9937efb68b87
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787408"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableRowEntry, élément pour TableRowEntries pour TableControl (Format)

Définit les données affichées dans une ligne de la table.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format)

## <a name="syntax"></a>Syntaxe

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableRowEntry` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour TableRowEntry pour table ((format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les objets dont les valeurs de propriété sont affichées dans la ligne.|
|[TableColumnItems, élément pour TableRowEntry pour TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les propriétés ou les scripts dont les valeurs sont affichées.|
|[Wrap, élément de TableRowEntry pour table ((format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie que le texte qui dépasse la largeur de colonne est affiché sur la ligne suivante.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TableRowEntries, élément pour TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Définit les lignes de la table.|

## <a name="remarks"></a>Notes

Un `TableColumnItems` élément et un `EntrySelectedBy` élément doivent être spécifiés.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableRowEntry` élément qui définit une ligne qui affiche les valeurs de deux propriétés de l' [objet System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
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
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[Élément EntrySelectedBy pour TableRowEntry pour table ((format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems, élément pour TableRowEntry pour TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries, élément pour TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Wrap, élément de TableRowEntry pour table ((format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
