---
ms.date: 09/13/2016
ms.topic: reference
title: Label, élément pour GroupBy (Format)
description: Label, élément pour GroupBy (Format)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649796"
---
# <a name="label-element-for-groupby-format"></a>Label, élément pour GroupBy (Format)

Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément label View (format) pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<Label>DisplayedLabel</Label>
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
|[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)|Définit le mode d’affichage d’un nouveau groupe d’objets.|

## <a name="text-value"></a>Valeur texte

Spécifiez le texte qui s’affiche chaque fois que Windows PowerShell rencontre une nouvelle propriété ou une nouvelle valeur de script.

## <a name="remarks"></a>Notes

En plus du texte spécifié par cet élément, Windows PowerShell affiche la nouvelle valeur qui démarre le groupe et ajoute une ligne vide avant et après le groupe.

## <a name="example"></a>Exemple

L’exemple suivant montre l’étiquette d’un nouveau groupe. L’étiquette affichée devrait ressembler à ceci : `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Voir aussi

[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
