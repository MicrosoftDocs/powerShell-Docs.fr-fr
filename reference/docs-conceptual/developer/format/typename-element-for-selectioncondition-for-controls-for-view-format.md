---
title: Élément TypeName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4795c3af40cf60fb8e71185feced18c192b3a0aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780047"
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
