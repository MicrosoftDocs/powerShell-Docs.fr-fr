---
ms.date: 09/13/2016
ms.topic: reference
title: Name, élément pour View (Format)
description: Name, élément pour View (Format)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666453"
---
# <a name="name-element-for-view-format"></a>Name, élément pour View (Format)

Spécifie le nom utilisé pour identifier la vue.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément Name (format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément. Un seul `Name` élément est autorisé pour chaque vue.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets .NET.|

## <a name="text-value"></a>Valeur texte

Spécifiez un nom convivial unique pour la vue. Ce nom peut inclure une référence au type de la vue (par exemple, une vue de table ou une vue Liste), l’objet ou l’ensemble d’objets qui utilisent la vue, la commande qui retourne les objets ou une combinaison de ceux-ci.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les différents types d’affichages, consultez les rubriques suivantes : [vue table](./creating-a-table-view.md), [mode liste](./creating-a-list-view.md), [vue étendue](./creating-a-wide-view.md)et [vue personnalisée](./creating-custom-controls.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `View` élément qui définit un affichage de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . Le nom de la vue est « service ».

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[View, élément (Format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
