---
title: Élément EntrySelectedBy pour ListEntry pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363828"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy, élément pour ListEntry pour ListControl (Format)

Définit les types .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée. Dans la plupart des cas, une seule définition est nécessaire pour une vue liste. Toutefois, vous pouvez fournir plusieurs définitions pour le mode liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément pour ListEntry pour ListControl (format) EntrySelectedBy, élément de ListEntry pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que cette définition de vue de liste soit utilisée.|
|[Élément SelectionSetName pour EntrySelectedBy pour ListControl (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de vue liste.|
|[Élément TypeName pour EntrySelectedBy pour ListControl (format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListEntry pour ListControl (format)](./listentry-element-for-listcontrol-format.md)|Définit le mode d’affichage des lignes de la liste.|

## <a name="remarks"></a>Remarks

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue de liste. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true`. Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir les objets pour une vue liste à l’aide de leur nom de type .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Voir aussi

[Élément ListEntry pour ListControl (format)](./listentry-element-for-listcontrol-format.md)

[Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Élément SelectionSetName pour EntrySelectedBy pour ListControl (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Élément TypeName pour EntrySelectedBy pour ListControl (format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Création d’un affichage de liste](./creating-a-list-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
