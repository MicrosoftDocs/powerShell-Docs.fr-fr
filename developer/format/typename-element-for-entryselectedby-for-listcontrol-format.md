---
title: Élément TypeName pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856105"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName, élément pour EntrySelectedBy pour ListControl (Format)

Spécifie un type .NET qui utilise cette entrée de la liste. Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une entrée de liste.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de TypeName ListEntry (Format) pour EntrySelectedBy pour ListControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour cette entrée à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarques

Chaque entrée de liste doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.

Pour plus d’informations sur la façon dont cet élément est utilisé dans une vue de liste, consultez [mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier une jeu de sélection pour une entrée d’une vue liste.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Élément EntrySelectedBy pour ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Élément SelectionSetName pour EnrtySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
