---
title: Élément CustomItem pour CustomEntry pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066377"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem, élément pour CustomEntry pour Controls pour View (Format)

Définit les données affichées par le contrôle et comment il est affiché. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de CustomItem pour CustomEntry pour les contrôles de vue (Format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomItem` élément. Pour plus d’informations, consultez la section Notes.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données qui sont affichées par le contrôle.|
|[Élément de frame pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.|
|[Élément de saut de ligne pour CustomItem pour les contrôles de vue (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément de texte pour CustomItem pour les contrôles de vue (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute du texte, tels que des parenthèses ou des crochets, à l’affichage du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Remarques

Lorsque vous spécifiez les éléments enfants de le `CustomItem` élément, gardez les points suivants à l’esprit :

- Les éléments enfants doivent être ajoutés dans l’ordre suivant : `ExpressionBinding`, `NewLine`, `Text`, et `Frame`.

- Il n’existe aucune limite maximale pour le nombre de séquences que vous pouvez spécifier.

- Dans chaque séquence, il n’existe aucune limite maximale pour le nombre de `ExpressionBinding` éléments que vous pouvez utiliser.

## <a name="see-also"></a>Voir aussi

[Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Élément de frame pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Élément de saut de ligne pour CustomItem pour les contrôles de vue (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Élément de texte pour CustomItem pour les contrôles de vue (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
