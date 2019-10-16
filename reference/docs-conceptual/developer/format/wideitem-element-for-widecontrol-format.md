---
title: Élément WideItem pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361398"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem, élément pour WideControl (Format)

Définit la propriété ou le script dont la valeur est affichée.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `WideItem`. L’élément `FormatString` est facultatif. Toutefois, vous devez spécifier un élément `PropertyName` ou `ScriptBlock`, mais vous ne pouvez pas spécifier les deux.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[FormatString, élément de WideItem pour WideControl (format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.|
|[PropertyName, élément de WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.|
|[Élément ScriptBlock pour WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Spécifie le script dont la valeur est affichée dans la vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de la vue étendue.|

## <a name="remarks"></a>Remarks

Pour plus d’informations sur les composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un élément `WideEntry` qui définit un seul élément `WideItem`. L’élément `WideItem` définit la propriété ou le script dont la valeur est affichée dans la vue.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[FormatString, élément de WideItem pour WideControl (format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName, élément de WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Élément ScriptBlock pour WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
