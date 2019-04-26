---
title: Élément EntrySelectedBy pour CustomEntry pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066275"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)

Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour cette entrée à utiliser.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour EntrySelectedBy de vue (Format) Élément pour CustomEntry de vue (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de l’affichage de contrôle.|
|[Élément TypeName pour EntrySelectedBy pour CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour la vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Définit les contrôles utilisés par des objets .NET spécifiques.|

## <a name="remarks"></a>Remarques

Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une entrée. Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Conditions de sélection permettent de définir une condition qui doit exister pour l’entrée à utiliser, par exemple quand un objet possède une propriété spécifique ou lorsqu’une valeur de propriété spécifique ou de script prend la valeur `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’une vue de contrôle personnalisé, consultez [affichage de contrôle personnalisé](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Élément TypeName pour EntrySelectedBy pour CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément CustomEntry pour CustomEntries pour la vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Affichage de contrôle personnalisé](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
