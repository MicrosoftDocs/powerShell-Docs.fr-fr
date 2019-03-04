---
title: Élément AutoSize pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857085"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize, élément pour WideControl (Format)

Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) Autosize élément de configuration pour WideControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `AutoSize` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideControl (Format)](./widecontrol-element-format.md)|Définit un (valeur unique) à l’échelle du format de liste pour la vue.|

## <a name="remarks"></a>Remarques

Lorsque vous définissez un affichage plus large, vous pouvez ajouter la `AutoSize` élément ou le [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) élément, mais vous ne pouvez pas ajouter à la fois.

Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

Pour obtenir un exemple d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Élément ColumnNumber pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Élément WideControl (Format)](./widecontrol-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
