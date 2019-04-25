---
title: Controls, élément de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066870"
---
# <a name="controls-element-for-configuration-format"></a>Controls, élément pour Configuration (Format)

Définit les contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme.

Élément de Controls (Format) d’élément de configuration de Configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Controls` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément de contrôle pour les contrôles de Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration (Format)](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Remarques

Vous pouvez créer un nombre quelconque de contrôles communs. Pour chaque contrôle, vous devez spécifier le nom qui est utilisé pour référencer le contrôle et les composants du contrôle.

## <a name="see-also"></a>Voir aussi

[Élément de configuration (Format)](./configuration-element-format.md)

[Élément de contrôle pour les contrôles de Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
