---
description: Décrit comment exécuter des travaux sur des ordinateurs distants.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 470fecd5d8eb0ef567d5d68d6a0fa940b6c819db
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524754"
---
# <a name="about-remote-jobs"></a>À propos des travaux distants

## <a name="short-description"></a>Description courte
Décrit comment exécuter des tâches en arrière-plan sur des ordinateurs distants.

## <a name="detailed-description"></a>Description détaillée

PowerShell exécute simultanément des commandes et des scripts par le biais de travaux. Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.

- `RemoteJob` -Les commandes et les scripts s’exécutent dans une session à distance.
- `BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local. Pour plus d’informations, consultez [à propos des_tâches](about_Jobs.md).
- `PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local. Pour plus d’informations, consultez [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).

L’exécution de scripts à distance, sur un ordinateur distinct ou dans un processus distinct, offre une grande isolation. Toutes les erreurs qui se produisent dans le travail distant n’affectent pas les autres travaux en cours d’exécution ou la session parente qui a démarré le travail. Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet. Tous les objets sont sérialisés et désérialisés lorsqu’ils sont transmis entre la session parente et la session distante (travail). La sérialisation d’objets de données complexes volumineux peut consommer de grandes quantités de ressources de calcul et de mémoire et transférer de grandes quantités de données sur le réseau.

> [!IMPORTANT]
> La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline. Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé. Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.

Il existe deux façons de contourner cette situation :

1. Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées. Consultez la section [processus détachés](#how-to-run-as-a-detached-process) de cet article.
1. Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail. Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).

## <a name="remote-jobs"></a>Travaux distants

Vous pouvez exécuter des travaux sur des ordinateurs distants à l’aide de trois méthodes différentes.

- Démarrer une session interactive sur un ordinateur distant. Démarrez ensuite un travail dans la session interactive. Les procédures sont les mêmes que l’exécution d’un travail local, bien que toutes les actions soient effectuées sur l’ordinateur distant.

- Exécuter une tâche sur un ordinateur distant qui retourne ses résultats à l’ordinateur local. Utilisez cette méthode lorsque vous souhaitez collecter les résultats des travaux et les conserver dans un emplacement central sur l’ordinateur local.

- Exécutez un travail sur un ordinateur distant qui conserve ses résultats sur l’ordinateur distant. Utilisez cette méthode lorsque les données du travail sont conservées de manière plus sécurisée sur l’ordinateur d’origine.

### <a name="start-a-job-in-an-interactive-session"></a>Démarrer un travail dans une session interactive

Vous pouvez démarrer une session interactive avec un ordinateur distant, puis démarrer un travail pendant la session interactive. Pour plus d’informations sur les sessions interactives, consultez about_Remote et `Enter-PSSession` .

La procédure de démarrage d’un travail dans une session interactive est presque identique à la procédure de démarrage d’une tâche en arrière-plan sur l’ordinateur local. Toutefois, toutes les opérations se produisent sur l’ordinateur distant, et non sur l’ordinateur local.

1. Utilisez l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec un ordinateur distant. Vous pouvez utiliser le paramètre ComputerName de `Enter-PSSession` pour établir une connexion temporaire pour la session interactive. Vous pouvez utiliser le paramètre session pour exécuter la session interactive dans une session PowerShell (PSSession).

   La commande suivante démarre une session interactive sur l’ordinateur SERVEUR01.

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   L’invite de commandes change pour indiquer que vous êtes maintenant connecté à l’ordinateur SERVEUR01.

   ```
   Server01\C:>
   ```

1. Pour démarrer un travail distant dans la session, utilisez l' `Start-Job` applet de commande. La commande suivante exécute une tâche distante qui obtient les événements dans le journal des événements Windows PowerShell sur l’ordinateur SERVEUR01. L' `Start-Job` applet de commande retourne un objet qui représente la tâche.

   Cette commande enregistre l’objet de traitement dans la `$job` variable.

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   Pendant l’exécution de la tâche, vous pouvez utiliser la session interactive pour exécuter d’autres commandes, y compris d’autres travaux. Toutefois, vous devez garder la session interactive ouverte jusqu’à ce que la tâche soit terminée. Si vous mettez fin à la session, le travail est interrompu et les résultats sont perdus.

1. Pour déterminer si la tâche est terminée, affichez la valeur de la `$job` variable ou utilisez l' `Get-Job` applet de commande pour obtenir la tâche. La commande suivante utilise l' `Get-Job` applet de commande pour afficher le travail.

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   La `Get-Job` sortie indique que la tâche est en cours d’exécution sur l’ordinateur « localhost », car le travail a démarré sur le même ordinateur (dans le cas présent, SERVEUR01).

