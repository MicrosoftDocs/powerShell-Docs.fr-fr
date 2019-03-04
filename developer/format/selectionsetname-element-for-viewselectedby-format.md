---
title: Élément SelectionSetName pour ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858335"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName, élément pour ViewSelectedBy (Format)

Spécifie un ensemble d’objets .NET qui sont affichés par la vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément ViewSelectedBy (Format) SelectionSetName élément de configuration pour ViewSelectedBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Définit les objets .NET qui sont affichés par la vue.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de sélection qui est défini par le `Name` élément pour l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage. Pour plus d’informations sur la définition et référencement des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier une jeu de sélection pour un affichage de liste. Le même schéma est utilisé pour les vues table, large et personnalisées.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Voir aussi

[Définition de jeux de sélection](./defining-selection-sets.md)

[Élément ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
