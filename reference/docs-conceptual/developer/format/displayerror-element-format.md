---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError, élément (Format)
description: DisplayError, élément (Format)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649931"
---
# <a name="displayerror-element-format"></a>DisplayError, élément (Format)

Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.

Élément de configuration (format) DefaultSettings, élément (format) DisplayError, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `DisplayError` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[DefaultSettings, élément (Format)](./defaultsettings-element-format.md)|Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|

## <a name="remarks"></a>Notes

Par défaut, lorsqu’une erreur se produit lors d’une tentative d’affichage d’un élément de données, l’emplacement des données est laissé vide. Lorsque cet élément est défini sur true, la chaîne de #ERR s’affiche.

## <a name="see-also"></a>Voir aussi

[DefaultSettings, élément (Format)](./defaultsettings-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
