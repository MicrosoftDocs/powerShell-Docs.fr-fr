---
title: Élément TypeName pour EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9af443067467f590df824b28636f57b807a4fc94
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780183"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName, élément pour EntrySelectedBy pour WideEntry (Format)

Spécifie un type .NET pour la définition. La définition est utilisée chaque fois que cet objet est affiché.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément TypeName pour WideEntry (format)

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
|[EntrySelectedBy, élément pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

Chaque entrée à grande largeur doit spécifier un ou plusieurs types .NET, un jeu de sélection ou la condition de sélection qui doit exister pour la définition à utiliser.

Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="see-also"></a>Voir aussi

[Création d’une vue large](./creating-a-wide-view.md)

[EntrySelectedBy, élément pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
