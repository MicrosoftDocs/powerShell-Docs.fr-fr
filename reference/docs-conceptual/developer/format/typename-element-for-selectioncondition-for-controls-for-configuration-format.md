---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)
description: TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: fddb8ddbac7c9292a05cadfa31f98db6439a557d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659675"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)

Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles de configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) SelectionCondition élément pour EntrySelectedBy pour CustomEntry pour la configuration (format) élément TypeName pour SelectionCondition pour les contrôles de configuration (format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry pour la configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry pour la configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
