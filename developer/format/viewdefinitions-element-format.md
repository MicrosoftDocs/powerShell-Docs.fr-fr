---
title: Élément ViewDefinitions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083703"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions, élément (Format)

Définit les vues utilisées pour afficher les objets .NET. Ces vues peuvent afficher les propriétés et valeurs de script d’un objet dans un format de table, format de liste, format large et format de contrôle personnalisé.

Élément de configuration (Format) d’élément ViewDefinitions (Format XML)

## <a name="syntax"></a>Syntaxe

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ViewDefinitions` élément. Il n’existe aucune limite au nombre de vues qui peuvent être définies dans un fichier de mise en forme, et ils peuvent être ajoutés dans n’importe quel ordre.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration (Format)](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants des différents types de vues, consultez les rubriques suivantes :

- [Création d’une vue de Table](./creating-a-table-view.md)

- [Création d’une vue liste](./creating-a-list-view.md)

- [Création d’un affichage plus large](./creating-a-wide-view.md)

- [Contrôles personnalisés](./creating-custom-controls.md)

## <a name="example"></a>Exemple

Cet exemple montre un `ViewDefinitions` élément qui contient les éléments parents pour une vue de table et une vue de liste.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Voir aussi

[Élément de configuration (Format)](./configuration-element-format.md)

[Élément d’affichage (Format)](./view-element-format.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Contrôles personnalisés](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
