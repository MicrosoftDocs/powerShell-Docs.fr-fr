---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour GroupBy (Format)
description: PropertyName, élément pour GroupBy (Format)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666142"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName, élément pour GroupBy (Format)

Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) PropertyName pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)|Définit le mode d’affichage d’un groupe d’objets .NET.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET.

## <a name="remarks"></a>Notes

Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de cette propriété change.

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-groupby-format.md) pour démarrer un nouveau groupe.

## <a name="example"></a>Exemple

L’exemple suivant montre comment démarrer un nouveau groupe lorsque la valeur d’une propriété change.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Voir aussi

[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)

[ScriptBlock, élément pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
