---
title: Élément FormatString de ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860335"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>FormatString, élément pour ListItem pour ListControl (Format)

Spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche.

Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés élément d’élément de ListEntry ListControl (Format) d’élément de ListItems ListControl (Format) pour l’objet ListControl (Format) Élément ListItem pour un élément FormatString de ListControl (Format) pour ListItem pour un objet ListControl (Format)

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
|[Élément ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le modèle qui est utilisé pour mettre en forme les données. Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur de n’importe quelle propriété est de type [System.Timespan](/dotnet/api/System.TimeSpan): {0 : MMM} {0:dd} {0:HH} : {0:mm}.

## <a name="remarks"></a>Remarques

Chaînes de format peuvent être utilisés lors de la création des vues des tables, vues de liste, affichage large ou des vues personnalisées. Pour plus d’informations sur la mise en forme une valeur affichée dans une vue, consultez [mise en forme les données affichées](./formatting-displayed-data.md).

Pour plus d’informations sur l’utilisation de chaînes de format dans les affichages de liste, consultez [création d’une vue de liste](./creating-a-list-view.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Élément ListItem (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Écriture d’un mise en forme de Windows PowerShell et de Types de fichier](./writing-a-powershell-formatting-file.md)
