---
title: GroupBy, élément de View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363628"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément de GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit le contrôle personnalisé qui affiche les nouveaux groupes.|
|[Élément CustomControlName pour GroupBy (format)](./customcontrolname-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.|
|[Élément label pour GroupBy (format)](./label-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.|
|[PropertyName, élément de GroupBy (format)](./propertyname-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.|
|[Élément ScriptBlock pour GroupBy (format)](./scriptblock-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (format)](./view-element-format.md)|Définit une vue qui affiche un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarks

Lorsque vous définissez le mode d’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou le script qui va démarrer le nouveau groupe. Toutefois, vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[Élément CustomControlName pour GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

[Élément label pour GroupBy (format)](./label-element-for-groupby-format.md)

[PropertyName, élément de GroupBy (format)](./propertyname-element-for-groupby-format.md)

[Élément ScriptBlock pour GroupBy (format)](./scriptblock-element-for-groupby-format.md)

[View, élément (format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
