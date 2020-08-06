---
title: Élément CustomItem pour CustomEntry pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785827"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem, élément pour CustomEntry pour CustomControl pour View (Format)

Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) CustomItem pour CustomEntry pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomItem` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Frame, élément pour CustomItem pour CustomControl pour View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|
|[Élément NewLine pour CustomItem pour un contrôle personnalisé pour View (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Élément de texte pour CustomItem pour CustomControl pour View (format)](./text-element-for-customitem-for-customview-for-view-format.md)|Élément facultatif.<br /><br /> Spécifie du texte supplémentaire pour les données affichées par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomEntries pour CustomControl pour View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fournit une définition de l’affichage de contrôle personnalisé.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding, élément pour CustomItem pour CustomControl pour View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Frame, élément pour CustomItem pour CustomControl pour View (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[NewLine, élément pour CustomItem pour CustomControl pour View (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Élément de texte pour CustomItem pour CustomControl pour View (format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
