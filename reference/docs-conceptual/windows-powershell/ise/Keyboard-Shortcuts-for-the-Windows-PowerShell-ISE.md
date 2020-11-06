---
ms.date: 01/02/2020
title: Raccourcis clavier pour Windows PowerShell ISE
description: Cet article représente une liste des raccourcis clavier utilisés dans PowerShell ISE.
ms.openlocfilehash: b7749f49d3ac2923b097e2ab94488263436980bd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663466"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Raccourcis clavier pour Windows PowerShell ISE

Pour effectuer des actions dans l’environnement d’écriture de scripts intégré de Windows PowerShell&reg;, utilisez les raccourcis clavier suivants. Windows PowerShell ISE est intégré aux systèmes d’exploitation Windows Server et Windows Client, mais peut également être installé sur certains systèmes d’exploitation Windows plus anciens comme composant du [package de téléchargement de Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Raccourcis clavier pour l’édition de texte

Lorsque vous éditez un texte, vous pouvez utiliser les raccourcis clavier suivants.

|              Action              |       Raccourcis clavier       |                                                                                                                                                 Utiliser dans                                                                                                                                                 |
| -------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Aide**                         | <kbd>F1</kbd>                  | Volet Script **Important :** vous pouvez spécifier que l’aide <kbd>F1</kbd> provient de la Bibliothèque TechNet sur le web ou de l’aide téléchargée (voir `Update-Help`). Pour opérer votre choix, cliquez sur **Outils** , **Options** , sur l’onglet **Paramètres généraux** , puis activez ou désactivez l’option **Utiliser le contenu de l’aide locale au lieu du contenu en ligne.** |
| **Copy**                         | <kbd>CTRL</kbd>+<kbd>C</kbd>   | Volets Script, Commande et Sortie                                                                                                                                                                                                                                                                 |
| **Couper**                          | <kbd>CTRL</kbd>+<kbd>X</kbd>   | Volets Script et Commande                                                                                                                                                                                                                                                                              |
| **Développer ou réduire le plan** | <kbd>CTRL</kbd>+<kbd>M</kbd>   | Volet Script                                                                                                                                                                                                                                                                                            |
| **Rechercher dans le script**               | <kbd>CTRL</kbd>+<kbd>F</kbd>   | Volet Script                                                                                                                                                                                                                                                                                            |
| **Rechercher suivant dans le script**          | <kbd>F3</kbd>                  | Volet Script                                                                                                                                                                                                                                                                                            |
| **Rechercher précédent dans le script**      | <kbd>SHIFT</kbd>+<kbd>F3</kbd> | Volet Script                                                                                                                                                                                                                                                                                            |
| **Rechercher l’accolade correspondante**          | <kbd>CTRL</kbd>+<kbd>]</kbd>   | Volet Script                                                                                                                                                                                                                                                                                            |
| **Coller**                        | <kbd>CTRL</kbd>+<kbd>V</kbd>   | Volets Script et Commande                                                                                                                                                                                                                                                                              |
| **Rétablir**                         | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | Volets Script et Commande                                                                                                                                                                                                                                                                              |
| **Remplacer dans le script**            | <kbd>CTRL</kbd>+<kbd>H</kbd>   | Volet Script                                                                                                                                                                                                                                                                                            |
| **Save**                         | <kbd>CTRL</kbd>+<kbd>S</kbd>   | Volet Script                                                                                                                                                                                                                                                                                            |
| **Sélectionner tout**                   | <kbd>CTRL</kbd>+<kbd>A</kbd>   | Volets Script, Commande et Sortie                                                                                                                                                                                                                                                                 |
| **Afficher les extraits de code**                | <kbd>CTRL</kbd>+<kbd>J</kbd>   | Volets Script et Commande                                                                                                                                                                                                                                                                              |
| **Annuler**                         | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | Volets Script et Commande                                                                                                                                                                                                                                                                              |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Raccourcis clavier pour exécuter les scripts

Lorsque vous exécutez des scripts dans le volet Script, vous pouvez utiliser les raccourcis clavier suivants.

|            Action            |                                                                                                             Raccourci clavier                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nouveau**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                                              |
| **Ouvrir**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                                              |
| **Exécuter**                      | <kbd>F5</kbd>                                                                                                                                                                                                                             |
| **Exécuter la sélection**            | <kbd>F8</kbd>                                                                                                                                                                                                                             |
| **Arrêter l’exécution**           | <kbd>CTRL</kbd>+<kbd>ARRÊTER</kbd>. Vous pouvez utiliser <kbd>CTRL</kbd>+<kbd>C</kbd> quand le contexte est sans ambiguïté (quand aucun texte n’est sélectionné).                                                                                              |
| **Tab** (pour accéder au script suivant)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **Remarque :** l’usage de la touche Tab pour accéder au script suivant fonctionne uniquement quand un seul onglet Windows PowerShell est ouvert ou, si plusieurs onglets Windows PowerShell sont ouverts, quand le focus est dans le volet Script.               |
| **Tab** (pour accéder au script précédent) | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>TAB</kbd> **Remarque :** l’usage de la touche Tab pour accéder au script précédent fonctionne uniquement quand un seul onglet Windows PowerShell est ouvert ou, si plusieurs onglets Windows PowerShell sont ouverts, quand le focus est dans le volet Script. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Raccourcis clavier pour la personnalisation de l’affichage

