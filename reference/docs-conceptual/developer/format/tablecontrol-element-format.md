---
title: Élément table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368198"
---
# <a name="tablecontrol-element-format"></a>TableControl, élément (Format)

Définit un format de table pour une vue.

Élément ViewDefinitions (format), élément de vue (format) élément table ((format)

## <a name="syntax"></a>Syntaxe

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TableControl`. Vous devez spécifier les lignes de la table. Tous les autres éléments enfants sont facultatifs.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[AutoSize, élément de table ((format)](./autosize-element-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.|
|[Élément HideTableHeaders pour table ((format)](./hidetableheaders-element-format.md)|Élément facultatif.<br /><br /> Indique si l’en-tête de la table n’est pas affiché.|
|[Élément TableHeaders pour table ((format)](./tableheaders-element-format.md)|Élément requis.<br /><br /> Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue table.|
|[Élément TableRowEntries pour table ((format)](./tablerowentries-element-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Fournit les définitions de la vue table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.|

## <a name="remarks"></a>Remarks

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un élément `TableControl` qui est utilisé pour afficher les propriétés de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de table](./creating-a-table-view.md)

[View, élément (format)](./view-element-format.md)

[AutoSize, élément de table ((format)](./autosize-element-for-tablecontrol-format.md)

[Élément HideTableHeaders (format)](./hidetableheaders-element-format.md)

[Élément TableHeaders (format)](./tableheaders-element-format.md)

[Élément TableRowEntries (format)](./tablerowentries-element-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
