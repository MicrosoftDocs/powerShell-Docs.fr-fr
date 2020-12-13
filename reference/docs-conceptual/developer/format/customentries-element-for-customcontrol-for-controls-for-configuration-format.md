---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)
description: CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655398"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)

Fournit les définitions d’un contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomEntries` élément. Vous devez spécifier un ou plusieurs éléments enfants.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit une définition du contrôle commun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomControl, élément de Control pour la configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Définit un contrôle commun.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, un contrôle n’a qu’une seule définition, qui est définie dans un `CustomEntry` élément unique. Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher différents objets .NET. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[CustomControl, élément de Control pour la configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
