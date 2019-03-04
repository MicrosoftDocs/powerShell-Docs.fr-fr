---
title: Élément TableRowEntry pour TableRowEntroes pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853585"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a>TableRowEntry, élément pour TableRowEntries pour TableControl (Format)

Définit les données qui s’affiche dans une ligne de la table.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries élément de configuration pour élément TableRowEntry de table (Format) pour TableRowEntries pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `TableRowEntry` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour TableRowEntry pour la table (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les objets dont les valeurs propriété sont affichés dans la ligne.|
|[Élément TableColumnItems pour TableRowEntry pour la table (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les propriétés ou les scripts dont les valeurs sont affichées.|
|[Encapsulez l’élément pour TableRowEntry pour TableCntrol (Format)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|Élément facultatif.<br /><br /> Spécifie que le texte qui dépasse la largeur de colonne est affichée sur la ligne suivante.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableRowEntries pour la table (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Définit les lignes de la table.|

## <a name="remarks"></a>Remarques

Un `TableColumnItems` et un élément `EntrySelectedBy` élément doit être spécifié.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableRowEntry` élément qui définit une ligne qui affiche les valeurs de deux propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

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

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément EntrySelectedBy pour TableRowEntry pour la table (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Élément TableColumnItems pour TableRowEntry pour la table (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Élément TableRowEntries pour la table (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Élément TableRowEntry pour TableRowEntries pour la table (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Encapsulez l’élément pour TableRowEntry pour TableCntrol (Format)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
