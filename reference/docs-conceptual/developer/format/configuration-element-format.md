---
title: Élément configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363498"
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

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Configuration`. Cet élément doit être l’élément racine de chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Controls, élément de configuration (format)](./controls-element-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.|
|[Élément DefaultSettings (format)](./defaultsettings-element-format.md)|Élément facultatif.<br /><br /> Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|
|[Format de l’élément SelectionSets](./selectionsets-element-format.md)|Élément facultatif.<br /><br /> Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.|
|[Élément ViewDefinitions (format)](./viewdefinitions-element-format.md)|Élément facultatif.<br /><br /> Définit les vues utilisées pour afficher des objets.|

### <a name="parent-elements"></a>Éléments parents

Aucune.

## <a name="remarks"></a>Remarks

Les fichiers de mise en forme définissent la façon dont les objets sont affichés. Dans la plupart des cas, cet élément racine contient un élément [ViewDefinitions](./viewdefinitions-element-format.md) qui définit la table, la liste et les vues larges du fichier de mise en forme. Outre les définitions de vue, le fichier de mise en forme peut définir des jeux de sélection, des paramètres et des contrôles communs que ces vues peuvent utiliser.

## <a name="see-also"></a>Voir aussi

[Controls, élément de configuration (format)](./controls-element-for-configuration-format.md)

[Élément DefaultSettings (format)](./defaultsettings-element-format.md)

[Élément SelectionSets (format)](./selectionsets-element-format.md)

[Élément ViewDefinitions (format)](./viewdefinitions-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
