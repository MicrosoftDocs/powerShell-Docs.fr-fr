---
title: Élément PropertyName pour TableColumnItem pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064606"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>PropertyName, élément pour TableColumnItem pour TableControl (Format)

Spécifie la propriété dont la valeur est affichée dans la colonne de la ligne.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément de table (Format) élément TableRowEntries (Format) TableRowEntry, élément (Format) TableColumnItems, élément (Format) TableColumnItem élément (Format) Élément PropertyName pour TableColumnItem (Format)

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `PropertyName` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété dont la valeur est affichée.

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableColumnItem` élément qui spécifie le `Status` propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
