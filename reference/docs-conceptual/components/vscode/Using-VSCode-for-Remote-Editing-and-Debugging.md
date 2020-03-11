---
title: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
description: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279128"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Utilisation de Visual Studio Code pour le débogage et l’édition à distance

Ceux d’entre vous qui sont familiarisés avec l’environnement ISE se rappelleront peut-être que vous pouvez exécuter `psedit file.ps1` à partir de la console intégrée pour ouvrir des fichiers, locaux ou distants, directement dans ISE.

Cette fonctionnalité est également disponible dans l’extension PowerShell pour VSCode. Ce guide vous explique comment procéder.

## <a name="prerequisites"></a>Prérequis

Ce guide suppose que vous disposez des éléments suivants :

- une ressource distante (par exemple une machine virtuelle, un conteneur) à laquelle vous avez accès ;
- PowerShell en cours d’exécution sur cette ressource et l’ordinateur hôte
- VSCode et l’extension PowerShell pour VSCode

Cette fonctionnalité fonctionne sur Windows PowerShell et PowerShell Core.

Cette fonctionnalité fonctionne également lorsque vous vous connectez à un ordinateur distant via WinRM, PowerShell Direct ou SSH. Si vous souhaitez utiliser SSH, mais sur Windows, consultez la [version Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).

> [!IMPORTANT]
> Les commandes `Open-EditorFile` et `psedit` fonctionnent uniquement dans la **console intégrée PowerShell** créée par l’extension PowerShell pour VSCode.

## <a name="usage-examples"></a>Exemples d'utilisation

Ces exemples montrent des modifications et un débogage à distance à partir d’un MacBook Pro sur une machine virtuelle Ubuntu s’exécutant dans Azure. Le processus est identique sur Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Modification d’un fichier local avec Open-EditorFile

Après avoir lancé l’extension PowerShell pour VSCode et ouvert la console PowerShell intégrée, nous pouvons taper `Open-EditorFile foo.ps1` ou `psedit foo.ps1` pour ouvrir le fichier local foo.ps1 directement dans l’éditeur.

![Open-EditorFile foo.ps1 fonctionne localement](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Le fichier `foo.ps1` doit déjà exister.

À partir de là, nous pouvons :

- ajouter des points d’arrêt à la marge

  ![ajout de points d’arrêt à la marge](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Appuyez sur F5 pour déboguer le script PowerShell.

  ![débogage du script local PowerShell](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Pendant le débogage, vous pouvez interagir avec la console de débogage, consultez les variables dans l’étendue à gauche, et exécutez tous les autres outils de débogage standard.

### <a name="remote-file-editing-with-open-editorfile"></a>Modification de fichiers à distance avec Open-EditorFile

Examinons maintenant la modification et le débogage de fichiers à distance. Les étapes sont presque identiques et nous n’avons qu’une seule tâche préalable à effectuer : ouvrir notre session PowerShell sur le serveur distant.

Nous utiliserons pour cela une applet de commande. Elle s’appelle `Enter-PSSession`.

Voici le fonctionnement détaillé de cette applet de commande :

- `Enter-PSSession -ComputerName foo` démarre une session via WinRM
- `Enter-PSSession -ContainerId foo` et `Enter-PSSession -VmId foo` démarrent une session via PowerShell Direct
- `Enter-PSSession -HostName foo` démarre une session via SSH

Pour plus d’informations, consultez la documentation [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Comme nous passons de macOS à une machine virtuelle Ubuntu dans Azure, nous utilisons SSH pour la communication à distance.

Tout d’abord, dans la console intégrée, exécutez `Enter-PSSession`. Vous êtes connecté à la session à distance lorsque `[<hostname>]` s’affiche à gauche de votre invite.

![L’appel à Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Maintenant, nous pouvons effectuer les mêmes étapes que si nous modifiions un script local.

1. Exécutez `Open-EditorFile test.ps1` ou `psedit test.ps1` pour ouvrir le fichier `test.ps1` distant

  ![Fichier Open-EditorFile the test.ps1](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Modifier le fichier/définir des points d’arrêt

   ![modifier et définir des points d’arrêt](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Démarrer le débogage (F5) du fichier distant

   ![débogage du fichier distant](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Si vous rencontrez des problèmes, vous pouvez ouvrir des tickets dans le [référentiel GitHub](https://github.com/powershell/vscode-powershell).
