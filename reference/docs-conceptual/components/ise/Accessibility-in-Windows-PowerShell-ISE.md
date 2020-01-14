---
ms.date: 12/19/2019
keywords: powershell,applet de commande
title: Accessibilité dans Windows PowerShell ISE
ms.openlocfilehash: e618daca98d76f767a8b60a3425760bfc0bd0f64
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736281"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Accessibilité dans Windows PowerShell ISE

Cette rubrique décrit les fonctionnalités d’accessibilité de Windows PowerShell Integrated Scripting Environment (ISE) qui peuvent s’avérer utiles.

- [Guide pratique pour modifier la taille et l’emplacement des volets Console et Script](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [Raccourcis clavier pour l’édition du texte](#keyboard-shortcuts-for-editing-text)
- [Raccourcis clavier pour l’exécution des scripts](#keyboard-shortcuts-for-running-scripts)
- [Raccourcis clavier pour la personnalisation de l’affichage](#keyboard-shortcuts-for-customizing-the-view)
- [Raccourcis clavier pour le débogage des scripts](#keyboard-shortcuts-for-debugging-scripts)
- [Raccourcis clavier pour les onglets Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
- [Raccourcis clavier pour le démarrage et la fermeture](#keyboard-shortcuts-for-starting-and-exiting)
- [Gestion des points d’arrêt avec cmdlets](#breakpoint-management)

Microsoft s'attache à rendre ses produits et services conviviaux. Les rubriques suivantes fournissent des informations sur les fonctionnalités, les produits et les services qui rendent Windows PowerShell ISE plus accessible aux personnes handicapées.

En plus des fonctionnalités et utilitaires d’accessibilité dans Microsoft Windows, les fonctionnalités suivantes rendent Windows PowerShell ISE plus accessible aux personnes handicapées :

- Raccourcis clavier

- Table de coloration de la syntaxe et capacité de modifier plusieurs autres paramètres de couleur à l’aide de l’objet de script [$psISE.Options](object-model/The-ISEOptions-Object.md).

- Modification de la taille du texte

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Comment modifier la taille et l’emplacement des volets Console et Script

Pour modifier la taille et l’emplacement des volets Console et Script, vous pouvez procéder comme suit. Quand vous rouvrez Windows PowerShell ISE, les modifications de taille et d’emplacement sont conservées.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Pour redimensionner les volets Script et Console

1. Placez le pointeur sur la ligne de séparation entre les volets Script et Console.

2. Lorsque le pointeur de la souris prend la forme d’une flèche à deux pointes, faites glisser la bordure pour modifier la taille du volet.

### <a name="to-move-the-script-pane-and-console-pane"></a>Pour déplacer les volets Script et Console

Effectuez l’une des actions suivantes :

- Pour déplacer le volet Script au-dessus du volet Console, appuyez sur <kbd>CTRL</kbd>+<kbd>1</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script en haut** ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script en haut**.

- Pour déplacer le volet Script à droite du volet Console, appuyez sur <kbd>CTRL</kbd>+<kbd>2</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script à droite** ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script à droite**.

- Pour agrandir le volet Script, appuyez sur <kbd>CTRL</kbd>+<kbd>3</kbd> ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script agrandi** ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script agrandi**.

- Pour agrandir le volet Console et masquer le volet Script, sur le bord de droit de la ligne d’onglets, cliquez sur l’icône **Masquer le volet Script**, ou, dans le menu **Affichage**, cliquez pour désactiver l’option de menu **Afficher le volet Script**.

- Pour afficher le volet Script quand le volet Console est agrandi, sur le bord de droit de la ligne d’onglets, cliquez sur l’icône **Afficher le volet Script**, ou, dans le menu **Affichage**, cliquez pour activer l’option de menu **Afficher le volet Script**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Raccourcis clavier pour l’édition de texte

Lorsque vous éditez un texte, vous pouvez utiliser les raccourcis clavier suivants.

|           Action            |       Raccourcis clavier       |          Utiliser dans           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copy**                    | <kbd>CTRL</kbd>+<kbd>C</kbd>   | Volet Script, volet Console |
| **Couper**                     | <kbd>CTRL</kbd>+<kbd>X</kbd>   | Volet Script, volet Console |
| **Rechercher dans le script**          | <kbd>CTRL</kbd>+<kbd>F</kbd>   | Volet Script               |
| **Rechercher suivant dans le script**     | <kbd>F3</kbd>                  | Volet Script               |
| **Rechercher précédent dans le script** | <kbd>SHIFT</kbd>+<kbd>F3</kbd> | Volet Script               |
| **Coller**                   | <kbd>CTRL</kbd>+<kbd>V</kbd>   | Volet Script, volet Console |
| **Rétablir**                    | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | Volet Script, volet Console |
| **Remplacer dans le script**       | <kbd>CTRL</kbd>+<kbd>H</kbd>   | Volet Script               |
| **Save**                    | <kbd>CTRL</kbd>+<kbd>S</kbd>   | Volet Script               |
| **Sélectionner tout**              | <kbd>CTRL</kbd>+<kbd>A</kbd>   | Volet Script, volet Console |
| **Annuler**                    | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | Volet Script, volet Console |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Raccourcis clavier pour exécuter les scripts

Lorsque vous exécutez des scripts dans le volet Script, vous pouvez utiliser les raccourcis clavier suivants.

|            Action            |                                                                                                     Raccourci clavier                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nouveau**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **Ouvrir**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **Exécuter**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **Exécuter la sélection**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **Arrêter l’exécution**           | <kbd>CTRL</kbd>+<kbd>ARRÊTER</kbd>. Vous pouvez utiliser <kbd>CTRL</kbd>+<kbd>C</kbd> quand le contexte est sans ambiguïté (quand aucun texte n’est sélectionné).                                                                               |
| **Tab** (pour accéder au script suivant)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **Remarque :** l’usage de la touche Tab pour accéder au script suivant fonctionne uniquement quand un seul onglet PowerShell est ouvert ou, si plusieurs onglets PowerShell sont ouverts, quand le focus est dans le volet Script.                |
| **Tab** (pour accéder au script précédent) | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>TAB</kbd> **Remarque :** l’usage de la touche Tab pour accéder au script précédent fonctionne uniquement quand un seul onglet PowerShell est ouvert ou, si plusieurs onglets PowerShell sont ouverts, quand le focus est dans le volet Script. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Raccourcis clavier pour la personnalisation de l’affichage

Pour personnaliser l’affichage dans Windows PowerShell ISE, vous pouvez utiliser les raccourcis clavier suivants. Ils sont accessibles à partir de tous les volets de l’application.

|           Action           |         Raccourci clavier        |
| -------------------------- | -------------------------------- |
| **Accéder au volet Console**     | <kbd>CTRL</kbd>+<kbd>D</kbd>     |
| **Accéder au volet Script**      | <kbd>CTRL</kbd>+<kbd>I</kbd>     |
| **Afficher le volet Script**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Masquer le volet Script**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Déplacer le volet Script vers le haut**    | <kbd>CTRL</kbd>+<kbd>1</kbd>     |
| **Déplacer le volet Script vers la droite** | <kbd>CTRL</kbd>+<kbd>2</kbd>     |
| **Maximiser le volet Script**   | <kbd>CTRL</kbd>+<kbd>3</kbd>     |
| **Zoom avant**                | <kbd>CTRL</kbd>+<kbd>PLUS</kbd>  |
| **Zoom arrière**               | <kbd>CTRL</kbd>+<kbd>MINUS</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Raccourcis clavier pour le débogage des scripts

Lors du débogage de scripts, vous pouvez utiliser les raccourcis clavier suivants.

|           Action           |               Raccourci clavier                |                Utiliser dans                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Exécuter/continuer**           | <kbd>F5</kbd>                                  | Volet Script, lors du débogage d’un script |
| **Pas à pas détaillé**              | <kbd>F11</kbd>                                 | Volet Script, lors du débogage d’un script |
| **Pas à pas principal**              | <kbd>F10</kbd>                                 | Volet Script, lors du débogage d’un script |
| **Pas à pas sortant**               | <kbd>MAJ</kbd>+<kbd>F11</kbd>                | Volet Script, lors du débogage d’un script |
| **Afficher la pile des appels**     | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>D</kbd>  | Volet Script, lors du débogage d’un script |
| **Afficher la liste des points d’arrêt**       | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>L</kbd>  | Volet Script, lors du débogage d’un script |
| **Basculer le point d’arrêt**      | <kbd>F9</kbd>                                  | Volet Script, lors du débogage d’un script |
| **Supprimer tous les points d’arrêt** | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>F9</kbd> | Volet Script, lors du débogage d’un script |
| **Arrêter le débogueur**          | <kbd>MAJ</kbd>+<kbd>F5</kbd>                 | Volet Script, lors du débogage d’un script |

> [!NOTE]
> Lors du débogage de scripts dans Windows PowerShell ISE, vous pouvez également utiliser les raccourcis clavier conçus pour la console Windows PowerShell. Pour utiliser ces raccourcis, vous devez les taper dans le volet Console, puis appuyer sur Entrée.

|                 Action                  |      Raccourci clavier       |                Utiliser dans                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **Continuer**                            | <kbd>C</kbd>                 | Volet Console, lors du débogage d’un script |
| **Pas à pas détaillé**                           | <kbd>S</kbd>                 | Volet Console, lors du débogage d’un script |
| **Pas à pas principal**                           | <kbd>V</kbd>                 | Volet Console, lors du débogage d’un script |
| **Pas à pas sortant**                            | <kbd>O</kbd>                 | Volet Console, lors du débogage d’un script |
| **Répéter la dernière commande**(effectuer un pas à pas détaillé/principal) | <kbd>ENTRÉE</kbd>             | Volet Console, lors du débogage d’un script |
| **Afficher la pile des appels**                  | <kbd>K</kbd>                 | Volet Console, lors du débogage d’un script |
| **Arrêter le débogage**                      | <kbd>Q</kbd>                 | Volet Console, lors du débogage d’un script |
| **Afficher le script**                     | <kbd>L</kbd>                 | Volet Console, lors du débogage d’un script |
| **Afficher les commandes de débogage de la console**  | <kbd>H</kbd> ou <kbd>?</kbd> | Volet Console, lors du débogage d’un script |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Raccourcis clavier pour les onglets Windows PowerShell

Lorsque vous utilisez les onglets Windows PowerShell, vous pouvez utiliser les raccourcis clavier suivants.

|             Action              |                                 Raccourci clavier                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **Fermer l’onglet PowerShell**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                       |
| **Nouvel onglet PowerShell**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                       |
| **Onglet PowerShell précédent**     | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>TAB</kbd> (Uniquement si aucun fichier n’est ouvert sous aucun onglet PowerShell)                 |
| **Onglet Windows PowerShell suivant** | <kbd>CTRL</kbd>+<kbd>TAB</kbd> (Uniquement si aucun fichier n’est ouvert sous aucun onglet PowerShell) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Raccourcis clavier pour le démarrage et la fermeture

Pour démarrer la console Windows PowerShell (**PowerShell.exe**) ou pour quitter Windows PowerShell ISE, vous pouvez utiliser les raccourcis clavier suivants.

|                        Action                         |               Raccourci clavier               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Quitter**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **Démarrer PowerShell.exe** (console Windows PowerShell) | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>Gestion des points d’arrêt

Pour les malvoyants, les informations de point d’arrêt sont disponibles via les applets de commande pour la gestion des points d’arrêt, telles que [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) et [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md).
Pour plus d’informations, voir « Comment gérer des points d’arrêt » dans [Comment déboguer des scripts dans Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md).

## <a name="see-also"></a>Voir aussi

[Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
