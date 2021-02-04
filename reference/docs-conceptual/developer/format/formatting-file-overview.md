---
ms.date: 09/13/2016
ms.topic: reference
title: Vue d’ensemble des fichiers de mise en forme
description: Vue d’ensemble des fichiers de mise en forme
ms.openlocfilehash: 769a86d274ef3b35a322d76e2f03cb551d9204a1
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879134"
---
# <a name="formatting-file-overview"></a>Vue d’ensemble des fichiers de mise en forme

Le format d’affichage des objets retournés par les commandes (applets de commande, fonctions et scripts) est défini à l’aide de fichiers de mise en forme (format.ps1fichiers XML). Plusieurs de ces fichiers sont fournis par PowerShell pour définir le format d’affichage des objets retournés par les commandes fournies par PowerShell, telles que l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) retourné par l’applet de commande `Get-Process` . Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisés pour remplacer les formats d’affichage par défaut ou vous pouvez écrire un fichier de mise en forme personnalisé pour définir l’affichage des objets retournés par vos propres commandes.

> [!IMPORTANT]
> La mise en forme des fichiers ne détermine pas les éléments d’un objet qui sont retournés au pipeline. Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles, même si certains ne sont pas affichés.

PowerShell utilise les données de ces fichiers de mise en forme pour déterminer ce qui est affiché et comment les données affichées sont mises en forme. Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un script. Les scripts sont utilisés si vous souhaitez afficher une valeur qui n’est pas directement disponible à partir des propriétés d’un objet, telles que l’ajout de la valeur de deux propriétés d’un objet, puis l’affichage de la somme sous la forme d’un élément de données. La mise en forme des données affichées s’effectue en définissant des vues pour les objets que vous souhaitez afficher. Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet. Il n’existe aucune limite quant au nombre d’affichages que vous pouvez définir.

## <a name="common-features-of-formatting-files"></a>Fonctionnalités courantes de mise en forme des fichiers

Chaque fichier de mise en forme peut définir les composants suivants qui peuvent être partagés entre toutes les vues définies par le fichier :

- Paramètre de configuration par défaut, par exemple si les données affichées dans les lignes des tables seront affichées sur la ligne suivante si les données sont plus longues que la largeur de la colonne. Pour plus d’informations sur ces paramètres, consultez [définition des paramètres de configuration communs](./defining-common-configuration-features.md).

- Ensembles d’objets qui peuvent être affichés par l’une des vues du fichier de mise en forme. Pour plus d’informations sur ces jeux (appelés *jeux de sélection*), consultez [définition de jeux d’objets](./defining-selection-sets.md).

- Contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme. Les contrôles vous permettent de mieux contrôler la façon dont les données sont affichées. Pour plus d’informations sur les contrôles, consultez [définition de contrôles personnalisés](./creating-custom-controls.md).

## <a name="formatting-views"></a>Mise en forme des vues

Les vues de mise en forme peuvent afficher des objets dans un format de tableau, un format de liste, un format étendu et un format personnalisé. Pour l’essentiel, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent la vue. Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, tels que les informations de colonne et de ligne pour une vue de table.

La vue table répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes. Chaque colonne représente une propriété unique de l’objet ou une valeur de script. Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet, ou une combinaison de propriétés et de valeurs de script. Chaque ligne de la table représente un objet retourné. La création d’un affichage de table est très similaire à l’acheminement d’un objet vers l’applet de commande `Format-Table` . Pour plus d’informations sur cette vue, consultez [vue table](./creating-a-table-view.md).

Le mode liste répertorie les propriétés d’un objet ou une valeur de script dans une seule colonne. Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété, suivi de la valeur de la propriété ou du script. La création d’un affichage de liste est très similaire à la conduite d’un objet à l’applet de commande `Format-List` . Pour plus d’informations sur cette vue, consultez [affichage de liste](./creating-a-list-view.md).

Vue larges répertorie une seule propriété d’un objet ou une valeur de script dans une ou plusieurs colonnes. Il n’y a pas d’étiquette ou d’en-tête pour cette vue. La création d’un affichage étendu est très similaire à la conduite d’un objet à l’applet de commande `Format-Wide` . Pour plus d’informations sur cette vue, consultez [vue étendue](./creating-a-wide-view.md).

Affichage personnalisé affiche une vue personnalisable des propriétés de l’objet ou des valeurs de script qui n’adhère pas à la structure rigide des vues de table, des affichages de liste ou des vues larges. Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par une autre vue, telle qu’une vue de table ou une vue de liste. La création d’un affichage personnalisé est très similaire à la conduite d’un objet à l’applet de commande `Format-Custom` . Pour plus d’informations sur cette vue, consultez [vue personnalisée](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Composants d’une vue

Les exemples XML suivants illustrent les composants XML de base d’une vue. Les éléments XML individuels varient en fonction de la vue que vous souhaitez créer, mais les composants de base des vues sont les mêmes.

Pour commencer, chaque vue a un `Name` élément qui spécifie un nom convivial utilisé pour référencer la vue. `ViewSelectedBy`élément qui définit les objets .net affichés par la vue et un élément de *contrôle* qui définit la vue.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Dans l’élément de contrôle, vous pouvez définir un ou plusieurs éléments d' *entrée* . Si vous utilisez plusieurs définitions, vous devez spécifier les objets .NET qui utilisent chaque définition. En général, une seule entrée, avec une seule définition, est nécessaire pour chaque contrôle.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

Dans chaque élément d’entrée d’une vue, vous spécifiez les éléments *Item* qui définissent les propriétés .net ou les scripts affichés par cette vue.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Comme indiqué dans les exemples précédents, le fichier de mise en forme peut contenir plusieurs vues, une vue peut contenir plusieurs définitions et chaque définition peut contenir plusieurs éléments.

## <a name="example-of-a-table-view"></a>Exemple d’affichage de table

L’exemple suivant montre les balises XML utilisées pour définir une vue de table qui contient deux colonnes. L’élément [ViewDefinitions](./viewdefinitions-element-format.md) est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme. L’élément [View](./view-element-format.md) définit la table, la liste, la largeur ou la vue personnalisée spécifique. Dans chaque élément de [vue](./view-element-format.md) , l’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue, l’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue, et les différents éléments de contrôle (tels que l' `TableControl` élément illustré dans l’exemple suivant) définissent le type de la vue.

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue de liste](./creating-a-list-view.md)

[Création d’une vue de table](./creating-a-table-view.md)

[Création d’une vue large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Écriture d’un fichier de mise en forme et de types PowerShell](./writing-a-powershell-formatting-file.md)
