---
title: Élément PropertyName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 251fc129896cfa4a6255330e23854b014675ac5f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780812"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a>PropertyName, élément pour SelectionCondition pour Controls pour View (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée est utilisée. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour l’élément View (format) SelectionCondition pour les contrôles pour l’élément View (format) PropertyName pour EntrySelectedBy pour les contrôles pour View (format)

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
|[SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET.

## <a name="remarks"></a>Notes

La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
