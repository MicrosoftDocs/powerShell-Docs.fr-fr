---
title: CustomControl, élément de GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368958"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomControl`. Vous pouvez spécifier n’importe quel nombre d’éléments enfants et les répertorier dans n’importe quel ordre.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntries pour CustomControl pour GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Élément requis.<br /><br /> Fournit les définitions pour le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)|Définit la manière dont Windows PowerShell affiche un nouveau groupe d’objets.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>Voir aussi

[Élément CustomEntries pour CustomControl pour GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
