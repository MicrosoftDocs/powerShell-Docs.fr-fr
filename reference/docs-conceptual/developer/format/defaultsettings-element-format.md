---
title: Élément DefaultSettings (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363868"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings, élément (Format)

Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme. Les paramètres courants incluent l’affichage des erreurs, l’habillage du texte dans les tables, la définition du développement des collections, etc.

Élément de configuration (format) DefaultSettings, élément (format)

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

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `DefaultSettings`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément DisplayError (format)](./displayerror-element-format.md)|Élément facultatif.<br /><br /> Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.|
|[Élément EnumerableExpansions (format)](./enumerableexpansions-element-format.md)|Élément facultatif.<br /><br /> Définit les différentes façons dont les objets .NET sont développés lorsqu’ils sont affichés dans une vue.|
|[PropertyCountForTable (format)](./propertycountfortable-element-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre minimal de propriétés qu’un objet doit avoir pour afficher l’objet dans une vue table.|
|[Élément ShowError (format)](./showerror-element-format.md)|Élément facultatif.<br /><br /> Spécifie que l’enregistrement complet de l’erreur s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.|
|[Élément WrapTables (format)](./wraptables-element-format.md)|Élément facultatif.<br /><br /> Spécifie que les données d’une table sont déplacées vers la ligne suivante si elles ne correspondent pas à la largeur de la colonne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>Voir aussi

[Élément de configuration](./configuration-element-format.md)

[Élément DisplayError (format)](./displayerror-element-format.md)

[Élément EnumerableExpansions (format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (format)](./propertycountfortable-element-format.md)

[Élément ShowError (format)](./showerror-element-format.md)

[Élément WrapTables (format)](./wraptables-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
