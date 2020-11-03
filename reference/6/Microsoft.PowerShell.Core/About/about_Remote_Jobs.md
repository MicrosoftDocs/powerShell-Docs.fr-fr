---
description: Décrit comment exécuter des tâches en arrière-plan sur des ordinateurs distants.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: ad0400c4b4c25c9b0c7133bd916af5056dab1430
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206921"
---
# <a name="about-remote-jobs"></a>À propos des travaux distants

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment exécuter des tâches en arrière-plan sur des ordinateurs distants.

## <a name="detailed-description"></a>DESCRIPTION DÉTAILLÉE

Une tâche en arrière-plan est une commande qui s’exécute de façon asynchrone sans interagir avec la session active. L’invite de commandes s’affiche immédiatement et vous pouvez continuer à utiliser la session pendant l’exécution de la tâche.

Par défaut, les travaux en arrière-plan s’exécutent sur l’ordinateur local. Toutefois, vous pouvez utiliser différentes procédures pour exécuter des tâches en arrière-plan sur des ordinateurs distants.

Cette rubrique explique comment exécuter une tâche en arrière-plan sur un ordinateur distant. Pour plus d’informations sur la façon d’exécuter des tâches en arrière-plan sur un ordinateur local, consultez [about_Jobs](about_Jobs.md). Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Job_Details](about_Job_Details.md).

## <a name="remote-background-jobs"></a>TRAVAUX EN ARRIÈRE-PLAN DISTANTS

Vous pouvez exécuter des tâches en arrière-plan sur des ordinateurs distants à l’aide de trois méthodes différentes.

- Démarrer une session interactive avec un ordinateur distant et démarrer un travail dans la session interactive. Les procédures sont les mêmes que l’exécution d’un travail local, bien que toutes les actions soient effectuées sur l’ordinateur distant.

- Exécuter une tâche en arrière-plan sur un ordinateur distant qui retourne ses résultats à l’ordinateur local. Utilisez cette méthode lorsque vous souhaitez collecter les résultats des tâches en arrière-plan et les conserver dans un emplacement central sur l’ordinateur local.

- Exécuter une tâche en arrière-plan sur un ordinateur distant qui conserve ses résultats sur l’ordinateur distant. Utilisez cette méthode lorsque les données du travail sont conservées de manière plus sécurisée sur l’ordinateur d’origine.

### <a name="start-a-background-job-in-an-interactive-session"></a>DÉMARRER UNE TÂCHE EN ARRIÈRE-PLAN DANS UNE SESSION INTERACTIVE

Vous pouvez démarrer une session interactive avec un ordinateur distant, puis démarrer un travail en arrière-plan pendant la session interactive. Pour plus d’informations sur les sessions interactives, consultez about_Remote, et consultez Enter-PSSession.

La procédure de démarrage d’une tâche en arrière-plan dans une session interactive est presque identique à la procédure de démarrage d’une tâche en arrière-plan sur l’ordinateur local. Toutefois, toutes les opérations se produisent sur l’ordinateur distant, et non sur l’ordinateur local.

#### <a name="step-1-enter-pssession"></a>ÉTAPE 1 : ENTER-PSSESSION

Utilisez l’applet de commande Enter-PSSession pour démarrer une session interactive avec un ordinateur distant. Vous pouvez utiliser le paramètre ComputerName de Enter-PSSession pour établir une connexion temporaire pour la session interactive. Vous pouvez utiliser le paramètre session pour exécuter la session interactive dans une session PowerShell (PSSession).

La commande suivante démarre une session interactive sur l’ordinateur SERVEUR01.

```powershell
C:\PS> Enter-PSSession -computername Server01
```

L’invite de commandes change pour indiquer que vous êtes maintenant connecté à l’ordinateur SERVEUR01.

```
Server01\C:>
```

#### <a name="step-2-start-job"></a>ÉTAPE 2 : START-JOB

Pour démarrer une tâche en arrière-plan dans la session, utilisez l’applet de commande Start-Job.

La commande suivante exécute une tâche en arrière-plan qui obtient les événements dans le journal des événements Windows PowerShell sur l’ordinateur SERVEUR01. L’applet de commande Start-Job retourne un objet qui représente la tâche.

Cette commande enregistre l’objet de traitement dans la \$ variable de travail.

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

Pendant l’exécution de la tâche, vous pouvez utiliser la session interactive pour exécuter d’autres commandes, y compris d’autres travaux en arrière-plan. Toutefois, vous devez garder la session interactive ouverte jusqu’à ce que la tâche soit terminée. Si vous mettez fin à la session, le travail est interrompu et les résultats sont perdus.

#### <a name="step-3-get-job"></a>ÉTAPE 3 : OBTENIR LE TRAVAIL

