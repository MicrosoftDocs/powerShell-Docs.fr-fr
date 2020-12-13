---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour Controls pour View (Format)
description: TypeName, élément pour EntrySelectedBy pour Controls pour View (Format)
ms.openlocfilehash: 03a70b0c6c71910932f1d032c94c602cef8ab964
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647891"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a>TypeName, élément pour EntrySelectedBy pour Controls pour View (Format)

Spécifie un type .NET qui utilise cette définition du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément CustomEntry (format)

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
|[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
