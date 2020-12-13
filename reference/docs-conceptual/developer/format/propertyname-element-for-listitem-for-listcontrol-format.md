---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ListItem pour ListControl (Format)
description: PropertyName, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665972"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName, élément pour ListItem pour ListControl (Format)

Spécifie la propriété .NET dont la valeur est affichée dans la liste.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) ListItems élément (format) élément ListItem (format) NomPropriété, élément pour ListItem (format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListItem, élément (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans la ligne de la vue liste.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Notes

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) .

Outre l’affichage de la valeur de propriété, vous pouvez également spécifier une étiquette pour la valeur ou une chaîne de format qui peut être utilisée pour modifier l’affichage de la valeur. Pour plus d’informations sur la spécification des données dans un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier l’étiquette et la propriété dont la valeur est affichée.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Voir aussi

[ScriptBlock, élément pour ListItem pour ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[Élément ListItem pour ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
