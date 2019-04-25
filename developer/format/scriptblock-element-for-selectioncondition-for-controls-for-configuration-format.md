---
title: Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064422"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition Configuration (Format) pour EntrySelectedBy pour les contrôles de Configuration (Format) Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Définit une condition qui doit exister pour la définition du contrôle commun à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarques

La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
