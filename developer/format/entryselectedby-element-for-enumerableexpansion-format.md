---
title: Élément EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066207"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy, élément pour EnumerableExpansion (Format)

Définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour cette définition à utiliser.

Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément pour EnumerableExpansion (Format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour développer la collection d’objets de cette définition.|
|[Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de la façon dont les objets de collection sont développés.|
|[Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de la façon dont les objets de collection sont développés.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Définit des collection .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.|

## <a name="remarks"></a>Remarques

Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une entrée de définition. Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou un script `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Définition des Conditions pour l’affichage des données](./defining-conditions-for-displaying-data.md)

[Élément EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
