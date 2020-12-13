---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour View (Format)
description: CustomEntries, élément pour CustomControl pour View (Format)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649972"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries, élément pour CustomControl pour View (Format)

Fournit les définitions de l’affichage de contrôle personnalisé. L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlEntries` élément. Vous devez spécifier un ou plusieurs éléments enfants.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Élément requis.<br /><br /> Fournit une définition de l’affichage de contrôle personnalisé.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément pour View (Format)](./customcontrol-element-for-view-format.md)|Élément requis.<br /><br /> Définit un format de contrôle personnalisé pour la vue.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un `CustomEntry` élément unique. Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[CustomControl, élément pour View (Format)](./customcontrol-element-for-view-format.md)

[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