1. Pour obtenir les résultats du travail, utilisez l’applet de commande `Receive-Job` . Vous pouvez afficher les résultats dans la session interactive ou les enregistrer dans un fichier sur l’ordinateur distant. La commande suivante obtient les résultats du travail dans la variable $job. La commande utilise l’opérateur de redirection ( `>` ) pour enregistrer les résultats de la tâche dans le fichier PsLog.txt sur l’ordinateur SERVEUR01.

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. Pour mettre fin à la session interactive, utilisez l’applet de commande `Exit-PSSession` . L’invite de commandes change pour indiquer que vous êtes à nouveau dans la session d’origine sur l’ordinateur local.

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. Pour afficher le contenu du `PsLog.txt` fichier sur l’ordinateur SERVEUR01 à tout moment, démarrez une autre session interactive ou exécutez une commande à distance. Ce type de commande est mieux exécuté dans une session PSSession (connexion persistante) au cas où vous souhaiteriez utiliser plusieurs commandes pour examiner et gérer les données dans le `PsLog.txt` fichier. Pour plus d’informations sur sessions PSSession, consultez [about_PSSessions](about_PSSessions.md).

   Les commandes suivantes utilisent l' `New-PSSession` applet de commande pour créer une **session PSSession** qui est connectée à l’ordinateur Serveur01, et elles utilisent l' `Invoke-Command` applet de commande pour exécuter une `Get-Content` commande dans la session PSSession afin d’afficher le contenu du fichier.

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>Démarrer une tâche distante qui retourne les résultats à l’ordinateur local (AsJob)

Pour démarrer un travail sur un ordinateur distant qui retourne les résultats de la commande à l’ordinateur local, utilisez le paramètre **AsJob** d’une applet de commande, telle que l’applet de commande `Invoke-Command` .

Quand vous utilisez le paramètre **AsJob** , l’objet de traitement est réellement créé sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant. Une fois le travail terminé, les résultats sont retournés à l’ordinateur local.

Vous pouvez utiliser les applets de commande qui contiennent le nom du travail (les applets de commande Job) pour gérer n’importe quel travail créé par une applet de commande. La plupart des applets de commande qui ont des paramètres **AsJob** n’utilisent pas la communication à distance PowerShell. vous pouvez donc les utiliser même sur des ordinateurs qui ne sont pas configurés pour la communication à distance et qui ne satisfont pas à la configuration requise pour la communication à distance.

1. La commande suivante utilise le paramètre **AsJob** de `Invoke-Command` pour démarrer un travail sur l’ordinateur SERVEUR01. La tâche exécute une `Get-Eventlog` commande qui obtient les événements dans le journal système. Vous pouvez utiliser le paramètre JobName pour attribuer un nom complet à la tâche.

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   Les résultats de la commande ressemblent à l’exemple de sortie suivant.

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   Lorsque le paramètre **AsJob** est utilisé, `Invoke-Command` retourne le même type d’objet de traitement que celui `Start-Job` retourné par. Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une `Get-Job` commande pour obtenir le travail.

   Notez que la valeur de la propriété Location indique que la tâche a été exécutée sur l’ordinateur SERVEUR01.

1. Pour gérer un travail démarré à l’aide du paramètre **AsJob** de l’applet de commande `Invoke-Command` , utilisez les applets de commande Job. Étant donné que l’objet de traitement qui représente le travail distant se trouve sur l’ordinateur local, vous n’avez pas besoin d’exécuter des commandes à distance pour gérer le travail.

   Pour déterminer si le travail est terminé, utilisez une `Get-Job` commande. La commande suivante obtient toutes les tâches qui ont été démarrées dans la session active.

   ```powershell
   Get-Job
   ```

   Étant donné que la tâche à distance a été démarrée dans la session active, une `Get-Job` commande locale obtient la tâche. La propriété State de l’objet de traitement indique que la commande a été correctement exécutée.

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. Pour obtenir les résultats du travail, utilisez l’applet de commande `Receive-Job` . Étant donné que les résultats du travail sont automatiquement retournés à l’ordinateur sur lequel se trouve l’objet de traitement, vous pouvez obtenir les résultats avec une `Receive-Job` commande locale.

   La commande suivante utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail. Elle utilise l’ID de session pour identifier le travail. Cette commande enregistre les résultats de la tâche dans la variable $results. Vous pouvez également rediriger les résultats vers un fichier.

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>Démarrer un travail distant qui conserve les résultats sur l’ordinateur distant

