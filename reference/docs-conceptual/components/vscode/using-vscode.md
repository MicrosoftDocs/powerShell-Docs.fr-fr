---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325242"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Utilisation de Visual Studio Code pour le développement PowerShell

En plus de [PowerShell ISE][ise], PowerShell est également bien pris en charge dans Visual Studio Code (VSCode). Par ailleurs, l’environnement ISE n’est pas pris en charge avec PowerShell Core, alors que VSCode est pris en charge pour PowerShell Core sur toutes les plateformes (Windows, macOS et Linux).

Vous pouvez utiliser VSCode sur Windows avec PowerShell version 5 en utilisant Windows 10 ou en installant [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) pour les systèmes d’exploitation Windows d’une version antérieure (par exemple Windows 8.1, etc.).

Avant de le démarrer, vérifiez que PowerShell est présent sur votre système. Pour les charges de travail modernes sur Windows, macOS et Linux, consultez :

- [Installation de PowerShell Core sur Linux][install-pscore-linux]
- [Installation de PowerShell Core sur macOS][install-pscore-macos]
- [Installation de PowerShell Core sur Windows][install-pscore-windows]

Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Édition avec VSCode

1. [Installation de VSCode](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux** : suivez les instructions d’installation de la page [Exécution de VSCode sur Linux](https://code.visualstudio.com/docs/setup/linux)
   - **macOS** : suivez les instructions d’installation de la page [Exécution de VSCode sur macOS](https://code.visualstudio.com/docs/setup/mac)

     > [!IMPORTANT]
     > Sur macOS, vous devez installer OpenSSL pour que l’extension PowerShell fonctionne correctement. Le moyen le plus simple de le faire est d’installer [Homebrew](https://brew.sh/), puis d’exécuter `brew install openssl`. VSCode peut désormais charger l’extension PowerShell.

   - **Windows** : suivez les instructions d’installation de la page [Exécution de VSCode sur Windows](https://code.visualstudio.com/docs/setup/windows)

2. Installation de l’extension PowerShell

   - Lancez l’application VSCode en procédant comme suit :
     - **Windows** : en tapant `code` dans votre session PowerShell
     - **Linux** : en tapant `code` dans votre terminal
     - **macOS** : en tapant `code` dans votre terminal
   - Lancez **Quick Open** en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>P</kbd> sur Mac).
   - Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.
   - La vue **Extensions** s’ouvre dans la barre latérale. Sélectionnez l’extension de PowerShell de Microsoft.
     Vous devez voir quelque chose semblable à ce qui présenté ci-dessous :

     ![VSCode](../../images/using-vscode/vscode.png)

   - Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.
   - Après l’installation, vous voyez le bouton **Installer** se changer en **Recharger**. Cliquez sur **Recharger**.
   - Une fois VSCode rechargé, vous êtes prêt pour l’édition.

Par exemple, pour créer un fichier, cliquez sur **Fichier->Nouveau**. Pour l’enregistrer, cliquez sur **Fichier->Enregistrer**, puis indiquez un nom de fichier, disons `HelloWorld.ps1`. Pour fermer le fichier, cliquez sur « x » en regard du nom de fichier. Pour quitter VSCode, **Fichier->Quitter**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installation de l’extension PowerShell sur des systèmes restreints

Certains systèmes sont configurés pour nécessiter la vérification de toutes les signatures de code et PowerShell Editor Services doit donc être manuellement approuvé pour s’exécuter sur le système. Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell mais recevez une erreur telle que :

```
Language server startup failed.
```

Pour approuver manuellement PowerShell Editor Services et, par conséquent, l’extension PowerShell pour VSCode, ouvrez une invite PowerShell et exécutez :

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Le message « Voulez-vous exécuter le logiciel de cet éditeur non approuvé ? » apparaît. Tapez `R` pour exécuter le fichier. Ouvrez ensuite VSCode et vérifiez que l’extension PowerShell fonctionne correctement. Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Choisir la version de PowerShell à utiliser avec l’extension

Maintenant que PowerShell Core peut s’installer côte à côte avec Windows PowerShell, il est possible d’utiliser une version spécifique de PowerShell avec l’extension PowerShell. Suivez ces étapes pour choisir la version :

1. Ouvrez la palette de commandes (<kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd> sur Windows et Linux, <kbd>Cmd</kbd> + <kbd>Maj</kbd>+<kbd>P</kbd> sur macOS).
1. Recherchez « Session ».
1. Cliquez sur « PowerShell : Afficher le menu de session ».
1. Choisissez la version de PowerShell que vous souhaitez utiliser dans la liste, par exemple, « PowerShell Core ».

> [!IMPORTANT]
> Cette fonctionnalité examine quelques chemins connus sur différents systèmes d’exploitation pour détecter les emplacements d’installation de PowerShell. Si vous avez installé PowerShell à un emplacement non standard, il risque de ne pas apparaître d’emblée dans le menu de session. Pour étendre le menu de session, [ajoutez vos propres chemins personnalisés](#adding-your-own-powershell-paths-to-the-session-menu) en suivant la procédure décrite ci-dessous.

>[!NOTE]
> Il existe un autre moyen d’afficher le menu de session. Quand un fichier PowerShell est ouvert dans l’éditeur, un numéro de version apparaît en vert en bas à droite. Cliquez dessus pour accéder au menu de session.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Ajouter ses propres chemins PowerShell au menu de session

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

Vous pouvez définir la version de PowerShell par défaut en attribuant le texte affiché dans le menu de session (soit `versionName` dans le dernier paramètre) comme valeur du paramètre `powershell.powerShellDefaultVersion` :

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

Après avoir défini ce paramètre, redémarrez VSCode ou utilisez l’action de la palette de commandes « Développeur : Recharger la fenêtre » pour recharger la fenêtre VSCode affichée.

Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.

> [!NOTE]
> Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.

#### <a name="configuration-settings-for-vscode"></a>Paramètres de configuration pour VSCode

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

À compter de VSCode version 1.9, vous pouvez déboguer les scripts PowerShell sans avoir à ouvrir le dossier qui les contient. Ouvrez un fichier de script PowerShell avec **Fichier->Ouvrir un fichier...** , définissez un point d’arrêt sur une ligne (appuyez sur <kbd>F9</kbd>), puis appuyez sur <kbd>F5</kbd> pour démarrer le débogage. Vous voyez apparaître le volet Actions de débogage, qui vous permet de vous arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.

### <a name="workspace-debugging"></a>Débogage d’espace de travail

Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier que vous avez ouvert dans Visual Studio Code en utilisant **Ouvrir un dossier...**  à partir du menu **Fichier**. Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.

Même dans ce mode, vous pouvez démarrer le débogage du script PowerShell actuellement sélectionné en appuyant simplement sur <kbd>F5</kbd>. Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert. Par exemple, vous pouvez ajouter des configurations pour :

- Lancer des tests Pester dans le débogueur
- Lancer un fichier spécifique avec des arguments dans le débogueur
- Lancer une session interactive dans le débogueur
- Attacher le débogueur à un processus hôte PowerShell

Suivez ces étapes pour créer votre fichier de configuration de débogage :

  1. Ouvrez la vue **Déboguer** en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd> (<kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd> sur Mac).
  2. Cliquez sur l’icône d’engrenage **Configurer** dans la barre d’outils.
  3. VSCode vous invite à **Sélectionner un environnement**. Choisissez **PowerShell**.

  Dans ce cas, VSCode crée un répertoire et un fichier « .vscode\launch.json » à la racine du dossier de votre espace de travail. C’est là que votre configuration de débogage est stockée. Si vos fichiers sont dans un dépôt Git, vous souhaitez généralement valider le fichier launch.json. Le contenu du fichier launch.json est :

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

  Ceci représente les scénarios de débogage courants. Cependant, quand vous ouvrez ce fichier dans l’éditeur, vous voyez un bouton **Ajouter une configuration**. Vous pouvez cliquer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell. Vous pouvez aussi ajouter la configuration très pratique **PowerShell : Lancer un script**. Avec cette configuration, vous pouvez spécifier un fichier déterminé avec des arguments facultatifs qui doit se lancer quand vous appuyez sur <kbd>F5</kbd>, quel que soit le fichier actuellement actif dans l’éditeur.

  Une fois établie la configuration de débogage, vous pouvez choisir la configuration à utiliser pendant une session de débogage en la sélectionnant dans la liste déroulante des configurations de débogage de la barre d’outils de la vue **Déboguer**.

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
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>Extension PowerShell pour VSCode

Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).
