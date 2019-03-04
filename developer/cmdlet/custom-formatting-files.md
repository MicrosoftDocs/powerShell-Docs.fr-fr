---
title: Fichiers de mise en forme personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860605"
---
# <a name="custom-formatting-files"></a>Fichiers de mise en forme personnalisée

Le format d’affichage pour les objets retournés par les applets de commande, les fonctions et les scripts sont définis à l’aide de la mise en forme fichiers (format.ps1xml). Plusieurs de ces fichiers sont fournis par PowerShell de Windows pour définir le format d’affichage par défaut pour ces objets retournés par les applets de commande Windows PowerShell. Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisées pour remplacer les formats d’affichage par défaut ou pour définir l’affichage des objets retournés par vos propres commandes.

Windows PowerShell utilise les données dans ces fichiers de mise en forme pour déterminer ce qui est affiché et la mise en forme les données. Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un bloc de script.  Blocs de script sont utilisées si vous souhaitez afficher une valeur qui n’est pas disponible directement à partir des propriétés d’un objet. Par exemple, vous souhaitez ajouter la valeur des deux propriétés d’un objet et afficher la somme en tant qu’une partie des données. Lorsque vous écrivez votre propre mise en forme de fichier, vous devez définir *vues* pour les objets que vous souhaitez afficher. Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet. Il n’existe aucune limite au nombre de vues que vous pouvez définir.

> [!IMPORTANT]
> Fichiers de mise en forme ne déterminent pas les éléments d’un objet qui sont retournés au pipeline. Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles.

## <a name="format-views"></a>Vues de format

Vues de mise en forme peuvent afficher des objets dans un format de table, un format de liste, un grand format et un format personnalisé. La plupart du temps, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent une vue. Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, telles que les informations de ligne et de colonne pour une vue de table.

Les vues suivantes sont disponibles.

Affichage de la table répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes. Chaque colonne représente une propriété de l’objet ou une valeur de bloc de script. Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet ou une combinaison de propriétés et valeurs de bloc de script. Chaque ligne de la table représente un objet retourné. Pour plus d’informations sur cette vue, consultez [Table vue](../format/creating-a-table-view.md).

Affichage de liste répertorie les propriétés d’un objet ou une valeur de bloc de script dans une seule colonne. Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété suivie de la valeur du bloc de propriété ou un script. Pour plus d’informations sur cette vue, consultez [mode liste](../format/creating-a-list-view.md).

Affichage large répertorie une seule propriété d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes. Il n’existe aucune étiquette ou un en-tête pour cette vue. Pour plus d’informations sur cette vue, consultez [Affichage large](../format/creating-a-wide-view.md).

Vue personnalisée affiche une vue personnalisable de propriétés de l’objet ou valeurs de bloc de script qui n’est pas conforme à la structure rigide de vues des tables, des affichages de listes ou des vues de larges. Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par un autre affichage, comme une liste ou un affichage de la table. Pour plus d’informations sur cette vue, consultez [vue personnalisée](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Afficher les éléments XML

L’exemple suivant montre les balises XML utilisés pour définir une vue de table qui contient deux colonnes. Le [ViewDefinitions](../format/viewdefinitions-element-format.md) élément est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme. Le [vue](../format/view-element-format.md) élément définit la table spécifique, la liste, l’affichage large ou personnalisé. Dans chaque vue, le [nom](../format/name-element-for-view-format.md) élément spécifie le nom de la vue, le [ViewSelectedBy](../format/viewselectedby-element-format.md) élément définit les objets qui utilisent la vue et les éléments de contrôle différent (tel que le `TableControl` élément) définissent le format de la vue.

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

[Vue de table](../format/creating-a-table-view.md)

[Affichage de liste](../format/creating-a-list-view.md)

[Affichage large](../format/creating-a-wide-view.md)

[Vue personnalisée](../format/creating-custom-controls.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
