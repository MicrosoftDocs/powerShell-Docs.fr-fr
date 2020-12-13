---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions, élément (Format)
description: EnumerableExpansions, élément (Format)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660184"
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

Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection. Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface  **System. Collections. ICollection** .

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
