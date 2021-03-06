---
ms.date: 09/13/2016
ms.topic: reference
title: ColumnNumber, élément pour WideControl (Format)
description: ColumnNumber, élément pour WideControl (Format)
ms.openlocfilehash: 1ddbbfbd5b53065afcc6c1326d6abf1fadedc67b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648389"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber, élément pour WideControl (Format)

Spécifie le nombre de colonnes affichées dans la vue étendue.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément WideControl (format) élément ColumnNumber pour WideControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ColumnNumber` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[WideControl, élément (Format)](./widecontrol-element-format.md)|Définit un format de liste larges (à valeur unique) pour la vue.|

## <a name="text-value"></a>Valeur texte

Spécifiez une valeur entière positive.

## <a name="remarks"></a>Notes

Lorsque vous définissez une vue étendue, vous pouvez ajouter l' `AutoSize` élément ou l' `ColumnNumber` élément, mais vous ne pouvez pas ajouter les deux.

Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

Pour obtenir un exemple de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[AutoSize, élément de WideControl (format)](./autosize-element-for-widecontrol-format.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Vue large (De base)](./wide-view-basic.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
