---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)
description: TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645744"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)

Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle personnalisé. Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une définition.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour l’élément (format) TypeName pour EntrySelectedBy pour la vue (format)

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
|[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisée ou la condition qui doit exister pour que cette définition soit utilisée.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

Chaque définition d’affichage de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.

Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
