---
title: Référence du schéma XML de format | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 4dfe27a5105d82fa18e35f965f92fad16d390a2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857785"
---
# <a name="format-schema-xml-reference"></a>Informations de référence sur le XML des schémas de format

Les rubriques de cette section décrivent les éléments XML utilisés par la mise en forme de fichiers (Format.ps1xml). Les fichiers de mise en forme définissent comment l’objet .NET est affichée ; elles ne changent pas l’objet lui-même.

## <a name="in-this-section"></a>Dans cette section

[Élément d’alignement pour TableColumnHeader pour la table (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) définit comment les données dans un en-tête de colonne s’affiche.

[Élément d’alignement pour TableColumnItem pour la table (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) définit comment les données dans la ligne sont affichées.

[AutoSize Élément pour la table (Format)](./autosize-element-for-tablecontrol-format.md) Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.

[AutoSize Élément pour WideControl (Format)](./autosize-element-for-widecontrol-format.md) Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.

[ColumnNumber Élément pour WideControl (Format)](./columnnumber-element-for-widecontrol-format.md) Spécifie le nombre de colonnes affichées dans l’affichage plus large.

[Élément de configuration (Format)](./configuration-element-format.md) représente l’élément de niveau supérieur du fichier de mise en forme.

[Control, élément pour les contrôles de Configuration (Format)](./control-element-for-controls-for-configuration-format.md) définit un contrôle commun qui peut être utilisé par toutes les vues de la mise en forme du fichier et le nom qui est utilisé pour référencer le contrôle.

[Control, élément pour les contrôles de vue (Format)](./control-element-for-controls-for-view-format.md) définit un contrôle qui peut être utilisé par la vue et le nom qui est utilisé pour référencer le contrôle.

[Contrôle d’élément de Configuration (Format)](./controls-element-for-configuration-format.md) définit les contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme.

[Controls, élément de vue (Format)](./controls-element-for-view-format.md) définit les contrôles d’affichage qui peuvent être utilisées par une vue spécifique.

[CustomControl Élément pour le contrôle de Configuration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) définit un contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[CustomControl Élément pour le contrôle pour les contrôles de vue (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md) définit un contrôle qui est utilisé par la vue.

[CustomControl Élément pour GroupBy (Format)](./customcontrol-element-for-groupby-format.md) définit le contrôle personnalisé qui affiche le nouveau groupe.

[CustomControl Élément (Format)](./customcontrol-element-for-groupby-format.md) définit un format de contrôle personnalisé pour la vue.

[CustomControlName Élément pour ExpressionBinding pour les contrôles de Configuration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Spécifie le nom d’un contrôle courant. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[CustomControlName Élément pour ExpressionBindine pour les contrôles de vue (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Spécifie le nom d’un contrôle commun ou un contrôle d’affichage. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[CustomControlName Élément de GroupBy (Format)](./customcontrolname-element-for-groupby-format.md) Spécifie le nom d’un contrôle personnalisé qui est utilisé pour afficher le nouveau groupe. Cet élément est utilisé lors de la définition d’une table, la liste, l’affichage de contrôle de larges ou personnalisé.

[CustomEntry Élément pour CustomControl pour les contrôles de Configuration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) fournit une définition du contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[CustomEntry Élément pour CustomEntries pour les contrôles de vue (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md) fournit une définition du contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[CustomEntry Élément pour CustomEntries pour la vue (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) fournit une définition de la vue de contrôle personnalisé.

[CustomEntry Élément pour CustomControl pour GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md) fournit une définition du contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[CustomEntries Élément pour CustomControl pour la Configuration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) fournit les définitions d’un contrôle courant. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[CustomEntries Élément pour CustomControl pour les contrôles de vue (Format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[CustomEntries Élément pour CustomControl pour GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md) fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[CustomEntries Élément pour CustomControl de vue (Format)](./customentries-element-for-customcontrol-for-view-format.md) fournit les définitions de la vue de contrôle personnalisé. L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.

[CustomItem Élément pour CustomEntry pour les contrôles de Configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md) définit les données affichées par le contrôle et comment il est affiché. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[CustomItem Élément pour CustomEntry pour les contrôles de vue (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md) définit les données affichées par le contrôle et comment il est affiché. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[CustomItem Élément pour CustomEntry pour la vue (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) définit les données affichées par la vue de contrôle personnalisé et comment il est affiché. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[CustomItem Élément pour CustomEntry pour GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md) définit les données affichées par la vue de contrôle personnalisé et comment il est affiché. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[DefaultSettings Élément (Format)](./defaultsettings-element-format.md) définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme. Paramètres courants comprennent l’affichage des erreurs, habillage du texte dans les tables, en définissant la façon dont les collections sont développées et bien plus encore.

[DisplayError Élément (Frmat)](./displayerror-element-format.md) Spécifie que la chaîne #ERR est affichée lorsqu’une erreur se produit à afficher un élément de données.

[EntrySelectedBy Élément pour CustomEntry pour les contrôles de Configuration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour ce contrôle à utiliser. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[EntrySelectedBy Élément pour CustomEntry pour les contrôles de vue (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[EntrySelectedBy Élément pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour cette entrée à utiliser.

[EntrySelectedBy Élément pour EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md) définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour cette définition à utiliser.

[EntrySelectedBy Élément pour CustomEntry pour GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md) définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[EntrySelectedBy Élément pour ListEntry pour ListControl (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) définit les types .NET qui utilisent cette définition de la vue liste ou la condition qui doit exister pour cette définition à utiliser. Dans la plupart des cas qu’une seule définition est nécessaire pour un affichage de liste. Toutefois, vous pouvez fournir plusieurs définitions pour l’affichage de liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.

[EntrySelectedBy Élément pour TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) définit les types .NET dont les valeurs propriété sont affichés dans la ligne.

[EntrySelectedBy Élément pour WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md) définit les types .NET qui utilisent cette définition de l’affichage plus large ou la condition qui doit exister pour cette définition à utiliser.

[EnumerableExpansion Élément (Format)](./enumerableexpansion-element-format.md) définit la collection de .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.

[EnumerableExpansions Élément (Format)](./enumerableexpansions-element-format.md) définit comment les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.

[EnumerateCollection Élément pour ExpressionBinding pour les contrôles de Configuration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) spécifié que les éléments des collections sont affichés par le contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[EnumerateCollection Élément pour ExpressionBinding pour les contrôles de vue (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) spécifié que les éléments des collections sont affichés. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[EnumerateCollection Élément pour l’Expression de liaison pour CustomControl de vue (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) indique que les éléments des collections sont affichés. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[EnumerateCollection Élément pour ExpressionBinding pour GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) indique que les éléments des collections sont affichés. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[Développez l’élément (Format)](./expand-element-format.md) spécifie la façon dont l’objet de collection est développé pour cette définition.

[ExpressionBinding Élément pour CustomItem pour les contrôles de Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[ExpressionBinding Élément pour CustomItem pour les contrôles de vue (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[ExpressionBinding Élément pour CustomItem pour CustomControl de vue (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[ExpressionBinding Élément pour CustomItem pour GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md) définit les données qui sont affichées par le contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[FirstLineHanging Élément pour Frame pour les contrôles de Configuration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[FirstLineHanging Élément de cadre de contrôles de vue (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[FirstLineHanging Élément pour Frame pour CustomControl de vue (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[FirstLineHanging Élément pour Frame pour GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[FirstLineIndent Élément pour Frame pour les contrôles de Configuration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[FirstLineIndent Élément de cadre de contrôles de vue (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[Élément de FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[FirstLineIndent Élément pour Frame pour GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[FormatString Élément de ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche.

[FormatString Élément pour TableColumnItem (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie un modèle de format qui définit comment la valeur de propriété ou un script de la table est affichée.

[FormatString Élément pour WideItem pour WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue.

[Élément des frames pour CustomItem pour les contrôles de Configuration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément des frames pour CustomItem pour les contrôles de vue (Format)](./frame-element-for-customitem-for-controls-for-view-format.md) définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[Élément des frames pour CustomItem pour CustomControl de vue (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[Élément des frames pour CustomItem pour GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md) définit l’affichage des données, telles que les données le décalage vers la gauche ou droite. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[GroupBy Élément de vue (Format)](./groupby-element-for-view-format.md) définit la façon dont Windows PowerShell affiche un nouveau groupe d’objets.

[HideTableHeaders Élément (Format)](./hidetableheaders-element-format.md) Spécifie que les en-têtes de la table ne sont pas affichés.

[ItemSelectionCondition Élément pour ExpressionBinding pour les contrôles de Configuration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) définit la condition qui doit exister pour ce contrôle à utiliser. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[ItemSelectionCondition Élément de ExpressionBinding pour les contrôles de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) définit la condition qui doit exister pour ce contrôle à utiliser. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[ItemSelectionCondition Élément pour l’Expression de liaison pour CustomControl de vue (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) définit la condition qui doit exister pour ce contrôle à utiliser. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[ItemSelectionCondition Élément pour ExpressionBinding pour GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) définit la condition qui doit exister pour ce contrôle à utiliser. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[ItemSelectionCondition Élément pour ListItem (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) définit la condition qui doit exister pour cet élément de liste à utiliser.

[L’étiquette d’élément pour ListItem pour ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) indique le nom de la valeur de propriété ou un script dans la ligne.

[L’étiquette d’élément pour GroupBy (Format)](./label-element-for-groupby-format.md) spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.

[L’étiquette d’élément pour TableColumnHeader (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) définit l’étiquette qui s’affiche en haut d’une colonne.

[Élément Macintosh pour Frame pour les contrôles de Configuration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de gauche. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément Macintosh de cadre de contrôles de vue (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de gauche. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[Élément Macintosh pour Frame pour CustomControl de vue (Format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de gauche. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[Élément Macintosh pour Frame pour GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de gauche. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[Élément objet ListControl (Format)](./listcontrol-element-format.md) définit un format de liste pour la vue.

[ListEntry Élément (Format)](./listentry-element-for-listcontrol-format.md) fournit une définition de la vue liste.

[Élément situés (Format)](./listentries-element-for-listcontrol-format.md) définit comment les lignes de la vue de liste sont affichées.

[ListItem Élément (Format)](./listitem-element-for-listitems-for-listcontrol-format.md) définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.

[ListItems Élément (Format)](./listitems-element-for-listentry-for-listcontrol-format.md) définit les propriétés et les scripts qui sont affichés dans la vue liste.

[Nom d’élément de contrôle pour les contrôles de Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md) Spécifie le nom du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Nom d’élément pour SelectionSet (Format)](./name-element-for-selectionset-format.md) Spécifie le nom utilisé pour référencer le jeu de sélection.

[Nom d’élément de vue (Format)](./name-element-for-view-format.md) Spécifie le nom qui est utilisé pour identifier la vue.

[Élément de saut de ligne pour CustomItem pour les contrôles de Configuration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément de saut de ligne pour CustomItem pour les contrôles de vue (Format)](./newline-element-for-customitem-for-controls-for-view-format.md) ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[Élément de saut de ligne pour CustomItem pour CustomControl de vue (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[Élément de saut de ligne pour CustomItem pour GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md) ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[PropertyName Élément pour ExpressionBinding pour les contrôles de Configuration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) spécifie la propriété .NET dont la valeur est affichée par le contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[PropertyName Élément pour ExpressionBinding pour les contrôles de vue (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) spécifie la propriété .NET dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[PropertyName Élément pour ExpressionBinding pour CustomControl de vue (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) spécifie la propriété .NET dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé

[PropertyName Élément pour ExpressionBinding pour GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) spécifie la propriété .NET dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[PropertyName Élément pour GroupBy (Format)](./propertyname-element-for-groupby-format.md) spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.

[PropertyName Élément pour ItemSeclectionCondition pour les contrôles de Configuration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[PropertyName Élément pour ItemSelectionCondition pour les contrôles de vue (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[PropertyName Élément pour ItemSelectionCondition pour CustomControl de vue (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[PropertyName Élément pour ItemSelectionCondition pour GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[PropertyName Élément pour ItemSelectionCondition pour ListItem (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et la vue est utilisée. Cet élément est utilisé lors de la définition d’un affichage de liste.

[PropertyName Élément pour ListItem pour un objet ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md) spécifie la propriété .NET dont la valeur est affichée dans la liste.

[PropertyName Élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et l’entrée est utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[PropertyName Élément pour SelectionCondition pour les contrôles de vue (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et l’entrée est utilisée. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[PropertyName Élément pour SelectionCondition pour CustomControl de vue (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[PropertyName Élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée.

[PropertyName Élément pour SelectionCondition pour GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[PropertyName Élément pour SelectionCondition pour EmtrySelectedBy pour ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et l’entrée de liste est utilisée.

[PropertyName Élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie, et l’entrée de table est utilisée.

[PropertyName Élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée.

[PropertyName Élément pour TableColumnItem (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la colonne de la ligne.

[PropertyName Élément pour WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété de l’objet dont la valeur est affichée dans l’affichage plus large.

[RightIndent Élément pour Frame pour les contrôles de Configuration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[RightIndent Élément de cadre de contrôles de vue (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de droite. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[Élément de RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de droite. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[RightIndent Élément pour Frame pour GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères les données s’éloigne de la marge de droite. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[ScriptBlock Élément pour ExpressionBinding pour les contrôles de Configuration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Spécifie le script dont la valeur est affichée par le contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[ScriptBlock Élément pour ExpressionBinding pour les contrôles de vue (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Spécifie le script dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[ScriptBlock Élément pour ExpressionBinding pour CustomCustomControl pour la vue (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Spécifie le script dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[ScriptBlock Élément pour ExpressionBinding pour GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Spécifie le script dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[ScriptBlock Élément pour GroupBy (Format)](./scriptblock-element-for-groupby-format.md) Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.

[ScriptBlock Élément pour ItemSelectionCondition pour les contrôles de Configuration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[ScriptBlock Élément pour ItemSelectionCondition pour les contrôles de vue (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[ScriptBlock Élément pour ItemSelectionCondition pour CustomControl de vue (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[ScriptBlock Élément pour ItemSelectionCondition pour GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[ScriptBlock Élément pour ItemSelectionCondition pour ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et l’élément de liste est utilisé. Cet élément est utilisé lors de la définition d’un affichage de liste.

[ScriptBlock Élément pour ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Spécifie le script dont la valeur est affichée dans la ligne de la liste.

[ScriptBlock Élément pour SelectionCondition pour les contrôles de Configuration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[ScriptBlock Élément pour SelectionCondition pour les contrôles de vue (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[ScriptBlock Élément pour SelectionCondition pour CustomControl de vue (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[ScriptBlock Élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie le script qui déclenche la condition.

[ScriptBlock Élément pour SelectionCondition pour GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[ScriptBlock Élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et l’entrée de liste est utilisée.

[ScriptBlock Élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Spécifie le bloc de script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et l’entrée de table est utilisée.

[ScriptBlock Élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie, et la définition de l’entrée large est utilisée.

[ScriptBlock Élément pour TableColumnItem (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Spécifie le script dont la valeur est affichée dans la colonne de la ligne.

[ScriptBlock Élément pour WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Spécifie le script dont la valeur est affichée dans l’affichage plus large.

[SelectionCondition Élément pour EntrySelectedBy pour CustomEntry pour la Configuration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) définit une condition qui doit exister pour une définition commune de contrôle à utiliser. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[SelectionCondition Élément pour EntrySelectedBy pour les contrôles de vue (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) définit une condition qui doit exister pour la définition du contrôle à utiliser. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[SelectionCondition Élément pour EntrySelectedBy pour CustomControl de vue (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[SelectionCondition Élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) définit la condition qui doit exister pour développer la collection d’objets de cette définition.

[SelectionCondition Élément pour EntrySelectedBy pour GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[SelectionCondition Élément pour EntrySelectedBy pour ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) définit la condition qui doit exister pour pouvoir utiliser cette définition de la vue liste. Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de liste.

[SelectionCondition Élément pour EntrySelectedBy pour TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) définit la condition qui doit exister pour pouvoir le pour utiliser pour cette définition de la vue de table. Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de table.

[SelectionCondition Élément pour EntrySelectedBy pour WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) définit la condition qui doit exister pour cette définition à utiliser. Il n’existe aucune limite au nombre de conditions de sélection qui peut être spécifié pour une définition de l’entrée de large.

[SelectionSet Élément (Format)](./selectionset-element-format.md) définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.

[SelectionSetName Élément pour EntrySelectedBy pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) spécifie un ensemble de types .NET qui utilisent cette définition du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[SelectionSetName Élément pour EntrySelectedBy pour les contrôles de vue (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) spécifie un ensemble de types .NET qui utilisent cette définition du contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[SelectionSetName Élément pour EntrySelectedBy pour CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) spécifie un jeu d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.

[SelectionSetName Élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie l’ensemble des types .NET qui sont développées par cette définition.

[SelectionSetName Élément pour EntrySelectedBy pour GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) spécifie un jeu d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[SelectionSetName Élément pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) spécifie un jeu d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.

[SelectionSetName Élément pour EntrySelectedBy pour TableRowEntry (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) spécifie un ensemble de .NET types l’utilisation de cette entrée de la vue de table. Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.

[SelectionSetName Élément pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) spécifie un jeu d’objets .NET pour la définition. La définition est utilisée chaque fois qu’un de ces objets s’affiche.

[SelectionSetName Élément pour SelectionCondition pour les contrôles de Configuration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[SelectionSetName Élément pour SelectionCondition pour les contrôles de vue (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[EntrySelectedBy Élément pour CustomEntry pour la vue (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[SelectionSetName Élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie.

[SelectionSetName Élément pour SelectionCondition pour GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[SelectionSetName Élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de la vue de liste.

[SelectionSetName Élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de la vue de table.

[SelectionSetName Élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de l’affichage plus large.

[SelectionSetName Élément pour ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets .NET qui sont affichés par la vue.

[SelectionSets Élément (Format)](./selectionsets-element-format.md) définit les ensembles d’objets .NET qui peuvent être utilisées par les affichages de chaque format.

[ShowError Élément (Format)](./showerror-element-format.md) Spécifie que l’enregistrement d’erreur complète est affichée lorsqu’une erreur se produit lors de l’affichage d’un élément de données.

[TableColumnHeader Élément pour TableHeaders pour la table (Format)](./tablecolumnheader-element-format.md) définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.

[TableColumnItem Élément (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.

[TableColumnItems Élément (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.

[Élément de table (Format)](./tablecontrol-element-format.md) définit un format de table pour une vue.

[TableHeaders Élément (Format)](./tableheaders-element-format.md) définit les en-têtes pour les colonnes d’une table.

[TableRowEntries Élément (Format)](./tablerowentries-element-for-tablecontrol-format.md) définit les lignes de la table.

[TableRowEntry Élément (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) définit les données qui s’affiche dans une ligne de la table.

[Élément de texte pour CustomItem pour les contrôles de Configuration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md) spécifie texte qui est ajouté aux données qui sont affichées par le contrôle, par exemple une étiquette, des crochets pour délimiter les données et les espaces à mettre en retrait les données. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément de texte pour CustomItem pour les contrôles de vue (Format)](./text-element-for-customitem-for-controls-for-view-format.md) spécifie texte qui est ajouté aux données qui sont affichées par le contrôle, par exemple une étiquette, des crochets pour délimiter les données et les espaces à mettre en retrait les données. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[Élément de texte pour CustomItem (Format)](./text-element-for-customitem-for-customview-for-view-format.md) spécifie texte qui est ajouté aux données qui sont affichées par le contrôle, par exemple une étiquette, des crochets pour délimiter les données et les espaces à mettre en retrait les données. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[Élément de texte pour CustomItem pour GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md) spécifie texte qui est ajouté aux données qui sont affichées par le contrôle, par exemple une étiquette, des crochets pour délimiter les données et les espaces à mettre en retrait les données. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[TypeName Élément pour EntrySelectedBy pour les contrôles de Configuration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) spécifie un type .NET qui utilise cette définition du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[TypeName Élément pour EntrySelectedBy pour les contrôles de vue (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) spécifie un type .NET qui utilise cette définition du contrôle. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[TypeName Élément pour EntrySelectedBy pour CustomEntry pour la vue (Format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) spécifie un type .NET qui utilise cette définition de la vue de contrôle personnalisé. Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une définition.

[TypeName Élément pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) spécifie un type .NET qui est étendu par cette définition. Cet élément est utilisé lors de la définition des paramètres de valeur par défaut.

[TypeName Élément pour EntrySelectedBy pour GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md) spécifie un type .NET qui utilise cette définition du contrôle personnalisé. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[TypeName Élément pour EntrySelectedBy pour ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) spécifie un type .NET qui utilise cette entrée de la liste. Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une entrée de liste.

[TypeName Élément pour EntrySelectedBy pour TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) spécifie un type .NET qui utilise cette entrée de la vue de table. Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une entrée de table.

[TypeName Élément pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md) spécifie un type .NET pour la définition. La définition est utilisée chaque fois que cet objet s’affiche.

[TypeName Élément pour SelectionCondition pour les contrôles de Configuration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[TypeName Élément pour SelectionCondition pour les contrôles de vue (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.

[TypeName Élément pour SelectionCondition pour CustomControl de vue (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.

[TypeName Élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) spécifie un type .NET qui déclenche la condition.

[TypeName Élément pour SelectionCondition pour GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md) spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.

[TypeName Élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, l’entrée de liste est utilisée.

[TypeName Élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, la condition est remplie, et la ligne de table est utilisée.

[TypeName Élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, la définition est utilisée.

[Élément de nom de type pour les Types (Format)](./typename-element-for-types-format.md) Spécifie le type .NET d’un objet qui appartient au jeu de sélection.

[TypeName Élément pour ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md) spécifie un objet .NET qui est affiché par la vue.

[Types d’élément (Format)](./types-element-for-selectionset-format.md) définit les objets .NET qui sont définies dans la sélection.

[Afficher l’élément (Format)](./view-element-format.md) définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.

[ViewDefinitions Élément (Format)](./viewdefinitions-element-format.md) définit les vues utilisées pour afficher les objets.

[ViewSelectedBy Élément (Format)](./viewselectedby-element-format.md) définit les objets .NET qui sont affichés par la vue.

[WideControl Élément (Format)](./widecontrol-element-format.md) définit une liste à l’échelle (valeur unique) mettre en forme pour l’affichage. Cette vue affiche une valeur de propriété unique ou une valeur de script pour chaque objet.

[WideEntries Élément (Format)](./wideentries-element-for-widecontrol-format.md) fournit les définitions de l’affichage plus large. L’affichage large doit spécifier une ou plusieurs définitions.

[WideEntry Élément (Format)](./wideentry-element-for-widecontrol-format.md) fournit une définition de l’affichage plus large.

[WideItem Élément (Format)](./wideitem-element-for-widecontrol-format.md) définit la propriété ou un script dont la valeur est affichée.

[Élément de la largeur (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) définit la largeur (en caractères) d’une colonne.

[Encapsulez l’élément (Format)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) Spécifie que le texte qui dépasse la largeur de colonne est affichée sur la ligne suivante.

[WrapTables Élément (Format)](./wraptables-element-format.md) Spécifie que les données dans une cellule de tableau sont déplacées vers la ligne suivante si les données sont supérieure à la largeur de la colonne.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
