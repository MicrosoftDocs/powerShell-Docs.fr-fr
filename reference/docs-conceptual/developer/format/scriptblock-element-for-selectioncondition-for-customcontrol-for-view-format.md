---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)
description: ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: 78b977548243b6f3a658f15a0249d8cad12e2f1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664913"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) élément CustomItem pour CustomControl pour la vue (format), élément de CustomEntry pour CustomControl pour la vue (format) élément ScriptBlock pour SelectionCondition pour la vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
