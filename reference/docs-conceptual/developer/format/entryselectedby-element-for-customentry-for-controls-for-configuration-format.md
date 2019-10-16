---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368768"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)

Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que la définition de contrôle commun soit utilisée.|
|[Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle commun.|
|[Élément TypeName pour EntrySelectedBy pour les contrôles de configuration (format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition du contrôle commun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour les contrôles de configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit une définition du contrôle commun.|

## <a name="remarks"></a>Remarks

Au minimum, chaque définition doit avoir au moins un type .NET, un jeu de sélection ou une condition de sélection spécifiés. Il n’existe pas de limite maximale pour le nombre de types, de jeux de sélection ou de conditions de sélection que vous pouvez spécifier.

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Élément CustomEntry pour CustomControl pour les contrôles de configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Élément TypeName pour EntrySelectedBy pour les contrôles de configuration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
