---
title: Élément TypeName pour ViewSelectedBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361438"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName, élément pour ViewSelectedBy (Format)

Spécifie un objet .NET qui est affiché par la vue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément ViewSelectedBy (format) TypeName, élément pour ViewSelectedBy (format)

## <a name="syntax"></a>Syntaxe

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `TypeName`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ViewSelectedBy (format)](./viewselectedby-element-format.md)|Définit les objets .NET affichés par la vue.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarks

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

[Création d’un affichage de liste](./creating-a-list-view.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’un affichage étendu](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Élément ViewSelectedBy (format)](./viewselectedby-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
