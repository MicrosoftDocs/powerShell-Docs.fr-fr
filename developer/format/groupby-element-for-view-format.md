---
title: Élément GroupBy de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065533"
---
# <a name="groupby-element-for-view-format"></a>GroupBy, élément pour View (Format)

Définit comment un nouveau groupe d’objets est affiché. Cet élément est utilisé lors de la définition d’une table, la liste, l’affichage de contrôle de larges ou personnalisé.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour afficher (Format)

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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomControl pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit le contrôle personnalisé qui affichent des groupes.|
|[Élément CustomControlName pour GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.|
|[Élément Label pour GroupBy (Format)](./label-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.|
|[Élément PropertyName pour GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET le démarre un nouveau groupe chaque fois que sa valeur change.|
|[Élément ScriptBlock pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui affiche un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarques

Lorsque vous définissez l’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou un script qui démarre le nouveau groupe ; Toutefois, vous ne pouvez pas spécifier à la fois.

## <a name="see-also"></a>Voir aussi

[Élément CustomControlName pour GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Élément Label pour GroupBy (Format)](./label-element-for-groupby-format.md)

[Élément PropertyName pour GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[Élément ScriptBlock pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Élément d’affichage (Format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
