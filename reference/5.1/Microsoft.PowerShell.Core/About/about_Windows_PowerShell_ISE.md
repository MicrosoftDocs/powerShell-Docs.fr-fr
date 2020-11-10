---
description: Décrit les fonctionnalités et la configuration système requise de Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ff543024d7c62c70217eeaf3ded192a5a24c4757
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388839"
---
# <a name="about-windows-powershell-ise"></a>À propos de Windows PowerShell ISE

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit les fonctionnalités et la configuration système requise de Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Windows PowerShell ISE est une application hôte graphique pour Windows PowerShell.
Dans Windows PowerShell ISE, vous pouvez exécuter des commandes et écrire, tester et déboguer des scripts dans une seule interface utilisateur graphique Windows. Ses fonctionnalités incluent IntelliSense, la modification multiligne, la saisie semi-automatique par tabulation, l’enregistrement automatique, la coloration syntaxique, l’exécution sélective, l’aide contextuelle, l’option Afficher la commande (composer des commandes dans une fenêtre) et la prise en charge des jeux de caractères codés sur deux octets et des langues de droite à gauche.

Windows PowerShell ISE est un excellent outil pour les débutants. L’onglet Afficher les Fenêtre Commande et nouveau PowerShell distant vous guide à travers les tâches afin que vous puissiez réussir la première tentative. Les extraits de code et les indicateurs d’erreur vous aident à apprendre le langage Windows PowerShell au fur et à mesure que vous travaillez.

Les utilisateurs avancés peuvent tirer parti des fonctionnalités de débogage sophistiquées, des modules complémentaires et du modèle objet Windows PowerShell ISE.

Nouveautés de Windows PowerShell ISE dans Windows PowerShell 4,0

Windows PowerShell ISE introduit deux nouvelles fonctionnalités dans Windows PowerShell 4,0.

- Windows PowerShell ISE prend désormais en charge le débogage de flux de travail Windows PowerShell et le débogage de script à distance. Pour plus d’informations, consultez about_Debuggers.

- La prise en charge d’IntelliSense a été ajoutée pour les configurations et les fournisseurs de configuration d’état souhaité Windows PowerShell.

## <a name="starting-windows-powershell-ise"></a>Démarrage de Windows PowerShell ISE

Windows PowerShell ISE est installé, activé et prêt à l’emploi dans toutes les versions prises en charge de Windows.

- Dans Windows 8.1, Windows 8, Windows Server 2012 R2 et Windows Server 2012, dans l’écran d’accueil, tapez PowerShell_ISE, puis cliquez sur PowerShell_ISE ou Windows PowerShell ISE.

- Dans Windows Server 2012 R2 et Windows Server 2012, dans Gestionnaire de serveur, dans le menu Outils, cliquez sur Windows PowerShell ISE.

- Dans les versions antérieures de Windows, cliquez sur Démarrer, tous les programmes, accessoires, Windows PowerShell, puis sur Windows PowerShell ISE.

- Dans une console Windows PowerShell, Cmd.exe ou la zone exécuter ou Rechercher dans Windows, tapez « PowerShell_ise.exe ». Vous pouvez également utiliser les paramètres de ligne de commande, y compris le commutateur noprofile. Pour plus d’informations, consultez [PowerShell_ISE.exe de l’aide](about_powershell_ise_exe.md)de la console.

## <a name="running-interactive-commands"></a>Exécution de commandes interactives

Vous pouvez exécuter une expression ou une commande Windows PowerShell dans Windows PowerShell ISE. Vous pouvez utiliser des applets de commande, des fournisseurs, des composants logiciels enfichables et des modules comme vous les utilisez dans la console Windows PowerShell.

Vous pouvez taper ou coller des commandes interactives dans le volet de la console. Pour exécuter les commandes, vous pouvez utiliser des boutons, des éléments de menu et des raccourcis clavier.

Vous pouvez utiliser la fonctionnalité d’édition multiligne pour taper ou coller plusieurs lignes de code dans le volet de la console en même temps. Lorsque vous appuyez sur la touche de direction haut pour rappeler la commande précédente, toutes les lignes de la commande sont rappelées. Quand vous tapez des commandes, appuyez sur Maj + Entrée pour faire apparaître une nouvelle ligne vide sous la ligne active.

