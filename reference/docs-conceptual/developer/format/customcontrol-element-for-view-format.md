---
title: CustomControl, élément de View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 660e8fd6531862790a2af7ab27a82e073c230693
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786048"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl, élément pour View (Format)

Définit un format de contrôle personnalisé pour la vue.

Élément de configuration (format) élément ViewDefinitions (format) élément View (format) CustomControl, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControl` élément. Vous devez spécifier un élément enfant.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomEntries, élément pour CustomControl pour View (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Élément requis.<br /><br /> Fournit les définitions de l’affichage de contrôle personnalisé.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, une seule définition est requise pour chaque vue de contrôle, mais il est possible de fournir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET. Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[CustomEntries, élément pour CustomControl pour View (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[View, élément (Format)](./view-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
