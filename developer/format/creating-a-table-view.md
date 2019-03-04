---
title: Création d’une vue de Table | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861495"
---
# <a name="creating-a-table-view"></a>Création d’une vue de table

Une vue de table affiche les données dans une ou plusieurs colonnes. Chaque ligne dans la table représente un objet .NET, et chaque colonne de la table représente une propriété de l’objet ou une valeur de script. Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet ou un sous-ensemble des propriétés d’un objet.

## <a name="a-table-view-display"></a>Un affichage de la vue Table

L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet qui est retourné par la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) applet de commande. Pour cet objet, Windows PowerShell a défini une vue de table qui affiche le `Status` propriété, le `Name` propriété (cette propriété est une propriété d’alias pour le `ServiceName` propriété) et le `DisplayName` propriété. Chaque ligne dans la table représente un objet retourné par l’applet de commande.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Définition de la vue de Table

Le code XML suivant montre le schéma de vue de table pour afficher la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objet. Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue de table.

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

Les éléments XML suivants sont utilisés pour définir une vue de liste :

- Le [vue](./view-element-format.md) élément est l’élément parent de la vue de table. (Ceci est le même élément parent pour obtenir la liste des vues de contrôle de large et personnalisées).

- Le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue. Cet élément est requis pour toutes les vues.

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue. Cet élément est requis.

- Le [GroupBy](./groupby-element-for-view-format.md) élément (non affiché dans cet exemple) définit quand un nouveau groupe d’objets s’affiche. Un nouveau groupe est démarré à chaque modification de la valeur d’une propriété spécifique ou d’un script. Cet élément est facultatif.

- Le [contrôles](./controls-element-for-view-format.md) élément (non affiché dans cet exemple) définit les contrôles personnalisés qui sont définies par la vue de table. Contrôles vous permettent de préciser la façon dont les données sont affichées. Cet élément est facultatif. Une vue peut définir ses propres contrôles personnalisés, ou il peut utiliser des contrôles communs qui peuvent être utilisées par n’importe quelle vue dans le fichier de mise en forme. Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

- Le [HideTableHeaders](./hidetableheaders-element-format.md) élément (pas montrer dans cet exemple) Spécifie que la table n’affiche pas toutes les étiquettes en haut de la table. Cet élément est facultatif.

- Le [table](./tablecontrol-element-format.md) élément qui définit les informations d’en-tête et de ligne de la table. Comme pour toutes les autres vues, une vue de table peut afficher les valeurs des propriétés de l’objet ou valeurs générées par des scripts.

## <a name="defining-column-headers"></a>Définition d’en-têtes de colonne

1. Le [TableHeaders](./tableheaders-element-format.md) élément et ses éléments enfants définissent ce qui est affiché en haut de la table.

2. Le [TableColumnHeader](./tablecolumnheader-element-format.md) élément définit ce qui est affiché en haut d’une colonne de la table. Spécifiez ces éléments dans l’ordre que vous souhaitez les en-têtes affichés.

   Il n’existe aucune limite le nombre de ces élément que vous pouvez utiliser, mais le nombre de [TableColumnHeader](./tablecolumnheader-element-format.md) éléments dans votre affichage de la table doivent égal au nombre de [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) éléments que vous utilisez.

3. Le [étiquette](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) élément spécifie le texte qui s’affiche. Cet élément est facultatif.

4. Le [largeur](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) élément spécifie la largeur (en caractères) de la colonne. Cet élément est facultatif.

5. Le [alignement](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) élément spécifie la façon dont l’étiquette est affichée. L’étiquette peut être aligné à gauche, à droite, ou centré. Cet élément est facultatif.

## <a name="defining-the-table-rows"></a>Définir les lignes de Table

Vues de table peuvent fournir une ou plusieurs définitions qui spécifient les données affichées dans les lignes de la table en utilisant les éléments enfants de la [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) élément. Notez que vous pouvez spécifier plusieurs définitions pour les lignes de la table, mais les en-têtes de lignes reste la même, quel que soit la définition de ligne est utilisé. En règle générale, une table aura qu’une seule définition.

Dans l’exemple suivant, la vue fournit une définition unique qui affiche les valeurs de plusieurs propriétés de la [System.Diagnostics.Process ? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objet. Une vue de table peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple) dans ses lignes.

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

