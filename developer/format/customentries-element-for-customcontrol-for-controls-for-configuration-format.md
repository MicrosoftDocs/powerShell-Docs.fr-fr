---
title: Élément CustomEntries pour CustomControl pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856305"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries, élément pour CustomControl pour Controls pour Configuration (Format)

Fournit les définitions d’un contrôle courant. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomEntries` élément. Vous devez spécifier un ou plusieurs éléments enfants.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit une définition du contrôle commun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomControl pour le contrôle de Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Définit un contrôle commun.|

## <a name="remarks"></a>Remarques

Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est définie dans un seul `CustomEntry` élément. Toutefois, il est possible d’avoir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents objets .NET. Dans ce cas, vous pouvez définir un `CustomEntry` élément pour chaque objet ou un ensemble d’objets.

## <a name="see-also"></a>Voir aussi

[Élément CustomControl pour le contrôle de Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
