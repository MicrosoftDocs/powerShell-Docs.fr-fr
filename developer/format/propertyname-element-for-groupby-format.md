---
title: Élément PropertyName pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075866"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName, élément pour GroupBy (Format)

Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément d’affichage (Format) PropertyName élément pour GroupBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)|Définit la façon dont un groupe d’objets .NET est affiché.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de propriété .NET.

## <a name="remarks"></a>Remarques

Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de cette propriété change.

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-groupby-format.md) élément pour démarrer un nouveau groupe.

## <a name="example"></a>Exemple

L’exemple suivant montre comment démarrer un nouveau groupe lorsque la valeur d’une propriété change.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Pour obtenir un exemple d’un fichier de mise en forme complète qui inclut cet élément, consultez [affichage plus large (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Voir aussi

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Élément ScriptBlock pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
