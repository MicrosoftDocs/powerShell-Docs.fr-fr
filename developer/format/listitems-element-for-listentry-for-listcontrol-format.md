---
title: Élément ListItems pour ListEntry pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858585"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems, élément pour ListEntry pour ListControl (Format)

Définit les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément de liste contrôle (Format) ListEntry élément d’élément de ListItems ListControl (Format) pour l’objet ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ListItems` élément. Il n’existe aucune limite au nombre d’éléments enfants qui peuvent être spécifiées. L’ordre des éléments enfants définit l’ordre que les valeurs sont affichées dans la vue liste.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem pour un objet ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou un script dont la valeur est affichée par la vue de liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListEntry pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Fournit une définition de la vue liste.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur ce type d’affichage, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre les éléments XML qui définissent les trois lignes de la vue liste.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Voir aussi

[Élément ListEntry pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Élément ListItem pour un objet ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
