---
title: Élément SelectionSetName pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856795"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)

Spécifie un ensemble d’objets .NET pour la définition. La définition est utilisée chaque fois qu’un de ces objets s’affiche.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionSetName WideEntry (Format) pour EntrySelectedBy pour WideEntry (Format)

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
|[Élément EntrySelectedBy pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Définit les types .NET qui utilisent cette entrée large ou la condition qui doit exister pour cette entrée à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

Chaque définition doit spécifier un nom de type, jeu de sélection ou le critère de sélection.

Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition définit des objets pour une vue](./defining-selection-sets.md).

Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Définition de jeux de sélection](./defining-selection-sets.md)

[Élément EntrySelectedBy pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
