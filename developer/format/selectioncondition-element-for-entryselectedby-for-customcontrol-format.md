---
title: Élément SelectionCondition pour EntrySelectedBy pour CustomControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075747"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>SelectionCondition, élément pour EntrySelectedBy pour CustomControl (Format)

Définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément pour élément d’affichage (Format) de CustomEntries pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomControl pour la vue ( Format), élément CustomItem pour CustomEntry pour CustomControl pour l’élément d’affichage (Format) de EntrySelectedBy pour CustomEntry pour CustomControl pour l’élément d’affichage (Format) de SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément PropertyName pour SelectionCondition pour CustomControl de vue (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour CustomControl de vue (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour la vue (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le jeu des types .NET qui déclenche la condition.|
|[Élément TypeName pour SelectionCondition pour CustomControl de vue (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour CustomControl de vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.|

## <a name="remarks"></a>Remarques

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour SelectionCondition pour CustomControl de vue (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément ScriptBlock pour SelectionCondition pour CustomControl de vue (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément SelectionSetName pour SelectionCondition pour un contrôle personnalisé pour la vue (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément TypeName pour SelectionCondition pour CustomControl de vue (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Élément EntrySelectedBy pour CustomEntry pour CustomControl de vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
