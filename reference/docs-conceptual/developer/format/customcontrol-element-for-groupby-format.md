---
title: CustomControl, élément de GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b8265e872d34ea5dbcedfaa1668d21df8c3b35eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786065"
---
# <a name="customcontrol-element-for-groupby-format"></a>CustomControl, élément pour GroupBy (Format)

Définit le contrôle personnalisé qui affiche le nouveau groupe.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControl` élément. Vous pouvez spécifier n’importe quel nombre d’éléments enfants et les répertorier dans n’importe quel ordre.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomEntries, élément pour CustomControl pour GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Élément requis.<br /><br /> Fournit les définitions pour le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)|Définit la manière dont Windows PowerShell affiche un nouveau groupe d’objets.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[CustomEntries, élément pour CustomControl pour GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[GroupBy, élément pour View (Format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
