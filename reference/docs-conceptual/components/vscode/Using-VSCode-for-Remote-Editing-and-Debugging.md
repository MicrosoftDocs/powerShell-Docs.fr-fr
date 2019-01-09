---
title: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
description: Utilisation de Visual Studio Code pour le débogage et l’édition à distance
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655608"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Utilisation de Visual Studio Code pour le débogage et l’édition à distance

Pour ceux d'entre vous qui ont été familiarisé avec l’environnement ISE, vous vous rappelez peut-être que vous pouvez exécuter `psedit file.ps1` à partir de la console intégrée pour ouvrir des fichiers - locales ou distants - avec le bouton droit dans l’environnement ISE.

En fait, cette fonctionnalité est également disponible dans l’extension PowerShell pour VSCode. Ce guide vous explique comment procéder.

## <a name="prerequisites"></a>Conditions préalables

Ce guide suppose que vous avez :

- une ressource distante (ex : une machine virtuelle, un conteneur) que vous avez accès à
- PowerShell en cours d’exécution et l’ordinateur hôte
- VSCode et l’extension PowerShell pour VSCode

Cette fonctionnalité fonctionne sur Windows PowerShell et PowerShell Core.

Cette fonctionnalité fonctionne également lorsque vous vous connectez à un ordinateur à distance via WinRM, PowerShell Direct ou SSH. Si vous souhaitez utiliser SSH, mais sont à l’aide de Windows, consultez le [version Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>C’est parti

Dans cette section, je vais vous guider avec modification à distance et le débogage à partir de mon MacBook Pro, à une VM Ubuntu s’exécutant dans Azure. Je ne pourrais pas être à l’aide de Windows, mais **le processus est identique**.

### <a name="local-file-editing-with-open-editorfile"></a>Modification avec EditorFile d’ouverture de fichier local

Avec l’extension PowerShell pour démarrer VSCode et la Console intégré PowerShell est ouvert, nous pouvons saisir `Open-EditorFile foo.ps1` ou `psedit foo.ps1` pour ouvrir le fichier local foo.ps1 se directement dans l’éditeur.

![Foo.ps1 se Open-EditorFile fonctionne localement](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 se doit déjà exister.

À partir de là, nous pouvons :

ajouter des points d’arrêt à la marge ![Ajout de point d’arrêt pour la reliure](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

et appuyez sur F5 pour déboguer le script PowerShell.
![déboguer le script local PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Pendant le débogage, vous pouvez interagir avec la console de débogage, consultez les variables dans la portée à gauche et standard outils de débogage.

### <a name="remote-file-editing-with-open-editorfile"></a>Modification avec Open-EditorFile de fichier distant

Maintenant nous allons apprendre à la modification et débogage des fichiers à distance. Les étapes sont presque identiques, il existe une seule chose que nous devons effectuer tout d’abord, entrez notre session PowerShell au serveur distant.

Il est une applet de commande au pour faire. Elle est appelée `Enter-PSSession`.

L’explication diluée vers le bas de l’applet de commande est :

- `Enter-PSSession -ComputerName foo` démarre une session via WinRM
- `Enter-PSSession -ContainerId foo` et `Enter-PSSession -VmId foo` démarrer une session via PowerShell Direct
- `Enter-PSSession -HostName foo` démarre une session via SSH

Pour plus d’informations sur `Enter-PSSession`, consultez la documentation [ici](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Je vais utiliser SSH pour l’accès distant dans la mesure où je veux à partir de macOS une VM Ubuntu dans Azure.

Tout d’abord, dans la Console intégrée, nous allons exécuter notre Enter-PSSession. Vous saurez que vous êtes dans la session, car `[something]` s’affiche à gauche de l’invite de commandes.

![L’appel à Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

À partir de là, nous pouvons effectuer les étapes exactes comme si nous étions en train de modifier un script local.

1. Exécutez `Open-EditorFile test.ps1` ou `psedit test.ps1` pour ouvrir l’élément distant `test.ps1` fichier ![Open-EditorFile le fichier test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Modifier les points d’arrêt/jeu de fichiers ![Modifiez et définissez des points d’arrêt](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Démarrer le débogage (F5) le fichier distant

![débogage de fichier distant](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

C’est tout cela ! Nous espérons que ce guide a permis à nettoyer des questions sur le débogage distant et la modification de PowerShell dans VSCode.

Si vous rencontrez des problèmes, n’hésitez pas à ouvrir des problèmes [sur le référentiel GitHub](http://github.com/powershell/vscode-powershell).
