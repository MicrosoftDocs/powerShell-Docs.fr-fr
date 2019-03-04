---
title: Élément de configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856325"
---
# <a name="configuration-element-format"></a>Configuration, élément (Format)

Représente l’élément de niveau supérieur d’un fichier de mise en forme.

Élément de configuration

## <a name="syntax"></a>Syntaxe

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Configuration` élément. Cet élément doit être l’élément racine pour chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément de Controls pour la Configuration (Format)](./controls-element-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme.|
|[Élément DefaultSettings (Format)](./defaultsettings-element-format.md)|Élément facultatif.<br /><br /> Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|
|[Format d’élément de SelectionSets](./selectionsets-element-format.md)|Élément facultatif.<br /><br /> Définit les jeux d’objets .NET qui peuvent être utilisées par toutes les vues du fichier de mise en forme courants.|
|[Élément ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Élément facultatif.<br /><br /> Définit les vues utilisées pour afficher les objets.|

### <a name="parent-elements"></a>Éléments parents

Aucune.

## <a name="remarks"></a>Remarques

Fichiers de mise en forme définissent comment les objets sont affichés. Dans la plupart des cas, cet élément racine contient un [ViewDefinitions](./viewdefinitions-element-format.md) élément qui définit la table, une liste et un affichage large du fichier de mise en forme. Outre les définitions de vue, le fichier de mise en forme pouvez définir des jeux de sélection, les paramètres et les contrôles ces vues peuvent utiliser courants.

## <a name="see-also"></a>Voir aussi

[Élément de Controls pour la Configuration (Format)](./controls-element-for-configuration-format.md)

[Élément DefaultSettings (Format)](./defaultsettings-element-format.md)

[Élément SelectionSets (Format)](./selectionsets-element-format.md)

[Élément ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
