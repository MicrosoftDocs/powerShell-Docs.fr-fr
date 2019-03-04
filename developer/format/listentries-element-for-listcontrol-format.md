---
title: Élément situés pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856785"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries, élément pour ListControl (Format)

Fournit les définitions de la vue liste. L’affichage de liste doit spécifier une ou plusieurs définitions.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ListEntries` élément. Au moins un élément enfant doit être spécifié.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ListEntry (Format)](./listentry-element-for-listcontrol-format.md)|Fournit une définition de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément objet ListControl (Format)](./listcontrol-element-format.md)|Définit un format de liste pour la vue.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les affichages de liste, consultez [mode liste](./creating-a-list-view.md).

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

[Élément objet ListControl (Format)](./listcontrol-element-format.md)

[Élément ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Affichage de liste](./creating-a-list-view.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
