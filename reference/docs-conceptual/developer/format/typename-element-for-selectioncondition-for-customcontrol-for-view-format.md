---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour CustomControl pour View (Format)
description: TypeName, élément pour SelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: ab02c6921985dbe86e5adcbc6565c76f6617399a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651287"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a>TypeName, élément pour SelectionCondition pour CustomControl pour View (Format)

Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) élément CustomItem pour CustomControl pour la vue (format), élément de CustomEntry pour CustomControl pour la vue (format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
