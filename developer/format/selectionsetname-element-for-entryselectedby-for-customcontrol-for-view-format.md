---
title: Élément SelectionSetName pour EntrySelectedBy pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855025"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)

Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour EntrySelectedBy de vue (Format) Élément pour CustomEntry pour l’élément d’affichage (Format) de SelectionSetName pour EntrySelectedBy pour CustomEntry (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour cette entrée à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

Chaque entrée de contrôle personnalisé doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.

Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).

Pour plus d’informations sur les composants d’une vue de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Élément EntrySelectedBy pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Affichage de contrôle personnalisé](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
