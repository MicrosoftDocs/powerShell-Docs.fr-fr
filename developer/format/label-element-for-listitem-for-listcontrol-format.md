---
title: L’étiquette d’élément pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854775"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label, élément pour ListItem pour ListControl (Format)

Spécifie l’étiquette qui s’affiche à gauche de la valeur de propriété ou un script dans la ligne.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour ListItems ListControl (Format) pour ListEntry pour l’élément de l’objet ListControl ( Format), élément ListItem pour ListItems pour l’élément Label ListControl (Format) ListItem pour un objet ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Label` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem pour ListItems pour ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur de texte

Spécifiez l’étiquette pour être affichée à gauche de la valeur de propriété ou un script.

## <a name="remarks"></a>Remarques

Si une étiquette n’est pas spécifiée, le nom de la propriété ou le script s’affiche. Pour plus d’informations sur l’utilisation des étiquettes dans un affichage de liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter une étiquette à une ligne.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Élément ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
