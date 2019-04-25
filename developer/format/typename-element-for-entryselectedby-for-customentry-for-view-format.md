---
title: Élément TypeName pour EntrySelectedBy pour CustomEntry pour la vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083975"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName, élément pour EntrySelectedBy pour CustomEntry pour View (Format)

Spécifie un type .NET qui utilise cette définition de la vue de contrôle personnalisé. Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une définition.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour EntrySelectedBy de vue (Format) Élément pour CustomEntry pour l’élément d’affichage (Format) de TypeName pour EntrySelectedBy pour CustomEntry pour la vue (Format)

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
|[Élément EntrySelectedBy pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Définit les types .NET qui utilisent cette définition de vue de contrôle personnalisé ou la condition qui doit exister pour cette définition à utiliser.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Remarques

Chaque définition de vue du contrôle personnalisé doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.

Pour plus d’informations sur les composants d’une vue de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

## <a name="see-also"></a>Voir aussi

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Élément EntrySelectedBy pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
