---
title: View, élément (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361458"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `View`. Vous devez spécifier un et un seul des éléments enfants du contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue. La définition de contrôles personnalisés, la façon de regrouper des objets et la spécification de si la vue est hors bande sont facultatives.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Controls, élément de View (format)](./controls-element-for-view-format.md)|Élément facultatif.<br /><br /> Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.|
|[CustomControl, élément (format)](./customcontrol-element-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit un format de contrôle personnalisé pour la vue.|
|[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)|Élément facultatif.<br /><br /> Définit le mode de regroupement des membres des objets .NET.|
|[Élément ListControl (format)](./listcontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de liste pour la vue.|
|[Élément Name pour View (format)](./name-element-for-view-format.md)|Élément requis.<br /><br /> Spécifie le nom utilisé pour référencer la vue.|
|[Élément table ((format)](./tablecontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de tableau pour la vue.|
|[Élément ViewSelectedBy pour View (format)](./viewselectedby-element-format.md)|Élément requis.<br /><br /> Définit les objets .NET que cet affichage affiche.|
|[Élément WideControl (format)](./widecontrol-element-format.md)|Élément facultatif.<br /><br /> Définit un format de liste larges (à valeur unique) pour la vue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ViewDefinitions (format)](./viewdefinitions-element-format.md)|Définit les vues utilisées pour afficher des objets.|

## <a name="remarks"></a>Remarks

Pour plus d’informations sur les composants de différents affichages et contrôles personnalisés, consultez les rubriques suivantes :

- [Composants de la vue table](./creating-a-table-view.md)

- [Composants de la vue Liste](./creating-a-list-view.md)

- [Composants de vue larges](./creating-a-wide-view.md)

- [Contrôles personnalisés](./creating-custom-controls.md)

## <a name="example"></a>Exemple

Cet exemple montre un élément `View` qui définit une vue de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Élément ViewDefinitions (format)](./viewdefinitions-element-format.md)

[Élément Name pour View (format)](./name-element-for-view-format.md)

[Élément ViewSelectedBy (format)](./viewselectedby-element-format.md)

[Controls, élément de View (format)](./controls-element-for-view-format.md)

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

[Élément table ((format)](./tablecontrol-element-format.md)

[Élément ListControl (format)](./listcontrol-element-format.md)

[Élément WideControl (format)](./widecontrol-element-format.md)

[CustomControl, élément (format)](./customcontrol-element-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
