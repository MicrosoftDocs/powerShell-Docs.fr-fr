---
title: Élément ColumnNumber pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364218"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber, élément pour WideControl (Format)

Spécifie le nombre de colonnes affichées dans la vue étendue.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément WideControl (format) élément ColumnNumber pour WideControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ColumnNumber`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideControl (format)](./widecontrol-element-format.md)|Définit un format de liste larges (à valeur unique) pour la vue.|

## <a name="text-value"></a>Valeur texte

Spécifiez une valeur entière positive.

## <a name="remarks"></a>Remarks

Lorsque vous définissez une vue étendue, vous pouvez ajouter l’élément `AutoSize` ou l’élément `ColumnNumber`, mais vous ne pouvez pas ajouter les deux.

Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

Pour obtenir un exemple de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[AutoSize, élément de WideControl (format)](./autosize-element-for-widecontrol-format.md)

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Vue étendue (de base)](./wide-view-basic.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