Pour personnaliser l’affichage dans Windows PowerShell ISE, vous pouvez utiliser les raccourcis clavier suivants. Ils sont accessibles à partir de tous les volets de l’application.

|                        Action                         |               Raccourci clavier               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Accéder au volet Commande (v2) ou Console (v3 et versions ultérieures)** | <kbd>CTRL</kbd>+<kbd>D</kbd>                  |
| **Accéder au volet Sortie (v2 uniquement)**                       | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>O</kbd> |
| **Accéder au volet Script**                                 | <kbd>CTRL</kbd>+<kbd>I</kbd>                  |
| **Afficher le volet Script**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **Masquer le volet Script**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **Déplacer le volet Script vers le haut**                               | <kbd>CTRL</kbd>+<kbd>1</kbd>                  |
| **Déplacer le volet Script vers la droite**                            | <kbd>CTRL</kbd>+<kbd>2</kbd>                  |
| **Maximiser le volet Script**                              | <kbd>CTRL</kbd>+<kbd>3</kbd>                  |
| **Zoom avant**                                           | <kbd>CTRL</kbd>+<kbd>+</kbd>                  |
| **Zoom arrière**                                          | <kbd>CTRL</kbd>+<kbd>-</kbd>                  |

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
> Lors du débogage de scripts dans Windows PowerShell ISE, vous pouvez également utiliser les raccourcis clavier conçus pour la console Windows PowerShell. Pour utiliser ces raccourcis, vous devez les taper dans le volet Commande, puis appuyer sur <kbd>ENTRÉE</kbd>.

|                        Action                        | Raccourci clavier |                Utiliser dans                 |
| ---------------------------------------------------- | ----------------- | ------------------------------------- |
| **Continuer**                                         | `C`               | Volet Console, lors du débogage d’un script |
| **Pas à pas détaillé**                                        | `S`               | Volet Console, lors du débogage d’un script |
| **Pas à pas principal**                                        | `V`               | Volet Console, lors du débogage d’un script |
| **Pas à pas sortant**                                         | `O`               | Volet Console, lors du débogage d’un script |
| **Répéter la dernière commande** (pour un pas à pas détaillé ou un pas à pas principal) | <kbd>ENTRÉE</kbd>  | Volet Console, lors du débogage d’un script |
| **Afficher la pile des appels**                               | `K`               | Volet Console, lors du débogage d’un script |
| **Arrêter le débogage**                                   | `Q`               | Volet Console, lors du débogage d’un script |
| **Afficher le script**                                  | `L`               | Volet Console, lors du débogage d’un script |
| **Afficher les commandes de débogage de la console**               | `H` ou `?`        | Volet Console, lors du débogage d’un script |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Raccourcis clavier pour les onglets Windows PowerShell

Lorsque vous utilisez les onglets Windows PowerShell, vous pouvez utiliser les raccourcis clavier suivants.

|             Action              |                                                        Raccourci clavier                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Fermer l’onglet PowerShell**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                                                                    |
| **Nouvel onglet PowerShell**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                                                                    |
| **Onglet PowerShell précédent**     | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>TAB</kbd>. Ce raccourci ne fonctionne que si aucun fichier n’est ouvert sous aucun onglet Windows PowerShell. |
| **Onglet Windows PowerShell suivant** | <kbd>CTRL</kbd>+<kbd>TAB</kbd>. Ce raccourci ne fonctionne que si aucun fichier n’est ouvert sous aucun onglet Windows PowerShell.                  |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Raccourcis clavier pour le démarrage et la fermeture

Pour démarrer la console Windows PowerShell (PowerShell.exe) ou pour quitter Windows PowerShell ISE, vous pouvez utiliser les raccourcis clavier suivants.

|                        Action                        |               Raccourci clavier               |
| ---------------------------------------------------- | --------------------------------------------- |
| **Quitter**                                             | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **Start PowerShell.exe** (Console Windows PowerShell) | <kbd>CTRL</kbd>+<kbd>MAJ</kbd>+<kbd>P</kbd> |

## <a name="see-also"></a>Voir aussi

- [PowerShell Magazine : Liste complète des raccourcis clavier pour Windows PowerShell ISE](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)
