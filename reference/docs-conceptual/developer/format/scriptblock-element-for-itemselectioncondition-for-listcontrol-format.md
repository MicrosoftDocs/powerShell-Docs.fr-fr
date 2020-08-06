---
title: Élément ScriptBlock pour ItemSelectionCondition pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787629"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et l’élément de liste est utilisé. Cet élément est utilisé lors de la définition d’un affichage de liste.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) élément ListEntry pour ListEntries pour ListControl (format) ListItems, élément de l’élément ItemSelectionCondition de l’élément ListControl pour ListControl (format) pour l’élément ListItems pour le contrôle List (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ItemSelectionCondition, élément pour ListItem pour ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Définit la condition qui doit exister pour l’élément de liste à utiliser.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Notes

Si cet élément est utilisé, vous ne pouvez pas spécifier l' `PropertyName` élément lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
