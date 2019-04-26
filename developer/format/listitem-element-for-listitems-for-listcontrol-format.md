---
title: Élément ListItem pour ListItems pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065765"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem, élément pour ListItems pour ListControl (Format)

Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés élément d’élément de ListEntry ListControl (Format) d’élément de ListItems ListControl (Format) pour l’objet ListControl (Format) ListItem pour l’élément objet ListControl (Format)

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

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ListItem` élément. Peut être spécifié qu’une seule propriété ou script.

### <a name="attributes"></a>Attributes

Aucune

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément FormatString de ListItem pour un objet ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie une chaîne de format qui définit comment la valeur de propriété ou un script s’affiche.|
|[Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour cet élément de liste à utiliser.|
|[Élément Label pour ListItem pour un objet ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Élément facultatif<br /><br /> Spécifie l’étiquette qui s’affiche à gauche de la valeur de propriété ou un script dans la ligne.|
|[Élément PropertyName pour ListItem pour un objet ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie la propriété .NET dont la valeur est affichée dans la ligne.|
|[Élément ScriptBlock pour ListItem pour un objet ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie le script dont la valeur est affichée dans la ligne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItems pour le contrôle de liste (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Définit les propriétés et les scripts dont les valeurs sont affichées dans la vue liste.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre les éléments XML qui définissent les trois lignes de la vue liste. Les deux premières lignes affichent la valeur d’une propriété .NET, et la dernière ligne affiche une valeur générée par un script.

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

[Élément ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Élément FormatString de ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Élément Label pour ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[Élément PropertyName pour ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Élément ScriptBlock pour ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
