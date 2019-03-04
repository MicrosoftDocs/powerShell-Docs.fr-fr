---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854145"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)

Définit une condition qui doit exister pour une définition commune de contrôle à utiliser. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour les contrôles pour Élément de CustomEntry de configuration (Format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition Configuration (Format) pour EntrySelectedBy pour CustomEntry pour Configuration (Format)

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
|[Élément PropertyName pour SelectionCondition pour les contrôles de Configuration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le jeu des types .NET qui déclenche la condition.|
|[Élément TypeName pour SelectionCondition pour les contrôles de Configuration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Définit les types .NET qui utilisent cette entrée de la définition du contrôle commun.|

## <a name="remarks"></a>Remarques

Les instructions suivantes doivent être suivies lors de la définition d’une condition de sélection :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour SelectionCondition pour les contrôles de Configuration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Élément SelectionSetName pour SelectionCondition pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Élément TypeName pour SelectionCondition pour les contrôles de Configuration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
