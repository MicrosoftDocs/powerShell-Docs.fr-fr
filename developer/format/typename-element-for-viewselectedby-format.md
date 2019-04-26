---
title: Élément TypeName pour ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083754"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName, élément pour ViewSelectedBy (Format)

Spécifie un objet .NET qui est affiché par la vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément ViewSelectedBy (Format) TypeName élément de configuration pour ViewSelectedBy (Format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, éléments enfants et les éléments parents de la `TypeName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Définit les objets .NET qui sont affichés par la vue.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur la façon dont cet élément est utilisé dans les différentes vues, consultez [création d’une vue de Table](./creating-a-table-view.md), [création d’une vue liste](./creating-a-list-view.md), [création d’un affichage plus large](./creating-a-wide-view.md), et [ Composants de la vue personnalisée](./creating-custom-controls.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet pour un affichage de liste. Le même schéma est utilisé pour les vues table, large et personnalisées.

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

[Création d’une vue liste](./creating-a-list-view.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Élément ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
