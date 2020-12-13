---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem, élément pour CustomEntry pour Controls pour View (Format)
description: CustomItem, élément pour CustomEntry pour Controls pour View (Format)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666754"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem, élément pour CustomEntry pour Controls pour View (Format)

Définit les données affichées par le contrôle et leur mode d’affichage. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle des contrôles pour l’élément View (format) CustomEntries pour CustomControl pour l’élément View (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément View (format) CustomItem pour la vue (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément. Pour plus d'informations, consultez la section Notes.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Frame, élément pour CustomItem pour Controls pour View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.|
|[NewLine, élément pour CustomItem pour Controls pour View (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Text, élément pour CustomItem pour Controls pour View (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomEntries pour Controls pour View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Notes

Lorsque vous spécifiez les éléments enfants de l' `CustomItem` élément, gardez à l’esprit les points suivants :

- Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding` , `NewLine` , `Text` et `Frame` .

- Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.

- Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d' `ExpressionBinding` éléments que vous pouvez utiliser.

## <a name="see-also"></a>Voir aussi

[ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Frame, élément pour CustomItem pour Controls pour View (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[NewLine, élément pour CustomItem pour Controls pour View (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Text, élément pour CustomItem pour Controls pour View (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
