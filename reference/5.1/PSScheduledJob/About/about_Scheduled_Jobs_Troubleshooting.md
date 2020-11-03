---
description: Explique comment résoudre les problèmes liés aux tâches planifiées
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: 924205edb9d44724cfef201d84baa304ecde67ad
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207246"
---
# <a name="about-scheduled-jobs-troubleshooting"></a>À propos de la résolution des problèmes de tâches planifiées

## <a name="short-description"></a>Description courte

Explique comment résoudre les problèmes liés aux tâches planifiées

## <a name="long-description"></a>Description longue

Ce document décrit certains des problèmes que vous pouvez rencontrer lors de l’utilisation des fonctionnalités de la tâche planifiée de PowerShell et propose des solutions à ces problèmes.

Avant d’utiliser les tâches planifiées PowerShell, consultez [about_Scheduled_Jobs](about_Scheduled_Jobs.md) et les tâches planifiées associées à propos des rubriques.

Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).

## <a name="cant-find-job-results"></a>Résultats du travail introuvables

### <a name="basic-method-for-getting-job-results-in-powershell"></a>Méthode de base pour obtenir les résultats d’un travail dans PowerShell

Lorsqu’une tâche planifiée s’exécute, elle crée une instance de la tâche planifiée. Pour afficher, gérer et obtenir les résultats des instances de tâche planifiée, utilisez les applets de commande Job.

> [!NOTE]
> Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session. Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .

Pour obtenir la liste de toutes les instances d’une tâche planifiée, utilisez l’applet de commande `Get-Job` .

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

L' `Get-Job` applet de commande envoie les objets **ProcessJob** vers le dessous du pipeline. L' `Format-Table` applet de commande affiche le **nom** , l' **ID** et les propriétés **PSBeginTime** d’une instance de tâche planifiée dans une table.

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

Pour obtenir les résultats d’une instance d’une tâche planifiée, utilisez l’applet de commande `Receive-Job` . La commande suivante obtient les résultats de l’instance la plus récente de ProcessJob (ID = 50).

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a>Méthode de base pour rechercher des résultats de travail sur disque

Pour gérer les tâches planifiées, utilisez les applets de commande Job, telles que `Get-Job` et `Receive-Job` .

Si `Get-Job` n’obtient pas l’instance de tâche ou `Receive-Job` n’obtient pas les résultats du travail, vous pouvez rechercher la tâche sur le disque dans les fichiers de l’historique d’exécution.
L’historique d’exécution contient un enregistrement de toutes les instances de tâche déclenchées.

Vérifiez qu’il existe un répertoire nommé timestamp dans le répertoire pour une tâche planifiée dans le chemin d’accès suivant :

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

Par exemple :

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

Par exemple, l' `Get-ChildItem` applet de commande obtient l’historique d’exécution sur le disque de la tâche planifiée **ProcessJob** .

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

Chaque répertoire nommé timestamp représente une instance de tâche. Les résultats de chaque instance de tâche sont enregistrés dans un fichier **Results.xml** dans le répertoire nommé timestamp.

Par exemple, la commande suivante obtient les fichiers de **Results.xml** pour chaque instance enregistrée de la tâche planifiée **ProcessJob** . Si le fichier **Results.xml** est manquant, PowerShell ne peut pas retourner ou afficher les résultats du travail.

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

L’applet de commande Job peut ne pas être en mesure d’obtenir des instances de tâche planifiée ou leurs résultats, car le module **PSScheduledJob** n’est pas importé dans la session.

> [!NOTE]
> Avant d’utiliser une applet de commande Job sur des instances de tâche planifiée, vérifiez que le module **PSScheduledJob** est inclus dans la session. Sans le module **PSScheduledJob** , les applets de commande Job ne peuvent pas obtenir les instances de tâche planifiée ou leurs résultats.

Pour importer le module **PSScheduledJob** :

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a>Receive-Job applet de commande a peut-être déjà retourné les résultats

Si `Receive-Job` ne retourne pas de résultats d’instance de travail, cela peut être dû au fait qu’une `Receive-Job` commande a été exécutée pour cette instance de tâche dans la session active sans le paramètre **Keep** .

Lorsque vous utilisez `Receive-Job` sans le paramètre **Keep** , `Receive-Job` retourne les résultats de la tâche et définit la propriété **HasMoreData** de l’instance de tâche sur **false** . La valeur **false** signifie que `Receive-Job` a retourné les résultats de la tâche et que l’instance n’a plus de résultats à retourner. Ce paramètre est approprié pour les travaux en arrière-plan standard, mais pas pour les instances de tâches planifiées, qui sont enregistrées sur le disque.

