---
ms.date: 09/13/2016
ms.topic: reference
title: Informations de référence sur le XML des schémas de format
description: Informations de référence sur le XML des schémas de format
ms.openlocfilehash: f59016df91fe458393655853b9eada0875a8dcb1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667927"
---
# <a name="format-schema-xml-reference"></a>Informations de référence sur le XML des schémas de format

Les rubriques de cette section décrivent les éléments XML utilisés par la mise en forme des fichiers (Format.ps1fichiers XML). Les fichiers de mise en forme définissent la façon dont l’objet .NET est affiché. elles ne modifient pas l’objet lui-même.

## <a name="in-this-section"></a>Dans cette section

[Élément Alignment pour TableColumnHeader pour table ((format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) Définit le mode d’affichage des données dans un en-tête de colonne.

[Élément Alignment pour TableColumnItem pour table ((format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) Définit le mode d’affichage des données dans la ligne.

[AutoSize, élément de table ((format)](./autosize-element-for-tablecontrol-format.md) Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.

[AutoSize, élément de WideControl (format)](./autosize-element-for-widecontrol-format.md) Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.

[Élément ColumnNumber pour WideControl (format)](./columnnumber-element-for-widecontrol-format.md) Spécifie le nombre de colonnes affichées dans la vue étendue.

[Élément configuration (format)](./configuration-element-format.md) Représente l’élément de niveau supérieur du fichier de mise en forme.

[Élément Control pour les contrôles de configuration (format)](./control-element-for-controls-for-configuration-format.md) Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.

[Control, élément de Controls pour View (format)](./control-element-for-controls-for-view-format.md) Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.

[Controls, élément de configuration (format)](./controls-element-for-configuration-format.md) Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.

[Controls, élément de View (format)](./controls-element-for-view-format.md) Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.

[CustomControl, élément de Control pour la configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) Définit un contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[CustomControl, élément de Control pour les contrôles pour View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md) Définit un contrôle qui est utilisé par la vue.

[CustomControl, élément de GroupBy (format)](./customcontrol-element-for-groupby-format.md) Définit le contrôle personnalisé qui affiche le nouveau groupe.

[CustomControl, élément (format)](./customcontrol-element-for-groupby-format.md) Définit un format de contrôle personnalisé pour la vue.

[Élément CustomControlName pour ExpressionBinding pour les contrôles de configuration (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Spécifie le nom d’un contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément CustomControlName pour ExpressionBindine pour les contrôles pour View (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Spécifie le nom d’un contrôle commun ou d’un contrôle View. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément CustomControlName de GroupBy (format)](./customcontrolname-element-for-groupby-format.md) Spécifie le nom d’un contrôle personnalisé utilisé pour afficher le nouveau groupe. Cet élément est utilisé lors de la définition d’une vue de contrôle de table, de liste, étendue ou personnalisée.

[Élément CustomEntry pour CustomControl pour les contrôles de configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) Fournit une définition du contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md) Fournit une définition du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément CustomEntry pour CustomEntries pour View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) Fournit une définition de l’affichage de contrôle personnalisé.

[Élément CustomEntry pour CustomControl pour GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md) Fournit une définition du contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément CustomEntries pour CustomControl pour la configuration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) Fournit les définitions d’un contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément CustomEntries pour CustomControl pour les contrôles View (format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) Fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément CustomEntries pour CustomControl pour GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md) Fournit les définitions pour le contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément CustomEntries pour CustomControl pour View (format)](./customentries-element-for-customcontrol-for-view-format.md) Fournit les définitions de l’affichage de contrôle personnalisé. L’affichage de contrôle personnalisé doit spécifier une ou plusieurs définitions.

[Élément CustomItem pour CustomEntry pour les contrôles de configuration](./customitem-element-for-customentry-for-controls-for-configuration-format.md) Définit les données affichées par le contrôle et leur mode d’affichage. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément CustomItem pour CustomEntry pour les contrôles pour View (format)](./customitem-element-for-customentry-for-controls-for-view-format.md) Définit les données affichées par le contrôle et leur mode d’affichage. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément CustomItem pour CustomEntry pour View (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément CustomItem pour CustomEntry pour GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md) Définit les données affichées par l’affichage de contrôle personnalisé et leur mode d’affichage. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément DefaultSettings (format)](./defaultsettings-element-format.md) Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme. Les paramètres courants incluent l’affichage des erreurs, l’habillage du texte dans les tables, la définition du développement des collections, etc.

