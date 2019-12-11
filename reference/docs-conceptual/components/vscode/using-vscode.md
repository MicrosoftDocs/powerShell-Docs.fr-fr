---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 4f197e71d3b79828f466584f5d862415726818b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117386"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Utilisation de Visual Studio Code pour le développement PowerShell

En plus de [PowerShell ISE][ise], PowerShell est également bien pris en charge dans Visual Studio Code (VSCode). Par ailleurs, l’environnement ISE n’est pas pris en charge avec PowerShell Core, alors que VSCode est pris en charge pour PowerShell Core sur toutes les plateformes : Windows, macOS et Linux.

Pour utiliser VSCode sur Windows avec PowerShell version 5, utilisez Windows 10 ou installez Windows Management Framework 5.1 pour les systèmes d’exploitation Windows de bas niveau, comme Windows 8.1. Pour plus d’informations, voir [Installer et configurer WMF 5.1](/powershell/scripting/wmf/setup/install-configure).

Avant de commencer, vérifiez que PowerShell est présent sur votre système. Pour les charges de travail modernes sur Windows, macOS et Linux, voir les liens suivants :

- [Installation de PowerShell Core sur Linux][install-pscore-linux]
- [Installation de PowerShell Core sur macOS][install-pscore-macos]
- [Installation de PowerShell Core sur Windows][install-pscore-windows]

Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Édition avec VSCode

