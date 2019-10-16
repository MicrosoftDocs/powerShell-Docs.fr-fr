---
title: Élément ListItems pour ListEntry pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362738"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems, élément pour ListEntry pour ListControl (Format)

Définit les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format) ListEntries, élément pour le contrôle de liste (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListItems`. Il n’existe aucune limite quant au nombre d’éléments enfants qui peuvent être spécifiés. L’ordre des éléments enfants définit l’ordre dans lequel les valeurs sont affichées en mode liste.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem pour ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou le script dont la valeur est affichée par le mode liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListEntry pour ListControl (format)](./listentry-element-for-listcontrol-format.md)|Fournit une définition de la vue liste.|

## <a name="remarks"></a>Remarks

Pour plus d’informations sur ce type d’affichage, consultez [création d’un affichage de liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre les éléments XML qui définissent trois lignes de la vue liste.

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

[Élément ListEntry pour ListControl (format)](./listentry-element-for-listcontrol-format.md)

[Élément ListItem pour ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Création d’un affichage de liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
