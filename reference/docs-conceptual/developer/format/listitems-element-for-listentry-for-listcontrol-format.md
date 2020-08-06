---
title: Élément ListItems pour ListEntry pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 03b89a3df2ab0498533d0c00f303f643e0039b25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781135"
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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListItems` élément. Il n’existe aucune limite quant au nombre d’éléments enfants qui peuvent être spécifiés. L’ordre des éléments enfants définit l’ordre dans lequel les valeurs sont affichées en mode liste.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ListItem pour ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Élément requis.<br /><br /> Définit la propriété ou le script dont la valeur est affichée par le mode liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListEntry, élément pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Fournit une définition de la vue liste.|

## <a name="remarks"></a>Notes

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

[ListEntry, élément pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Élément ListItem pour ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
