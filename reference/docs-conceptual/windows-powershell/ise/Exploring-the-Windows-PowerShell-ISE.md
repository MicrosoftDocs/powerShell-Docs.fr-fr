---
ms.date: 01/02/2020
title: Découverte de Windows PowerShell ISE
description: Cet article offre une vue d’ensemble des fonctionnalités de l’environnement Windows PowerShell ISE
ms.topic: conceptual
ms.custom: ISE-F1-page
ms.openlocfilehash: 91161763c817972a62b4da1558a7ca119d8c8616
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090444"
---
# <a name="exploring-the-windows-powershell-ise"></a>Découverte de Windows PowerShell ISE

Vous pouvez utiliser l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell pour créer, exécuter et déboguer des commandes et des scripts. Windows PowerShell ISE se compose d’une barre de menus, d’onglets Windows PowerShell, d’une barre d’outils, d’onglets de script, d’un volet Script, d’un volet Console, d’une barre d’état, d’un curseur de taille de texte et d’une aide contextuelle.

## <a name="menu-bar"></a>Barre de menus

La barre de menus contient les menus **Fichier**, **Modifier**, **Affichage**, **Outils**, **Débogage**, **Modules complémentaires** et **Aide**. Les boutons dans les menus permettent d’effectuer des tâches liées à l’écriture et à l’exécution de scripts, ainsi qu’à l’exécution de commandes dans Windows PowerShell ISE. En outre, il est possible de placer un [outil complémentaire](object-model/The-ISEAddOnTool-Object.md) sur la barre de menus en exécutant des scripts qui utilisent la [Hiérarchie du modèle objet ISE](object-model/The-ISE-Object-Model-Hierarchy.md).

## <a name="windows-powershell-tabs"></a>Onglets Windows PowerShell

Un onglet Windows PowerShell est un environnement dans lequel s’exécute un script Windows PowerShell. Vous pouvez ouvrir de nouveaux onglets Windows PowerShell dans Windows PowerShell ISE pour créer des environnements distincts sur votre ordinateur local ou sur des ordinateurs distants. Vous pouvez avoir au maximum huit onglets PowerShell ouverts simultanément.

Pour plus d’informations, consultez [Comment créer un onglet PowerShell dans l’ISE Windows PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md).

## <a name="toolbar"></a>Barre d'outils

La barre d’outils contient les boutons suivants.

|             Bouton             |                                                                                     Fonction                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nouveau**                        | Ouvre un nouveau script.                                                                                                                                                              |
| **Ouvrir**                       | Ouvre un fichier ou un script existant.                                                                                                                                                |
| **Save**                       | Enregistre un script ou un fichier.                                                                                                                                                          |
| **Couper**                        | Coupe le texte sélectionné et le copie dans le Presse-papiers.                                                                                                                           |
| **Copy**                       | Copie le texte sélectionné dans le Presse-papiers.                                                                                                                                       |
| **Coller**                      | Colle le contenu du Presse-papiers à l’emplacement du curseur.                                                                                                                     |
| **Effacer le volet de sortie**          | Efface tout le contenu du volet sortie.                                                                                                                                           |
| **Annuler**                       | Annule l’action qui vient d’être exécutée.                                                                                                                                     |
| **Rétablir**                       | Effectue l’action qui vient d’être annulée.                                                                                                                                        |
| **Exécuter un script**                 | Exécute un script.                                                                                                                                                                   |
| **Exécuter la sélection**              | Exécute une partie sélectionnée d’un script.                                                                                                                                             |
| **Arrêter l’exécution**             | Arrête un script en cours d’exécution.                                                                                                                                                  |
| **Nouvel onglet PowerShell à distance**  | Crée un onglet PowerShell qui établit une session sur un ordinateur distant. Une boîte de dialogue s’affiche et vous invite à entrer les détails requis pour établir la connexion à distance. |
| **Démarrer PowerShell.exe**       | Ouvre une console PowerShell.                                                                                                                                                      |
| **Afficher le volet Script en haut**       | Déplace le volet Script vers le haut de l’écran.                                                                                                                                 |
| **Afficher le volet Script à droite**     | Déplace le volet Script vers la droite de l’écran.                                                                                                                               |
| **Afficher le volet Script agrandi** | Agrandit le volet Script.                                                                                                                                                       |

## <a name="script-tab"></a>Onglet de script

Affiche le nom du script que vous modifiez. Vous pouvez cliquer sur un onglet de script pour sélectionner le script à modifier.

Lorsque vous pointez sur l’onglet de script, le chemin d’accès complet au fichier de script s’affiche dans une info-bulle.

## <a name="script-pane"></a>Volet Script

Permet de créer et d’exécuter des scripts. Vous pouvez ouvrir, modifier et exécuter des scripts dans le volet Script. Pour plus d’informations, consultez [Comment écrire et exécuter des scripts dans l’ISE Windows PowerShell](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md).

## <a name="console-pane"></a>Volet de la console

Affiche les résultats des commandes et des scripts que vous avez exécutés. Vous pouvez exécuter des commandes dans le volet de la console. Vous pouvez également copier et effacer le contenu du volet de la console.

Pour plus d’informations, consultez les articles suivants :

- [Comment utiliser le volet Console dans Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
- [Déboguer les scripts dans l’ISE Windows PowerShell](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)
- [Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)

## <a name="status-bar"></a>Barre d’état

Permet de voir si l’exécution de commandes et de scripts est terminée. La barre d’état figure au bas de l’écran. La barre d’état affiche des parties sélectionnées des messages d’erreur.

## <a name="text-size-slider"></a>Curseur de taille de texte

Augmente ou diminue la taille du texte à l’écran.

## <a name="help"></a>Aide

L’aide sur Windows PowerShell ISE est disponible sur le site docs.microsoft.com. Vous pouvez ouvrir l’aide en cliquant sur **Aide Windows PowerShell ISE** dans le menu **Aide** ou en appuyant sur la touche <kbd>F1</kbd> n’importe où, sauf quand le curseur est positionné sur un nom de cmdlet dans le volet Script ou Console.
À partir du menu **Aide** vous pouvez également exécuter la cmdlet `Update-Help` et afficher la fenêtre Commande qui vous aide à construire des commandes en affichant tous les paramètres disponibles pour une cmdlet et en vous permettant d’entrer les paramètres dans un formulaire simple d’utilisation.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Comment utiliser des profils dans Windows PowerShell ISE](How-to-Use-Profiles-in-Windows-PowerShell-ISE.md)
- [Accessibilité dans Windows PowerShell ISE](Accessibility-in-Windows-PowerShell-ISE.md)
- [Raccourcis clavier pour Windows PowerShell ISE](Keyboard-Shortcuts-for-the-Windows-PowerShell-ISE.md)
