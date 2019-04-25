---
title: Élément TypeName pour SelectionCondition pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083771"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a>TypeName, élément pour SelectionCondition pour GroupBy (Format)

Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy d’élément de TypeName GroupBy (Format) pour SelectionCondition pour GroupBy (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Définit une condition qui doit exister pour la définition du contrôle à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarques

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le `SelectionSetName` élément. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
