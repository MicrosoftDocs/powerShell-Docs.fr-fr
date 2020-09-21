---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 181746e7d3df2880223d1f15a0c8b99b324f5b98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782529"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Utilisation de Visual Studio Code pour le développement PowerShell

[Visual Studio Code][vscode] est un éditeur de scripts multiplateforme de Microsoft. Avec [l’extension PowerShell][psext], il fournit une expérience d’édition de script riche et interactive, ce qui facilite l’écriture de scripts PowerShell fiables. Visual Studio Code avec l’extension PowerShell est l’éditeur recommandé pour l’écriture de scripts PowerShell.

Il prend en charge les versions suivantes de PowerShell :

- PowerShell 7 et versions ultérieures (Windows, macOS et Linux)
- PowerShell Core 6 (Windows, macOS et Linux)
- Windows PowerShell 5.1 (Windows uniquement)

> [!NOTE]
> Visual Studio Code est différent de [Visual Studio][].

## <a name="getting-started"></a>Prise en main

Avant de commencer, vérifiez que PowerShell est présent sur votre système. Pour les charges de travail modernes sur Windows, macOS et Linux, voir les liens suivants :

- [Installation de PowerShell sur Linux][install-pscore-linux]
- [Installation de PowerShell sur macOS][install-pscore-macos]
- [Installation de PowerShell sur Windows][install-pscore-windows]

Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].

> [!IMPORTANT]
> L’environnement [ISE Windows PowerShell][ise] est toujours disponible pour Windows. Toutefois, il ne fait plus partie du développement de fonctionnalités actif. L’environnement ISE ne fonctionne pas avec PowerShell 6 et versions ultérieures. En tant que composant de Windows, il continue d’être officiellement pris en charge pour la sécurité et les correctifs de maintenance de haute priorité.
> Nous n’avons aucun projet de supprimer l’environnement ISE de Windows.

## <a name="editing-with-visual-studio-code"></a>Édition avec Visual Studio Code

1. Installer Visual Studio Code. Pour plus d’informations, voir la vue d’ensemble [Configurer Visual Studio Code][vsc-setup].

   Les instructions d’installation sont propres à chaque plateforme :

   - **Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows][vsc-setup-win].
   - **macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS][vsc-setup-macOS].
   - **Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux][vsc-setup-linux].

1. Installez l’extension PowerShell.

   1. Lancez l’application Visual Studio Code en tapant `code` dans une console, ou `code-insiders` si vous avez installé Visual Studio Code Insiders.
   1. Lancez **Quick Open** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd>. Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.
   1. La vue **Extensions** s’ouvre dans la barre latérale. Sélectionnez l’extension de PowerShell de Microsoft.
      Un écran Visual Studio Code semblable à l’image suivante apparaît :

      ![Visual Studio Code - vue de l’extension PowerShell](media/using-vscode/vscode.png)

   1. Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.
   1. Après l’installation, si vous voyez le bouton **Installer** se changer en **Recharger**, cliquez sur **Recharger**.
   1. Une fois Visual Studio Code rechargé, vous pouvez passer à l’édition.

Par exemple, pour créer un fichier, cliquez sur **Fichier > Nouveau**. Pour l’enregistrer, cliquez sur **Fichier > Enregistrer**, puis indiquez un nom de fichier, comme `HelloWorld.ps1`. Pour fermer le fichier, cliquez sur `X` à côté du nom de fichier. Pour quitter Visual Studio Code, cliquez sur **Fichier > Quitter**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installation de l’extension PowerShell sur des systèmes restreints

Certains systèmes sont configurés pour exiger la validation de toutes les signatures de code. Vous risquez de recevoir l’erreur suivante :

```
Language server startup failed.
```

Ce problème peut se produire lorsque la stratégie d’exécution de PowerShell est définie par la stratégie de groupe Windows. Pour approuver manuellement PowerShell Editor Services et l’extension PowerShell pour Visual Studio Code, ouvrez une invite PowerShell et exécutez la commande suivante :

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Le message **Voulez-vous exécuter le logiciel provenant de cet éditeur non approuvé ?** apparaît. Tapez `A` pour exécuter le fichier. Ouvrez ensuite Visual Studio Code et vérifiez que l’extension PowerShell fonctionne correctement. Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [Problèmes GitHub][].