1. Installez VSCode. Pour plus d’informations, voir la vue d’ensemble [Configurer Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).

   Les instructions d’installation sont propres à chaque plateforme :

   - **Linux** : suivez les instructions d’installation de la page [Exécuter VSCode sur Linux](https://code.visualstudio.com/docs/setup/linux).
   - **macOS** : suivez les instructions d’installation de la page [Exécuter VSCode sur macOS](https://code.visualstudio.com/docs/setup/mac).

     > [!IMPORTANT]
     > Sur macOS, vous devez installer OpenSSL pour que l’extension PowerShell fonctionne correctement. Le moyen le plus simple de le faire est d’installer [Homebrew](https://brew.sh/), puis d’exécuter `brew install openssl`. VSCode peut désormais charger l’extension PowerShell.

   - **Windows** : suivez les instructions d’installation de la page [Exécuter VSCode sur Windows](https://code.visualstudio.com/docs/setup/windows).

1. Installez l’extension PowerShell.

   1. Lancez l’application VSCode en procédant comme suit :
      - **Windows** : en tapant `code` dans votre session PowerShell
      - **Linux** : en tapant `code` dans votre terminal
      - **macOS** : en tapant `code` dans votre terminal
   1. Lancez **Quick Open** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd>. Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.
   1. La vue **Extensions** s’ouvre dans la barre latérale. Sélectionnez l’extension de PowerShell de Microsoft.
      Un écran VSCode apparaît :

      ![VSCode](../../images/using-vscode/vscode.png)

   1. Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.
   1. Après l’installation, vous voyez le bouton **Installer** se changer en **Recharger**. Cliquez sur **Recharger**.
   1. Une fois VSCode rechargé, vous pouvez passer à l’édition.

Par exemple, pour créer un fichier, cliquez sur **Fichier > Nouveau**. Pour l’enregistrer, cliquez sur **Fichier > Enregistrer**, puis indiquez un nom de fichier, comme `HelloWorld.ps1`. Pour fermer le fichier, cliquez sur `X` à côté du nom de fichier. Pour quitter VSCode, **Fichier > Quitter**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installation de l’extension PowerShell sur des systèmes restreints

Certains systèmes sont configurés de façon à imposer la vérification de toutes les signatures de code et l’approbation manuelle de PowerShell Editor Services pour qu’il puisse s’exécuter sur le système. Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell, mais recevez une erreur de ce type :

```
Language server startup failed.
```

Pour approuver manuellement PowerShell Editor Services et l’extension PowerShell pour VSCode, ouvrez une invite PowerShell et exécutez la commande suivante :

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Le message **Voulez-vous exécuter le logiciel provenant de cet éditeur non approuvé ?** apparaît. Tapez `A` pour exécuter le fichier. Ouvrez ensuite VSCode et vérifiez que l’extension PowerShell fonctionne correctement. Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Choisir la version de PowerShell à utiliser avec l’extension

Maintenant que PowerShell Core peut s’installer côte à côte avec Windows PowerShell, il est possible d’utiliser une version donnée de PowerShell avec l’extension PowerShell. Suivez les étapes ci-dessous pour choisir la version :

1. Ouvrez la **Palette de commandes** sous Windows ou Linux avec <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>. Sur macOS, utilisez <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.
1. Recherchez **Session**.
1. Cliquez sur **PowerShell : Afficher le menu de session**.
1. Choisissez la version de PowerShell que vous souhaitez utiliser dans la liste, par exemple : **PowerShell Core**.

> [!IMPORTANT]
> Cette fonctionnalité examine quelques chemins connus sur différents systèmes d’exploitation pour détecter les emplacements d’installation de PowerShell. Si vous avez installé PowerShell à un emplacement non standard, il risque de ne pas apparaître d’emblée dans le menu de session. Pour étendre le menu de session, [ajoutez vos propres chemins personnalisés](#adding-your-own-powershell-paths-to-the-session-menu) en suivant la procédure décrite ci-dessous.

>[!NOTE]
> Il existe un autre moyen d’accéder au menu de session. Quand un fichier PowerShell est ouvert dans l’éditeur, un numéro de version apparaît en vert en bas à droite. Cliquez dessus pour accéder au menu de session.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Ajouter ses propres chemins PowerShell au menu de session

Il est possible d’ajouter d’autres chemins d’exécutables PowerShell au menu de session avec un paramètre VSCode.

Ajoutez un élément à la liste `powershell.powerShellAdditionalExePaths` ou créez la liste si elle n’existe pas dans `settings.json` :

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

Chaque élément doit comporter :

* `exePath` : chemin de l’exécutable `pwsh` ou `powershell`.
* `versionName` : texte qui s’affichera dans le menu de session.

Vous pouvez définir la version de PowerShell par défaut avec le paramètre `powershell.powerShellDefaultVersion` en le définissant sur le texte qui s’affiche dans le menu de session (soit `versionName` dans le dernier paramètre) :

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

Après avoir configuré ce paramètre, redémarrez VSCode ou rechargez la fenêtre VSCode active avec la **Palette de commandes**, puis tapez **Développeur : Recharger la fenêtre**.

Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.

> [!NOTE]
> Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.

### <a name="configuration-settings-for-vscode"></a>Paramètres de configuration pour VSCode

En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.

Nous recommandons les paramètres de configuration suivants pour VSCode :

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations propres à un langage. Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`. Par exemple :

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Pour plus d’informations sur l’encodage de fichier dans VSCode, consultez [Compréhension de l’encodage de fichier](understanding-file-encoding.md).

## <a name="debugging-with-vscode"></a>Débogage avec VSCode

### <a name="no-workspace-debugging"></a>Débogage sans espace de travail

À partir de VSCode version 1.9, il est possible de déboguer des scripts PowerShell sans avoir à ouvrir le dossier qui les contient. Ouvrez un fichier de script PowerShell avec **Fichier > Ouvrir un fichier…** , définissez un point d’arrêt sur une ligne (appuyez sur <kbd>F9</kbd>), puis appuyez sur <kbd>F5</kbd> pour démarrer le débogage. Le volet Actions de débogage apparaît ; il permet de s’arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.

### <a name="workspace-debugging"></a>Débogage d’espace de travail

Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier ouvert dans Visual Studio Code dans le menu **Fichier**  avec **Ouvrir le dossier…** . Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.

Même dans ce mode, vous pouvez lancer le débogage du script PowerShell actuellement sélectionné en appuyant sur <kbd>F5</kbd>. Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert. Par exemple, vous pouvez ajouter une configuration pour :

- lancer des tests Pester dans le débogueur ;
- lancer un fichier spécifique avec des arguments dans le débogueur ;
- lancer une session interactive dans le débogueur ;
- attacher le débogueur à un processus hôte PowerShell.

Suivez ces étapes pour créer votre fichier de configuration de débogage :

  1. Ouvrez la vue **Déboguer** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>. Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.
  1. Cliquez sur l’icône d’engrenage **Configurer** dans la barre d’outils.
  1. VSCode vous invite à **Sélectionner un environnement**. Choisissez **PowerShell**.

VSCode crée alors un répertoire et un fichier `.vscode\launch.json` à la racine du dossier de votre espace de travail. C’est là que votre configuration de débogage est stockée. Si vos fichiers se trouvent dans un référentiel Git, il est généralement préférable de valider le fichier `launch.json`. Le fichier `launch.json` présente le contenu suivant :

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

Ce fichier représente les scénarios de débogage courants. Quand vous ouvrez ce fichier dans l’éditeur, un bouton **Ajouter une configuration…** apparaît. Vous pouvez cliquer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell. Il est utile d’ajouter la configuration **PowerShell : Lancer un script**. Avec cette configuration, vous pouvez spécifier un fichier avec des arguments facultatifs qui doit se lancer quand vous appuyez sur <kbd>F5</kbd>, quel que soit le fichier actuellement actif dans l’éditeur.

Une fois la configuration de débogage établie, vous pouvez sélectionner la configuration que vous souhaitez utiliser lors d’une session de débogage. Sélectionnez une configuration dans la liste déroulante de la configuration de débogage, dans la barre d’outils de la vue **Déboguer**.

Quelques blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :

- [Extension PowerShell][ps-extension]
- [Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]
- [Aide sur le débogage avec Visual Studio Code][vscode-guide]
- [Débogage de PowerShell dans Visual Studio Code][ps-vscode]
- [Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]
- [Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]
- [Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]
- [Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]
- [Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>Extension PowerShell pour VSCode

Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).
