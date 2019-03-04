---
title: Élément FormatString pour TableColumnItem pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854325"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString, élément pour TableColumnItem pour TableControl (Format)

Spécifie un modèle de format qui définit comment la valeur de propriété ou un script de la table est affichée.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément de table (Format) élément TableRowEntries (Format) TableRowEntry, élément (Format) TableColumnItems, élément (Format) TableColumnItem élément (Format) Élément FormatString pour TableColumnItem (Format)

## <a name="syntax"></a>Syntaxe

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `FormatString` élément.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le modèle qui est utilisé pour mettre en forme les données. Par exemple, ce modèle peut être utilisé pour mettre en forme la valeur de n’importe quelle propriété est de type [System.Timespan](/dotnet/api/System.TimeSpan): {0 : MMM} {0:dd} {0:HH} : {0:mm}.

## <a name="remarks"></a>Remarques

Chaînes de format peuvent être utilisés lors de la création des vues des tables, vues de liste, affichage large ou des vues personnalisées. Pour plus d’informations sur la mise en forme une valeur affichée dans une vue, consultez [mise en forme les données affichées](./formatting-displayed-data.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [Table vue](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de Table](./creating-a-table-view.md)

[Mise en forme des données affichées](./formatting-displayed-data.md)

[Élément TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
