---
title: PropertyName, élément de SelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: aa3955b84b8de9901f394e8108f31440fcb6c942
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780795"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour l’élément View (format) CustomItem pour CustomEntry pour CustomControl pour View (format) EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (format) SelectionCondition element pour EntrySelectedBy pour CustomControl pour l’élément View (format) PropertyName pour SelectionCondition pour CustomControl pour View (format)

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
|[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom de la propriété .NET.

## <a name="remarks"></a>Notes

La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux. Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
