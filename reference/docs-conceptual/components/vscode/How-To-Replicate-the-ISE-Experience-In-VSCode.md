---
title: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
description: Guide pratique de réplication de l’expérience ISE dans Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012481"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Guide pratique de réplication de l’expérience ISE dans Visual Studio Code

Bien que l’extension PowerShell pour VSCode ne recherche une parité complète avec PowerShell ISE, il existe des fonctionnalités en place pour rendre l’expérience VSCode plus naturel pour les utilisateurs de l’environnement ISE.

Ce document tente de paramètres de la liste que vous pouvez configurer dans VSCode pour faciliter l’expérience d’un peu plus connue par rapport à l’environnement ISE utilisateur.

## <a name="key-bindings"></a>Combinaisons de touches

| Fonction                              | Liaison de l’ISE                  | Liaison de VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Interrompre et arrêter le débogueur          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Exécuter le texte de ligne/la mise en surbrillance en cours | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Liste des extraits de code disponibles               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Combinaisons de touches personnalisées

Vous pouvez [configurer vos propres combinaisons de touches](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) dans VSCode également.

## <a name="tab-completion"></a>Saisie semi-automatique via la touche Tab

Pour activer plus ISE semblable à la touche TAB, ajoutez ce paramètre :

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Ce paramètre a été ajouté directement à VSCode (et non dans l’extension). Son comportement est déterminé par VSCode directement et ne peut pas être modifié par l’extension.

## <a name="no-focus-on-console-when-executing"></a>Sans le focus sur la console lors de l’exécution

Pour conserver le focus dans l’éditeur lorsque vous exécutez avec <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

La valeur par défaut est `true` à des fins d’accessibilité.

## <a name="dont-start-integrated-console-on-startup"></a>Ne démarrent pas console intégrée au démarrage

Pour arrêter la console intégrée au démarrage, définissez :

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Le processus PowerShell en arrière-plan démarre toujours dans la mesure où qui fournit IntelliSense, analyse de script, navigation dans les symboles, etc.. Mais la console ne sera pas affichée.

## <a name="assume-files-are-powershell-by-default"></a>Supposons que les fichiers sont PowerShell par défaut

Pour rendre les fichiers de nouveau/sans titre, inscrire en tant que PowerShell par défaut :

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Modèle de couleurs

Il existe un nombre de thèmes de l’ISE pour VSCode rendre l’éditeur ressemble beaucoup plus à l’environnement ISE.

Dans le [Palette de commandes] type `theme` pour obtenir `Preferences: Color Theme` et appuyez sur <kbd>entrée</kbd>.
Dans la liste déroulante, sélectionnez `PowerShell ISE`.

Vous pouvez définir ce thème dans les paramètres avec :

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>Explorateur de commande PowerShell

Grâce à des travaux de [ @corbob ](https://github.com/corbob), l’extension PowerShell a les débuts de son propre Explorateur de commande.

Dans le [Palette de commandes], entrez `PowerShell Command Explorer` et appuyez sur <kbd>entrée</kbd>.

## <a name="open-in-the-ise"></a>Ouvrir dans l’environnement ISE

Si vous vous retrouvez souhaite ouvrir un fichier dans l’environnement ISE en tout cas, vous pouvez utiliser <kbd>MAJ</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Autres ressources

- 4sysops a [un excellent article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sur la configuration de VSCode pour être plus comme l’environnement ISE.
- Mike F Robbins a [un billet excellent](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sur la configuration de VSCode.
- Découvrez PowerShell a [une excellente écriture des](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sur l’obtention de VSCode d’installation pour PowerShell.

## <a name="more-settings"></a>Paramètres supplémentaires

Si vous connaissez d’autres moyens de rendre VSCode environnement plus familier pour les utilisateurs ISE, contribuent à ce document. S’il existe une configuration de compatibilité que vous recherchez, mais vous ne trouvez aucun moyen de l’activer, [de signaler un problème](https://github.com/PowerShell/vscode-powershell/issues/new/choose) et demandez !

Nous sommes toujours heureux d’accepter les demandes de tirage et les contributions également !

## <a name="vscode-tips"></a>Conseils de VSCode

### <a name="command-palette"></a>Palette de commandes

<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>MAJ</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Shift</kbd>+<kbd>P</kbd> sur macOS)

Un moyen pratique de l’exécution de commandes dans VSCode.
Pour plus d’informations, consultez [les documents VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Palette de commandes]: #command-palette
