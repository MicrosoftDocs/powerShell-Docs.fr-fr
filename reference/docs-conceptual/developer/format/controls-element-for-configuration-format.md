---
title: Controls, élément de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783787"
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
