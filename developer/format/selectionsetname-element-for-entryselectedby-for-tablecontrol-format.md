---
title: Élément SelectionSetName pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063919"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)

Spécifie qu'un ensemble de .NET types l’utilisation de cette entrée de la vue de table. Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) table, élément (Format) TableRowEntries, élément (Format) TableRowEntry, élément (Format) EntrySelectedBy, élément (Format) SelectionSetName élément de configuration pour EntrySelectedBy pour TableRowEntry (Format)

## <a name="syntax"></a>Syntaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour cette entrée à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de l’ensemble de la sélection.

## <a name="remarks"></a>Remarques

Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues. Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets. Pour plus d’informations sur la définition de jeux de sélection, consultez [définition définit des objets pour une vue](./defining-selection-sets.md).

Si vous spécifiez une jeu de sélection pour une entrée, vous ne pouvez pas spécifier un nom de type. Pour plus d’informations sur la façon de spécifier un type .NET, consultez [TypeName élément pour EntrySelectedBy pour TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="see-also"></a>Voir aussi

[Élément EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Définition de jeux d’objets pour une vue](./defining-selection-sets.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