Pour déterminer si la tâche est terminée, affichez la valeur de la \$ variable de tâche ou utilisez l’applet de commande Get-Job pour obtenir la tâche. La commande suivante utilise l’applet de commande Get-Job pour afficher le travail.

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

La sortie de Get-Job indique que le travail est en cours d’exécution sur l’ordinateur « localhost », car le travail a démarré sur et s’exécute sur le même ordinateur (dans ce cas, SERVEUR01).

#### <a name="step-4-receive-job"></a>ÉTAPE 4 : RÉCEPTION-TRAVAIL

Pour obtenir les résultats du travail, utilisez l’applet de commande Receive-Job. Vous pouvez afficher les résultats dans la session interactive ou les enregistrer dans un fichier sur l’ordinateur distant. La commande suivante obtient les résultats du travail dans la variable $job. La commande utilise l’opérateur de redirection (>) pour enregistrer les résultats de la tâche dans le fichier PsLog.txt sur l’ordinateur SERVEUR01.

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a>ÉTAPE 5 : QUITTER-PSSESSION

Pour mettre fin à la session interactive, utilisez l’applet de commande Exit-PSSession. L’invite de commandes change pour indiquer que vous êtes à nouveau dans la session d’origine sur l’ordinateur local.

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a>ÉTAPE 6 : INVOKE-COMMAND : OBTENIR-CONTENT

Pour afficher le contenu du fichier PsLog.txt sur l’ordinateur SERVEUR01 à tout moment, démarrez une autre session interactive ou exécutez une commande à distance. Ce type de commande est mieux exécuté dans une session PSSession (connexion persistante) au cas où vous souhaiteriez utiliser plusieurs commandes pour examiner et gérer les données dans le fichier PsLog.txt. Pour plus d’informations sur sessions PSSession, consultez about_PSSessions.

Les commandes suivantes utilisent l’applet de commande New-PSSession pour créer une session PSSession qui est connectée à l’ordinateur Serveur01, et elles utilisent l’applet de commande Invoke-Command pour exécuter une commande Get-Content dans la session PSSession afin d’afficher le contenu du fichier.

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>DÉMARRER une tâche distante qui renvoie les résultats à l’ordinateur LOCAL \( AsJob\)

Pour démarrer une tâche en arrière-plan sur un ordinateur distant qui retourne les résultats de la commande à l’ordinateur local, utilisez le paramètre AsJob d’une applet de commande, telle que l’applet de commande Invoke-Command.

Quand vous utilisez le paramètre AsJob, l’objet de traitement est réellement créé sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant. Une fois le travail terminé, les résultats sont retournés à l’ordinateur local.

Vous pouvez utiliser les applets de commande qui contiennent le nom du travail (les applets de commande Job) pour gérer n’importe quel travail créé par une applet de commande. La plupart des applets de commande qui ont des paramètres AsJob n’utilisent pas la communication à distance PowerShell. vous pouvez donc les utiliser même sur des ordinateurs qui ne sont pas configurés pour la communication à distance et qui ne satisfont pas à la configuration requise pour la communication à distance.

#### <a name="step-1-invoke-command--asjob"></a>ÉTAPE 1 : INVOKE-COMMAND-ASJOB

La commande suivante utilise le paramètre AsJob de Invoke-Command pour démarrer une tâche en arrière-plan sur l’ordinateur SERVEUR01. La tâche exécute une commande Get-Eventlog qui obtient les événements du journal système. Vous pouvez utiliser le paramètre JobName pour attribuer un nom complet à la tâche.

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

Les résultats de la commande ressemblent à l’exemple de sortie suivant.

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

Lorsque le paramètre AsJob est utilisé, Invoke-Command retourne le même type d’objet de traitement que Start-Job retourne. Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une commande Get-Job pour obtenir le travail.

Notez que la valeur de la propriété Location indique que la tâche a été exécutée sur l’ordinateur SERVEUR01.

#### <a name="step-2-get-job"></a>ÉTAPE 2 : OBTENIR LE TRAVAIL

Pour gérer un travail démarré à l’aide du paramètre AsJob de l’applet de commande Invoke-Command, utilisez les applets de commande Job. Étant donné que l’objet de traitement qui représente le travail distant se trouve sur l’ordinateur local, vous n’avez pas besoin d’exécuter des commandes à distance pour gérer le travail.

Pour déterminer si le travail est terminé, utilisez une commande Get-Job. La commande suivante obtient toutes les tâches qui ont été démarrées dans la session active.

```powershell
get-job
```

Étant donné que la tâche à distance a été démarrée dans la session active, une commande Get-Job locale obtient la tâche. La propriété State de l’objet de traitement indique que la commande a été correctement exécutée.

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a>ÉTAPE 3 : RÉCEPTION-TRAVAIL

