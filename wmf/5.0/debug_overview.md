---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="improvements-in-powershell-script-debugging"></a>Améliorations apportées au débogage de script PowerShell

Un certain nombre d’améliorations ont été apportées à PowerShell 5.0 pour améliorer l’expérience de débogage :

## <a name="break-all"></a>Interrompre tout

La console PowerShell et Windows PowerShell ISE vous permettent désormais de vous arrêter dans le débogueur pour exécuter des scripts. Cela fonctionne dans les sessions locales et distantes.

Dans la console, appuyez sur **Ctrl+Pause**.

Dans ISE, appuyez sur **Ctrl+B** ou utilisez la commande de menu **Déboguer -> Interrompre tout**.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Débogage à distance et modification de fichiers à distance dans Windows PowerShell ISE

Windows PowerShell ISE vous permet désormais d’ouvrir et de modifier des fichiers dans une session à distance en exécutant la commande PSEdit.
Par exemple, vous pouvez ouvrir un fichier pour le modifier à partir de la ligne de commande dans une session distante en procédant comme suit :

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

De plus, vous pouvez maintenant modifier et enregistrer les modifications dans un fichier distant qui est ouvert automatiquement dans Windows PowerShell ISE quand vous atteignez un point d’arrêt.
Désormais, vous pouvez déboguer un fichier de script qui s’exécute sur un ordinateur distant, modifier le fichier pour corriger une erreur puis réexécuter le script modifié.

## <a name="advanced-script-debugging"></a>Débogage de script avancé

Il existe de nouvelles fonctionnalités de débogage avancées qui vous permettent de joindre tout processus de l’ordinateur local ayant chargé Windows PowerShell, et de déboguer des instances d’exécution arbitraires dans ce processus.

### <a name="runspace-debugging"></a>Débogage d’instance d’exécution

De nouvelles applets de commande permettent de répertorier les instances en cours d’exécution dans un processus et d’attacher la console Windows PowerShell ou le débogueur ISE à cette instance d’exécution pour le débogage de script :

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Joindre au processus hébergeant PowerShell

Vous pouvez désormais joindre n’importe quel processus de l’ordinateur ayant chargé Windows PowerShell. Pour cela, vous devez établir une session interactive avec le processus, comme vous le faites pour établir une session interactive à distance en exécutant l’applet de commande Enter-PSSession :

-   Enter-PSHostProcess
-   Exit-PSHostProcess
