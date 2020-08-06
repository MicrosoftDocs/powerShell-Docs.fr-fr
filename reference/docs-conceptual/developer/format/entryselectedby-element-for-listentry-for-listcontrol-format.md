---
title: Élément EntrySelectedBy pour ListEntry pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774114"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy, élément pour ListEntry pour ListControl (Format)

Définit les types .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée. Dans la plupart des cas, une seule définition est nécessaire pour une vue liste. Toutefois, vous pouvez fournir plusieurs définitions pour le mode liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément pour ListEntry pour ListControl (format) EntrySelectedBy, élément pour ListEntry pour ListControl (format)

## <a name="syntax"></a>Syntaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit la condition qui doit exister pour que cette définition de vue de liste soit utilisée.|
|[SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un ensemble de types .NET qui utilisent cette définition de vue liste.|
|[TypeName, élément pour EntrySelectedBy pour ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Spécifie un type .NET qui utilise cette définition de la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListEntry, élément pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Définit le mode d’affichage des lignes de la liste.|

## <a name="remarks"></a>Notes

Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue de liste. Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.

Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true` . Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir les objets pour une vue liste à l’aide de leur nom de type .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Voir aussi

[ListEntry, élément pour ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName, élément pour EntrySelectedBy pour ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Création d’une vue de liste](./creating-a-list-view.md)

[Définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
