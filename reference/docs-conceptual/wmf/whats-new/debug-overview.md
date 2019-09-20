---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations apportées au débogage de script PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147809"
---
# <a name="improvements-in-powershell-script-debugging"></a>Améliorations apportées au débogage de script PowerShell

PowerShell 5.0 intègre plusieurs améliorations qui perfectionnent l’expérience de débogage.

## <a name="break-all"></a>Interrompre tout

La console PowerShell et PowerShell ISE permettent à présent d’interrompre le débogueur pour exécuter des scripts. Cela fonctionne dans les sessions locales et distantes.

Dans la console, appuyez sur <kbd>Ctrl</kbd>+<kbd>Pause</kbd>.

Dans ISE, appuyez sur <kbd>Ctrl</kbd>+<kbd>B</kbd> ou utilisez la commande de menu **Déboguer -> Tout interrompre**.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Débogage à distance et modification de fichiers à distance dans PowerShell ISE

PowerShell ISE permet à présent d’ouvrir et de modifier des fichiers dans une session à distance en exécutant la commande PSEdit.
Par exemple, vous pouvez ouvrir un fichier pour le modifier à partir de la ligne de commande dans une session distante en procédant comme suit :

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Par ailleurs, vous pouvez maintenant modifier et enregistrer les modifications dans un fichier distant qui s’ouvre automatiquement dans PowerShell ISE quand vous atteignez un point d’arrêt. Désormais, vous pouvez déboguer un fichier de script qui s’exécute sur un ordinateur distant, modifier le fichier pour corriger une erreur puis réexécuter le script modifié.

## <a name="advanced-script-debugging"></a>Débogage de script avancé

Il existe de nouvelles fonctionnalités avancées de débogage qui permettent de joindre n’importe quel processus de l’ordinateur local ayant chargé PowerShell, et d’y déboguer des instances d’exécution.

### <a name="runspace-debugging"></a>Débogage d’instance d’exécution

De nouvelles cmdlets permettent de lister les instances d’exécution actives dans un processus et de joindre la console PowerShell ou le débogueur PowerShell ISE à l’une d’entre elles pour le débogage de script :

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Joindre au processus hébergeant PowerShell

Il est à présent possible de joindre n’importe quel processus de l’ordinateur ayant chargé PowerShell. Pour cela, ouvrez une session interactive avec le processus hôte. Pour plus d’informations, voir :

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
