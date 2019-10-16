---
title: Élément WideEntry pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367898"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry, élément pour WideControl (Format)

Fournit une définition de la vue étendue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format) WideEntries, élément (format) WideEntry, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `WideEntry`. Vous devez spécifier un seul élément enfant `WideItem`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition d’entrée étendue ou la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou le script dont la valeur est affichée.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)|Fournit les définitions de la vue étendue.|

## <a name="remarks"></a>Remarks

Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet. Contrairement à d’autres types de vues, vous ne pouvez spécifier qu’un seul élément Item pour chaque définition de vue. Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un élément `WideEntry` qui définit un seul élément `WideItem`. L’élément `WideItem` définit la propriété dont la valeur est affichée dans la vue.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Élément SelectionCondition pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Élément TypeName pour WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)

[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