## <a name="viewing-output"></a>Affichage de la sortie

Les résultats des commandes et des scripts s’affichent dans le volet de la console. Vous pouvez déplacer ou copier les résultats à partir du volet console à l’aide des raccourcis clavier ou du bouton Copier de la barre d’outils, et vous pouvez coller les résultats dans le volet script ou dans les volets de la console ou dans d’autres programmes. Pour effacer le volet de la console, cliquez sur le bouton « Effacer le volet de sortie » ou tapez l’une des commandes suivantes :

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a>Écriture de scripts et de fonctions

Dans le volet script, vous pouvez ouvrir, composer, modifier et exécuter des scripts. Le volet script vous permet de modifier des scripts à l’aide de boutons et de raccourcis clavier. Vous pouvez également copier, couper et coller du texte entre le volet de script et le volet de la console.

Vous pouvez utiliser la fonctionnalité d’exécution sélective pour exécuter l’intégralité ou une partie d’un script. Pour exécuter une partie d’un script, sélectionnez le texte que vous souhaitez exécuter, puis cliquez sur le bouton exécuter la sélection ou appuyez sur F8. Par défaut, F8 exécute la ligne active.

Les fonctionnalités d’édition avancées incluent la correspondance des accolades, les agrandissements, les numéros de ligne, les indicateurs d’erreur, la modification de bloc et la mise en retrait, la copie riche et la conversion de casse.

## <a name="getting-help"></a>Obtenir de l’aide

Windows PowerShell ISE contient des rubriques d’aide qui décrivent son utilisation. En outre, tous les fichiers d’aide installés sont accessibles à partir des volets script et commande.

Windows PowerShell ISE prend également en charge l’aide contextuelle. Pour obtenir de l’aide sur une applet de commande, un fournisseur ou un mot clé particulier, placez le curseur dans le nom de l’élément et appuyez sur F1. Pour rechercher dans les rubriques d’aide, appuyez sur F1 et tapez le terme de recherche.

Pour mettre à jour les rubriques d’aide sur l’ordinateur, utilisez l’élément d’aide mettre à jour Windows PowerShell dans le menu aide. Cet élément met à jour l’aide pour les modules de la session active dans la culture d’interface utilisateur actuelle. Cela équivaut à exécuter l’applet de commande Update-Help sans paramètres. Pour mettre à jour l’aide pour les applets de commande fournies avec Windows PowerShell, démarrez Windows PowerShell ISE avec l’option « Exécuter en tant qu’administrateur ».

Vous pouvez également utiliser les applets de commande obtenir-aide, enregistrer-aide et Update-Help dans Windows PowerShell ISE, tout comme vous les utilisez dans la console Windows PowerShell. Toutefois, dans Windows PowerShell ISE, la fonction d’aide affiche l’intégralité de la rubrique d’aide, pas une page à la fois.

## <a name="debugging-scripts"></a>Scripts de débogage

Vous pouvez utiliser le débogueur Windows PowerShell ISE pour déboguer un script ou une fonction Windows PowerShell. Lorsque vous déboguez un script, vous pouvez utiliser des éléments de menu et des touches de raccourci pour effectuer la plupart des tâches que vous effectuez dans la console Windows PowerShell. Par exemple, pour définir un point d’arrêt de ligne dans un script, cliquez avec le bouton droit sur la ligne de code, puis cliquez sur basculer le point d’arrêt.

À mesure que vous parcourez un script pendant le débogage, le surligneur de débogage montre précisément quelle partie de la commande est en cours d’exécution et ouvre automatiquement les fichiers qui incluent des fonctions et des scripts appelés.

Par défaut, l’élément de menu basculer le point d’arrêt définit un point d’arrêt sur une ligne entière dans un script, mais vous pouvez définir un point d’arrêt sur une variable ou un nom de commande.
Vous pouvez également définir un point d’arrêt sur une commande par numéro de ligne et de colonne, ce qui facilite le débogage des commandes de pipeline longues.

