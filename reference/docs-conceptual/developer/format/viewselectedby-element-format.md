---
title: Élément ViewSelectedBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367968"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ViewSelectedBy`. Cet élément doit contenir au moins un `TypeName` ou un élément enfant `SelectionSetName`. Il n’existe aucune limite quant au nombre d’éléments enfants qui peuvent être spécifiés et dont l’ordre est significatif.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément TypeName pour ViewSelectedBy (format)](./typename-element-for-viewselectedby-format.md)|Élément facultatif.<br /><br /> Spécifie un objet .NET qui est affiché par la vue.|
|[Élément SelectionSetName pour ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md)|Élément facultatif.<br /><br /> Spécifie un jeu d’objets .NET qui sont affichés par la vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (format)](./view-element-format.md)|Définit une vue qui affiche un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarks

Pour plus d’informations sur l’utilisation de cet élément dans différents affichages, consultez [composants de vue de table](./creating-a-table-view.md), composants de vue de [liste](./creating-a-list-view.md), composants de [vue larges](./creating-a-wide-view.md)et [composants de contrôle personnalisé](./creating-custom-controls.md).

L’élément `SelectionSetName` est utilisé lorsque le fichier de mise en forme définit un ensemble d’objets qui sont affichés par plusieurs vues. Pour plus d’informations sur la façon dont les jeux de sélection sont définis et référencés, consultez [définition de jeux d’objets](./defining-selection-sets.md).

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

[Création d’un affichage de liste](./creating-a-list-view.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Définition des jeux de sélection](./defining-selection-sets.md)

[Élément SelectionSetName pour ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName, élément (format)](./typename-element-for-viewselectedby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
