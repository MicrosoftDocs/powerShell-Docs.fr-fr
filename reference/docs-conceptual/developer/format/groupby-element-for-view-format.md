---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy, élément pour View (Format)
description: GroupBy, élément pour View (Format)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652096"
---
# <a name="groupby-element-for-view-format"></a>GroupBy, élément pour View (Format)

Définit le mode d’affichage d’un nouveau groupe d’objets. Cet élément est utilisé lors de la définition d’une vue de contrôle de table, de liste, étendue ou personnalisée.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit le contrôle personnalisé qui affiche les nouveaux groupes.|
|[CustomControlName, élément pour GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.|
|[Label, élément pour GroupBy (Format)](./label-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.|
|[PropertyName, élément pour GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.|
|[ScriptBlock, élément pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui affiche un ou plusieurs objets .NET.|

## <a name="remarks"></a>Notes

Lorsque vous définissez le mode d’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou le script qui va démarrer le nouveau groupe. Toutefois, vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[CustomControlName, élément pour GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Label, élément pour GroupBy (Format)](./label-element-for-groupby-format.md)

[PropertyName, élément pour GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[ScriptBlock, élément pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[View, élément (Format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
