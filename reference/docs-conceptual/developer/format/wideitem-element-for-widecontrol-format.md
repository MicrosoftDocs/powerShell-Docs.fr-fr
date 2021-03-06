---
ms.date: 09/13/2016
ms.topic: reference
title: WideItem, élément pour WideControl (Format)
description: WideItem, élément pour WideControl (Format)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647809"
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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideItem` élément. L’élément `FormatString` est facultatif. Toutefois, vous devez spécifier un `PropertyName` `ScriptBlock` élément ou, mais vous ne pouvez pas spécifier les deux.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[FormatString, élément pour WideItem pour WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.|
|[PropertyName, élément de WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.|
|[Élément ScriptBlock pour WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Spécifie le script dont la valeur est affichée dans la vue étendue.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)|Fournit une définition de la vue étendue.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un `WideEntry` élément qui définit un `WideItem` élément unique. L' `WideItem` élément définit la propriété ou le script dont la valeur est affichée dans la vue.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="see-also"></a>Voir aussi

[FormatString, élément pour WideItem pour WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName, élément de WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Élément ScriptBlock pour WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
