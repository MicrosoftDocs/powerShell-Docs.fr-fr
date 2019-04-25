---
title: Élément ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083822"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy, élément (Format)

Définit les objets .NET qui sont affichés par la vue. Chaque vue doit spécifier au moins un objet .NET.

ViewDefinitions élément (Format) vue (Format) ViewSelectedBy élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ViewSelectedBy` élément. Cet élément doit contenir au moins un `TypeName` ou `SelectionSetName` élément enfant. Il n’existe aucune limite au nombre d’éléments enfants qui peuvent être spécifiées, ni leur ordre n’est significative.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément TypeName pour ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Élément facultatif.<br /><br /> Spécifie un objet .NET qui est affiché par la vue.|
|[Élément SelectionSetName pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble d’objets .NET qui sont affichés par la vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui affiche un ou plusieurs objets .NET.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur la façon dont cet élément est utilisé dans les différentes vues, consultez [les composants de vue de Table](./creating-a-table-view.md), [les composants de vue de liste](./creating-a-list-view.md), [les composants de vue large](./creating-a-wide-view.md)et [Composants de contrôle personnalisé](./creating-custom-controls.md).

Le `SelectionSetName` élément est utilisé lorsque le fichier de mise en forme définit un ensemble d’objets qui sont affichés par plusieurs vues. Pour plus d’informations sur comment les jeux de sélection sont définis et référencés, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet pour un affichage de liste. Le même schéma est utilisé pour les vues table, large et personnalisées.

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

[Création d’une vue liste](./creating-a-list-view.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Définition de jeux de sélection](./defining-selection-sets.md)

[Élément SelectionSetName pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName, élément (Format)](./typename-element-for-viewselectedby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
