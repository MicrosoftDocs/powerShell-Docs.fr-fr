---
title: Élément TypeName pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855725"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName, élément pour EntrySelectedBy pour TableControl (Format)

Spécifie un type .NET qui utilise cette entrée de la vue de table. Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une entrée de table.

Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy, élément (Format) TypeName élément de configuration pour EntrySelectedBy pour TableRowEntry (Format)

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
|[Élément EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour cette entrée à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom du type .NET.

## <a name="remarks"></a>Remarques

Chaque entrée de liste doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
