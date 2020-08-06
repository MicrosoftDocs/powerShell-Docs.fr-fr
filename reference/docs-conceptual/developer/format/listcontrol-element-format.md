---
title: Élément ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785725"
---
# <a name="listcontrol-element-format"></a>ListControl, élément (Format)

Définit un format de liste pour la vue.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListControl` élément. Cet élément ne doit contenir qu’un seul élément enfant.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ListEntries, élément (format)](./listentries-element-for-listcontrol-format.md)|Élément requis.<br /><br /> Fournit les définitions de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un affichage de liste pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Voir aussi

[View, élément (Format)](./view-element-format.md)

[ListEntries, élément (format)](./listentries-element-for-listcontrol-format.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
