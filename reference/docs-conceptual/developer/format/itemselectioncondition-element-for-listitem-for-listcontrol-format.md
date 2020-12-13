---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition, élément pour ListItem pour ListControl (Format)
description: ItemSelectionCondition, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667808"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition, élément pour ListItem pour ListControl (Format)

Définit la condition qui doit exister pour l’élément de liste à utiliser.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) ListItems, élément de ListEntry pour ListControl (format) ListItem, élément de ListItems pour ListControl (format) élément ItemSelectionCondition pour ListItem pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListItem, élément pour ListItems pour ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="remarks"></a>Notes

Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[ListItem, élément pour ListItems pour ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