[Élément DisplayError (format)](./displayerror-element-format.md) Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.

[Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.

[Élément EntrySelectedBy pour EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md) Définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour que cette définition soit utilisée.

[Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md) Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément EntrySelectedBy pour ListEntry pour ListControl (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Définit les types .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée. Dans la plupart des cas, une seule définition est nécessaire pour une vue liste. Toutefois, vous pouvez fournir plusieurs définitions pour le mode liste si vous souhaitez utiliser la même vue de liste pour afficher des données différentes pour différents objets.

[Élément EntrySelectedBy pour TableRowEntry (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Définit les types .NET dont les valeurs de propriété sont affichées dans la ligne.

[Élément EntrySelectedBy pour WideEntry (format)](./entryselectedby-element-for-wideentry-format.md) Définit les types .NET qui utilisent cette définition de la vue étendue ou de la condition qui doit exister pour que cette définition soit utilisée.

[Élément EnumerableExpansion (format)](./enumerableexpansion-element-format.md) Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.

[Élément EnumerableExpansions (format)](./enumerableexpansions-element-format.md) Définit la façon dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.

[Élément EnumerateCollection pour ExpressionBinding pour les contrôles de configuration (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) Spécifie que les éléments des collections sont affichés par le contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément EnumerateCollection pour ExpressionBinding pour les contrôles pour View (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) Spécifie que les éléments des collections sont affichés. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément EnumerateCollection pour la liaison d’expression pour CustomControl pour View (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Spécifie que les éléments des collections sont affichés. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément EnumerateCollection pour ExpressionBinding pour GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Spécifie que les éléments des collections sont affichés. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Expand, élément (format)](./expand-element-format.md) Spécifie comment l’objet de collection est développé pour cette définition.

[Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément ExpressionBinding pour CustomItem pour CustomControl pour View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément ExpressionBinding pour CustomItem pour GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md) Définit les données affichées par le contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément FirstLineHanging pour frame pour les contrôles de configuration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément FirstLineHanging de frame de contrôles de vue (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément FirstLineHanging pour frame pour CustomControl pour View (format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément FirstLineHanging pour frame pour GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément FirstLineIndent pour frame pour les contrôles de configuration (format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément FirstLineIndent de frame de contrôles de vue (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément FirstLineIndent pour frame pour GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément FormatString pour ListItem (format)](./formatstring-element-for-listitem-for-listcontrol-format.md) Spécifie un modèle de format qui définit l’affichage de la valeur de la propriété ou du script.

[FormatString, élément de TableColumnItem (format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script de la table.

[FormatString, élément de WideItem pour WideControl (format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.

[Élément Frame pour CustomItem pour les contrôles de configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément Frame pour CustomItem pour les contrôles pour View (format)](./frame-element-for-customitem-for-controls-for-view-format.md) Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément Frame pour CustomItem pour CustomControl pour View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément Frame pour CustomItem pour GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md) Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[GroupBy, élément de View (format)](./groupby-element-for-view-format.md) Définit la manière dont Windows PowerShell affiche un nouveau groupe d’objets.

[Élément HideTableHeaders (format)](./hidetableheaders-element-format.md) Spécifie que les en-têtes de la table ne sont pas affichés.

[Élément ItemSelectionCondition pour ExpressionBinding pour les contrôles de configuration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) Définit la condition qui doit exister pour que ce contrôle soit utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) Définit la condition qui doit exister pour que ce contrôle soit utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) Définit la condition qui doit exister pour que ce contrôle soit utilisé. Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément ItemSelectionCondition pour ExpressionBinding pour GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) Définit la condition qui doit exister pour que ce contrôle soit utilisé. Il n’existe pas de limite au nombre de conditions de sélection qui peuvent être spécifiées pour un élément de contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément ItemSelectionCondition pour ListItem (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Définit la condition qui doit exister pour l’élément de liste à utiliser.

[Élément label pour ListItem pour ListControl (format)](./label-element-for-listitem-for-listcontrol-format.md) Spécifie l’étiquette de la valeur de la propriété ou du script dans la ligne.

[Élément label pour GroupBy (format)](./label-element-for-groupby-format.md) Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.

[Élément label pour TableColumnHeader (format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Définit l’étiquette qui s’affiche en haut d’une colonne.

[LeftIndent, élément de frame pour les contrôles de configuration (format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[LeftIndent, élément de frame de contrôles de vue (format)](./leftindent-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[LeftIndent, élément de frame pour CustomControl pour View (format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[LeftIndent, élément de frame pour GroupBy (format)](./leftindent-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères de décalage des données par rapport à la marge de gauche. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément ListControl (format)](./listcontrol-element-format.md) Définit un format de liste pour la vue.

[Élément ListEntry (format)](./listentry-element-for-listcontrol-format.md) Fournit une définition de la vue liste.

[ListEntries, élément (format)](./listentries-element-for-listcontrol-format.md) Définit le mode d’affichage des lignes de la vue liste.

[ListItem, élément (format)](./listitem-element-for-listitems-for-listcontrol-format.md) Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.

[Élément ListItems (format)](./listitems-element-for-listentry-for-listcontrol-format.md) Définit les propriétés et scripts affichés en mode liste.

[Élément Name pour le contrôle des contrôles pour la configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md) Spécifie le nom du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément Name pour SelectionSet (format)](./name-element-for-selectionset-format.md) Spécifie le nom utilisé pour référencer le jeu de sélection.

[Élément Name pour View (format)](./name-element-for-view-format.md) Spécifie le nom utilisé pour identifier la vue.

[Élément NewLine pour CustomItem pour les contrôles de configuration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) Ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément NewLine pour CustomItem pour les contrôles pour View (format)](./newline-element-for-customitem-for-controls-for-view-format.md) Ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément NewLine pour CustomItem pour CustomControl pour View (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) Ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément NewLine pour CustomItem pour GroupBy (format)](./newline-element-for-customitem-for-groupby-format.md) Ajoute une ligne vide à l’affichage du contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[PropertyName, élément de ExpressionBinding pour les contrôles de configuration (format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Spécifie la propriété .NET dont la valeur est affichée par le contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément PropertyName pour ExpressionBinding pour les contrôles pour View (format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Spécifie la propriété .NET dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément PropertyName pour ExpressionBinding pour CustomControl pour View (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Spécifie la propriété .NET dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé

[PropertyName, élément de ExpressionBinding pour GroupBy (format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Spécifie la propriété .NET dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[PropertyName, élément de GroupBy (format)](./propertyname-element-for-groupby-format.md) Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.

[PropertyName, élément de ItemSeclectionCondition pour les contrôles de configuration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément PropertyName pour ItemSelectionCondition pour les contrôles pour View (format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) spécifie la propriété .net qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[PropertyName, élément de ItemSelectionCondition pour GroupBy (format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[PropertyName, élément de ItemSelectionCondition pour ListItem (format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la vue est utilisée. Cet élément est utilisé lors de la définition d’un affichage de liste.

[PropertyName, élément de ListItem pour ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md) Spécifie la propriété .NET dont la valeur est affichée dans la liste.

[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée est utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément PropertyName pour SelectionCondition pour les contrôles pour View (format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée est utilisée. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément PropertyName pour SelectionCondition pour CustomControl pour View (format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.

[PropertyName, élément de SelectionCondition pour GroupBy (format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée de liste est utilisée.

[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée de table est utilisée.

[PropertyName, élément de SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.

[PropertyName, élément de TableColumnItem (format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Spécifie la propriété dont la valeur est affichée dans la colonne de la ligne.

[PropertyName, élément de WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.

[RightIndent, élément de frame pour les contrôles de configuration (format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément RightIndent du frame des contrôles de vue (format)](./rightindent-element-for-frame-for-controls-for-view-format.md) Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[RightIndent, élément de frame pour GroupBy (format)](./rightindent-element-for-frame-for-groupby-format.md) Spécifie le nombre de caractères dont les données sont décalées en dehors de la marge de droite. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément ScriptBlock pour ExpressionBinding pour les contrôles de configuration (format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Spécifie le script dont la valeur est affichée par le contrôle commun. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément ScriptBlock pour ExpressionBinding pour les contrôles pour View (format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Spécifie le script dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément ScriptBlock pour ExpressionBinding pour CustomCustomControl pour View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Spécifie le script dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément ScriptBlock pour ExpressionBinding pour GroupBy (format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Spécifie le script dont la valeur est affichée par le contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément ScriptBlock pour GroupBy (format)](./scriptblock-element-for-groupby-format.md) Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.

[Élément ScriptBlock pour ItemSelectionCondition pour les contrôles de configuration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément ScriptBlock pour ItemSelectionCondition pour les contrôles pour View (format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément ScriptBlock pour ItemSelectionCondition pour CustomControl pour View (format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément ScriptBlock pour ItemSelectionCondition pour GroupBy (format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément ScriptBlock pour ItemSelectionCondition pour ListControl (format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et l’élément de liste est utilisé. Cet élément est utilisé lors de la définition d’un affichage de liste.

[Élément ScriptBlock pour ListItem (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Spécifie le script dont la valeur est affichée dans la ligne de la liste.

[Élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément ScriptBlock pour SelectionCondition pour les contrôles pour View (format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie le script qui déclenche la condition.

[Élément ScriptBlock pour SelectionCondition pour GroupBy (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et l’entrée de liste est utilisée.

[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Spécifie le bloc de script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et l’entrée de table est utilisée.

[Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true` , la condition est remplie et la définition d’entrée étendue est utilisée.

[Élément ScriptBlock pour TableColumnItem (format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Spécifie le script dont la valeur est affichée dans la colonne de la ligne.

[Élément ScriptBlock pour WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Spécifie le script dont la valeur est affichée dans la vue étendue.

[Élément SelectionCondition pour EntrySelectedBy pour CustomEntry pour la configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) Définit une condition qui doit exister pour que la définition de contrôle soit utilisée. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) Définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) Définit la condition qui doit exister pour développer les objets de collection de cette définition.

[Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) Définit une condition qui doit exister pour une définition de contrôle à utiliser. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Définit la condition qui doit exister pour utiliser cette définition de la vue liste. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de liste.

[Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) Définit la condition qui doit exister pour être utilisée pour cette définition de la vue de table. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition de table.

[Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Définit la condition qui doit exister pour que cette définition soit utilisée. Il n’existe aucune limite au nombre de conditions de sélection qui peuvent être spécifiées pour une définition d’entrée étendue.

[Élément SelectionSet (format)](./selectionset-element-format.md) Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.

[Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément SelectionSetName pour EntrySelectedBy pour les contrôles pour View (format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.

[Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie l’ensemble des types .NET développés par cette définition.

[Élément SelectionSetName pour EntrySelectedBy pour GroupBy (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Spécifie un ensemble d’objets .NET pour l’entrée de liste. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.

[Élément SelectionSetName pour EntrySelectedBy pour TableRowEntry (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Spécifie un ensemble de types .NET utilisés par cette entrée de la vue table. Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.

[Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Spécifie un jeu d’objets .NET pour la définition. La définition est utilisée chaque fois que l’un de ces objets est affiché.

[Élément SelectionSetName pour SelectionCondition pour les contrôles de configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément EntrySelectedBy pour CustomEntry pour View (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie.

[Élément SelectionSetName pour SelectionCondition pour GroupBy (format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue liste.

[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue table.

[Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Spécifie l’ensemble des types .NET qui déclenchent la condition. Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue étendue.

[Élément SelectionSetName pour ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md) Spécifie un jeu d’objets .NET qui sont affichés par la vue.

[Élément SelectionSets (format)](./selectionsets-element-format.md) Définit les jeux d’objets .NET qui peuvent être utilisés par des affichages de format individuels.

[Élément ShowError (format)](./showerror-element-format.md) Spécifie que l’enregistrement complet de l’erreur s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.

[Élément TableColumnHeader pour TableHeaders pour table ((format)](./tablecolumnheader-element-format.md) Définit l’étiquette, la largeur de la colonne et l’alignement de l’étiquette pour une colonne de la table.

[Élément TableColumnItem (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.

[Élément TableColumnItems (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) Définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.

[Élément table ((format)](./tablecontrol-element-format.md) Définit un format de table pour une vue.

[Élément TableHeaders (format)](./tableheaders-element-format.md) Définit les en-têtes pour les colonnes d’une table.

[Élément TableRowEntries (format)](./tablerowentries-element-for-tablecontrol-format.md) Définit les lignes de la table.

[Élément TableRowEntry (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) Définit les données affichées dans une ligne de la table.

[Élément Text pour CustomItem pour les contrôles de configuration (format)](./text-element-for-customitem-for-controls-for-configuration-format.md) Spécifie le texte qui est ajouté aux données affichées par le contrôle, telles qu’une étiquette, les crochets pour encadrer les données et les espaces pour mettre en retrait les données. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément Text pour CustomItem pour les contrôles pour View (format)](./text-element-for-customitem-for-controls-for-view-format.md) Spécifie le texte qui est ajouté aux données affichées par le contrôle, telles qu’une étiquette, les crochets pour encadrer les données et les espaces pour mettre en retrait les données. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément Text pour CustomItem (format)](./text-element-for-customitem-for-customview-for-view-format.md) Spécifie le texte qui est ajouté aux données affichées par le contrôle, telles qu’une étiquette, les crochets pour encadrer les données et les espaces pour mettre en retrait les données. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément Text pour CustomItem pour GroupBy (format)](./text-element-for-customitem-for-groupby-format.md) Spécifie le texte qui est ajouté aux données affichées par le contrôle, telles qu’une étiquette, les crochets pour encadrer les données et les espaces pour mettre en retrait les données. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément TypeName pour EntrySelectedBy pour les contrôles de configuration (format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Spécifie un type .NET qui utilise cette définition du contrôle. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément TypeName pour EntrySelectedBy pour les contrôles pour View (format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Spécifie un type .NET qui utilise cette définition du contrôle. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément TypeName pour EntrySelectedBy pour CustomEntry pour View (format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle personnalisé. Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une définition.

[Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie un type .NET qui est développé par cette définition. Cet élément est utilisé lors de la définition des paramètres par défaut.

[Élément TypeName pour EntrySelectedBy pour GroupBy (format)](./typename-element-for-entryselectedby-for-groupby-format.md) Spécifie un type .NET qui utilise cette définition du contrôle personnalisé. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément TypeName pour EntrySelectedBy pour ListControl (format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Spécifie un type .NET qui utilise cette entrée de la vue liste. Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de liste.

[Élément TypeName pour EntrySelectedBy pour TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Spécifie un type .NET qui utilise cette entrée de la vue table. Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de table.

[Élément TypeName pour EntrySelectedBy pour WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md) Spécifie un type .NET pour la définition. La définition est utilisée chaque fois que cet objet est affiché.

[Élément TypeName pour SelectionCondition pour les contrôles de configuration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.

[Élément TypeName pour SelectionCondition pour les contrôles pour View (format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

[Élément TypeName pour SelectionCondition pour CustomControl pour View (format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Spécifie un type .NET qui déclenche la condition.

[Élément TypeName pour SelectionCondition pour GroupBy (format)](./typename-element-for-selectioncondition-for-groupby-format.md) Spécifie un type .NET qui déclenche la condition. Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListControl (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, l’entrée de liste est utilisée.

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, la condition est remplie et la ligne de table est utilisée.

[Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Spécifie un type .NET qui déclenche la condition. Lorsque ce type est présent, la définition est utilisée.

[TypeName, élément de types (format)](./typename-element-for-types-format.md) Spécifie le type .NET d’un objet qui appartient au jeu de sélection.

[Élément TypeName pour ViewSelectedBy (format)](./typename-element-for-viewselectedby-format.md) Spécifie un objet .NET qui est affiché par la vue.

[Élément types (format)](./types-element-for-selectionset-format.md) Définit les objets .NET qui se trouvent dans le jeu de sélection.

[View, élément (format)](./view-element-format.md) Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.

[Élément ViewDefinitions (format)](./viewdefinitions-element-format.md) Définit les vues utilisées pour afficher des objets.

[Élément ViewSelectedBy (format)](./viewselectedby-element-format.md) Définit les objets .NET affichés par la vue.

[Élément WideControl (format)](./widecontrol-element-format.md) Définit un format de liste larges (à valeur unique) pour la vue. Cette vue affiche une valeur de propriété ou une valeur de script unique pour chaque objet.

[Élément WideEntries (format)](./wideentries-element-for-widecontrol-format.md) Fournit les définitions de la vue étendue. La vue étendue doit spécifier une ou plusieurs définitions.

[Élément WideEntry (format)](./wideentry-element-for-widecontrol-format.md) Fournit une définition de la vue étendue.

[Élément WideItem (format)](./wideitem-element-for-widecontrol-format.md) Définit la propriété ou le script dont la valeur est affichée.

[Width, élément (format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Définit la largeur (en caractères) d’une colonne.

[Wrap, élément (format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Spécifie que le texte qui dépasse la largeur de colonne est affiché sur la ligne suivante.

[Élément WrapTables (format)](./wraptables-element-format.md) Spécifie que les données d’une cellule de tableau sont déplacées vers la ligne suivante si les données sont plus longues que la largeur de la colonne.

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
