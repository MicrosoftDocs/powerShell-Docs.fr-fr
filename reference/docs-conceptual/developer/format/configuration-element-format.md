---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration, élément (Format)
description: Configuration, élément (Format)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655682"
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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Configuration` élément. Cet élément doit être l’élément racine de chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Controls, élément pour Configuration (Format)](./controls-element-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.|
|[DefaultSettings, élément (Format)](./defaultsettings-element-format.md)|Élément facultatif.<br /><br /> Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.|
|[Format de l’élément SelectionSets](./selectionsets-element-format.md)|Élément facultatif.<br /><br /> Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.|
|[ViewDefinitions, élément (Format)](./viewdefinitions-element-format.md)|Élément facultatif.<br /><br /> Définit les vues utilisées pour afficher des objets.|

### <a name="parent-elements"></a>Éléments parents

Aucun.

## <a name="remarks"></a>Notes

Les fichiers de mise en forme définissent la façon dont les objets sont affichés. Dans la plupart des cas, cet élément racine contient un élément [ViewDefinitions](./viewdefinitions-element-format.md) qui définit la table, la liste et les vues larges du fichier de mise en forme. Outre les définitions de vue, le fichier de mise en forme peut définir des jeux de sélection, des paramètres et des contrôles communs que ces vues peuvent utiliser.

## <a name="see-also"></a>Voir aussi

[Controls, élément pour Configuration (Format)](./controls-element-for-configuration-format.md)

[DefaultSettings, élément (Format)](./defaultsettings-element-format.md)

[SelectionSets, élément (Format)](./selectionsets-element-format.md)

[ViewDefinitions, élément (Format)](./viewdefinitions-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
