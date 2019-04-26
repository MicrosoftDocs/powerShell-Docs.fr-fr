---
title: Élément EntrySelectedBy pour ListEntry pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066190"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy, élément pour ListEntry pour ListControl (Format)

Définit les types .NET qui utilisent cette définition de la vue liste ou la condition qui doit exister pour cette définition à utiliser. Dans la plupart des cas qu’une seule définition est nécessaire pour un affichage de liste. Toutefois, vous pouvez fournir plusieurs définitions pour l’affichage de liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour ListEntry d’élément de EntrySelectedBy ListControl (Format) pour ListEntry pour ListControl (Format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cette définition de vue de liste à utiliser.|
|[Élément SelectionSetName pour EntrySelectedBy pour ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de la vue liste.|
|[Élément TypeName pour EntrySelectedBy pour ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListEntry pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Définit comment les lignes de la liste sont affichées.|

## <a name="remarks"></a>Remarques

Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une définition de vue de liste. Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou un script `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir les objets pour un affichage de liste à l’aide de leur nom de type .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Voir aussi

[Élément ListEntry pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
