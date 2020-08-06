---
title: FormatString, élément de WideItem pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4f1f0826a1cebb1526858875df640baac9d4ce48
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781526"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString, élément pour WideItem pour WideControl (Format)

Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.

Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément WideControl (format) élément WideEntries (format) WideEntry élément pour WideControl (format) élément WideItem pour WideControl (format) FormatString, élément pour WideItem (format)

## <a name="syntax"></a>Syntaxe

```xml
<FormatString>PropertyPattern</FormatString>
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
|[WideItem, élément pour WideControl (Format)](./wideitem-element-for-widecontrol-format.md)|Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur texte

Spécifiez le modèle qui est utilisé pour mettre en forme les données. Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur d’une propriété de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.

## <a name="remarks"></a>Notes

Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées. Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).

Pour plus d’informations sur l’utilisation des chaînes de format dans les vues larges, consultez [création d’une vue étendue](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue large](./creating-a-wide-view.md)

[WideItem, élément pour WideControl (Format)](./wideitem-element-for-widecontrol-format.md)

[Écriture d’un fichier de mise en forme et de types Windows PowerShell](./writing-a-powershell-formatting-file.md)
