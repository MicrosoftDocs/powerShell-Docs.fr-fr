---
title: Élément objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065255"
---
# <a name="listcontrol-element-format"></a>ListControl, élément (Format)

Définit un format de liste pour la vue.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl élément (Format)

## <a name="syntax"></a>Syntaxe

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ListControl` élément. Cet élément doit contenir uniquement un seul élément enfant.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément situés (Format)](./listentries-element-for-listcontrol-format.md)|Élément requis.<br /><br /> Fournit les définitions de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou plusieurs objets.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’une vue liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

Cet exemple montre une vue de liste pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.

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

[Élément d’affichage (Format)](./view-element-format.md)

[Élément situés (Format)](./listentries-element-for-listcontrol-format.md)

[Création d’une vue liste](./creating-a-list-view.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
