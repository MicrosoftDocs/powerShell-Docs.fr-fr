---
title: Élément ItemSelectionCondition pour ExpressionBinding pour CustomControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781186"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition, élément pour ExpressionBinding pour CustomControl (Format)

Définit la condition qui doit exister pour que ce contrôle soit utilisé. Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) CustomControl, élément (format) CustomEntries élément pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour la vue (format) élément CustomItem pour la liaison d’expression pour la vue (format) CustomEntry pour la vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ItemSelectionCondition` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour ItemSelectionCondition pour CustomControl pour View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Définit les données affichées par le contrôle.|

## <a name="remarks"></a>Notes

Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)

[ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
