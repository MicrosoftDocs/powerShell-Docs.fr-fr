---
title: Élément FormatString pour WideItem pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860935"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString, élément pour WideItem pour WideControl (Format)

Spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue.

Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) WideEntry élément d’élément de WideItem WideControl (Format) pour l’élément FormatString de WideControl (Format) pour WideItem pour WideControl (Format)

## <a name="syntax"></a>Syntaxe

```xml
<FormatString>PropertyPattern</FormatString>
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
|[Élément WideItem pour WideControl (Format)](./wideitem-element-for-widecontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le modèle qui est utilisé pour mettre en forme les données. Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur de n’importe quelle propriété est de type [System.Timespan](/dotnet/api/System.TimeSpan): {0 : MMM} {0:dd} {0:HH} : {0:mm}.

## <a name="remarks"></a>Remarques

Chaînes de format peuvent être utilisés lors de la création des vues des tables, vues de liste, affichage large ou des vues personnalisées. Pour plus d’informations sur la mise en forme une valeur affichée dans une vue, consultez [mise en forme les données affichées](./formatting-displayed-data.md).

Pour plus d’informations sur l’utilisation de chaînes de format dans les vues larges, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Voir aussi

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Élément WideItem pour WideControl (Format)](./wideitem-element-for-widecontrol-format.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
