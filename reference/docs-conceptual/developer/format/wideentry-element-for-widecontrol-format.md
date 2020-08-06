---
title: Élément WideEntry pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780013"
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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideEntry` élément. Vous devez spécifier un seul `WideItem` élément enfant.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Élément facultatif.<br /><br /> Définit les types .NET qui utilisent cette définition d’entrée étendue ou la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou le script dont la valeur est affichée.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)|Fournit les définitions de la vue étendue.|

## <a name="remarks"></a>Notes

Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet. Contrairement à d’autres types de vues, vous ne pouvez spécifier qu’un seul élément Item pour chaque définition de vue. Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideEntry` élément qui définit un `WideItem` élément unique. L' `WideItem` élément définit la propriété dont la valeur est affichée dans la vue.

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

[Création d’une vue large](./creating-a-wide-view.md)

[Élément SelectionCondition pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Élément SelectionSetName pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Élément TypeName pour WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)

[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
