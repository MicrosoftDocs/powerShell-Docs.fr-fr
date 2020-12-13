---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl, élément (Format)
description: WideControl, élément (Format)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651272"
---
# <a name="widecontrol-element-format"></a>WideControl, élément (Format)

Définit un format de liste larges (à valeur unique) pour la vue. Cette vue affiche une valeur de propriété ou une valeur de script unique pour chaque objet.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideControl` élément. Vous ne pouvez pas spécifier les `AutoSize` `ColumnNumber` éléments et en même temps.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[AutoSize, élément pour WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.|
|[ColumnNumber, élément pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de colonnes affichées dans la vue étendue.|
|[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)|Élément requis.<br /><br /> Fournit les définitions de la vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

## <a name="remarks"></a>Notes

Lorsque vous définissez une vue étendue, vous pouvez ajouter l' `AutoSize` élément ou le, `ColumnNumber` mais vous ne pouvez pas ajouter les deux.

Dans la plupart des cas, une seule définition est requise pour chaque vue étendue, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET. Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.

Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideControl` élément utilisé pour afficher une propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[AutoSize, élément de WideControl (format)](./autosize-element-for-widecontrol-format.md)

[ColumnNumber, élément pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[View, élément (Format)](./view-element-format.md)

[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)

[Vue large (De base)](./wide-view-basic.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
