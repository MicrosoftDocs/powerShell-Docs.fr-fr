---
title: Élément PropertyName pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855735"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName, élément pour ListItem pour ListControl (Format)

Spécifie la propriété .NET dont la valeur est affichée dans la liste.

Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) ListItems, élément (Format) élément ListItem (Format) PropertyName élément pour ListItem (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans la ligne de la vue liste.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Remarques

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément.

Outre l’affichage de la valeur de propriété, vous pouvez également spécifier une étiquette pour la valeur ou une chaîne de format qui peut être utilisée pour modifier l’affichage de la valeur. Pour plus d’informations sur la spécification des données dans un affichage de liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier l’étiquette et la propriété dont la valeur est affichée.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Voir aussi

[Élément ScriptBlock pour ListItem pour un objet ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Élément ListItem pour ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