Pour démarrer un travail sur un ordinateur distant qui conserve les résultats de la commande sur l’ordinateur distant, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande sur un ordinateur distant. Vous pouvez utiliser cette méthode pour exécuter des travaux sur plusieurs ordinateurs.

Lorsque vous exécutez une `Start-Job` commande à distance, l’objet de traitement est créé sur l’ordinateur distant et les résultats de la tâche sont conservés sur l’ordinateur distant.
Du point de vue du travail, toutes les opérations sont locales. Vous exécutez simplement des commandes à distance pour gérer un travail local sur l’ordinateur distant.

1. Utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande sur un ordinateur distant.

   Cette commande requiert une session PSSession (connexion persistante). Si vous utilisez le paramètre ComputerName de `Invoke-Command` pour établir une connexion temporaire, la `Invoke-Command` commande est considérée comme terminée lorsque l’objet de traitement est retourné. Par conséquent, la connexion temporaire est fermée et le travail est annulé.

   La commande suivante utilise l' `New-PSSession` applet de commande pour créer une session PSSession qui est connectée à l’ordinateur SERVEUR01. La commande enregistre la session PSSession dans la `$s` variable.

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   La commande suivante utilise l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande dans la session PSSession. La `Start-Job` commande et la `Get-Eventlog` commande sont placées entre accolades.

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   Les résultats ressemblent à l’exemple de sortie suivant.

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   Lorsque vous exécutez une `Start-Job` commande à distance, `Invoke-Command` retourne le même type d’objet de traitement que celui `Start-Job` retourné par. Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une `Get-Job` commande pour obtenir le travail.

   Notez que la valeur de la propriété **location** indique que la tâche a été exécutée sur l’ordinateur local, appelée « localhost », même si la tâche a été exécutée sur l’ordinateur SERVEUR01. Étant donné que l’objet de traitement est créé sur l’ordinateur SERVEUR01 et que la tâche s’exécute sur le même ordinateur, il est considéré comme une tâche en arrière-plan locale.

1. Pour gérer un travail distant, utilisez les applets de commande **Job** . Étant donné que l’objet de traitement se trouve sur l’ordinateur distant, vous devez exécuter des commandes à distance pour obtenir, arrêter, attendre ou récupérer les résultats de la tâche.

   Pour voir si le travail est terminé, utilisez une `Invoke-Command` commande pour exécuter une `Get-Job` commande dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   La commande retourne un objet de traitement. La propriété **State** de l’objet de traitement indique que la commande a été correctement exécutée.

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. Pour obtenir les résultats du travail, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.

   La commande suivante utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail. Elle utilise l’ID de session pour identifier le travail. Cette commande enregistre les résultats de la tâche dans la `$results` variable. Elle utilise le paramètre Keep de `Receive-Job` pour conserver le résultat dans le cache de travaux sur l’ordinateur distant.

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   Vous pouvez également rediriger les résultats vers un fichier sur l’ordinateur local ou distant.
   La commande suivante utilise un opérateur de redirection pour enregistrer les résultats dans un fichier sur l’ordinateur SERVEUR01.

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a>Comment exécuter en tant que processus détaché

Comme mentionné précédemment, lorsque la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants. Vous pouvez utiliser la communication à distance sur l’ordinateur local pour exécuter des tâches qui ne sont pas attachées à la session PowerShell en cours.

Créez une nouvelle session PowerShell sur l’ordinateur local. Utilisé `Invoke-Command` pour démarrer un travail dans cette session. `Invoke-Command` vous permet de déconnecter une session à distance et de mettre fin à la session parente. Plus tard, vous pouvez démarrer une nouvelle session PowerShell et vous connecter à la session précédemment déconnectée pour reprendre la surveillance du travail. Toutefois, toutes les données qui ont été retournées à la session PowerShell d’origine sont perdues lorsque cette session est arrêtée. Seuls les nouveaux objets de données générés après la déconnexion sont retournés lors de la reconnexion.

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

Pour cet exemple, les travaux sont toujours attachés à une session PowerShell parente.
Toutefois, la session parente n’est pas la session PowerShell d’origine où `Invoke-Command` a été exécuté.

## <a name="see-also"></a>Voir aussi

- [about_Jobs](about_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_Remote_Variables](about_Remote_Variables.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
