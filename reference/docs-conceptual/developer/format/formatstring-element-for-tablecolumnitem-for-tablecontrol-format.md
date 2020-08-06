---
title: FormatString, élément de TableColumnItem pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781543"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString, élément pour TableColumnItem pour TableControl (Format)

Spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script de la table.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) TableColumnItems, élément (format) TableColumnItem élément (format) FormatString élément pour TableColumnItem (format)

## <a name="syntax"></a>Syntaxe

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `FormatString` élément.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément TableColumnItem (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.|

## <a name="text-value"></a>Valeur texte

Spécifiez le modèle qui est utilisé pour mettre en forme les données. Par exemple, ce modèle peut être utilisé pour mettre en forme la valeur d’une propriété qui est de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.

## <a name="remarks"></a>Notes

Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées. Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).

Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[Mise en forme des données affichées](./formatting-displayed-data.md)

[Élément TableColumnItem (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
