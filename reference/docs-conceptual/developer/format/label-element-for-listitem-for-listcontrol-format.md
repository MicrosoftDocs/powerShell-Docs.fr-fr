---
title: Élément label pour ListItem pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362888"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label, élément pour ListItem pour ListControl (Format)

Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément pour ListControl (format) ListItems pour l’élément ListEntry pour ListControl ( Format) élément ListItem de ListItems pour ListControl (format) élément label pour ListItem pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Label`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem pour ListItems pour ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur texte

Spécifiez l’étiquette à afficher à gauche de la valeur de la propriété ou du script.

## <a name="remarks"></a>Remarks

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

[Création d’un affichage de liste](./creating-a-list-view.md)

[ListItem, élément (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
