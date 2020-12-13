---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy, élément (Format)
description: ViewSelectedBy, élément (Format)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667706"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy, élément (Format)

Définit les objets .NET affichés par la vue. Chaque vue doit spécifier au moins un objet .NET.

Élément ViewDefinitions (format), élément de vue (format) élément ViewSelectedBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ViewSelectedBy` élément. Cet élément doit contenir au moins un `TypeName` `SelectionSetName` élément enfant ou. Il n’existe aucune limite quant au nombre d’éléments enfants qui peuvent être spécifiés et dont l’ordre est significatif.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[TypeName, élément pour ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Élément facultatif.<br /><br /> Spécifie un objet .NET qui est affiché par la vue.|
|[SelectionSetName, élément pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Élément facultatif.<br /><br /> Spécifie un jeu d’objets .NET qui sont affichés par la vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui affiche un ou plusieurs objets .NET.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur l’utilisation de cet élément dans différents affichages, consultez [composants de vue de table](./creating-a-table-view.md), composants de vue de [liste](./creating-a-list-view.md), composants de [vue larges](./creating-a-wide-view.md)et [composants de contrôle personnalisé](./creating-custom-controls.md).

L' `SelectionSetName` élément est utilisé lorsque le fichier de mise en forme définit un ensemble d’objets qui sont affichés par plusieurs vues. Pour plus d’informations sur la façon dont les jeux de sélection sont définis et référencés, consultez [définition de jeux d’objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) pour un affichage de liste. Le même schéma est utilisé pour les vues de table, larges et personnalisées.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Définition de jeux de sélections](./defining-selection-sets.md)

[SelectionSetName, élément pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName, élément (format)](./typename-element-for-viewselectedby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
