---
title: Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064660"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et l’entrée de table est utilisée.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy élément de configuration pour TableRowEntry (Format) Élément SelectionCondition pour EntrySelectedBy d’élément de PropertyName TableRowEntry (Format) pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Définit la condition qui doit exister pour cette entrée de table à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de propriété .NET.

## <a name="remarks"></a>Remarques

La condition de sélection doit spécifier nom d’au moins une propriété ou un bloc de script, mais ne peut pas spécifier à la fois. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
