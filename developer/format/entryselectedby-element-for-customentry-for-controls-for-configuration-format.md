---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066292"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)

Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour ce contrôle à utiliser. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour la définition du contrôle commun à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle commun.|
|[Élément TypeName pour EntrySelectedBy pour les contrôles de Configuration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition du contrôle commun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit une définition du contrôle commun.|

## <a name="remarks"></a>Remarques

Au minimum, chaque définition doit avoir au moins un type .NET, jeu de sélection ou le critère de sélection spécifié. Il n’existe aucune limite maximale pour le nombre de types, des jeux de sélection ou des conditions de sélection que vous pouvez spécifier.

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Élément TypeName pour EntrySelectedBy pour les contrôles de Configuration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
