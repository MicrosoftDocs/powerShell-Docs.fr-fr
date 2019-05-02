---
title: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
description: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086666"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Utilisation de Visual Studio Code pour le débogage et l’édition à distance

Ceux d’entre vous qui sont familiarisés avec l’environnement ISE se rappelleront peut-être que vous pouvez exécuter `psedit file.ps1` à partir de la console intégrée pour ouvrir des fichiers, locaux ou distants, directement dans ISE.

En fait, cette fonctionnalité est également disponible dans l’extension PowerShell pour VSCode. Ce guide vous explique comment procéder.

## <a name="prerequisites"></a>Conditions préalables

Ce guide suppose que vous disposez des éléments suivants :

- une ressource distante (par exemple une machine virtuelle, un conteneur) à laquelle vous avez accès ;
- PowerShell en cours d’exécution sur cette ressource et l’ordinateur hôte
- VSCode et l’extension PowerShell pour VSCode

Cette fonctionnalité fonctionne sur Windows PowerShell et PowerShell Core.

Cette fonctionnalité fonctionne également lorsque vous vous connectez à un ordinateur distant via WinRM, PowerShell Direct ou SSH. Si vous souhaitez utiliser SSH, mais sur Windows, consultez la [version Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).

## <a name="lets-go"></a>C’est parti

Dans cette section, je vais effectuer des modifications et un débogage à distance à partir de mon MacBook Pro sur une machine virtuelle Ubuntu s’exécutant dans Azure. Je n’utiliserai peut-être pas Windows, mais **le processus est identique**.

### <a name="local-file-editing-with-open-editorfile"></a>Modification d’un fichier local avec Open-EditorFile

Après avoir lancé l’extension PowerShell pour VSCode et ouvert la console PowerShell intégrée, nous pouvons taper `Open-EditorFile foo.ps1` ou `psedit foo.ps1` pour ouvrir le fichier local foo.ps1 directement dans l’éditeur.

![Open-EditorFile foo.ps1 fonctionne localement](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 se doit déjà exister.

À partir de là, nous pouvons :

ajouter des points d’arrêt à la gouttière ![ajout de point d’arrêt à la gouttière](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

et appuyer sur F5 pour déboguer le script PowerShell.
![débogage du script local PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Pendant le débogage, vous pouvez interagir avec la console de débogage, consultez les variables dans l’étendue à gauche, et exécutez tous les autres outils de débogage standard.

### <a name="remote-file-editing-with-open-editorfile"></a>Modification de fichiers à distance avec Open-EditorFile

Examinons maintenant la modification et le débogage de fichiers à distance. Les étapes sont presque identiques et nous n’avons qu’une seule tâche préalable à effectuer : ouvrir notre session PowerShell sur le serveur distant.

Nous utiliserons pour cela une applet de commande. Elle s’appelle `Enter-PSSession`.

Voici le fonctionnement détaillé de cette applet de commande :

- `Enter-PSSession -ComputerName foo` démarre une session via WinRM
- `Enter-PSSession -ContainerId foo` et `Enter-PSSession -VmId foo` démarrent une session via PowerShell Direct
- `Enter-PSSession -HostName foo` démarre une session via SSH

Pour plus d’informations sur `Enter-PSSession`, consultez la documentation disponible [ici](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

J’utiliserai SSH pour l’accès distant puisque je passerai de macOS vers une machine virtuelle Ubuntu dans Azure.

Tout d’abord, dans la console intégrée, exécutons Enter-PSSession. Vous saurez que vous êtes dans la session car `[something]` s’affichera à gauche de l’invite de commandes.

![L’appel à Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

De là, nous pouvons effectuer les étapes exactes comme si nous modifiions un script local.

1. Exécutez `Open-EditorFile test.ps1` ou `psedit test.ps1` pour ouvrir le fichier `test.ps1` distant ![Open-EditorFile fichier test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Modifier le fichier/définir des points d’arrêt ![modifier et définir des points d’arrêt](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Démarrer le débogage (F5) du fichier distant

![débogage du fichier distant](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Voilà, c’est tout ! Nous espérons que ce guide a répondu à vos questions sur le débogage et les modifications à distance à l’aide de PowerShell dans VSCode.

Si vous rencontrez des problèmes, n’hésitez pas à nous le faire savoir [sur le référentiel GitHub](http://github.com/powershell/vscode-powershell).