Pour réafficher les résultats de l’instance de tâche, démarrez une nouvelle session PowerShell en tapant `PowerShell` . Importez le module **PSScheduledJob** , puis réessayez d' `Receive-Job` exécuter la commande.

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a>Utilisation du paramètre Keep pour obtenir des résultats plus d’une fois dans une session

Pour obtenir le résultat d’une instance de tâche plus d’une fois dans une session, utilisez le paramètre **Keep** de l’applet de commande `Receive-Job` .

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a>La tâche planifiée est peut-être endommagée

Si une tâche planifiée est endommagée, PowerShell supprime la tâche planifiée endommagée et ses résultats. Vous ne pouvez pas récupérer les résultats d’une tâche planifiée endommagée.

Pour déterminer si une tâche planifiée existe toujours, utilisez l’applet de commande `Get-ScheduledJob` .

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a>Le nombre de résultats a peut-être dépassé le ExecutionHistoryLength

La propriété **ExecutionHistoryLength** d’une tâche planifiée détermine le nombre d’instances de travail, ainsi que leurs résultats, qui sont enregistrés sur le disque. La valeur par défaut est 32.
Lorsque le nombre d’instances d’une tâche planifiée dépasse cette valeur, PowerShell supprime l’instance de tâche la plus ancienne pour faire de la place pour chaque nouvelle instance de tâche.

Pour obtenir la valeur de la propriété **ExecutionHistoryLength** d’une tâche planifiée, utilisez le format de commande suivant :

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

Par exemple, la commande suivante obtient la valeur de la propriété **ExecutionHistoryLength** de la tâche planifiée **ProcessJob** .

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

Pour définir ou modifier la valeur de la propriété **ExecutionHistoryLength** , utilisez le paramètre **MaxResultCount** des applets de commande `Register-ScheduledJob` et `Set-ScheduledJob` .

La commande suivante augmente la valeur de la propriété **ExecutionHistoryLength** à 50.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a>Les résultats de l’instance de tâche ont peut-être été supprimés

Le paramètre **ClearExecutionHistory** de l' `Set-ScheduledJob` applet de commande supprime l’historique d’exécution d’un travail. Vous pouvez utiliser cette fonctionnalité pour libérer de l’espace disque ou supprimer des résultats qui ne sont pas nécessaires, ou déjà utilisés, analysés ou enregistrés à un autre emplacement.

Pour supprimer l’historique d’exécution d’une tâche planifiée, utilisez le paramètre **ClearExecutionHistory** de la tâche planifiée.

La commande suivante supprime l’historique d’exécution de la tâche planifiée **ProcessJob** .

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

En outre, l’applet de commande supprime les résultats de la `Remove-Job` tâche. Lorsque vous utilisez `Remove-Job` pour supprimer une tâche planifiée, elle supprime toutes les instances du travail sur le disque, y compris l’historique d’exécution et tous les résultats de la tâche.

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a>Les travaux démarrés à l’aide de l’applet de commande Start-Job ne sont pas enregistrés sur le disque

Lorsque vous utilisez `Start-Job` pour démarrer une tâche planifiée, au lieu d’utiliser un déclencheur de tâche, `Start-Job` démarre une tâche en arrière-plan standard. La tâche en arrière-plan et ses résultats ne sont pas stockés dans l’historique d’exécution du travail sur le disque.

Vous pouvez utiliser l' `Get-Job` applet de commande pour obtenir le travail et l' `Receive-Job` applet de commande pour obtenir les résultats de la tâche, mais les résultats sont disponibles uniquement jusqu’à ce que vous les receviez, à moins que vous n’utilisiez le paramètre Keep de l’applet de commande `Receive-Job` .

En outre, les travaux en arrière-plan et leurs résultats sont spécifiques à la session ; ils existent uniquement dans la session dans laquelle ils sont créés. Si vous supprimez le travail avec `Remove-Job` , fermez la session ou fermez PowerShell, l’instance de tâche et ses résultats sont supprimés.

## <a name="scheduled-job-doesnt-run"></a>La tâche planifiée ne s’exécute pas

Les tâches planifiées ne s’exécutent pas automatiquement si le travail est déclenché ou si la tâche planifiée est désactivée.

Utilisez l' `Get-ScheduledJob` applet de commande pour récupérer la tâche planifiée. Vérifiez que la valeur de la propriété **Enabled** de la tâche planifiée est **true** .

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

