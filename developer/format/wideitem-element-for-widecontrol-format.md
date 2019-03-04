---
title: Élément WideItem pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862625"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem, élément pour WideControl (Format)

Définit la propriété ou un script dont la valeur est affichée.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) WideItem élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `WideItem` élément. L'élément `FormatString` est facultatif. Toutefois, vous devez spécifier un `PropertyName` ou `ScriptBlock` élément, mais vous ne pouvez pas spécifier à la fois.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément FormatString pour WideItem pour WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue.|
|[Élément PropertyName pour WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Spécifie la propriété de l’objet dont la valeur est affichée dans l’affichage plus large.|
|[Élément ScriptBlock pour WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Spécifie le script dont la valeur est affichée dans l’affichage plus large.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de l’affichage plus large.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideEntry` élément qui définit un seul `WideItem` élément. Le `WideItem` élément définit la propriété ou un script dont la valeur est affichée dans la vue.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[Élément FormatString pour WideItem pour WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Élément PropertyName pour WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Élément ScriptBlock pour WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Élément WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
