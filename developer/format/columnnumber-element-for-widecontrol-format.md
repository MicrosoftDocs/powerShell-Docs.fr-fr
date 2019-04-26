---
title: Élément ColumnNumber pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066904"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber, élément pour WideControl (Format)

Spécifie le nombre de colonnes affichées dans l’affichage plus large.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) ColumnNumber élément de configuration pour WideControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ColumnNumber` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideControl (Format)](./widecontrol-element-format.md)|Définit un (valeur unique) à l’échelle du format de liste pour la vue.|

## <a name="text-value"></a>Valeur de texte

Spécifiez une valeur entière positive.

## <a name="remarks"></a>Remarques

Lorsque vous définissez un affichage plus large, vous pouvez ajouter la `AutoSize` élément ou `ColumnNumber` élément, mais vous ne pouvez pas ajouter à la fois.

Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

Pour obtenir un exemple d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Élément AutoSize pour WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Affichage plus large (Basic)](./wide-view-basic.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
