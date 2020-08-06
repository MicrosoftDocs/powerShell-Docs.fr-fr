---
title: Élément DefaultSettings (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7da7948fc0814e38a8f3910596e223470ec27d75
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787731"
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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `DefaultSettings` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[DisplayError, élément (Format)](./displayerror-element-format.md)|Élément facultatif.<br /><br /> Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.|
|[EnumerableExpansions, élément (Format)](./enumerableexpansions-element-format.md)|Élément facultatif.<br /><br /> Définit les différentes façons dont les objets .NET sont développés lorsqu’ils sont affichés dans une vue.|
|[PropertyCountForTable (format)](./propertycountfortable-element-format.md)|Élément facultatif.<br /><br /> Spécifie le nombre minimal de propriétés qu’un objet doit avoir pour afficher l’objet dans une vue table.|
|[ShowError, élément (Format)](./showerror-element-format.md)|Élément facultatif.<br /><br /> Spécifie que l’enregistrement complet de l’erreur s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.|
|[WrapTables, élément (Format)](./wraptables-element-format.md)|Élément facultatif.<br /><br /> Spécifie que les données d’une table sont déplacées vers la ligne suivante si elles ne correspondent pas à la largeur de la colonne.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de configuration](./configuration-element-format.md)|Représente l’élément de niveau supérieur d’un fichier de mise en forme.|

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Élément de configuration](./configuration-element-format.md)

[DisplayError, élément (Format)](./displayerror-element-format.md)

[EnumerableExpansions, élément (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (format)](./propertycountfortable-element-format.md)

[ShowError, élément (Format)](./showerror-element-format.md)

[WrapTables, élément (Format)](./wraptables-element-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
