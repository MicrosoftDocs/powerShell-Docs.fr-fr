---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour ViewSelectedBy (Format)
description: TypeName, élément pour ViewSelectedBy (Format)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667723"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName, élément pour ViewSelectedBy (Format)

Spécifie un objet .NET qui est affiché par la vue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément ViewSelectedBy (format) TypeName, élément pour ViewSelectedBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `TypeName` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ViewSelectedBy, élément (Format)](./viewselectedby-element-format.md)|Définit les objets .NET affichés par la vue.|

## <a name="text-value"></a>Valeur texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Notes

Pour plus d’informations sur l’utilisation de cet élément dans différents affichages, consultez [création d’un affichage de table](./creating-a-table-view.md), [création d’un affichage de liste](./creating-a-list-view.md), [création d’un affichage étendu](./creating-a-wide-view.md)et [composants de vue personnalisés](./creating-custom-controls.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) pour un affichage de liste. Le même schéma est utilisé pour les vues de table, larges et personnalisées.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[ViewSelectedBy, élément (Format)](./viewselectedby-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
