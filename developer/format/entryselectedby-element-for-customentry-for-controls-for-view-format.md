---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066241"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)

Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `EntrySelectedBy` élément. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection d’une définition. Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour les contrôles de vue (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.|
|[Élément TypeName pour EntrySelectedBy pour les contrôles de vue (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Remarques

Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique ou lorsqu’une valeur de propriété spécifique ou de script prend la valeur `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
