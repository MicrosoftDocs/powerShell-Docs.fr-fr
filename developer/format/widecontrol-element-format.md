---
title: Élément WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859825"
---
# <a name="widecontrol-element-format"></a>WideControl, élément (Format)

Définit un (valeur unique) à l’échelle du format de liste pour la vue. Cette vue affiche une valeur de propriété unique ou une valeur de script pour chaque objet.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) WideControl élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `WideControl` élément. Vous ne pouvez pas spécifier le `AutoSize` et `ColumnNumber` éléments en même temps.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément AutoSize pour WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.|
|[Élément ColumnNumber pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de colonnes affichées dans l’affichage plus large.|
|[Élément WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Élément requis.<br /><br /> Fournit les définitions de l’affichage plus large.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarques

Lorsque vous définissez un affichage plus large, vous pouvez ajouter la `AutoSize` élément ou le `ColumnNumber` , mais vous ne pouvez pas ajouter à la fois.

Dans la plupart des cas, qu’une seule définition est requise pour chaque affichage plus large, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher les différents objets .NET. Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.

Pour plus d’informations sur les composants d’un affichage plus large, consultez [les composants de vue large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideControl` élément qui est utilisé pour afficher une propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

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

Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Élément AutoSize pour WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Élément ColumnNumber pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Élément d’affichage (Format)](./view-element-format.md)

[Élément WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Affichage plus large (Basic)](./wide-view-basic.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
