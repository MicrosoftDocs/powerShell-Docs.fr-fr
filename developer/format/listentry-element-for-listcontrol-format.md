---
title: Élément ListEntry pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065221"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry, élément pour ListControl (Format)

Fournit une définition de la vue liste.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ListEntry` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit les objets .NET qui utilisent cette définition de la vue liste ou la condition qui doit exister pour cette définition à utiliser.|
|[Élément ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Élément requis.<br /><br /> Définit les propriétés et les scripts dont les valeurs sont affichées par la vue de liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément situés (Format)](./listentries-element-for-listcontrol-format.md)|Fournit les définitions de la vue liste.|

## <a name="remarks"></a>Remarques

Un affichage de liste est un format de liste qui affiche les valeurs de propriété ou de valeurs de script pour chaque objet. Pour plus d’informations sur les affichages de liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre les éléments XML qui définissent l’affichage de liste pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.

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

[Création d’une vue liste](./creating-a-list-view.md)

[Élément EntrySelectedBy pour ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Élément situés (Format)](./listentries-element-for-listcontrol-format.md)

[Élément ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
