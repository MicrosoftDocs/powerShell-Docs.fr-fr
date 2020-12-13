---
ms.date: 09/13/2016
ms.topic: reference
title: Fichiers de mise en forme personnalisée
description: Fichiers de mise en forme personnalisée
ms.openlocfilehash: 16e1c1046e25b35ff346585a5fd930c449c04bf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653249"
---
# <a name="custom-formatting-files"></a>Fichiers de mise en forme personnalisée

Le format d’affichage des objets retournés par les applets de commande, les fonctions et les scripts est défini à l’aide de fichiers de mise en forme (format.ps1fichiers XML). Plusieurs de ces fichiers sont fournis par Windows PowerShell pour définir le format d’affichage par défaut pour les objets retournés par les applets de commande Windows PowerShell. Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisés pour remplacer les formats d’affichage par défaut ou pour définir l’affichage des objets retournés par vos propres commandes.

Windows PowerShell utilise les données de ces fichiers de mise en forme pour déterminer ce qui est affiché et la façon dont les données sont mises en forme. Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un bloc de script.  Les blocs de script sont utilisés si vous souhaitez afficher une valeur qui n’est pas directement disponible à partir des propriétés d’un objet. Par exemple, vous souhaiterez peut-être ajouter la valeur de deux propriétés d’un objet et afficher la somme sous la forme d’un élément de données distinct. Lorsque vous écrivez votre propre fichier de mise en forme, vous devez définir des *vues* pour les objets que vous souhaitez afficher. Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet. Il n’existe aucune limite quant au nombre d’affichages que vous pouvez définir.

> [!IMPORTANT]
> La mise en forme des fichiers ne détermine pas les éléments d’un objet qui sont retournés au pipeline. Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles.

## <a name="format-views"></a>Mettre en forme les vues

Les vues de mise en forme peuvent afficher des objets dans un format de tableau, un format de liste, un format étendu et un format personnalisé. Pour l’essentiel, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent une vue. Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, tels que les informations de colonne et de ligne pour une vue de table.

Les vues suivantes sont disponibles.

La vue table répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes. Chaque colonne représente une propriété de l’objet ou une valeur de bloc de script. Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet, ou une combinaison de propriétés et de valeurs de bloc de script. Chaque ligne de la table représente un objet retourné. Pour plus d’informations sur cette vue, consultez [vue table](../format/creating-a-table-view.md).

Le mode liste répertorie les propriétés d’un objet ou une valeur de bloc de script dans une seule colonne. Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété, suivi de la valeur de la propriété ou du bloc de script. Pour plus d’informations sur cette vue, consultez [affichage de liste](../format/creating-a-list-view.md).

Vue larges répertorie une seule propriété d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes. Il n’y a pas d’étiquette ou d’en-tête pour cette vue. Pour plus d’informations sur cette vue, consultez [vue étendue](../format/creating-a-wide-view.md).

Affichage personnalisé affiche une vue personnalisable des propriétés de l’objet ou des valeurs de bloc de script qui n’adhère pas à la structure rigide des vues de table, des affichages de liste ou des vues larges. Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par une autre vue, telle qu’une vue de table ou une vue de liste. Pour plus d’informations sur cette vue, consultez [vue personnalisée](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Afficher les éléments XML

L’exemple suivant montre les balises XML utilisées pour définir une vue de table qui contient deux colonnes. L’élément [ViewDefinitions](../format/viewdefinitions-element-format.md) est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme. L’élément [View](../format/view-element-format.md) définit la table, la liste, la largeur ou la vue personnalisée spécifique. Dans chaque vue, l’élément [Name](../format/name-element-for-view-format.md) spécifie le nom de la vue, l’élément [ViewSelectedBy](../format/viewselectedby-element-format.md) définit les objets qui utilisent la vue, et les différents éléments de contrôle (tels que l' `TableControl` élément) définissent le format de la vue.

```xml
ViewDefinitions
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

[Vue table](../format/creating-a-table-view.md)

[Mode liste](../format/creating-a-list-view.md)

[Vue étendue](../format/creating-a-wide-view.md)

[Vue personnalisée](../format/creating-custom-controls.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
