---
ms.date: 09/13/2016
ms.topic: reference
title: Controls, élément pour Configuration (Format)
description: Controls, élément pour Configuration (Format)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668097"
---
# <a name="controls-element-for-configuration-format"></a>Controls, élément pour Configuration (Format)

Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format)

## <a name="syntax"></a>Syntaxe

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Controls` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Control, élément pour Controls pour Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Configuration, élément (Format)](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Notes

Vous pouvez créer n’importe quel nombre de contrôles communs. Pour chaque contrôle, vous devez spécifier le nom utilisé pour référencer le contrôle et les composants du contrôle.

## <a name="see-also"></a>Voir aussi

[Configuration, élément (Format)](./configuration-element-format.md)

[Control, élément pour Controls pour Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
