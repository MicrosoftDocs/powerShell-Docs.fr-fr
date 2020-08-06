---
title: Élément TypeName pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780265"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>TypeName, élément pour EntrySelectedBy pour GroupBy (Format)

Spécifie un type .NET qui utilise cette définition du contrôle personnalisé. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour l’élément GroupBy (format) CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour l’élément GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.

Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Création de contrôles personnalisés](./creating-custom-controls.md)

[EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
