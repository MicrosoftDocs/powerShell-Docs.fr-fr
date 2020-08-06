---
title: Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783413"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)

Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles de configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) EntrySelectedBy, élément pour CustomEntry pour les contrôles pour la configuration (format) SelectionCondition, élément pour EntrySelectedBy

## <a name="syntax"></a>Syntaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionCondition` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie une propriété .NET qui déclenche la condition.|
|[ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie le script qui déclenche la condition.|
|[SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie l’ensemble des types .NET qui déclenchent la condition.|
|[TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui déclenche la condition.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Définit les types .NET qui utilisent cette entrée de la définition de contrôle commune.|

## <a name="remarks"></a>Notes

Les instructions suivantes doivent être suivies lors de la définition d’une condition de sélection :

- La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.

- La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.

Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
