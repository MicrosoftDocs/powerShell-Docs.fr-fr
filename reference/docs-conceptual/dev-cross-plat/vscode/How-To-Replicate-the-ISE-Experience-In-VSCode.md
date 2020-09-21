---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 6b0b8ce054695d6cc0fc578290c554e2dc1472bc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784620"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Guide pratique de réplication de l’expérience ISE dans Visual Studio Code

Bien que l’extension PowerShell pour VS Code ne vise pas une parité complète des fonctionnalités avec PowerShell ISE, il existe des fonctionnalités qui rendent l’expérience offerte par VS Code plus naturelle pour les utilisateurs d’ISE.

Ce document vise à lister les paramètres configurables dans VS Code pour rendre l’expérience utilisateur plus proche d’ISE.

## <a name="ise-mode"></a>Mode ISE

> [!NOTE]
> Cette fonctionnalité est disponible dans l’extension PowerShell Preview à partir de la version 2019.12.0 et dans l’extension PowerShell à partir de la version 2020.3.0.

Le moyen le plus simple de répliquer l’expérience ISE dans Visual Studio Code consiste à activer le « Mode ISE ».
Pour cela, ouvrez la palette de commandes (<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> ou <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS) et tapez « Mode ISE ». Sélectionnez « PowerShell : Activer le mode ISE » dans la liste.

Cette commande applique automatiquement les paramètres décrits ci-dessous. Le résultat ressemble à ceci :

![Visual Studio Code en mode ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>Paramètres de configuration du mode ISE

Le mode ISE apporte les modifications suivantes aux paramètres de VS Code.

- Combinaisons de touches

  |               Fonction                |         Combinaison ISE          |              Liaison de VS Code                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | Interrompre et arrêter le débogueur          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | Exécuter la ligne active/le texte mis en surbrillance | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
  | Lister les extraits de code disponibles               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

  > [!NOTE]
  > Vous pouvez également [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VS Code.

- Interface utilisateur de type ISE simplifiée

  Si vous envisagez de simplifier l’interface utilisateur Visual Studio Code pour vous rapprocher de l’interface utilisateur de l’environnement ISE, appliquez les deux paramètres suivants :

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  Ces paramètres masquent les sections « Barre d’activité » et « Barre latérale de débogage » indiquées ci-dessous dans l’encadré rouge :

  ![La section en surbrillance comprend une barre d’activité et une barre latérale de débogage](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  Le résultat final ressemble à ceci :

  ![Vue simplifiée de VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- Saisie semi-automatique via la touche Tab

  Pour activer une autocomplétion semblable à ISE, ajoutez ce paramètre :

  ```json
  "editor.tabCompletion": "on",
  ```

- Aucun focus sur la console lors de l'exécution

  Pour maintenir le focus dans l’éditeur lors des exécutions avec <kbd>F8</kbd> :

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  La valeur par défaut est `true` pour des raisons d'accessibilité.

- Ne pas lancer la console intégrée au démarrage

  Pour arrêter la console intégrée au démarrage, définissez :

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > Le processus PowerShell en arrière-plan démarre toujours pour fournir IntelliSense, l’analyse de script, la navigation dans les symboles, etc., mais la console ne s’affiche pas.

- Considérer par défaut les fichiers comme PowerShell

  Pour que les nouveaux fichiers et les fichiers sans titre soient par défaut inscrits comme PowerShell :

  ```json
  "files.defaultLanguage": "powershell",
  ```

- Modèle de couleurs

  De nombreux thèmes ISE, qui font ressembler l’éditeur à ISE, sont disponibles pour VS Code.

  Dans la [palette de commandes][], tapez `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>Entrée</kbd>. Dans la liste déroulante, sélectionnez `PowerShell ISE`.

  Pour définir ce thème dans les paramètres :

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- Explorateur de commandes PowerShell

  Grâce au travail de [@corbob](https://github.com/corbob), l’extension PowerShell a un début d’explorateur de commandes.

  Dans la [palette de commandes][], entrez `PowerShell Command Explorer` et appuyez sur <kbd>Entrée</kbd>.

- Ouvrir dans ISE

  Si vous souhaitez quand même ouvrir un fichier dans l’ISE Windows PowerShell, ouvrez la [Palette de commandes][], recherchez « ouvrir dans ISE », puis sélectionnez **PowerShell : Ouvre le fichier actif dans l’ISE PowerShell**.

## <a name="other-resources"></a>Autres ressources

- 4sysops propose un [excellent article][4sysops] qui explique comment configurer VS Code comme ISE.
- Mike F Robbins a publié un [remarquable billet][mikefrobbins] sur la configuration de VS Code.
<!-- - Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell. -->

## <a name="vs-code-tips"></a>Conseils relatifs à VS Code

- Palette de commandes

  La Palette de commandes est un moyen pratique d’exécuter des commandes dans VS Code. Ouvrez la palette de commandes à l’aide de <kbd>F1</kbd> OU <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> OU <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur macOS.

  Pour plus d’informations, consultez la [documentation VS Code][vsc-docs].

- Désactiver la console de débogage

  Si vous planifiez uniquement l’utilisation de VS Code pour les scripts PowerShell, vous pouvez masquer la **Console de débogage**, car elle n’est pas utilisée par l’extension PowerShell. Pour ce faire, cliquez avec le bouton droit sur **Console de débogage** puis cliquez sur la coche pour la masquer.

## <a name="more-settings"></a>Paramètres supplémentaires

Si vous connaissez d’autres moyens de rendre VS Code plus intuitif pour les utilisateurs d’ISE, contribuez à ce document. Si vous êtes à la recherche d’une configuration de compatibilité, mais que vous ne trouvez aucun moyen de l’activer, [signalez le problème][] !

Les PR et les contributions sont également les bienvenues, comme toujours !

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Palette de commandes]: #vs-code-tips
[ouvrir un problème]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
