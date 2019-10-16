---
title: Élément WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367988"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `WideControl`. Vous ne pouvez pas spécifier les éléments `AutoSize` et `ColumnNumber` en même temps.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[AutoSize, élément de WideControl (format)](./autosize-element-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.|
|[Élément ColumnNumber pour WideControl (format)](./columnnumber-element-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre de colonnes affichées dans la vue étendue.|
|[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)|Élément requis.<br /><br /> Fournit les définitions de la vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarks

Lorsque vous définissez une vue étendue, vous pouvez ajouter l’élément `AutoSize` ou la `ColumnNumber`, mais vous ne pouvez pas ajouter les deux.

Dans la plupart des cas, une seule définition est requise pour chaque vue étendue, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET. Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.

Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un élément `WideControl` utilisé pour afficher une propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

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

[Élément ColumnNumber pour WideControl (format)](./columnnumber-element-for-widecontrol-format.md)

[View, élément (format)](./view-element-format.md)

[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md)

[Vue étendue (de base)](./wide-view-basic.md)

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
