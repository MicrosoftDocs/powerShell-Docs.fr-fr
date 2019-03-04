---
title: Vue d’ensemble du fichier de mise en forme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863295"
---
# <a name="formatting-file-overview"></a>Vue d’ensemble des fichiers de mise en forme

Le format d’affichage pour les objets qui sont retournés par les commandes (applets de commande, fonctions et des scripts) sont définis à l’aide de fichiers de mise en forme (fichiers format.ps1xml). Plusieurs de ces fichiers sont fournis par PowerShell pour définir le format d’affichage pour les objets retournés par les commandes PowerShell fourni, comme le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet retourné par la `Get-Process` applet de commande. Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisées pour remplacer les formats d’affichage par défaut, ou vous pouvez écrire un fichier de mise en forme personnalisé pour définir l’affichage des objets retournés par vos propres commandes.

> [!IMPORTANT]
> Fichiers de mise en forme ne déterminent pas les éléments d’un objet qui sont retournés au pipeline. Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles même si certaines ne sont pas affichés.

PowerShell utilise les données dans ces fichiers de mise en forme pour déterminer ce qui est affiché et la mise en forme les données affichées. Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un script. Les scripts sont utilisés si vous souhaitez afficher une valeur qui n’est pas disponible directement à partir des propriétés d’un objet, telles que l’ajout de la valeur des deux propriétés d’un objet, puis en affichant la somme en tant qu’un élément de données. Mise en forme des données affichées est effectuée en définissant des vues pour les objets que vous souhaitez afficher. Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet. Il n’existe aucune limite au nombre de vues que vous pouvez définir.

## <a name="common-features-of-formatting-files"></a>Fonctionnalités communes de la mise en forme de fichiers

Chaque fichier de mise en forme peut définir les composants suivants qui peuvent être partagées entre toutes les vues définies par le fichier :

- Paramètre de configuration, tels que si les données affichées dans les lignes de tables seront affichera sur la ligne suivante si les données sont supérieure à la largeur de la colonne par défaut. Pour plus d’informations sur ces paramètres, consultez [définissant les paramètres de Configuration courants](./defining-common-configuration-features.md).

- Ensembles d’objets qui peuvent être affichées par tous les affichages du fichier de mise en forme. Pour plus d’informations sur ces ensembles (appelé *des jeux de sélection*), consultez [définition définit des objets](./defining-selection-sets.md).

- Contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme. Contrôles vous donnent un contrôle plus précis sur la façon dont les données sont affichées. Pour plus d’informations sur les contrôles, consultez [définition des contrôles personnalisés](./creating-custom-controls.md).

## <a name="formatting-views"></a>Mise en forme de vues

Vues de mise en forme peuvent afficher des objets dans un format de table, format de liste, format large et format personnalisé. La plupart du temps, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent la vue. Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, telles que les informations de ligne et de colonne pour une vue de table.

Affichage de tableau répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes. Chaque colonne représente une propriété unique de l’objet ou une valeur de script. Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet ou une combinaison de propriétés et valeurs de script. Chaque ligne de la table représente un objet retourné. Création d’une vue de table est très similaire à quand vous dirigez un objet à le `Format-Table` applet de commande. Pour plus d’informations sur cette vue, consultez [Table vue](./creating-a-table-view.md).

Liste de la vue répertorie les propriétés d’un objet ou une valeur de script dans une seule colonne. Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété suivie de la valeur de la propriété ou un script. Création d’un affichage de liste est très similaire à la canalisation d’un objet à le `Format-List` applet de commande. Pour plus d’informations sur cette vue, consultez [mode liste](./creating-a-list-view.md).

Affichage large répertorie une seule propriété d’un objet ou une valeur de script dans une ou plusieurs colonnes. Il n’existe aucune étiquette ou un en-tête pour cette vue. Création d’un affichage plus large est très similaire à la canalisation d’un objet à le `Format-Wide` applet de commande. Pour plus d’informations sur cette vue, consultez [Affichage large](./creating-a-wide-view.md).

Vue personnalisée affiche une vue personnalisable de propriétés de l’objet ou valeurs de script qui n’est pas conforme à la structure rigide de vues des tables, des affichages de listes ou des vues de larges. Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par un autre affichage, comme une liste ou un affichage de la table. Création d’une vue personnalisée est très similaire à la canalisation d’un objet à le `Format-Custom` applet de commande. Pour plus d’informations sur cette vue, consultez [vue personnalisée](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Composants d’une vue

Les exemples XML suivants indiquent les composants de base XML d’une vue. Les éléments XML individuels varient selon le mode dans lequel vous souhaitez créer, mais les composants de base des vues sont identiques.

Pour commencer, chaque vue a un `Name` élément qui spécifie un nom convivial qui est utilisé pour référencer la vue. un `ViewSelectedBy` élément qui définit les objets .NET sont affichés par la vue, et un *contrôle* élément qui définit la vue.

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

Dans l’élément de contrôle, vous pouvez définir un ou plusieurs *entrée* éléments. Si vous utilisez plusieurs définitions, vous devez spécifier les objets .NET utilisent chaque définition. En général qu’une seule entrée, avec une seule définition, est nécessaire pour chaque contrôle.

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

Au sein de chaque élément d’entrée d’une vue, vous spécifiez le *élément* éléments qui définissent les propriétés .NET ou les scripts qui sont affichés par cette vue.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Comme indiqué dans les exemples précédents, le fichier de mise en forme peut contenir plusieurs vues, une vue peut contenir plusieurs définitions, et chaque définition peut contenir plusieurs éléments.

## <a name="example-of-a-table-view"></a>Exemple d’une vue de Table

L’exemple suivant montre les balises XML utilisés pour définir une vue de table qui contient deux colonnes. Le [ViewDefinitions](./viewdefinitions-element-format.md) élément est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme. Le [vue](./view-element-format.md) élément définit la table spécifique, la liste, l’affichage large ou personnalisé. Dans chacun d’eux [vue](./view-element-format.md) élément, le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue, le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue et les différentes contrôler les éléments (tels que le `TableControl` élément présenté dans l’exemple suivant) définissent le type de la vue.

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
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Voir aussi

[Création d’une vue liste](./creating-a-list-view.md)

[Création d’une vue de Table](./creating-a-table-view.md)

[Création d’un affichage plus large](./creating-a-wide-view.md)

[Création de contrôles personnalisés](./creating-custom-controls.md)

[Écriture d’une mise en forme de PowerShell et le fichier de Types](./writing-a-powershell-formatting-file.md)
