---
title: Élément TableRowEntry pour TableRowEntries pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361798"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableRowEntry`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour TableRowEntry pour table ((format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les objets dont les valeurs de propriété sont affichées dans la ligne.|
|[Élément TableColumnItems pour TableRowEntry pour table ((format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les propriétés ou les scripts dont les valeurs sont affichées.|
|[Wrap, élément de TableRowEntry pour table ((format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie que le texte qui dépasse la largeur de colonne est affiché sur la ligne suivante.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableRowEntries pour table ((format)](./tablerowentries-element-for-tablecontrol-format.md)|Définit les lignes de la table.|

## <a name="remarks"></a>Remarks

Un élément `TableColumnItems` et un élément `EntrySelectedBy` doivent être spécifiés.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un élément `TableRowEntry` qui définit une ligne qui affiche les valeurs de deux propriétés de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Élément TableColumnItems pour TableRowEntry pour table ((format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Élément TableRowEntries pour table ((format)](./tablerowentries-element-for-tablecontrol-format.md)

[Wrap, élément de TableRowEntry pour table ((format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
