---
title: Élément EnumerableExpansions (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2b536b1ab9b34b0089d0a38d3c5dc7a937176443
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774012"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions, élément (Format)

Définit la façon dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.

Élément de configuration (format) DefaultSettings, élément (format) EnumerableExpansions, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EnumerableExpansions` élément. Il n’existe aucune limite quant au nombre d’éléments enfants que vous pouvez utiliser.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[EnumerableExpansion, élément (Format)](./enumerableexpansion-element-format.md)|Élément facultatif.<br /><br /> Définit les objets de collection .NET spécifiques qui sont développés lorsqu’ils sont affichés dans une vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[DefaultSettings, élément (Format)](./defaultsettings-element-format.md)|Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|

## <a name="remarks"></a>Notes

Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection. Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