Utilisez l' `Get-JobTrigger` applet de commande pour récupérer les déclencheurs de la tâche planifiée.
Vérifiez que la valeur de la propriété **Enabled** du déclencheur de tâche est **true** .

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a>Les tâches planifiées ne s’exécutent pas automatiquement si les déclencheurs de tâche ne sont pas valides

Par exemple, un déclencheur de tâche peut spécifier une date passée ou une date qui ne se produit pas, par exemple, le 5e lundi du mois.

Les tâches planifiées ne s’exécutent pas automatiquement si les conditions du déclencheur de tâche ou des options de tâche ne sont pas satisfaites.

Par exemple, une tâche planifiée qui s’exécute uniquement lorsqu’un utilisateur particulier ouvre une session sur l’ordinateur ne s’exécutera pas si cet utilisateur ne se connecte pas ou ne se connecte qu’à distance.

Examinez les options de la tâche planifiée et assurez-vous qu’elles sont satisfaites.
Par exemple, une tâche planifiée qui requiert que l’ordinateur soit inactif ou nécessite une connexion réseau, ou qui a un long **IdleDuration** ou un bref **IdleTimeout** peut ne jamais s’exécuter.

Utilisez l' `Get-ScheduledJobOption` applet de commande pour examiner les options de tâche et leurs valeurs.

```powershell
Get-ScheduledJob -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Pour obtenir une description des options de tâche planifiée, consultez [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).

### <a name="the-scheduled-job-instance-might-have-failed"></a>L’instance de tâche planifiée a peut-être échoué

Si une commande de tâche planifiée échoue, PowerShell la signale immédiatement en générant un message d’erreur. Toutefois, si le travail échoue quand Planificateur de tâches tente de l’exécuter, l’erreur n’est pas disponible pour PowerShell.

Utilisez les méthodes suivantes pour détecter et corriger les échecs de tâche :

Recherchez les erreurs dans le journal des événements Planificateur de tâches. Pour vérifier le journal, utilisez observateur d’événements ou une commande PowerShell telle que la suivante :

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

Vérifiez l’enregistrement du travail dans Planificateur de tâches. Les tâches planifiées PowerShell sont stockées dans le dossier planifié de tâches suivant :

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a>La tâche planifiée peut ne pas s’exécuter en raison d’une autorisation insuffisante

Les tâches planifiées s’exécutent avec les autorisations de l’utilisateur qui a créé le travail ou les autorisations de l’utilisateur spécifié par le paramètre **Credential** dans la `Register-ScheduledJob` `Set-ScheduledJob` commande ou.

Si cet utilisateur n’est pas autorisé à exécuter les commandes ou les scripts, le travail échoue.

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a>Impossible d’effectuer une tâche planifiée ou une tâche planifiée endommagée

Dans de rares occasions, les tâches planifiées peuvent être endommagées ou contenir des contradictions internes qui ne peuvent pas être résolues. En général, cela se produit lorsque les fichiers XML de la tâche planifiée sont modifiés manuellement, ce qui génère un code XML non valide.

Lorsqu’une tâche planifiée est endommagée, PowerShell tente de supprimer la tâche planifiée, son historique d’exécution et ses résultats sur le disque.

S’il ne peut pas supprimer la tâche planifiée, vous obtiendrez un message d’erreur de travail endommagé chaque fois que vous exécutez l’applet de commande `Get-ScheduledJob` .

Pour supprimer une tâche planifiée endommagée, utilisez l’une des méthodes suivantes :

Supprimez le `<ScheduledJobName>` Répertoire de la tâche planifiée. Ne supprimez pas le répertoire **ScheduledJob** .

Emplacement du répertoire :

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

Par exemple :

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

Utilisez Planificateur de tâches pour supprimer la tâche planifiée. Les tâches planifiées PowerShell s’affichent dans le chemin d’accès Planificateur de tâches suivant :

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a>Les applets de commande Job ne peuvent pas trouver régulièrement des tâches planifiées

Lorsque le module **PSScheduledJob** n’est pas dans la session active, les applets de commande Job ne peuvent pas obtenir de tâches planifiées, les démarrer ou obtenir leurs résultats.

Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou exécutez ou récupérez une applet de commande dans le module, telle que l’applet de commande `Get-ScheduledJob` .
À compter de PowerShell 3,0, les modules sont importés automatiquement lorsque vous récupérez ou utilisez une applet de commande dans le module.

Lorsque le module **PSScheduledJob** n’est pas dans la session active, la séquence de commandes suivante est possible.

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

Ce comportement se produit parce que la `Get-ScheduledJob` commande importe automatiquement le module **PSScheduledJob** , puis exécute la commande.

## <a name="see-also"></a>Voir aussi

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)

[Planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-reference)
