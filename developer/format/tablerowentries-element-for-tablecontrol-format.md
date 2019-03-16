---
title: Élément TableRowEntries pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055731"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries, élément pour TableControl (Format)

Définit les lignes de la table.

Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) table, élément (Format) TableRowEntries élément de configuration pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableRowEntries` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément TableRowEntry pour TableRowEntries pour la table (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Élément requis.<br /><br /> Définit les données qui s’affiche dans une ligne de la table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de table (Format)](./tablecontrol-element-format.md)|Définit un format de table pour une vue.|

## <a name="remarks"></a>Remarques

Vous devez spécifier un ou plusieurs `TableRowEntry` éléments pour l’affichage de la table. Il n’existe aucune limite maximale pour le nombre de `TableRowEntry` les éléments qui peuvent être ajoutées ni leur ordre n’est significative.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableRowEntries` élément qui définit une ligne qui affiche les valeurs de deux propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

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

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément de table (Format)](./tablecontrol-element-format.md)

[Élément TableRowEntry (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
