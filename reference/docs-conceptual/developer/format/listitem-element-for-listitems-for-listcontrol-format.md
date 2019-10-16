---
title: Élément ListItem pour ListItems pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365128"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem, élément pour ListItems pour ListControl (Format)

Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format) ListItem pour l’élément ListControl (format)

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

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListItem`. Une seule propriété ou un seul script peut être spécifié.

### <a name="attributes"></a>Attributs

aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[FormatString, élément de ListItem pour ListControl (format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie une chaîne de format qui définit le mode d’affichage de la valeur de la propriété ou du script.|
|[Élément ItemSelectionCondition pour ListItem pour ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour l’élément de liste à utiliser.|
|[Élément label pour ListItem pour ListControl (format)](./label-element-for-listitem-for-listcontrol-format.md)|Élément facultatif<br /><br /> Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.|
|[PropertyName, élément de ListItem pour ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée dans la ligne.|
|[Élément ScriptBlock pour ListItem pour ListControl (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée dans la ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItems pour le contrôle List (format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Définit les propriétés et les scripts dont les valeurs sont affichées en mode liste.|

## <a name="remarks"></a>Remarks

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

[Création d’un affichage de liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
