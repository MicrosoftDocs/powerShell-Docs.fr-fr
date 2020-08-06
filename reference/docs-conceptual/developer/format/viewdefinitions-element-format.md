---
title: Élément ViewDefinitions (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772482"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions, élément (Format)

Définit les vues utilisées pour afficher des objets .NET. Ces vues peuvent afficher les propriétés et les valeurs de script d’un objet dans un format de tableau, un format de liste, un format étendu et un format de contrôle personnalisé.

Élément de configuration (format) ViewDefinitions (format XML)

## <a name="syntax"></a>Syntaxe

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ViewDefinitions` élément. Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme et ils peuvent être ajoutés dans n’importe quel ordre.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Configuration, élément (Format)](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants des différents types d’affichages, consultez les rubriques suivantes :

- [Création d’une vue de table](./creating-a-table-view.md)

- [Création d’une vue de liste](./creating-a-list-view.md)

- [Création d’une vue large](./creating-a-wide-view.md)

- [Contrôles personnalisés](./creating-custom-controls.md)

## <a name="example"></a>Exemple

Cet exemple montre un `ViewDefinitions` élément qui contient les éléments parents d’une vue de table et d’une vue liste.

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

[Configuration, élément (Format)](./configuration-element-format.md)

[View, élément (Format)](./view-element-format.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Contrôles personnalisés](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
