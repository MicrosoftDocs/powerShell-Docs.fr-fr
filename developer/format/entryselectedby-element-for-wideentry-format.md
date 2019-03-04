---
title: Élément EntrySelectedBy pour WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854975"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy, élément pour WideEntry (Format)

Définit les types .NET qui utilisent cette définition de l’affichage plus large ou la condition qui doit exister pour cette définition à utiliser.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément de configuration pour WideEntry (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
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
|[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition d’affichage plus large à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition d’affichage plus large.|
|[Élément TypeName pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition d’affichage plus large.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de l’affichage plus large.|

## <a name="remarks"></a>Remarques

Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une définition d’affichage plus large. Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou la valeur de script `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Élément WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Définition des Conditions pour l’affichage des données](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
