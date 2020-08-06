---
title: Élément CustomItem pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783719"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem, élément pour CustomEntry pour GroupBy (Format)

Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomItem GroupBy (format) pour CustomEntry pour GroupBy (format)

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
|[ExpressionBinding, élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par le contrôle.|
|[Frame, élément pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage.|
|[NewLine, élément pour CustomItem pour GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Ajoute une ligne vide à l’affichage du contrôle.|
|[Text, élément pour CustomItem pour GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Élément facultatif.<br /><br /> Spécifie du texte supplémentaire pour les données affichées par le contrôle.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomEntry, élément pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fournit une définition de l’affichage de contrôle personnalisé.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[CustomEntry, élément pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding, élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Frame, élément pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[NewLine, élément pour CustomItem pour GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Text, élément pour CustomItem pour GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
