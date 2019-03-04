---
title: Élément DefaultSettings (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855665"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings, élément (Format)

Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme. Paramètres courants comprennent l’affichage des erreurs, habillage du texte dans les tables, en définissant la façon dont les collections sont développées et bien plus encore.

Élément de DefaultSettings (Format) d’élément de configuration (Format)

## <a name="syntax"></a>Syntaxe

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `DefaultSettings` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément DisplayError (Frmat)](./displayerror-element-format.md)|Élément facultatif.<br /><br /> Spécifie que la chaîne #ERR est affichée lorsqu’une erreur se produit lors de l’affichage d’un élément de données.|
|[Élément EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Élément facultatif.<br /><br /> Définit les différentes façons dont les objets .NET sont développés lorsqu’ils sont affichés dans une vue.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre minimal de propriétés que doit avoir un objet pour afficher l’objet dans un tableau.|
|[Élément ShowError (Format)](./showerror-element-format.md)|Élément facultatif.<br /><br /> Spécifie que l’enregistrement d’erreur complète est affichée lorsqu’une erreur se produit lors de l’affichage d’un élément de données.|
|[Élément WrapTables (Format)](./wraptables-element-format.md)|Élément facultatif.<br /><br /> Spécifie que les données dans une table sont déplacées vers la ligne suivante si elle ne tient pas dans la largeur de la colonne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Remarques

## <a name="see-also"></a>Voir aussi

[Élément de configuration](./configuration-element-format.md)

[Élément DisplayError (Frmat)](./displayerror-element-format.md)

[Élément EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[Élément ShowError (Format)](./showerror-element-format.md)

[Élément WrapTables (Format)](./wraptables-element-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
