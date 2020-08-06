---
title: Élément ListEntry pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785691"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry, élément pour ListControl (Format)

Fournit une définition de la vue liste.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format)

## <a name="syntax"></a>Syntaxe

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListEntry` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément EntrySelectedBy pour ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Élément facultatif.<br /><br /> Définit les objets .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée.|
|[Élément ListItems (format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Élément requis.<br /><br /> Définit les propriétés et les scripts dont les valeurs sont affichées par la vue liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ListEntries, élément (format)](./listentries-element-for-listcontrol-format.md)|Fournit les définitions de la vue liste.|

## <a name="remarks"></a>Notes

Un affichage de liste est un format de liste qui affiche des valeurs de propriété ou des valeurs de script pour chaque objet. Pour plus d’informations sur les affichages de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

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

[Création d’une vue de liste](./creating-a-list-view.md)

[Élément EntrySelectedBy pour ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries, élément (format)](./listentries-element-for-listcontrol-format.md)

[Élément ListItems (format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
