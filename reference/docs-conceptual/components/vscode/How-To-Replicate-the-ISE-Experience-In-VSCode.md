---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279244"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Guide pratique de réplication de l’expérience ISE dans Visual Studio Code

Bien que l’extension PowerShell pour VSCode ne vise pas une parité complète des fonctionnalités avec PowerShell ISE, il existe des fonctionnalités qui rendent l’expérience offerte par VSCode plus naturelle pour les utilisateurs d’ISE.

Ce document vise à lister les paramètres configurables dans VSCode pour rendre l’expérience utilisateur plus proche d’ISE.

## <a name="ise-mode"></a>Mode ISE

> [!NOTE]
> Cette fonctionnalité est disponible dans l’extension PowerShell Preview à partir de la version 2019.12.0 et dans l’extension PowerShell à partir de la version 2020.3.0.

Le moyen le plus simple de répliquer l’expérience ISE dans Visual Studio Code consiste à activer le « Mode ISE ».
Pour cela, ouvrez la palette de commandes (<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> ou <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS) et tapez « Mode ISE ».
Sélectionnez « PowerShell : Activer le mode ISE » dans la liste.

Cette commande applique automatiquement la plupart des paramètres figurant dans ce document.
Le résultat ressemble à ceci :

![Mode ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

La suite de cet article contient des informations plus détaillées sur les paramètres du mode ISE et certains paramètres supplémentaires.

## <a name="key-bindings"></a>Combinaisons de touches

| Fonction                              | Combinaison ISE                  | Combinaison VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Interrompre et arrêter le débogueur          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Exécuter la ligne active/le texte mis en surbrillance | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lister les extraits de code disponibles               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Combinaisons de touches personnalisées

Vous pouvez également [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VSCode.

## <a name="simplified-ise-like-ui"></a>Interface utilisateur de type ISE simplifiée

Si vous envisagez de simplifier l’interface utilisateur Visual Studio Code pour vous rapprocher de l’interface utilisateur de l’environnement ISE, appliquez les deux paramètres suivants :

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> Ces paramètres sont inclus dans le [« Mode ISE »](#ise-mode).

Ceci permet de masquer les sections « Barre d’activité » et « Barre latérale de débogage » ci-dessous dans l’encadré rouge :

![la section en surbrillance comprend une barre d’activité et une barre latérale de débogage](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Le résultat final ressemble à ceci :

![Vue simplifiée de VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Saisie semi-automatique via la touche Tab

Pour activer une autocomplétion semblable à ISE, ajoutez ce paramètre :

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Ce paramètre a été ajouté directement à VSCode (et non dans l’extension). Son comportement, déterminé par VSCode, n’est pas modifiable par l’extension.

> [!NOTE]
> Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).

## <a name="no-focus-on-console-when-executing"></a>Aucun focus sur la console lors de l'exécution

Pour maintenir le focus dans l’éditeur lors des exécutions avec <kbd>F8</kbd> :

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).

La valeur par défaut est `true` pour des raisons d'accessibilité.

## <a name="dont-start-integrated-console-on-startup"></a>Ne pas lancer la console intégrée au démarrage

Pour arrêter la console intégrée au démarrage, définissez :

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Le processus PowerShell en arrière-plan démarrera toujours, dans la mesure où il apporte IntelliSense, l’analyse de script, la navigation dans les symboles, etc. La console, en revanche, ne s’affichera pas.

## <a name="assume-files-are-powershell-by-default"></a>Considérer par défaut les fichiers comme PowerShell

Pour que les nouveaux fichiers et les fichiers sans titre soient par défaut inscrits comme PowerShell :

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).

## <a name="color-scheme"></a>Modèle de couleurs

De nombreux thèmes ISE, qui font ressembler l’éditeur à ISE, sont disponibles pour VSCode.

Dans la [palette de commandes], tapez `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>Entrée</kbd>.
Dans la liste déroulante, sélectionnez `PowerShell ISE`.

Pour définir ce thème dans les paramètres :

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> Ce paramètre est inclus dans le [« Mode ISE »](#ise-mode).

## <a name="powershell-command-explorer"></a>Explorateur de commandes PowerShell

Grâce au travail de [@corbob](https://github.com/corbob), l’extension PowerShell a un début d’explorateur de commandes.

Dans la [palette de commandes], entrez `PowerShell Command Explorer` et appuyez sur <kbd>Entrée</kbd>.

> [!NOTE]
> Il s’affiche automatiquement en [« Mode ISE »](#ise-mode).

## <a name="open-in-the-ise"></a>Ouvrir dans ISE

Si vous souhaitez quand même ouvrir un fichier dans ISE, vous pouvez utiliser <kbd>Maj</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Autres ressources

- 4sysops propose un [excellent article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) qui explique comment configurer VSCode comme ISE.
- Mike F Robbins a publié un [remarquable billet](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sur la configuration de VSCode.
- Learn PowerShell fait un [compte rendu brillant](https://www.learnpwsh.com/setup-vs-code-for-powershell/) de la configuration de VSCode pour PowerShell.

## <a name="more-settings"></a>Paramètres supplémentaires

Si vous connaissez d’autres moyens de rendre VSCode plus intuitif pour les utilisateurs d’ISE, contribuez à ce document. Si vous êtes à la recherche d’une configuration de compatibilité, mais que vous ne trouvez aucun moyen de l’activer, [signalez le problème](https://github.com/PowerShell/vscode-powershell/issues/new/choose) !

Les PR et les contributions sont également les bienvenues, comme toujours !

## <a name="vscode-tips"></a>Conseils VSCode

### <a name="command-palette"></a>Palette de commandes

<kbd>F1</kbd> OU <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS)

Un moyen pratique d’exécuter des commandes dans VSCode.
Pour plus d’informations, voir les [documents VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Palette de commandes]: #command-palette
