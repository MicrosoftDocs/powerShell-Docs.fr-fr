---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntries, élément pour ListControl (Format)
description: ListEntries, élément pour ListControl (Format)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666601"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries, élément pour ListControl (Format)

Fournit les définitions de la vue liste. Le mode liste doit spécifier une ou plusieurs définitions.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListEntries` élément. Au moins un élément enfant doit être spécifié.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ListEntry (format)](./listentry-element-for-listcontrol-format.md)|Fournit une définition de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListControl, élément (Format)](./listcontrol-element-format.md)|Définit un format de liste pour la vue.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les affichages de liste, consultez [affichage de liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre les éléments XML qui définissent le mode liste de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Voir aussi

[ListControl, élément (Format)](./listcontrol-element-format.md)

[Élément ListEntry (format)](./listentry-element-for-listcontrol-format.md)

[Mode liste](./creating-a-list-view.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
