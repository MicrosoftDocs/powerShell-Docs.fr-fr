---
title: Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064133"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)

Définit la condition qui doit exister pour développer la collection d’objets de cette définition.

Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément d’élément de SelectionCondition EnumerableExpansion (Format) pour EntrySelectedBy pour EnumerableExpansion (Format)

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

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionCondition` élément. Vous devez spécifier un seul `PropertyName` ou `ScriptBlock` élément. Le `SelectionSetName` et `TypeName` éléments sont facultatifs. Vous pouvez spécifier une de des deux éléments.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie le jeu des types .NET qui déclenche la condition.|
|[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Définit les objets de collection .NET sont développées par cette définition.|

## <a name="remarks"></a>Remarques

Chaque définition doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour les données de Diplaying](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
