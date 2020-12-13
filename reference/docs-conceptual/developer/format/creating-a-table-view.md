---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une vue de table
description: Création d’une vue de table
ms.openlocfilehash: 035d42f7968a9e8babec692a7a5873e24b36cd97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660295"
---
# <a name="creating-a-table-view"></a>Création d’une vue de table

Un affichage de table affiche les données dans une ou plusieurs colonnes. Chaque ligne de la table représente un objet .NET, et chaque colonne de la table représente une propriété de l’objet ou une valeur de script. Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet ou un sous-ensemble des propriétés d’un objet.

## <a name="a-table-view-display"></a>Affichage d’une vue de table

L’exemple suivant montre comment Windows PowerShell affiche l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) qui est retourné par l’applet de commande [« obtient-service »](/powershell/module/microsoft.powershell.management/get-service) . Pour cet objet, Windows PowerShell a défini une vue de table qui affiche la `Status` propriété, la `Name` propriété (cette propriété est une propriété d’alias pour la `ServiceName` propriété) et la `DisplayName` propriété. Chaque ligne de la table représente un objet retourné par l’applet de commande.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Définition de la vue table

Le code XML suivant montre le schéma de la vue table pour afficher [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet. Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue table.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Les éléments XML suivants sont utilisés pour définir un mode liste :

- L’élément [View](./view-element-format.md) est l’élément parent de la vue table. (Il s’agit du même élément parent pour les vues de contrôle de liste, larges et personnalisées.)

- L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue. Cet élément est requis pour toutes les vues.

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue. Cet élément est obligatoire.

- L’élément [GroupBy](./groupby-element-for-view-format.md) (non illustré dans cet exemple) définit le moment où un nouveau groupe d’objets est affiché. Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change. Cet élément est facultatif.

- L’élément [Controls](./controls-element-for-view-format.md) (non illustré dans cet exemple) définit les contrôles personnalisés qui sont définis par la vue table. Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées. Cet élément est facultatif. Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme. Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

- L’élément [HideTableHeaders](./hidetableheaders-element-format.md) (pas dans cet exemple) spécifie que la table n’affichera aucune étiquette en haut de la table. Cet élément est facultatif.

- Élément [table (](./tablecontrol-element-format.md) qui définit les informations d’en-tête et de ligne de la table. Comme pour toutes les autres vues, une vue de table peut afficher les valeurs des propriétés ou valeurs d’objet générées par les scripts.

## <a name="defining-column-headers"></a>Définition des en-têtes de colonnes

1. L’élément [TableHeaders](./tableheaders-element-format.md) et ses éléments enfants définissent ce qui est affiché en haut de la table.

2. L’élément [TableColumnHeader](./tablecolumnheader-element-format.md) définit ce qui est affiché en haut d’une colonne de la table. Spécifiez ces éléments dans l’ordre d’affichage des en-têtes.

   Il n’y a pas de limite au nombre de ces éléments que vous pouvez utiliser, mais le nombre d’éléments [TableColumnHeader](./tablecolumnheader-element-format.md) dans votre vue de table doit être égal au nombre d’éléments [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) que vous utilisez.

3. L’élément [label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie le texte qui est affiché. Cet élément est facultatif.

4. L’élément [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie la largeur (en caractères) de la colonne. Cet élément est facultatif.

5. L’élément [alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie le mode d’affichage de l’étiquette. L’étiquette peut être alignée à gauche, à droite ou centrée. Cet élément est facultatif.

## <a name="defining-the-table-rows"></a>Définition des lignes de la table

Les vues de table peuvent fournir une ou plusieurs définitions qui spécifient les données affichées dans les lignes de la table à l’aide des éléments enfants de l’élément [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) . Notez que vous pouvez spécifier plusieurs définitions pour les lignes de la table, mais que les en-têtes pour les lignes restent les mêmes, quelle que soit la définition de ligne utilisée. En règle générale, une table n’a qu’une seule définition.

Dans l’exemple suivant, la vue fournit une définition unique qui affiche les valeurs de plusieurs propriétés de [System. Diagnostics. Process ? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) , objet. Une vue de table peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple) dans ses lignes.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une ligne :

- L’élément [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) et ses éléments enfants définissent ce qui est affiché dans les lignes de la table.

- L’élément [TableRowEntry](./listentry-element-for-listcontrol-format.md) fournit une définition de la ligne. Au moins un [TableRowEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter. Dans la plupart des cas, une vue n’a qu’une seule définition.

- L’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) spécifie les objets qui sont affichés par une définition spécifique. Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [TableRowEntry](./listentry-element-for-listcontrol-format.md) qui affichent des objets différents.

- L’élément [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) spécifie que le texte qui dépasse la largeur de colonne est affiché sur la ligne suivante. Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.

- L’élément [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.

- L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne. Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne. La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.

- L’élément [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.

- L’élément [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

- L’élément [FormatString](./label-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script. Cet élément est facultatif.

- L’élément [alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la manière dont la valeur de la propriété ou du script est affichée. La valeur peut être alignée à gauche, à droite ou centrée. Cet élément est facultatif.

## <a name="defining-the-objects-that-use-the-table-view"></a>Définition des objets qui utilisent la vue table

Il existe deux façons de définir les objets .NET qui utilisent la vue table. Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue. Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .

L’exemple suivant montre comment définir les objets affichés par la vue table à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) . Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par la vue table :

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.

- L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie l’objet .net qui est affiché par la vue. Le nom complet du type .NET est obligatoire. Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets. Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.

- L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue. Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de table à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) . À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée. Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Lors de la création de plusieurs définitions de la vue table, vous ne pouvez pas spécifier d’en-têtes de colonnes différents. Vous pouvez spécifier uniquement ce qui est affiché dans les lignes de la table, telles que les objets affichés.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par une définition spécifique de la vue Liste :

- L’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) définit les objets qui sont affichés par la définition.

- L’élément [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) spécifie l’objet .net qui est affiché par la définition. Lors de l’utilisation de cet élément, le nom complet du type .NET est requis. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

- L’élément [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

- L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Utilisation de chaînes de format

La mise en forme des chaînes peut être ajoutée à une vue pour définir davantage la façon dont les données sont affichées. L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :

- L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne. Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne. La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.

- L’élément [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.

- L’élément [FormatString](./label-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script.

Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script. Les scripts peuvent appeler n’importe quelle méthode d’un objet. Par conséquent, si un objet a une méthode, telle que `ToString` , qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

L’élément XML suivant peut être utilisé pour appeler la `ToString` méthode :

- L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne. Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne. La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.

- L’élément [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
