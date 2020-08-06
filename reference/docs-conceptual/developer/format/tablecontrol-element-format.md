---
title: Élément table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 34e20006a7501650f2a22f71a3d7e999fb8b2337
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785130"
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

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TableControl` élément. Vous devez spécifier les lignes de la table. Tous les autres éléments enfants sont facultatifs.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[AutoSize, élément pour TableControl (Format)](./autosize-element-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.|
|[Élément HideTableHeaders pour table ((format)](./hidetableheaders-element-format.md)|Élément facultatif.<br /><br /> Indique si l’en-tête de la table n’est pas affiché.|
|[Élément TableHeaders pour table ((format)](./tableheaders-element-format.md)|Élément requis.<br /><br /> Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue table.|
|[TableRowEntries, élément pour TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Fournit les définitions de la vue table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[View, élément (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableControl` élément qui est utilisé pour afficher les propriétés de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[View, élément (Format)](./view-element-format.md)

[AutoSize, élément pour TableControl (Format)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders, élément (Format)](./hidetableheaders-element-format.md)

[TableHeaders, élément (Format)](./tableheaders-element-format.md)

[Élément TableRowEntries (format)](./tablerowentries-element-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
