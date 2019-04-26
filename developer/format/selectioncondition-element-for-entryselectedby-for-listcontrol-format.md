---
title: Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064099"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)

Définit la condition qui doit exister pour pouvoir utiliser cette définition de la vue liste. Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de liste.

Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy pour ListEntry (Format)

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
|[Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Élément facultatif.<br /><br /> Spécifie l’ensemble des types .NET qui déclenchent la condition.|
|[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les types .NET qui utilisent cette entrée de table ou de la condition qui doit exister pour cette entrée à utiliser.|

## <a name="remarks"></a>Remarques

LLorsque vous définissez une condition de sélection, les conditions suivantes s’appliquent :

- La condition de sélection doit spécifier un nom d’un propriété minimum ou un bloc de script, mais vous ne pouvez pas spécifier à la fois.

- La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois.

Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur d’autres composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour ListEntry (Format)](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
