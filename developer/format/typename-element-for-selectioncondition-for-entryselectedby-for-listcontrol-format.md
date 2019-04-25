---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083856"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)

Spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, l’entrée de liste est utilisée.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour situés d’élément de EntrySelectedBy ListControl (Format) pour ListEntry d’élément de SelectionCondition ListControl (Format) pour EntrySelectedBy d’élément de TypeName ListControl (Format) pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Définit la condition qui doit exister pour cette entrée de liste à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarques

La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les autres composants d’une vue de liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
