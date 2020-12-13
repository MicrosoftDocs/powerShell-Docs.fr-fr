---
ms.date: 09/13/2016
ms.topic: reference
title: ListItem, élément pour ListItems pour ListControl (Format)
description: ListItem, élément pour ListItems pour ListControl (Format)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666550"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem, élément pour ListItems pour ListControl (Format)

Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format) ListItem pour l’élément ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListItem` élément. Une seule propriété ou un seul script peut être spécifié.

### <a name="attributes"></a>Attributs

None

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[FormatString, élément de ListItem pour ListControl (format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie une chaîne de format qui définit le mode d’affichage de la valeur de la propriété ou du script.|
|[ItemSelectionCondition, élément pour ListItem pour ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour l’élément de liste à utiliser.|
|[Label, élément pour ListItem pour ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Élément facultatif<br /><br /> Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.|
|[PropertyName, élément pour ListItem pour ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée dans la ligne.|
|[ScriptBlock, élément pour ListItem pour ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée dans la ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItems pour le contrôle List (format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Définit les propriétés et les scripts dont les valeurs sont affichées en mode liste.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre les éléments XML qui définissent trois lignes de la vue liste. Les deux premières lignes affichent la valeur d’une propriété .NET et la dernière ligne affiche une valeur générée par un script.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Voir aussi

[Élément ListItems (format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Élément FormatString pour ListItem (format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Élément label pour ListItem (format)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName, élément de ListItem (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Élément ScriptBlock pour ListItem (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
