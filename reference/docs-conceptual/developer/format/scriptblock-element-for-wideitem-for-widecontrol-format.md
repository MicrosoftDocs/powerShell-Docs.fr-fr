---
title: Élément ScriptBlock pour WideItem pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787595"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock, élément pour WideItem pour WideControl (Format)

Spécifie le script dont la valeur est affichée dans la vue étendue.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) élément WideEntries (format) WideEntry élément (format) WideItem élément (format) élément ScriptBlock pour WideItem (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)|Définit la propriété ou le bloc de script dont la valeur est affichée dans la vue étendue.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script dont la valeur est affichée.

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `WideItem` élément qui définit un script dont la valeur est affichée dans la vue.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Voir aussi

[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
