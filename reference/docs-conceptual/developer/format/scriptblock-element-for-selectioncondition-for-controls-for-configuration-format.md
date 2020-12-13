---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)
description: ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: 42e9d2b00f7690e46242b2c4602245e4bf391bbf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664959"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) CustomEntry, élément de CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) élément SelectionCondition pour EntrySelectedBy pour les contrôles pour la configuration (format) élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Définit une condition qui doit exister pour que la définition de contrôle commun soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