Pour obtenir les résultats du travail, utilisez l’applet de commande Receive-Job. Étant donné que les résultats du travail sont automatiquement retournés à l’ordinateur sur lequel se trouve l’objet de traitement, vous pouvez obtenir les résultats avec une commande de Receive-Job locale.

La commande suivante utilise l’applet de commande Receive-Job pour obtenir les résultats du travail. Elle utilise l’ID de session pour identifier le travail. Cette commande enregistre les résultats de la tâche dans la variable $results. Vous pouvez également rediriger les résultats vers un fichier.

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>DÉMARRER UN TRAVAIL DISTANT QUI CONSERVE LES RÉSULTATS SUR L’ORDINATEUR DISTANT

Pour démarrer une tâche en arrière-plan sur un ordinateur distant qui conserve les résultats de la commande sur l’ordinateur distant, utilisez l’applet de commande Invoke-Command pour exécuter une commande Start-Job sur un ordinateur distant. Vous pouvez utiliser cette méthode pour exécuter des tâches en arrière-plan sur plusieurs ordinateurs.

Lorsque vous exécutez une commande Start-Job à distance, l’objet de traitement est créé sur l’ordinateur distant et les résultats de la tâche sont conservés sur l’ordinateur distant.
Du point de vue du travail, toutes les opérations sont locales. Vous exécutez simplement des commandes à distance pour gérer un travail local sur l’ordinateur distant.

#### <a name="step-1-invoke-command-start-job"></a>ÉTAPE 1 : APPELER-COMMAND START-JOB

Utilisez l’applet de commande Invoke-Command pour exécuter une commande Start-Job sur un ordinateur distant.

Cette commande requiert une session PSSession (connexion persistante). Si vous utilisez le paramètre ComputerName de Invoke-Command pour établir une connexion temporaire, la commande Invoke-Command est considérée comme terminée lorsque l’objet de traitement est retourné. Par conséquent, la connexion temporaire est fermée et le travail est annulé.

La commande suivante utilise l’applet de commande New-PSSession pour créer une session PSSession qui est connectée à l’ordinateur SERVEUR01. La commande enregistre la session PSSession dans la \$ variable s.

```powershell
$s = new-pssession -computername Server01
```

La commande suivante utilise l’applet de commande Invoke-Command pour exécuter une commande Start-Job dans la session PSSession. La commande Start-Job et la commande Get-Eventlog sont placées entre accolades.

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

Les résultats ressemblent à l’exemple de sortie suivant.

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

Lorsque vous exécutez une commande Start-Job à distance, Invoke-Command retourne le même type d’objet de traitement que Start-Job retourne. Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une commande Get-Job pour obtenir le travail.

Notez que la valeur de la propriété Location indique que la tâche a été exécutée sur l’ordinateur local, appelée « LocalHost », même si la tâche a été exécutée sur l’ordinateur SERVEUR01. Étant donné que l’objet de traitement est créé sur l’ordinateur SERVEUR01 et que la tâche s’exécute sur le même ordinateur, il est considéré comme une tâche en arrière-plan locale.

#### <a name="step-2-invoke-command-get-job"></a>ÉTAPE 2 : INVOKE-COMMAND, OBTENIR-JOB

Pour gérer un travail en arrière-plan distant, utilisez les applets de commande Job. Étant donné que l’objet de traitement se trouve sur l’ordinateur distant, vous devez exécuter des commandes à distance pour obtenir, arrêter, attendre ou récupérer les résultats de la tâche.

Pour voir si le travail est terminé, utilisez une commande Invoke-Command pour exécuter une commande Get-Job dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.

```powershell
invoke-command -session $s -scriptblock {get-job}
```

La commande retourne un objet de traitement. La propriété State de l’objet de traitement indique que la commande a été correctement exécutée.

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a>ÉTAPE 3 : APPELER-COMMAND RECEIVE-JOB

Pour obtenir les résultats du travail, utilisez l’applet de commande Invoke-Command pour exécuter une commande Receive-Job dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.

La commande suivante utilise l’applet de commande Receive-Job pour obtenir les résultats du travail. Elle utilise l’ID de session pour identifier le travail. Cette commande enregistre les résultats de la tâche dans la \$ variable results. Elle utilise le paramètre Keep de Receive-Job pour conserver le résultat dans le cache de travaux sur l’ordinateur distant.

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

Vous pouvez également rediriger les résultats vers un fichier sur l’ordinateur local ou distant.
La commande suivante utilise un opérateur de redirection pour enregistrer les résultats dans un fichier sur l’ordinateur SERVEUR01.

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a>VOIR AUSSI

[about_Jobs](about_Jobs.md)

[about_Job_Details](about_Job_Details.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)

[Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)

[Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)

[Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)

[Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
