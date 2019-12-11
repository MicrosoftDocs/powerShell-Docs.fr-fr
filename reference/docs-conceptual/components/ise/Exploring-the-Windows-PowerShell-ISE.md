---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Découverte de Windows PowerShell ISE
ms.openlocfilehash: 7949b690cda73148f07922985b1fc30fe1e8b2d0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117439"
---
# <a name="exploring-the-windows-powershell-ise"></a>Découverte de Windows PowerShell ISE

Vous pouvez utiliser l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell® pour créer, exécuter et déboguer des commandes et des scripts. Windows PowerShell ISE se compose d’une barre de menus, d’onglets Windows PowerShell, d’une barre d’outils, d’onglets de script, d’un volet Script, d’un volet Console, d’une barre d’état, d’un curseur de taille de texte et d’une aide contextuelle.

> [!NOTE]
> Depuis Windows PowerShell ISE 3.0, les volets Commande et Sortie ont été combinés en un seul volet Console.

## <a name="menu-bar"></a>Barre de menus

La barre de menus contient les menus **Fichier**, **Modifier**, **Affichage**, **Outils**, **Débogage**, **Modules complémentaires** et **Aide**. Les boutons dans les menus permettent d’effectuer des tâches liées à l’écriture et à l’exécution de scripts, ainsi qu’à l’exécution de commandes dans Windows PowerShell ISE. En outre, il est possible de placer un [outil complémentaire](object-model/The-ISEAddOnTool-Object.md) sur la barre de menus en exécutant des scripts qui utilisent la [Hiérarchie du modèle objet ISE](object-model/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> Dans Windows PowerShell ISE 2.0, les menus **Outils** et **Modules complémentaires** n’étaient pas présents.

## <a name="windows-powershell-tabs"></a>Onglets Windows PowerShell

Un onglet Windows PowerShell est un environnement dans lequel s’exécute un script Windows PowerShell. Vous pouvez ouvrir de nouveaux onglets Windows PowerShell dans Windows PowerShell ISE pour créer des environnements distincts sur votre ordinateur local ou sur des ordinateurs distants. Vous pouvez avoir au maximum huit onglets PowerShell ouverts simultanément.

## <a name="toolbar"></a>Barre d’outils

La barre d’outils contient les boutons suivants.

|Bouton|Fonction|
|----------|------------|
|**Nouveau**|Ouvre un nouveau script.|
|**Ouvrir**|Ouvre un fichier ou un script existant.|
|**Enregistrer**|Enregistre un script ou un fichier.|
|**Couper**|Coupe le texte sélectionné et le copie dans le Presse-papiers.|
|**Copier**|Copie le texte sélectionné dans le Presse-papiers.|
|**Coller**|Colle le contenu du Presse-papiers à l’emplacement du curseur.|
|**Effacer le volet de sortie**|Efface tout le contenu du volet sortie.|
|**Annuler**|Annule l’action qui vient d’être exécutée.|
|**Rétablir**|Effectue l’action qui vient d’être annulée.|
|**Exécuter un script**|Exécute un script.|
|**Exécuter la sélection**|Exécute une partie sélectionnée d’un script.|
|**Arrêter l’exécution**|Arrête un script en cours d’exécution.|
|**Nouvel onglet PowerShell à distance**|Crée un onglet PowerShell qui établit une session sur un ordinateur distant. Une boîte de dialogue s’affiche et vous invite à entrer les détails requis pour établir la connexion à distance.|
|**Démarrer PowerShell.exe**|Ouvre une console PowerShell.|
|**Afficher le volet Script en haut**|Déplace le volet Script vers le haut de l’écran.|
|**Afficher le volet Script à droite**|Déplace le volet Script vers la droite de l’écran.|
|**Afficher le volet Script agrandi**|Agrandit le volet Script.|

## <a name="script-tab"></a>Onglet de script

Affiche le nom du script que vous modifiez. Vous pouvez cliquer sur un onglet de script pour sélectionner le script à modifier.

Lorsque vous pointez sur l’onglet de script, le chemin d’accès complet au fichier de script s’affiche dans une info-bulle.

## <a name="script-pane"></a>Volet Script

Permet de créer et d’exécuter des scripts. Vous pouvez ouvrir, modifier et exécuter des scripts dans le volet Script.

## <a name="output-pane"></a>Volet Sortie

Affiche les résultats des commandes et des scripts que vous avez exécutés. Vous pouvez également copier et effacer le contenu du volet de sortie.

## <a name="command-pane"></a>Volet Commande

Permet d’écrire des commandes. Vous pouvez exécuter une commande d’une ou plusieurs lignes dans le volet Commande. Appuyez sur Maj+Entrée pour entrer chaque ligne d’une commande en comportant plusieurs, puis appuyez sur Entrée après la dernière ligne pour exécuter la commande multiligne. L’invite affichée en haut du volet Commandes affiche le chemin d’accès au répertoire de travail actif.

## <a name="status-bar"></a>Barre d’état

Permet de voir si l’exécution de commandes et de scripts est terminée. La barre d’état figure au bas de l’écran. La barre d’état affiche des parties sélectionnées des messages d’erreur.

## <a name="text-size-slider"></a>Curseur de taille de texte

Augmente ou diminue la taille du texte à l’écran.

## <a name="help"></a>Aide

L’aide sur Windows PowerShell ISE est disponible sur le web dans la bibliothèque TechNet. Vous pouvez accéder à l’aide en cliquant sur **Aide Windows PowerShell ISE** dans le menu **Aide**, ou en appuyant sur la touche F1 n’importe où, sauf quand le curseur est positionné sur un nom d’applet de commande dans le volet Script ou Console. À partir du menu **Aide** vous pouvez également exécuter l’applet de commande Update-Help et afficher la fenêtre Commande qui vous aide à construire des commandes en affichant tous les paramètres disponibles pour une applet de commande, et en vous permettant d’entrer les paramètres dans un formulaire simple d’utilisation.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
