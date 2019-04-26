---
title: Élément SelectionCondition pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063980"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition, élément pour EntrySelectedBy pour WideControl (Format)

Définit la condition qui doit exister pour cette définition à utiliser. Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de l’entrée de large.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy pour WideEntry (Format)

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
|[Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le bloc de script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Élément facultatif.<br /><br /> Spécifie le jeu des types .NET qui déclenche la condition.|
|[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Définit les types .NET qui utilisent cette entrée large ou la condition qui doit exister pour cette entrée à utiliser.|

## <a name="remarks"></a>Remarques

Chaque entrée large doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.

Lorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément EntrySelectedBy pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
