---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Accessibilité dans Windows PowerShell ISE
ms.openlocfilehash: 416b18dd492ca04d98b5adf9f7f0f88ea495740a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030638"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Accessibilité dans Windows PowerShell ISE

Cette rubrique décrit les fonctionnalités d’accessibilité de Windows PowerShell Integrated Scripting Environment (ISE) qui peuvent s’avérer utiles.

* [Guide pratique pour modifier la taille et l’emplacement des volets Console et Script](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Raccourcis clavier pour l’édition du texte](#keyboard-shortcuts-for-editing-text)
* [Raccourcis clavier pour l’exécution des scripts](#keyboard-shortcuts-for-running-scripts)
* [Raccourcis clavier pour la personnalisation de l’affichage](#keyboard-shortcuts-for-customizing-the-view)
* [Raccourcis clavier pour le débogage des scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Raccourcis clavier pour les onglets Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Raccourcis clavier pour le démarrage et la fermeture](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft s'attache à rendre ses produits et services conviviaux. Les rubriques suivantes fournissent des informations sur les fonctionnalités, les produits et les services qui rendent Windows PowerShell ISE plus accessible aux personnes handicapées.

Windows PowerShell ISE prend en charge l’affichage à contraste élevé. Pour les malvoyants, les informations de point d’arrêt sont disponibles via les applets de commande pour la gestion des points d’arrêt, telles que [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) et [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Pour plus d’informations, voir « Comment gérer des points d’arrêt » dans [Comment déboguer des scripts dans Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). En plus des fonctionnalités et utilitaires d’accessibilité dans Microsoft Windows, les fonctionnalités suivantes rendent Windows PowerShell ISE plus accessible aux personnes handicapées :

- Raccourcis clavier

- Table de coloration de la syntaxe et capacité de modifier plusieurs autres paramètres de couleur à l’aide de l’objet de script [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb).

- Modification de la taille du texte

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Comment modifier la taille et l’emplacement des volets Console et Script

Pour modifier la taille et l’emplacement des volets Console et Script, vous pouvez procéder comme suit. Quand vous rouvrez Windows PowerShell ISE, les modifications de taille et d’emplacement sont conservées.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Pour redimensionner les volets Script et Console

1. Placez le pointeur sur la ligne de séparation entre les volets Script et Console.

2. Lorsque le pointeur de la souris prend la forme d’une flèche à deux pointes, faites glisser la bordure pour modifier la taille du volet.

### <a name="to-move-the-script-pane-and-console-pane"></a>Pour déplacer les volets Script et Console

Effectuez l'une des opérations suivantes :

- Pour déplacer le volet Script au-dessus du volet Console, appuyez sur **Ctrl+1** ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script en haut**, ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script en haut**.

- Pour déplacer le volet Script à droite du volet Console, appuyez sur **Ctrl+2** ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script à droite**, ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script à droite**.

- Pour agrandir le volet Script, appuyez sur **Ctrl+3** ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script agrandi**, ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script agrandi**.

- Pour agrandir le volet Console et masquer le volet Script, sur le bord de droit de la ligne d’onglets, cliquez sur l’icône **Masquer le volet Script**, ou, dans le menu **Affichage**, cliquez pour désactiver l’option de menu **Afficher le volet Script**.

- Pour afficher le volet Script quand le volet Console est agrandi, sur le bord de droit de la ligne d’onglets, cliquez sur l’icône **Afficher le volet Script**, ou, dans le menu **Affichage**, cliquez pour activer l’option de menu **Afficher le volet Script**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Raccourcis clavier pour l’édition de texte

Lorsque vous éditez un texte, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourcis clavier|Utiliser dans|
|----------|----------------------|----------|
|**Copier**|Ctrl+C|Volet Script, volet Console|
|**Couper**|Ctrl+X|Volet Script, volet Console|
|**Rechercher dans le script**|Ctrl+F|Volet Script|
|**Rechercher suivant dans le script**|F3|Volet Script|
|**Rechercher précédent dans le script**|Maj+F3|Volet Script|
|**Coller**|Ctrl+V|Volet Script, volet Console|
|**Rétablir**|Ctrl+Y|Volet Script, volet Console|
|**Remplacer dans le script**|Ctrl+H|Volet Script|
|**Enregistrer**|Ctrl+S|Volet Script|
|**Sélectionner tout**|Ctrl+A|Volet Script, volet Console|
|**Annuler**|Ctrl+Z|Volet Script, volet Console|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Raccourcis clavier pour exécuter les scripts

Lorsque vous exécutez des scripts dans le volet Script, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|
|----------|---------------------|
|**Nouveau**|Ctrl+N|
|**Ouvrir**|Ctrl+O|
|**Exécuter**|F5|
|**Exécuter la sélection**|F8|
|**Arrêter l’exécution**|CTRL+PAUSE. Vous pouvez utiliser Ctrl+C quand le contexte est sans ambiguïté (quand aucun texte n’est sélectionné).|
|**Tab** (pour accéder au script suivant)|CTRL+TAB **Remarque :** l’usage de la touche Tab pour accéder au script suivant fonctionne uniquement quand un seul onglet PowerShell est ouvert ou, si plusieurs onglets PowerShell sont ouverts, quand le focus est dans le volet Script.|
|**Tab** (pour accéder au script précédent)|CTRL+MAJ+TAB **Remarque :** l’usage de la touche Tab pour accéder au script précédent fonctionne uniquement quand un seul onglet PowerShell est ouvert ou, si plusieurs onglets PowerShell sont ouverts, quand le focus est dans le volet Script.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Raccourcis clavier pour la personnalisation de l’affichage

Pour personnaliser l’affichage dans Windows PowerShell ISE, vous pouvez utiliser les raccourcis clavier suivants. Ils sont accessibles à partir de tous les volets de l’application.

|Action|Raccourci clavier|
|----------|---------------------|
|**Accéder au volet Console**|Ctrl+D|
|**Accéder au volet Script**|Ctrl+I|
|**Afficher le volet Script**|Ctrl+R|
|**Masquer le volet Script**|Ctrl+R|
||
|**Déplacer le volet Script vers le haut**|Ctrl+1|
|**Déplacer le volet Script vers la droite**|Ctrl+2|
|**Maximiser le volet Script**|Ctrl+3|
|**Zoom avant**|Ctrl+Signe Plus|
|**Zoom arrière**|Ctrl+Signe Moins|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Raccourcis clavier pour le débogage des scripts

Lors du débogage de scripts, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|Utiliser dans|
|----------|---------------------|----------|
|**Exécuter/continuer**|F5|Volet Script, lors du débogage d’un script|
|**Pas à pas détaillé**|F11|Volet Script, lors du débogage d’un script|
|**Pas à pas principal**|F10|Volet Script, lors du débogage d’un script|
|**Pas à pas sortant**|Maj+F11|Volet Script, lors du débogage d’un script|
|**Afficher la pile des appels**|Ctrl+Maj+D|Volet Script, lors du débogage d’un script|
|**Afficher la liste des points d’arrêt**|Ctrl+Maj+L|Volet Script, lors du débogage d’un script|
|**Basculer le point d’arrêt**|F9|Volet Script, lors du débogage d’un script|
|**Supprimer tous les points d’arrêt**|Ctrl+Maj+F9|Volet Script, lors du débogage d’un script|
|**Arrêter le débogueur**|Maj+F5|Volet Script, lors du débogage d’un script|

> [!NOTE]
>
> Lors du débogage de scripts dans Windows PowerShell ISE, vous pouvez également utiliser les raccourcis clavier conçus pour la console Windows PowerShell. Pour utiliser ces raccourcis, vous devez les taper dans le volet Console, puis appuyer sur Entrée.

|Action|Raccourci clavier|Utiliser dans|
|----------|---------------------|----------|
|**Continuer**|C|Volet Console, lors du débogage d’un script|
|**Pas à pas détaillé**|S|Volet Console, lors du débogage d’un script|
|**Pas à pas principal**|V|Volet Console, lors du débogage d’un script|
|**Pas à pas sortant**|O|Volet Console, lors du débogage d’un script|
|**Répéter la dernière commande** (pour un pas à pas détaillé ou un pas à pas principal)|ENTRÉE|Volet Console, lors du débogage d’un script|
|**Afficher la pile des appels**|K|Volet Console, lors du débogage d’un script|
|**Arrêter le débogage**|Q|Volet Console, lors du débogage d’un script|
|**Afficher le script**|L|Volet Console, lors du débogage d’un script|
|**Afficher les commandes de débogage de la console**|H ou ?|Volet Console, lors du débogage d’un script|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Raccourcis clavier pour les onglets Windows PowerShell

Lorsque vous utilisez les onglets Windows PowerShell, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|
|----------|---------------------|
|**Fermer l’onglet PowerShell**|Ctrl+W|
|**Nouvel onglet PowerShell**|CTRL+T|
|**Onglet PowerShell précédent**|Ctrl+Maj+Tab Ce raccourci ne fonctionne que si aucun fichier n’est ouvert sous aucun onglet PowerShell.|
|**Onglet Windows PowerShell suivant**|CTRL+Tab Ce raccourci ne fonctionne que si aucun fichier n’est ouvert sous aucun onglet PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Raccourcis clavier pour le démarrage et la fermeture

Pour démarrer la console Windows PowerShell (PowerShell.exe) ou pour quitter Windows PowerShell ISE, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|
|----------|---------------------|
|**Quitter**|ALT+F4|
|**Démarrer PowerShell.exe** (console Windows PowerShell)|Ctrl+Maj+P|

## <a name="see-also"></a>Voir aussi

[Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
