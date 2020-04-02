---
title: Utilisation de Visual Studio Code pour le développement PowerShell
description: Utilisation de Visual Studio Code pour le développement PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 8644aa7c648d649651ca679238e0b79ff35ac579
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500912"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Utilisation de Visual Studio Code pour le développement PowerShell

[Visual Studio Code](https://code.visualstudio.com/) est un éditeur de scripts multiplateforme (Windows, macOS et Linux) de Microsoft. Avec l'[extension PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), il fournit une expérience d’édition de script riche et interactive, ce qui facilite l’écriture de scripts PowerShell fiables.

Visual Studio Code avec l’extension PowerShell est l’éditeur recommandé pour l’écriture de scripts PowerShell.
Il prend en charge les versions suivantes de PowerShell :

- PowerShell 7 et versions ultérieures
- PowerShell Core 6
- Windows PowerShell 5.1

Avant de commencer, vérifiez que PowerShell est présent sur votre système. Pour les charges de travail modernes sur Windows, macOS et Linux, voir les liens suivants :

- [Installation de PowerShell sur Linux][install-pscore-linux]
- [Installation de PowerShell sur macOS][install-pscore-macos]
- [Installation de PowerShell sur Windows][install-pscore-windows]

Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].

> [!NOTE]
> Visual Studio Code est différent de [Visual Studio](https://visualstudio.microsoft.com/).

> [!IMPORTANT]
> [Windows PowerShell ISE][ise] est également toujours disponible pour Windows, mais il n’est plus dans le développement actif de fonctionnalités et ne fonctionne ni avec PowerShell 7 et les versions ultérieures, ni avec PowerShell Core 6.
> En tant que composant d’expédition de Windows, il continue d’être officiellement pris en charge pour la sécurité et les correctifs de maintenance de haute priorité. Nous n’avons actuellement aucun projet de supprimer l’environnement ISE de Windows.

## <a name="editing-with-visual-studio-code"></a>Édition avec Visual Studio Code

1. Installer Visual Studio Code. Pour plus d’informations, voir la vue d’ensemble [Configurer Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).

    Les instructions d’installation sont propres à chaque plateforme :

    - **Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows](https://code.visualstudio.com/docs/setup/windows).
    - **macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS](https://code.visualstudio.com/docs/setup/mac).
    - **Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux](https://code.visualstudio.com/docs/setup/linux).

1. Installez l’extension PowerShell.

   1. Lancez l’application Visual Studio Code en tapant `code` dans une console, ou `code-insiders` si vous avez installé Visual Studio Code Insiders.
   1. Lancez **Quick Open** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>P</kbd>. Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.
   1. La vue **Extensions** s’ouvre dans la barre latérale. Sélectionnez l’extension de PowerShell de Microsoft.
      Un écran Visual Studio Code semblable à l’image suivante apparaît :

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.
   1. Après l’installation, si vous voyez le bouton **Installer** se changer en **Recharger**, cliquez sur **Recharger**.
   1. Une fois Visual Studio Code rechargé, vous pouvez passer à l’édition.

Par exemple, pour créer un fichier, cliquez sur **Fichier > Nouveau**. Pour l’enregistrer, cliquez sur **Fichier > Enregistrer**, puis indiquez un nom de fichier, comme `HelloWorld.ps1`. Pour fermer le fichier, cliquez sur `X` à côté du nom de fichier. Pour quitter Visual Studio Code, cliquez sur **Fichier > Quitter**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installation de l’extension PowerShell sur des systèmes restreints

Certains systèmes sont configurés de façon à imposer la vérification de toutes les signatures de code et l’approbation manuelle de PowerShell Editor Services pour qu’il puisse s’exécuter sur le système. Une mise à jour de la stratégie de groupe qui modifie la stratégie d’exécution est une cause probable si vous avez installé l’extension PowerShell, mais recevez une erreur de ce type :

```
Language server startup failed.
```

Pour approuver manuellement PowerShell Editor Services et l’extension PowerShell pour Visual Studio Code, ouvrez une invite PowerShell et exécutez la commande suivante :

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Le message **Voulez-vous exécuter le logiciel provenant de cet éditeur non approuvé ?** apparaît.
Tapez `A` pour exécuter le fichier. Ouvrez ensuite Visual Studio Code et vérifiez que l’extension PowerShell fonctionne correctement. Si vous rencontrez toujours des problèmes de mise en route, faites-le-nous savoir sur [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

> [!NOTE]
> L’extension PowerShell pour Visual Studio Code ne prend pas en charge l’exécution en mode de langage avec contrainte. Pour plus d’informations, consultez le [Problème de suivi de cette prise en charge par GitHub](https://github.com/PowerShell/vscode-powershell/issues/606).

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Utilisation d’une version antérieure de l’extension PowerShell pour Windows PowerShell v3 et v4

Bien que l’extension PowerShell actuelle [ne prenne plus en charge v3 et v4](https://github.com/PowerShell/vscode-powershell/issues/1310), vous pouvez toujours utiliser la dernière version de l’extension qui a été exécutée.

> [!NOTE]
> Il n’y aura aucun correctif supplémentaire pour cette version antérieure de l’extension. Bien que fournie « TELLE QUELLE », elle est à votre disposition si vous utilisez encore Windows PowerShell v3 et Windows PowerShell v4.

Tout d’abord, ouvrez le volet Extension et recherchez `PowerShell`. Cliquez ensuite sur l’engrenage, puis sélectionnez **Installer une autre version...** .

![Installer une autre version...](media/using-vscode/install-another-version.png)

Sélectionnez ensuite la version **`2020.1.0`** . Cette version de l’extension était la dernière version à prendre en charge v3 et v4.

Ajoutez également le paramètre suivant afin que la version de votre extension ne soit pas mise à jour automatiquement :

```json
{
    "extensions.autoUpdate": false
}
```

Même si cela fonctionnera dans un avenir proche, Visual Studio Code pourrait implémenter une modification qui arrêterait cette version de l’extension.
Pour cette raison et à cause de l’absence de support, nous vous recommandons plutôt de procéder comme suit :

- Téléchargez PowerShell 7 : il s’agit d’une installation côte à côte avec Windows PowerShell qui fonctionne de manière optimale avec l’extension PowerShell
- Mise à niveau vers Windows PowerShell 5.1

La section [Édition avec Visual Studio Code](#editing-with-visual-studio-code) de cet article contient des liens vers l’emplacement d’installation.

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

Après avoir configuré ce paramètre, redémarrez Visual Studio Code ou rechargez la fenêtre Visual Studio Code active avec la **Palette de commandes**, puis tapez **Développeur : Recharger la fenêtre**.

Si vous ouvrez le menu de session, vous trouvez à présent les versions supplémentaires de PowerShell.

> [!NOTE]
> Si vous générez PowerShell à partir de la source, c’est un excellent moyen de tester votre build locale de PowerShell.

### <a name="configuration-settings-for-visual-studio-code"></a>Paramètres de configuration de Visual Studio Code

Tout d’abord, si vous n’êtes pas familiarisé avec la modification des paramètres dans Visual Studio Code, nous vous recommandons de consulter la [documentation des paramètres de Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).

En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.

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
> Pour plus d’informations sur l’encodage de fichier dans Visual Studio Code, consultez [Présentation de l’encodage de fichier](understanding-file-encoding.md).
>
> Consultez également [Comment répliquer l’expérience ISE dans Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) pour obtenir d’autres conseils de configuration de Visual Studio Code pour l’édition avec PowerShell.

## <a name="debugging-with-visual-studio-code"></a>Débogage avec Visual Studio Code

### <a name="no-workspace-debugging"></a>Débogage sans espace de travail

À partir de Visual Studio Code version 1.9, il est possible de déboguer des scripts PowerShell sans ouvrir le dossier qui les contient. Ouvrez un fichier de script PowerShell avec **Fichier > Ouvrir un fichier…** , définissez un point d’arrêt sur une ligne (appuyez sur <kbd>F9</kbd>), puis appuyez sur <kbd>F5</kbd> pour démarrer le débogage. Le volet Actions de débogage apparaît ; il permet de s’arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.

### <a name="workspace-debugging"></a>Débogage d’espace de travail

Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier ouvert dans Visual Studio Code dans le menu **Fichier**  avec **Ouvrir le dossier…** . Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.

Même dans ce mode, vous pouvez lancer le débogage du script PowerShell actuellement sélectionné en appuyant sur <kbd>F5</kbd>. Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert. Nous y arriverons dans un instant.

Suivez ces étapes pour créer votre fichier de configuration de débogage :

  1. Ouvrez la vue **Déboguer** sur Windows ou Linux en appuyant sur <kbd>Ctrl</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>. Sur macOS, appuyez sur <kbd>Cmd</kbd>+<kbd>Maj</kbd>+<kbd>D</kbd>.
  1. Cliquez sur le lien « Créer un fichier launch. JSON ».
  1. Visual Studio Code vous invite à **Sélectionner un environnement**. Choisissez **PowerShell**.
  1. Enfin, choisissez le type de débogage que vous souhaitez utiliser :

- **Lancer le fichier actuel** : lancer et déboguer le fichier dans la fenêtre de l’éditeur actuellement active
- **Lancer le script** : lancer et déboguer le fichier ou la commande spécifiés
- **Session interactive** : déboguer les commandes exécutées à partir de la console intégrée
- **Attacher** : attacher le débogueur à un processus hôte PowerShell en cours d’exécution

Visual Studio Code crée alors un répertoire et un fichier `.vscode\launch.json` à la racine du dossier de votre espace de travail. C’est là que votre configuration de débogage est stockée. Si vos fichiers se trouvent dans un référentiel Git, il est généralement préférable de valider le fichier `launch.json`. Le fichier `launch.json` présente le contenu suivant :

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

## <a name="useful-resources"></a>Ressources utiles

Quelques vidéos et billets de blogs peuvent être utiles pour bien démarrer avec l’extension PowerShell pour Visual Studio Code :

### <a name="videos"></a>Videos

- [Utilisation de Visual Studio Code comme éditeur PowerShell par défaut](https://youtu.be/bGn45vIeAMM)
- [Visual Studio Code : exploration du débogage de vos scripts PowerShell](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>Billets de blog :

- [Extension PowerShell][ps-extension]
- [Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]
- [Aide sur le débogage avec Visual Studio Code][vscode-guide]
- [Débogage de PowerShell dans Visual Studio Code][ps-vscode]
- [Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]
- [Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]
- [Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]
- [Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]
- [Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]

## <a name="powershell-extension-for-visual-studio-code"></a>Extension PowerShell pour Visual Studio Code

Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).

Si vous êtes intéressé à contribuer, les demandes de tirage sont très appréciées. Pour commencer, suivez les [instructions de la documentation du développeur sur GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md).

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Résolution des problèmes de l’extension PowerShell pour Visual Studio Code

Si vous rencontrez des problèmes lors de l’utilisation de Visual Studio Code pour le développement de scripts PowerShell, consultez le [guide de résolution des problèmes de sur GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)

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
