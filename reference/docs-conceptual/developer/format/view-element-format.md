---
ms.date: 09/13/2016
ms.topic: reference
title: View, élément (Format)
description: View, élément (Format)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649732"
---
# <a name="view-element-format"></a>View, élément (Format)

Définit une vue qui affiche un ou plusieurs objets .NET. Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme.

Élément de configuration (format) élément ViewDefinitions (format), élément de vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `View` élément. Vous devez spécifier un et un seul des éléments enfants du contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue. La définition de contrôles personnalisés, la façon de regrouper des objets et la spécification de si la vue est hors bande sont facultatives.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Controls, élément pour View (Format)](./controls-element-for-view-format.md)|Élément facultatif.<br /><br /> Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.|
|[CustomControl, élément (format)](./customcontrol-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit un format de contrôle personnalisé pour la vue.|
|[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)|Élément facultatif.<br /><br /> Définit le mode de regroupement des membres des objets .NET.|
|[ListControl, élément (Format)](./listcontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de liste pour la vue.|
|[Name, élément pour View (Format)](./name-element-for-view-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer la vue.|
|[TableControl, élément (Format)](./tablecontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de tableau pour la vue.|
|[Élément ViewSelectedBy pour View (format)](./viewselectedby-element-format.md)|Élément requis.<br /><br /> Définit les objets .NET que cet affichage affiche.|
|[WideControl, élément (Format)](./widecontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de liste larges (à valeur unique) pour la vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ViewDefinitions, élément (Format)](./viewdefinitions-element-format.md)|Définit les vues utilisées pour afficher des objets.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants de différents affichages et contrôles personnalisés, consultez les rubriques suivantes :

- [Composants de la vue table](./creating-a-table-view.md)

- [Composants de la vue Liste](./creating-a-list-view.md)

- [Composants de vue larges](./creating-a-wide-view.md)

- [Contrôles personnalisés](./creating-custom-controls.md)

## <a name="example"></a>Exemple

Cet exemple montre un `View` élément qui définit un affichage de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Voir aussi

[ViewDefinitions, élément (Format)](./viewdefinitions-element-format.md)

[Name, élément pour View (Format)](./name-element-for-view-format.md)

[ViewSelectedBy, élément (Format)](./viewselectedby-element-format.md)

[Controls, élément pour View (Format)](./controls-element-for-view-format.md)

[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)

[TableControl, élément (Format)](./tablecontrol-element-format.md)

[ListControl, élément (Format)](./listcontrol-element-format.md)

[WideControl, élément (Format)](./widecontrol-element-format.md)

[CustomControl, élément (format)](./customcontrol-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
