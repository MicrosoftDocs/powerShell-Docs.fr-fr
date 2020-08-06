---
title: Élément CustomItem pour CustomEntry pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bb8124242496f192717127f201674bc1428e5de0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785861"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)

Définit les données affichées par le contrôle et leur mode d’affichage. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément CustomItem pour CustomEntry pour les contrôles de configuration

## <a name="syntax"></a>Syntaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément. Pour plus d'informations, consultez la section Notes.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Frame, élément pour CustomItem pour Controls pour Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.|
|[NewLine, élément pour CustomItem pour Controls pour Configuration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Text, élément pour CustomItem pour Controls pour Configuration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Élément facultatif.<br /><br /> Ajoute du texte, tel que des parenthèses ou des crochets, à l’affichage du contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fournit une définition du contrôle.|

## <a name="remarks"></a>Notes

Lorsque vous spécifiez les éléments enfants de l' `CustomItem` élément, gardez à l’esprit les points suivants :

- Les éléments enfants doivent être ajoutés dans la séquence suivante : `ExpressionBinding` , `NewLine` , `Text` et `Frame` .

- Il n’existe pas de limite maximale pour le nombre de séquences que vous pouvez spécifier.

- Dans chaque séquence, il n’existe pas de limite maximale pour le nombre d' `ExpressionBinding` éléments que vous pouvez utiliser.

## <a name="see-also"></a>Voir aussi

[ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Frame, élément pour CustomItem pour Controls pour Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[NewLine, élément pour CustomItem pour Controls pour Configuration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Text, élément pour CustomItem pour Controls pour Configuration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
