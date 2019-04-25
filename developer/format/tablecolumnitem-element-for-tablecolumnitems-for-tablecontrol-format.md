---
title: Élément TableColumnItem pour TableColumnItems pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063936"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem, élément pour TableColumnItems pour TableControl (Format)

Définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries élément de configuration pour élément TableRowEntry de table (Format) pour TableRowEntries pour la table (Format) Élément TableColumnItems pour TableControlEntry pour élément TableColumnItem de table (Format) pour TableColumnItems pour la table (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `TableColumnItem` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément d’alignement pour TableColumnItem pour la table (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit comment les données dans une colonne de la ligne sont affichées.|
|[Élément FormatString pour TableColumnItem pour la table (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Spécifie un modèle de format qui est utilisé pour mettre en forme les données dans la colonne de la ligne.|
|[Élément PropertyName pour TableColumnItem pour la table (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le nom de la propriété dont la valeur est affichée.|
|[Élément ScriptBlock pour TableColumnItem pour la table (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnItems pour TableControlEntry pour la table (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.|

## <a name="remarks"></a>Remarques

Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne. Si aucun élément enfant n’est spécifié, l’élément est un espace réservé, et aucune donnée n’est affichée.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément d’alignement pour TableColumnItem pour la table (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Élément TableColumnItems (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Élément FormatString pour TableColumnItem pour la table (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Élément PropertyName pour TableColumnItem pour la table (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Élément ScriptBlock pour TableColumnItem pour la table (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