Souvent, vous pouvez déboguer des erreurs de syntaxe dans un script en ouvrant simplement le fichier de script dans Windows PowerShell ISE. Les indicateurs d’erreur identifient les erreurs de syntaxe et les fonctionnalités en mode plan vous permettent de réduire les parties du script afin de vous concentrer sur les points problématiques.

Vous pouvez également utiliser les applets de commande du débogueur Windows PowerShell dans le volet de commandes de la même façon que vous les utilisez dans la console.

## <a name="running-remote-commands"></a>Exécution de commandes à distance

Grâce à la nouvelle fonctionnalité de l’onglet PowerShell à distance, il est facile d’établir une session Windows PowerShell permanente gérée par l’utilisateur (« PSSession ») sur l’ordinateur local ou sur un ordinateur distant. La commande ouvre une fenêtre indépendante qui vous invite à entrer un nom d’ordinateur et le compte d’utilisateur qui a l’autorisation d’exécuter des commandes sur l’ordinateur distant.

## <a name="customizing-the-view"></a>Personnalisation de l’affichage

Vous pouvez utiliser les fonctionnalités de Windows PowerShell ISE pour déplacer et redimensionner le volet de la console et le volet de script. Vous pouvez afficher et masquer l’un des volets, et vous pouvez modifier la taille du texte dans tous les volets.

Vous pouvez également utiliser la fenêtre Options pour personnaliser l’apparence et le fonctionnement de Windows PowerShell ISE. En outre, Windows PowerShell ISE a une variable hôte personnalisée, $psISE, que vous pouvez utiliser pour personnaliser Windows PowerShell ISE, y compris pour ajouter des menus et des éléments de menu.

## <a name="windows-powershell-ise-profile"></a>Profil de Windows PowerShell ISE

Windows PowerShell ISE possède son propre profil Windows PowerShell, Microsoft.PowerShellISE_profile.ps1. Dans ce profil, vous pouvez stocker des fonctions, des alias, des variables et des commandes que vous utilisez dans Windows PowerShell ISE.

Les éléments des profils AllHosts de Windows PowerShell (CurrentUser \\ AllHosts et ALLUSERS \\ AllHosts) sont également disponibles dans Windows PowerShell ISE, tout comme dans n’importe quel programme hôte Windows PowerShell. Toutefois, les éléments de vos profils de console Windows PowerShell ne sont pas disponibles dans Windows PowerShell ISE.

Les instructions relatives au déplacement et à la reconfiguration de vos profils sont disponibles dans Windows PowerShell ISE de l’aide et dans about_Profiles.

## <a name="notes"></a>REMARQUES

Windows PowerShell ISE est une fonctionnalité Windows facultative qui est activée par défaut sur les versions client et serveur de Windows. Pour activer et désactiver les Windows PowerShell ISE dans les versions client de Windows, utilisez l’option Activer ou désactiver des fonctionnalités Windows du panneau de configuration. Pour activer et désactiver les Windows PowerShell ISE dans les versions serveur de Windows, utilisez l’Assistant Ajout de rôles et de fonctionnalités dans Gestionnaire de serveur.

Étant donné que Windows PowerShell ISE nécessite une interface utilisateur, il ne fonctionne pas sur les installations Server Core de Windows Server. Toutefois, si vous ajoutez la fonctionnalité Windows PowerShell ISE, l’installation se convertit automatiquement en serveur avec une interface graphique utilisateur.

Windows PowerShell ISE repose sur Windows Presentation Foundation (WPF).
Si les éléments graphiques de Windows PowerShell ISE ne s’affichent pas correctement sur votre système, vous pouvez résoudre le problème en ajoutant ou en ajustant les paramètres de rendu des graphiques « désactiver l’accélération matérielle WPF » sur votre système. Pour plus d’informations, consultez [Paramètres du Registre pour le rendu des graphiques](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings).

## <a name="see-also"></a>VOIR AUSSI

[about_Debuggers](about_Debuggers.md)

[about_Profiles](about_Profiles.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-IseSnippet](xref:ISE.Get-IseSnippet)

[Import-IseSnippet](xref:ISE.Import-IseSnippet)

[New-IseSnippet](xref:ISE.New-IseSnippet)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Show-Command](xref:Microsoft.PowerShell.Utility.Show-Command)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
