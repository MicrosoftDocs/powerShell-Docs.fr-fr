---
title: Élément label pour ListItem pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783634"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label, élément pour ListItem pour ListControl (Format)

Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément pour ListControl (format) ListItems pour l’élément ListControl pour ListControl (format) ListItem, élément de ListItems pour ListControl (format) élément label pour ListItem pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Label` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListItem, élément pour ListItems pour ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur texte

Spécifiez l’étiquette à afficher à gauche de la valeur de la propriété ou du script.

## <a name="remarks"></a>Notes

Si aucune étiquette n’est spécifiée, le nom de la propriété ou du script est affiché. Pour plus d’informations sur l’utilisation des étiquettes dans un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter une étiquette à une ligne.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[ListItem, élément (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
