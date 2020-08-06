---
title: Élément TableColumnItem pour TableColumnItems pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: beadf771f02519394d799a03db374050e3302321
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785164"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem, élément pour TableColumnItems pour TableControl (Format)

Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément table ((format) élément TableRowEntries pour table ((format) élément TableRowEntry pour TableRowEntries pour table ((format) élément TableColumnItems pour TableControlEntry (format) table (élément pour TableColumnItem (format)

## <a name="syntax"></a>Syntaxe

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableColumnItem` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Alignment, élément pour TableColumnItem pour TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Définit le mode d’affichage des données dans une colonne de la ligne.|
|[FormatString, élément pour TableColumnItem pour TableControl (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Spécifie un modèle de format utilisé pour mettre en forme les données dans la colonne de la ligne.|
|[PropertyName, élément pour TableColumnItem pour TableControl (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le nom de la propriété dont la valeur est affichée.|
|[ScriptBlock, élément pour TableColumnItem pour TableControl (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée dans la colonne d’une ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnItems pour TableControlEntry pour table ((format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.|

## <a name="remarks"></a>Notes

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

[Alignment, élément pour TableColumnItem pour TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Élément TableColumnItems (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString, élément pour TableColumnItem pour TableControl (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName, élément pour TableColumnItem pour TableControl (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[ScriptBlock, élément pour TableColumnItem pour TableControl (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
