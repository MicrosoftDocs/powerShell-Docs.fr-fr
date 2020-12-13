---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour Controls pour View (Format)
description: TypeName, élément pour SelectionCondition pour Controls pour View (Format)
ms.openlocfilehash: e70fc05667c27fa3b68f3c9a1802c1e3bba8b7ce
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651341"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a>TypeName, élément pour SelectionCondition pour Controls pour View (Format)

Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour l’élément View (format) SelectionCondition pour les contrôles pour l’élément View (format) TypeName pour EntrySelectedBy pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
