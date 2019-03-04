---
title: Élément de table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858915"
---
# <a name="tablecontrol-element-format"></a>TableControl, élément (Format)

Définit un format de table pour une vue.

ViewDefinitions élément (Format) vue (Format) table élément (Format)

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

Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `TableControl` élément. Vous devez spécifier les lignes de la table. Tous les autres éléments enfants sont facultatifs.

### <a name="attributes"></a>Attributes

Aucune.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément AutoSize pour la table (Format)](./autosize-element-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.|
|[Élément HideTableHeaders pour la table (Format)](./hidetableheaders-element-format.md)|Élément facultatif.<br /><br /> Indique si l’en-tête de la table n’est pas affiché.|
|[Élément TableHeaders pour la table (Format)](./tableheaders-element-format.md)|Élément requis.<br /><br /> Définit les étiquettes, les largeurs et l’alignement des données pour les colonnes de la vue de table.|
|[Élément TableRowEntries pour TableCotrol (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Élément facultatif.<br /><br /> Fournit les définitions de la vue de table.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément d’affichage (Format)](./view-element-format.md)|Définit une vue qui est utilisée pour afficher les membres d’un ou plusieurs objets.|

## <a name="remarks"></a>Remarques

Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).

## <a name="example"></a>Exemple

Cet exemple montre un `TableControl` élément qui est utilisé pour afficher les propriétés de la [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.

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

[Création d’une vue de Table](./creating-a-table-view.md)

[Élément d’affichage (Format)](./view-element-format.md)

[Élément AutoSize pour la table (Format)](./autosize-element-for-tablecontrol-format.md)

[Élément HideTableHeaders (Format)](./hidetableheaders-element-format.md)

[Élément TableHeaders (Format)](./tableheaders-element-format.md)

[Élément TableRowEntries (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
