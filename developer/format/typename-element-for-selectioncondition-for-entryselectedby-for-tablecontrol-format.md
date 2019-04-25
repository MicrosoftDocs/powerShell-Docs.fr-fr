---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083839"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TypeName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)

Spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, la condition est remplie, et la ligne de table est utilisée.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy élément de configuration pour TableRowEntry (Format) Élément SelectionCondition pour EntrySelectedBy d’élément de TypeName TableRowEntry (Format) pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Définit la condition qui doit exister pour cette ligne de tableau à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarques

La condition de sélection peut spécifier n’importe quel nombre de types .NET ou sélection définit, mais ne peut pas spécifier à la fois. Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
