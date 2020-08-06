---
title: Élément PropertyName pour ItemSelectionCondition pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780863"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la vue est utilisée. Cet élément est utilisé lors de la définition d’un affichage de liste.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément de ListControl (format) élément ListItems pour l’élément ListItem pour ListControl (format) ListItem pour l’élément ListItems pour ListControl (format) ItemSelectionCondition, élément pour ListItem pour l’élément ListControls PropertyName pour ItemSelectionCondition pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `PropertyName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ItemSelectionCondition, élément pour ListItem pour ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément ScriptBlock pour ItemSelectionCondition pour ListIControl (format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition, élément pour ListItem pour ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
