---
title: Élément CustomItem pour CustomEntry pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364028"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)

Définit les données affichées par le contrôle et leur mode d’affichage. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) CustomItem, élément pour CustomEntry pour les contrôles de configuration

## <a name="syntax"></a>Syntaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomItem`. Pour plus d’informations, consultez la section Notes.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Élément Frame pour CustomItem pour les contrôles de configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.|
|[Élément NewLine pour CustomItem pour les contrôles de configuration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément Text pour CustomItem pour les contrôles de configuration (format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CustomEntry pour CustomControl pour les contrôles de configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Remarks

Lorsque vous spécifiez les éléments enfants de l’élément `CustomItem`, gardez à l’esprit les points suivants :

- Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding`, `NewLine`, `Text` et `Frame`.

- Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.

- Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d’éléments `ExpressionBinding` que vous pouvez utiliser.

## <a name="see-also"></a>Voir aussi

[Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Élément Frame pour CustomItem pour les contrôles de configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Élément NewLine pour CustomItem pour les contrôles de configuration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Élément Text pour CustomItem pour les contrôles de configuration (format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
