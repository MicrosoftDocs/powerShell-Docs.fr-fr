---
title: Élément ScriptBlock pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064575"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock, élément pour ListItem pour ListControl (Format)

Spécifie le script dont la valeur est affichée dans la ligne.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour situés d’élément de ListItems ListControl (Format) pour ListEntry élément de ListItem ListControl (Format) pour ListItems pour ListControl (Format), élément ScriptBlock pour ListItem pour un objet ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script dont la valeur est affichée dans la ligne.

## <a name="remarks"></a>Remarques

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément.

Pour plus d’informations sur la spécification des scripts dans un affichage de liste, consultez [mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier la propriété dont la valeur est affichée.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour ListItem pour un objet ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Élément ListItem pour ListItems pour ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
