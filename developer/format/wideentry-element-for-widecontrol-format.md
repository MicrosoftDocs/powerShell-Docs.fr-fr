---
title: Élément WideEntry pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083669"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry, élément pour WideControl (Format)

Fournit une définition de l’affichage plus large.

Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) WideControl, élément (Format) WideEntries, élément (Format) WideEntry élément de configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `WideEntry` élément. Vous devez spécifier un seul `WideItem` élément enfant.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition de l’entrée large ou la condition qui doit exister pour cette définition à utiliser.|
|[Élément WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou un script dont la valeur est affichée.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Fournit les définitions de l’affichage plus large.|

## <a name="remarks"></a>Remarques

Un affichage plus large est un format de liste qui affiche une valeur de propriété unique ou une valeur de script pour chaque objet. Contrairement à d’autres types de vues, vous pouvez spécifier qu’un seul élément pour chaque définition de la vue. Pour plus d’informations sur les autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideEntry` élément qui définit un seul `WideItem` élément. Le `WideItem` élément définit la propriété dont la valeur est affichée dans la vue.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Élément SelectionCondition pour WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Élément TypeName pour WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Élément WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Élément WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
