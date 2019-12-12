---
title: Controls, élément de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368998"
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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Controls`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément Control pour les contrôles de configuration (format)](./control-element-for-controls-for-configuration-format.md)|Élément requis.<br /><br /> Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément configuration (format)](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Remarks

Vous pouvez créer n’importe quel nombre de contrôles communs. Pour chaque contrôle, vous devez spécifier le nom utilisé pour référencer le contrôle et les composants du contrôle.

## <a name="see-also"></a>Voir aussi

[Élément configuration (format)](./configuration-element-format.md)

[Élément Control pour les contrôles de configuration (format)](./control-element-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
