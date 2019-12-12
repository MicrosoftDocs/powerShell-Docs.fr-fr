---
title: PropertyName, élément de GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362518"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName, élément pour GroupBy (Format)

Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) PropertyName pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)|Définit le mode d’affichage d’un groupe d’objets .NET.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété .NET.

## <a name="remarks"></a>Remarks

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

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

[Élément ScriptBlock pour GroupBy (format)](./scriptblock-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
