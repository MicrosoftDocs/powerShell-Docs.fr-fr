---
title: Afficher l’élément (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083720"
---
# <a name="view-element-format"></a>View, élément (Format)

Définit une vue qui affiche un ou plusieurs objets .NET. Il n’existe aucune limite au nombre de vues qui peuvent être définies dans un fichier de mise en forme.

Élément d’affichage de configuration (Format) d’élément ViewDefinitions, élément (Format) (Format)

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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `View` élément. Vous devez spécifier un seul et unique les enfants d’éléments de contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue. Définition des contrôles personnalisés, comment regrouper des objets et en spécifiant si la vue est hors-bande sont facultatifs.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément de Controls pour la vue (Format)](./controls-element-for-view-format.md)|Élément facultatif.<br /><br /> Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.|
|[Élément CustomControl (Format)](./customcontrol-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit un format de contrôle personnalisé pour la vue.|
|[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)|Élément facultatif.<br /><br /> Définit comment les membres des objets .NET sont regroupés.|
|[Élément objet ListControl (Format)](./listcontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de liste pour la vue.|
|[Name, élément pour afficher (Format)](./name-element-for-view-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer la vue.|
|[Élément de table (Format)](./tablecontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de table pour la vue.|
|[Élément ViewSelectedBy de vue (Format)](./viewselectedby-element-format.md)|Élément requis.<br /><br /> Définit les objets .NET qui affiche cette vue.|
|[Élément WideControl (Format)](./widecontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un (valeur unique) à l’échelle du format de liste pour la vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Définit les vues utilisées pour afficher les objets.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants de différentes vues et des contrôles personnalisés, consultez les rubriques suivantes :

- [Composants de vue de table](./creating-a-table-view.md)

- [Composants de vue de liste](./creating-a-list-view.md)

- [Composants d’affichage plus large](./creating-a-wide-view.md)

- [Contrôles personnalisés](./creating-custom-controls.md)

## <a name="example"></a>Exemple

Cet exemple montre un `View` élément qui définit un mode d’affichage pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.

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

[Élément ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Name, élément pour afficher (Format)](./name-element-for-view-format.md)

[Élément ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Élément de Controls pour la vue (Format)](./controls-element-for-view-format.md)

[Élément GroupBy de vue (Format)](./groupby-element-for-view-format.md)

[Élément de table (Format)](./tablecontrol-element-format.md)

[Élément objet ListControl (Format)](./listcontrol-element-format.md)

[Élément WideControl (Format)](./widecontrol-element-format.md)

[Élément CustomControl (Format)](./customcontrol-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
