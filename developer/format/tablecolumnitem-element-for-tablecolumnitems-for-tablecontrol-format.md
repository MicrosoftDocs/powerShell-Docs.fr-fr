---
title: Élément TableColumnItem pour TableColumnItems pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143584"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem, élément pour TableColumnItems pour TableControl (Format)

Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) Élément TableColumnItems pour TableControlEntry pour table ((format) TableColumnItem, élément pour TableColumnItems pour table ((format)

## <a name="syntax"></a>Syntaxe

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent `TableColumnItem` de l’élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément Alignment pour TableColumnItem pour table ((format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit le mode d’affichage des données dans une colonne de la ligne.|
|[FormatString, élément de TableColumnItem pour table ((format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Spécifie un modèle de format utilisé pour mettre en forme les données dans la colonne de la ligne.|
|[PropertyName, élément de TableColumnItem pour table ((format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le nom de la propriété dont la valeur est affichée.|
|[Élément ScriptBlock pour TableColumnItem pour table ((format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnItems pour TableControlEntry pour table ((format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.|

## <a name="remarks"></a>Remarques

Vous pouvez spécifier une propriété d’un objet ou un script dans chaque colonne de la ligne. Si aucun élément enfant n’est spécifié, l’élément est un espace réservé et aucune donnée n’est affichée.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableColumnItem` élément qui affiche la valeur de la `Status` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[Élément Alignment pour TableColumnItem pour table ((format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Élément TableColumnItems (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString, élément de TableColumnItem pour table ((format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName, élément de TableColumnItem pour table ((format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Élément ScriptBlock pour TableColumnItem pour table ((format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
