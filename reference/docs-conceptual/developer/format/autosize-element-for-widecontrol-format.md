---
title: AutoSize, élément de WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 64e62142738916978b37eb1cd3a73536b0447099
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783872"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize, élément pour WideControl (Format)

Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) élément WideControl (format) élément AutoSize pour WideControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `AutoSize` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[WideControl, élément (Format)](./widecontrol-element-format.md)|Définit un format de liste larges (à valeur unique) pour la vue.|

## <a name="remarks"></a>Notes

Lorsque vous définissez une vue étendue, vous pouvez ajouter l' `AutoSize` élément ou l’élément [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) , mais vous ne pouvez pas ajouter les deux.

Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

Pour obtenir un exemple de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[ColumnNumber, élément pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Création d’une vue large](./creating-a-wide-view.md)

[WideControl, élément (Format)](./widecontrol-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
