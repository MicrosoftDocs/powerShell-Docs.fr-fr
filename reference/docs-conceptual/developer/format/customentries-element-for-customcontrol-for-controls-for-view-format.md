---
title: Élément CustomEntries pour CustomControl pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783702"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries, élément pour CustomControl pour Controls pour View (Format)

Fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomEntries` élément. Il n’existe pas de limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiés.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomEntries pour Controls pour View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Élément requis.<br /><br /> Fournit une définition du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément pour Control pour View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Définit le contrôle utilisé par la vue.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est spécifiée dans un `CustomEntry` élément unique. Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[CustomEntry, élément pour CustomEntries pour Controls pour View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl, élément pour Control pour View (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
