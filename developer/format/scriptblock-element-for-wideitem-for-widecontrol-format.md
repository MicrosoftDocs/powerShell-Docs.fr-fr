---
title: Élément ScriptBlock pour WideItem pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858025"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock, élément pour WideItem pour WideControl (Format)

Spécifie le script dont la valeur est affichée dans l’affichage plus large.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) élément WideEntries (Format) WideEntry, élément (Format) WideItem, élément (Format) ScriptBlock élément de configuration pour WideItem (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ScriptBlock` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Définit le bloc de script ou de la propriété dont la valeur est affichée dans l’affichage plus large.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le script dont la valeur est affichée.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `WideItem` élément qui définit un script dont la valeur est affichée dans la vue.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Voir aussi

[Élément WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
