---
ms.date: 12/31/2019
title: Hiérarchie du modèle objet ISE
description: Cet article présente la hiérarchie des objets qui font partie de l’environnement d’écriture de scripts intégré de Windows PowerShell (ISE).
ms.openlocfilehash: 00980cda72f05bc6ccb398079b129de13a98f783
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658333"
---
# <a name="the-ise-object-model-hierarchy"></a>Hiérarchie du modèle objet ISE

Cet article présente la hiérarchie des objets qui font partie de l’environnement d’écriture de scripts intégré de Windows PowerShell (ISE). Windows PowerShell ISE est inclus dans Windows PowerShell 3.0, 4.0 et 5.1. Cliquez sur un objet pour accéder à la documentation de référence de la classe qui définit l’objet.

## <a name="psise-object"></a>Objet $psISE

L’objet `$psISE` est l’[objet racine](The-ObjectModelRoot-Object.md) de la hiérarchie d’objets Windows PowerShell ISE. Cet objet de premier niveau fournit les objets de script suivants :

## <a name="psisecurrentfile"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

L'objet `$psISE.CurrentFile` est une instance de la classe [ISEFile](The-ISEFile-Object.md).

## <a name="psisecurrentpowershelltab"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

L'objet `$psISE.CurrentPowerShellTab` est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

L'objet `$psISE.CurrentVisibleHorizontalTool` est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord supérieur de la fenêtre Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

L'objet `$psISE.CurrentVisibleHorizontalTool` est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord droit de la fenêtre Windows PowerShell ISE.

## <a name="psiseoptions"></a>[$psISE.Options](The-ISEOptions-Object.md)

L’objet `$psISE.Options` est une instance de la classe [ISEOptions](The-ISEOptions-Object.md). L’objet ISEOptions représente différents paramètres pour Windows PowerShell ISE. Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabs"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

L'objet `$psISE.PowerShellTabs` est une instance de la classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). Cet objet est une collection de tous les onglets PowerShell ouverts qui représentent les environnements d’exécution Windows PowerShell disponibles sur l’ordinateur local ou sur les ordinateurs distants connectés. Chaque membre de la collection est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Voir aussi

- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
