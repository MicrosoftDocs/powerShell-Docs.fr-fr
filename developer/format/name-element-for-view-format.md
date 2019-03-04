---
title: Nom d’élément de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859505"
---
# <a name="name-element-for-view-format"></a>Name, élément pour View (Format)

Spécifie le nom qui est utilisé pour identifier la vue.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) nom élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Name` élément. Seul `Name` l’élément est autorisé pour chaque vue.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou plusieurs objets .NET.|

## <a name="text-value"></a>Valeur de texte

Spécifiez un nom convivial unique pour la vue. Ce nom peut inclure une référence au type de la vue (par exemple, un affichage tableau ou liste), objet ou les objets utiliser la vue, quelle commande retourne les objets, ou une combinaison de ces éléments.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les différents types de vues, consultez les rubriques suivantes : [Affichage tableau](./creating-a-table-view.md), [mode liste](./creating-a-list-view.md), [Affichage large](./creating-a-wide-view.md), et [affichage personnalisé](./creating-custom-controls.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `View` élément qui définit un mode d’affichage pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet. Le nom de la vue est « service ».

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

[Création d’une vue liste](./creating-a-list-view.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Élément d’affichage (Format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
