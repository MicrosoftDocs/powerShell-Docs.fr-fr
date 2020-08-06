---
title: Élément ScriptBlock pour ListItem pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785453"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock, élément pour ListItem pour ListControl (Format)

Spécifie le script dont la valeur est affichée dans la ligne.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) élément ListItems pour l’élément ListEntry pour ListControl (format) ListItem pour l’élément ListItems pour ListControl (format) ScriptBlock pour ListControl pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
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
|[ListItem, élément (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script dont la valeur est affichée dans la ligne.

## <a name="remarks"></a>Notes

Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .

Pour plus d’informations sur la spécification de scripts dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier la propriété dont la valeur est affichée.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Voir aussi

[PropertyName, élément pour ListItem pour ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[ListItem, élément pour ListItems pour ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
