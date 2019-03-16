---
title: Élément EntrySelectedBy pour TableRowEntry pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058757"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>EntrySelectedBy, élément pour TableRowEntry pour TableControl (Format)

Définit les types .NET qui utilisent cette définition de la vue de la table ou la condition qui doit exister pour cette définition à utiliser.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément de table (Format) élément TableRowEntries (Format) élément TableRowEntry (Format) EntrySelectedBy élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour la table (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition de vue de table à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour la table (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de vue de table.|
|[Élément TypeName pour EntrySelectedBy pour la table (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de vue de table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableRowEntry pour la table (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Définit les données qui s’affiche dans une ligne de la table.|

## <a name="remarks"></a>Remarques

Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une définition de vue de table. Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou un script `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `TableRowEntry` élément qui est utilisé pour afficher les propriétés de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément SelectionCondition pour EntrySelectedBy pour la table (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour la table (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Élément TableRowEntry pour la table (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour la table (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
