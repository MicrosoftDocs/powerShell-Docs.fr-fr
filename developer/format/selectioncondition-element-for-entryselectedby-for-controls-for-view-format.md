---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064227"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)

Définit une condition qui doit exister pour la définition du contrôle à utiliser. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Format)

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
|[Élément PropertyName pour SelectionCondition pour les contrôles de vue (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour les contrôles de vue (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le jeu des types .NET qui déclenche la condition.|
|[Élément TypeName pour SelectionCondition pour les contrôles de vue (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.|

## <a name="remarks"></a>Remarques

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour SelectionCondition pour les contrôles de vue (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Élément ScriptBlock pour SelectionCondition pour les contrôles de vue (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Élément TypeName pour SelectionCondition pour les contrôles de vue (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