> [!NOTE]
> L’extension PowerShell pour Visual Studio Code ne prend pas en charge l’exécution en mode de langage avec contrainte. Pour plus d’informations, consultez le [problème GitHub n° 606][i606].

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Choisir la version de PowerShell à utiliser avec l’extension

Maintenant que PowerShell Core peut s’installer côte à côte avec Windows PowerShell, il est possible d’utiliser une version spécifique de PowerShell avec l’extension PowerShell. Cette fonctionnalité examine quelques chemins connus sur différents systèmes d’exploitation pour détecter les installations de PowerShell.

Suivez les étapes ci-dessous pour choisir la version :

1. Ouvrez la **Palette de commandes** sous Windows ou Linux avec <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>. Sur macOS, utilisez <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>P</kbd>.
1. Recherchez **Session**.
1. Cliquez sur **PowerShell : Afficher le menu de session**.
1. Choisissez la version de PowerShell que vous souhaitez utiliser dans la liste, par exemple : **PowerShell Core**.

Si vous avez installé PowerShell à un emplacement non standard, il risque de ne pas apparaître d’emblée dans le menu de session. Pour étendre le menu de session, [ajoutez vos propres chemins personnalisés](#adding-your-own-powershell-paths-to-the-session-menu) en suivant la procédure décrite ci-dessous.

> [!NOTE]
> Le menu de session PowerShell est également accessible à partir du numéro de version vert dans le coin inférieur droit de la barre d’état. Cliquez dessus pour accéder au menu de session.

## <a name="configuration-settings-for-visual-studio-code"></a>Paramètres de configuration de Visual Studio Code

Tout d’abord, si vous n’êtes pas familiarisé avec la modification des paramètres dans Visual Studio Code, nous vous recommandons de lire la [documentation des paramètres de Visual Studio Code][vsc-settings].

Après avoir lu la documentation, vous pouvez ajouter des paramètres de configuration dans `settings.json`.

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, Visual Studio Code permet également des configurations par langage. Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`. Par exemple :

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> Pour plus d’informations sur l’encodage de fichier dans Visual Studio Code, consultez [Présentation de l’encodage de fichier][file-encoding].
>
> Consultez également [Comment répliquer l’expérience ISE dans Visual Studio Code][vsc-ise] pour obtenir d’autres conseils de configuration de Visual Studio Code pour l’édition avec PowerShell.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Ajouter ses propres chemins PowerShell au menu de session

Il est possible d’ajouter d’autres chemins d’exécutables PowerShell au menu de session via le [paramètre Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) : `powershell.powerShellAdditionalExePaths`.

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

- `exePath`: chemin de l’exécutable `pwsh` ou `powershell`.
- `versionName`: texte qui s’affichera dans le menu de session.

Pour définir la version PowerShell par défaut, définissez la valeur `powershell.powerShellDefaultVersion` sur le texte affiché dans le menu de session (également connu sous le nom de `versionName`) :

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

Après avoir configuré ce paramètre, redémarrez Visual Studio Code ou rechargez la fenêtre Visual Studio Code active avec la **Palette de commandes**, puis tapez **Développeur : Recharger la fenêtre**.

Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.

> [!NOTE]
> Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Utilisation d’une version antérieure de l’extension PowerShell pour Windows PowerShell v3 et v4

L’extension PowerShell actuelle ne prend pas en charge [PowerShell v3 et v4][i1310]. Toutefois, vous pouvez utiliser la dernière version de l’extension qui prend en charge PowerShell v3 et v4.

> [!CAUTION]
> Il n’y aura aucun correctif supplémentaire pour cette version antérieure de l’extension. Bien que fournie « TELLE QUELLE », elle est à votre disposition si vous utilisez encore Windows PowerShell v3 et Windows PowerShell v4.

Tout d’abord, ouvrez le volet Extension et recherchez `PowerShell`. Cliquez ensuite sur l’engrenage, puis sélectionnez **Installer une autre version...** .

![Élément de menu - Installer une autre version...](media/using-vscode/install-another-version.png)

Sélectionnez ensuite la version **2020.1.0**. Cette version de l’extension était la dernière version à prendre en charge v3 et v4. Veillez à ajouter le paramètre suivant afin que la version de votre extension ne soit pas mise à jour automatiquement :

```json
{
    "extensions.autoUpdate": false
}
```

La version **2020.1.0** fonctionnera très bientôt. Toutefois, Visual Studio Code pourrait implémenter une modification qui arrêterait cette version de l’extension. Pour cette raison et à cause de l’absence de support, nous vous recommandons de procéder comme suit :

- Mise à niveau vers Windows PowerShell 5.1
- Installer PowerShell 7, une installation côte à côte avec Windows PowerShell qui fonctionne de manière optimale avec l’extension PowerShell

## <a name="debugging-with-visual-studio-code"></a>Débogage avec Visual Studio Code

### <a name="no-workspace-debugging"></a>Débogage sans espace de travail

Dans Visual Studio Code version 1.9 (ou ultérieure), il est possible de déboguer des scripts PowerShell sans ouvrir le dossier qui les contient.

1. Ouvrir le fichier de script PowerShell avec **Fichier > Ouvrir le fichier...**
1. Définissez un point d’arrêt : sélectionnez une ligne, puis appuyez sur <kbd>F9</kbd>
1. Appuyez sur <kbd>F5</kbd> pour démarrer le débogage

Le volet Actions de débogage apparaît ; il permet de s’arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.

### <a name="workspace-debugging"></a>Débogage d’espace de travail

Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier ouvert dans le menu **Fichier**  avec **Ouvrir le dossier…** . Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell ou la racine de votre dépôt Git. Le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.

Suivez ces étapes pour créer un fichier de configuration de débogage :

1. Ouvrez la vue **Déboguer** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>. Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.
1. Cliquez sur le lien **Créer un fichier launch.json**.
1. À partir de l’invite **Sélectionner l’environnement**, choisissez **PowerShell**.
1. Choisissez le type de débogage que vous souhaitez utiliser :

   - **Lancer le fichier actuel** : lancer et déboguer le fichier dans la fenêtre de l’éditeur actuellement active
   - **Lancer le script** : lancer et déboguer le fichier ou la commande spécifiés
   - **Session interactive** : déboguer les commandes exécutées à partir de la console intégrée
   - **Attacher** : attacher le débogueur à un processus hôte PowerShell en cours d’exécution

Visual Studio Code crée un répertoire et un fichier `.vscode\launch.json` à la racine du dossier de votre espace de travail pour stocker la configuration de débogage. Si vos fichiers se trouvent dans un référentiel Git, il est généralement préférable de valider le fichier `launch.json`. Le fichier `launch.json` présente le contenu suivant :

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

Ce fichier représente les scénarios de débogage courants. Quand vous ouvrez ce fichier dans l’éditeur, un bouton **Ajouter une configuration…** apparaît. Vous pouvez cliquer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell. Il est utile d’ajouter la configuration **PowerShell : Lancer un script**. Avec cette configuration, vous pouvez spécifier un fichier avec des arguments facultatifs qui sont utilisés quand vous appuyez sur <kbd>F5</kbd>, quel que soit le fichier actif dans l’éditeur.

Une fois la configuration de débogage établie, vous pouvez sélectionner la configuration que vous souhaitez utiliser lors d’une session de débogage. Sélectionnez une configuration dans la liste déroulante de la configuration de débogage, dans la barre d’outils de la vue **Déboguer**.

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Résolution des problèmes de l’extension PowerShell pour Visual Studio Code

Si vous rencontrez des problèmes lors de l’utilisation de Visual Studio Code pour le développement de scripts PowerShell, consultez le [guide de résolution des problèmes][troubleshooting] sur GitHub.

## <a name="useful-resources"></a>Ressources utiles

Quelques vidéos et billets de blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :

### <a name="videos"></a>Videos

- [Utilisation de Visual Studio Code comme éditeur PowerShell par défaut](https://youtu.be/bGn45vIeAMM)
- [Visual Studio Code : exploration du débogage de vos scripts PowerShell](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>Billets de blog :

- [Extension PowerShell][pscdn]
- [Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]
- [Aide sur le débogage avec Visual Studio Code][psdbgblog]
- [Débogage de PowerShell dans Visual Studio Code][psdbg-gh]
- [Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]
- [Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]
- [Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]
- [Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]
- [Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>Code source du projet d’extension PowerShell

Vous trouverez le code source de l’extension PowerShell sur [GitHub][psext-src].

Si vous êtes intéressé à contribuer, les demandes de tirage (Pull requests) sont très appréciées. Pour commencer, suivez les [instructions de la documentation du développeur][dev-docs] sur GitHub.

<!-- related articles -->
[ise]:                    ../../windows-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[Problèmes GitHub]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
