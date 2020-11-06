---
ms.date: 08/25/2017
title: Objet ObjectModelRoot
description: L’objet $psISE, qui est l’objet racine principal dans PowerShell ISE est une instance de la classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot. Cette rubrique décrit les propriétés de l’objet ObjectModelRoot.
ms.openlocfilehash: c8ae703c2663256ca037090fd3b1eb239cfc431a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660947"
---
# <a name="the-objectmodelroot-object"></a>Objet ObjectModelRoot

L’objet `$psISE`, qui est l’objet racine principal dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell&reg; est une instance de la classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot. Cette rubrique décrit les propriétés de l’objet **ObjectModelRoot**.

## <a name="properties"></a>Propriétés

### <a name="currentfile"></a>CurrentFile

> Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient le fichier associé à cet objet hôte ayant actuellement le focus.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient l’onglet PowerShell ayant le focus.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient l’outil complémentaire Windows PowerShell ISE qui est actuellement visible dans le volet d’outils horizontal en bas de l’éditeur.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient l’outil complémentaire Windows PowerShell ISE qui est actuellement visible dans le volet d’outils vertical à droite de l’éditeur.

### <a name="options"></a>Options

> Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient les diverses options permettant de modifier des paramètres dans Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Propriété en lecture seule qui obtient la collection des onglets PowerShell ouverts dans Windows PowerShell ISE. Par défaut, cet objet contient un seul onglet PowerShell. Toutefois, vous pouvez ajouter plusieurs onglets PowerShell à cet objet à l’aide de scripts ou en utilisant les menus dans Windows PowerShell ISE.

## <a name="see-also"></a>Voir aussi

- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
