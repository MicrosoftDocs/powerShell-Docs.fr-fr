---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251385"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Utilisation de Visual Studio Code pour le développement PowerShell

En plus de [PowerShell ISE][ise], PowerShell est également bien pris en charge dans Visual Studio Code.
De plus, l’environnement ISE n’est pas pris en charge avec PowerShell Core, alors que Visual Studio Code est pris en charge pour PowerShell Core sur toutes les plateformes (macOS, Windows et Linux)

Vous pouvez utiliser Visual Studio Code sur Windows avec PowerShell version 5 avec Windows 10 ou en installant [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) pour les systèmes d’exploitation Windows d’une version antérieure (par exemple Windows 8.1, etc.).

Avant de le démarrer, vérifiez que PowerShell est présent sur votre système.
Pour les charges de travail modernes sur Windows, macOS et Linux, consultez :

- [Installation de PowerShell Core sous Linux][install-pscore-linux]
- [Installation de PowerShell Core sous macOS][install-pscore-macos]
- [Installation de PowerShell Core sur Windows][install-pscore-windows]

Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Édition avec Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Installation de Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux](https://code.visualstudio.com/docs/setup/linux)

- **macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS](https://code.visualstudio.com/docs/setup/mac)

  > [!IMPORTANT]
  > Sur macOS, vous devez installer OpenSSL pour que l’extension PowerShell fonctionne correctement.
  > Le moyen le plus simple de le faire est d’installer [Homebrew](https://brew.sh/), puis d’exécuter `brew install openssl`.
  > VS Code peut désormais charger l’extension de PowerShell.

- **Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows](https://code.visualstudio.com/docs/setup/windows)

### <a name="2-installing-powershell-extension"></a>2. Installation de l’extension PowerShell

- Lancez l’application Visual Studio Code comme suit :
  - **Windows** : en tapant `code` dans votre session PowerShell
  - **Linux** : en tapant `code` dans votre terminal
  - **macOS** : en tapant `code` dans votre terminal

- Lancez **Quick Open** en appuyant sur **Ctrl+P** (**Cmd+P** sur Mac).
- Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.
- La vue **Extensions** s’ouvre dans la barre latérale. Sélectionnez l’extension de PowerShell de Microsoft.
  Vous devez voir quelque chose semblable à ce qui présenté ci-dessous :

  ![VSCode](../../images/vscode.png)

- Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.
- Après l’installation, vous voyez le bouton **Installer** se changer en **Recharger**.
  Cliquez sur **Recharger**.
- Une fois Visual Studio Code rechargé, vous êtes prêt pour l’édition.

Par exemple, pour créer un fichier, cliquez sur **Fichier->Nouveau**.
Pour l’enregistrer, cliquez sur **Fichier->Enregistrer**, puis indiquez un nom de fichier, disons `HelloWorld.ps1`.
Pour fermer le fichier, cliquez sur « x » en regard du nom de fichier.
Pour quitter Visual Studio Code, cliquez sur **Fichier->Quitter**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>L’installation de l’Extension PowerShell sur les systèmes restreints

Certains systèmes sont configurés de manière qui nécessite toutes les signatures de code à vérifier et nécessite donc PowerShell Editor Services doivent être manuellement approuvées pour s’exécuter sur le système.
Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell mais qui atteignent une erreur telle que :

```
Language server startup failed.
```

Pour approuver manuellement PowerShell Editor Services et, par conséquent, l’extension PowerShell pour VSCode ouvrent un invite et exécution de PowerShell :

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Vous êtes invité avec « Voulez-vous exécuter des logiciels à partir de ce serveur de publication non approuvé ? »
Type `R` pour exécuter le fichier. Ensuite, ouvrez Visual Studio Code et vérifiez que l’extension PowerShell fonctionne correctement. Si vous rencontrez des problèmes de mise en route, faites-le nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="using-a-specific-installed-version-of-powershell"></a>Utilisation d’une version installée spécifique de PowerShell

Si vous voulez utiliser une installation spécifique de PowerShell avec Visual Studio Code, vous devez ajouter une nouvelle variable à votre fichier de paramètres utilisateur.

1. Cliquez sur **Fichier -> Préférences -> Paramètres**
1. Deux volets de l’éditeur apparaissent.
   Dans le volet le plus à droite (`settings.json`), insérez le paramètre ci-dessous approprié pour votre système d’exploitation quelque part entre les deux accolades (`{` et `}`) et remplacez **\<la version \>** par la version installée de PowerShell :

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. Remplacez le paramètre par le chemin vers l’exécutable PowerShell souhaité
1. Enregistrez le fichier de paramètres et redémarrez Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Paramètres de configuration de Visual Studio Code

En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.

Nous recommandons les paramètres de configuration suivants pour Visual Studio Code :

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

Si vous ne souhaitez pas ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations de langage. Créer un paramètre de langue spécifique en plaçant des paramètres dans un `[<language-name>]` champ. Par exemple :

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Pour plus d’informations sur le fichier de codage dans VS Code, consultez [comprendre l’encodage du fichier](understanding-file-encoding.md).

## <a name="debugging-with-visual-studio-code"></a>Débogage avec Visual Studio Code

### <a name="no-workspace-debugging"></a>Débogage sans espace de travail

À compter de Visual Studio Code version 1.9, vous pouvez déboguer des scripts PowerShell sans avoir à ouvrir le dossier contenant le script PowerShell. Ouvrez le fichier de script PowerShell avec **fichier -> Ouvrir un fichier...** , définissez un point d’arrêt sur une ligne (appuyez sur F9) et appuyez sur F5 pour démarrer le débogage. Vous voyez apparaître le volet Actions de débogage, qui vous permet de vous arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.

### <a name="workspace-debugging"></a>Débogage d’espace de travail

Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier que vous avez ouvert dans Visual Studio Code en utilisant **Ouvrir un dossier...**  à partir du menu **Fichier**.
Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.

Même dans ce mode, vous pouvez démarrer le débogage du script PowerShell actuellement sélectionné en appuyant simplement sur F5.
Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.
Par exemple, vous pouvez ajouter des configurations pour :

- Lancer des tests Pester dans le débogueur
- Lancer un fichier spécifique avec des arguments dans le débogueur
- Lancer une session interactive dans le débogueur
- Attacher le débogueur à un processus hôte PowerShell

Suivez ces étapes pour créer votre fichier de configuration de débogage :

  1. Ouvrez la vue **Déboguer** en appuyant sur **Ctrl+Maj+D** (**Cmd+Maj+D** sur Mac).
  2. Appuyez sur l’icône d’engrenage **Configurer** dans la barre d’outils.
  3. Visual Studio Code vous invite à **Sélectionner un environnement**. Choisissez **PowerShell**.

  Dans ce cas, Visual Studio Code crée un répertoire et un fichier «.vscode\launch.json » à la racine du dossier de votre espace de travail.
  C’est là que votre configuration de débogage est stockée. Si vos fichiers sont dans un dépôt Git, vous souhaitez généralement valider le fichier launch.json.
  Le contenu du fichier launch.json est :

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

  Ceci représente les scénarios de débogage courants.
  Cependant, quand vous ouvrez ce fichier dans l’éditeur, vous voyez un bouton **Ajouter une configuration**.
  Vous pouvez appuyer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell. **PowerShell : Lancer un script** est une configuration très pratique que vous pouvez ajouter.
  Avec cette configuration, vous pouvez spécifier un fichier spécifique avec des arguments facultatifs, qui doit être lancé quand vous appuyez sur F5, quel que soit le fichier actif dans l’éditeur.

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

## <a name="powershell-extension-for-visual-studio-code"></a>Extension PowerShell pour Visual Studio Code

Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).
