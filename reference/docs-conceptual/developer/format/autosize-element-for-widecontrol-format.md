---
title: AutoSize, élément de WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369048"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize, élément pour WideControl (Format)

Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) élément WideControl (format) élément AutoSize pour WideControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `AutoSize`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideControl (format)](./widecontrol-element-format.md)|Définit un format de liste larges (à valeur unique) pour la vue.|

## <a name="remarks"></a>Remarks

Lorsque vous définissez une vue étendue, vous pouvez ajouter l’élément `AutoSize` ou l’élément [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) , mais vous ne pouvez pas ajouter les deux.

Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

Pour obtenir un exemple de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Élément ColumnNumber pour WideControl (format)](./columnnumber-element-for-widecontrol-format.md)

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Élément WideControl (format)](./widecontrol-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
