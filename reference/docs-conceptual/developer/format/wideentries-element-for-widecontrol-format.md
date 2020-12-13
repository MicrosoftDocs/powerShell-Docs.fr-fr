---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntries, élément pour WideControl (Format)
description: WideEntries, élément pour WideControl (Format)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651231"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries, élément pour WideControl (Format)

Fournit les définitions de la vue étendue. La vue étendue doit spécifier une ou plusieurs définitions.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) WideEntries, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideEntries` élément. Au moins un élément enfant doit être spécifié.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de la vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[WideControl, élément (Format)](./widecontrol-element-format.md)|Définit un format de liste larges (à valeur unique) pour la vue.|

## <a name="remarks"></a>Notes

Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet. Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideEntries` élément qui définit un `WideEntry` élément unique. L' `WideEntry` élément contient un `WideItem` élément unique qui définit la valeur de la propriété ou du script qui est affichée dans la vue.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue large](./creating-a-wide-view.md)

[WideControl, élément (Format)](./widecontrol-element-format.md)

[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