- Le [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) élément et ses éléments enfants définissent ce qui est affiché dans les lignes de la table.

- Le [TableRowEntry](./listentry-element-for-listcontrol-format.md) élément fournit une définition de la ligne. Au moins un [TableRowEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe aucune limite maximale pour le nombre d’éléments que vous pouvez ajouter. Dans la plupart des cas, une vue aura qu’une seule définition.

- Le [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) élément spécifie les objets qui sont affichés par une définition spécifique. Cet élément est facultatif et est nécessaire uniquement lorsque vous définissez plusieurs [TableRowEntry](./listentry-element-for-listcontrol-format.md) éléments qui affichent des objets différents.

- Le [encapsuler](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) élément spécifie que le texte qui dépasse la largeur de colonne s’affiche sur la ligne suivante. Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.

- Le [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) élément définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.

- Le [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne. Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément est requis pour chaque colonne de la ligne. La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.

- Le [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie la propriété dont la valeur est affichée dans la ligne. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.

- Le [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie le script dont la valeur est affichée dans la ligne. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

- Le [FormatString](./label-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche. Cet élément est facultatif.

- Le [alignement](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie la façon dont la valeur de la propriété ou le script s’affiche. La valeur peut être alignée à gauche, à droite, ou centrée. Cet élément est facultatif.

## <a name="defining-the-objects-that-use-the-table-view"></a>Définition des objets qui utilisent la vue de Table

Il existe deux façons de définir les objets .NET utilisent la vue de table. Vous pouvez utiliser la [ViewSelectedBy](./viewselectedby-element-format.md) élément pour définir les objets qui peuvent être affichées par toutes les définitions de la vue, ou vous pouvez utiliser la [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément pour définir quels objets sont affichés par un définition spécifique de la vue. Dans la plupart des cas, une vue n'a qu’une seule définition, donc les objets sont généralement définies par le [ViewSelectedBy](./viewselectedby-element-format.md) élément.

L’exemple suivant montre comment définir les objets qui sont affichés par la vue de table en utilisant le [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) éléments. Il n’existe aucune limite au nombre de [TypeName](./typename-element-for-viewselectedby-format.md) éléments que vous pouvez spécifier, et leur ordre n’est pas significatif.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de table :

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.

- Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie l’objet .NET qui est affiché par la vue. Le nom de type .NET complet est requis. Vous devez spécifier au moins un type ou la sélection définie pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

L’exemple suivant utilise le [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) éléments. Utiliser des jeux de sélection où vous avez un ensemble d’objets qui sont affichés à l’aide de plusieurs vues, comme lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets liés. Pour plus d’informations sur la création d’un jeu de sélection, consultez [définissant des ensembles de sélection](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de liste :

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.

- Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément spécifie un ensemble d’objets qui peuvent être affichés par la vue. Vous devez spécifier au moins un jeu de sélection ou de type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de table en utilisant le [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) élément. À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un ensemble de la sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée. Pour plus d’informations sur la façon de créer une sélection des conditions, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Lorsque vous créez plusieurs définitions de la vue de table que vous ne pouvez pas spécifier des en-têtes de colonnes différentes. Vous pouvez spécifier uniquement ce qui est affiché dans les lignes de la table, telles que les objets sont affichés.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de la vue de liste :

- Le [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) élément définit les objets qui sont affichés par la définition.

- Le [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) élément spécifie l’objet .NET qui est affiché par la définition. Lorsque vous utilisez cet élément, le nom de type .NET complet est requis. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

- Le [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie un ensemble d’objets qui peuvent être affichées par cette définition. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

- Le [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie une condition qui doit exister pour cette définition à utiliser. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>À l’aide de chaînes de Format

Mise en forme de chaînes peuvent être ajoutés à une vue pour définir plus précisément la façon dont les données sont affichées. L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :

- Le [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne. Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément est requis pour chaque colonne de la ligne. La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.

- Le [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie la propriété dont la valeur est affichée dans la ligne. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.

- Le [FormatString](./label-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche.

Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script. Scripts peuvent appeler n’importe quelle méthode d’un objet. Par conséquent, si un objet possède une méthode, tel que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

L’élément XML suivant peut être utilisé pour appeler le `ToString` méthode :

- Le [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne. Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément est requis pour chaque colonne de la ligne. La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.

- Le [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie le script dont la valeur est affichée dans la ligne. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
