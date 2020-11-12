---
description: Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6ddb54bac62e7bc11a045874700acb3982a0093b
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524452"
---
# <a name="about-jobs"></a>À propos des travaux

## <a name="short-description"></a>Description courte
Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.

## <a name="long-description"></a>Description longue

PowerShell exécute simultanément des commandes et des scripts par le biais de travaux. Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.

- `RemoteJob` -Les commandes et les scripts s’exécutent sur une session à distance. Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).
- `BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local.
- `PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local. Pour plus d’informations, consultez [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).

L’exécution de scripts à distance, sur un ordinateur distinct ou dans un processus distinct, offre une grande isolation. Toutes les erreurs qui se produisent dans le travail distant n’affectent pas les autres travaux en cours d’exécution ou la session parente qui a démarré le travail. Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet. Tous les objets sont sérialisés et désérialisés lorsqu’ils sont transmis entre la session parente et la session distante (travail). La sérialisation d’objets de données complexes volumineux peut consommer de grandes quantités de ressources de calcul et de mémoire et transférer de grandes quantités de données sur le réseau.

Les travaux basés sur les threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents. Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus sont terminés.

Toutefois, les travaux basés sur les threads nécessitent moins de traitement. Ils n’utilisent pas la couche de communication à distance ou la sérialisation. Les objets de résultats sont retournés en tant que références aux objets actifs dans la session active. Sans cette surcharge, les travaux basés sur les threads s’exécutent plus rapidement et utilisent moins de ressources que les autres types de travaux.

> [!IMPORTANT]
> La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline. Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé. Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.

Il existe deux façons de contourner cette limitation :

1. Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées. Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).
1. Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail. Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).

## <a name="the-job-cmdlets"></a>Applets de commande Job

|Applet de commande          |Description                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |Démarre une tâche en arrière-plan sur un ordinateur local.           |
|`Get-Job`       |Obtient les tâches en arrière-plan qui ont été démarrées dans le      |
|                |session active.                                       |
|`Receive-Job`   |Obtient les résultats des tâches en arrière-plan.                   |
|`Stop-Job`      |Arrête une tâche en arrière-plan.                                |
|`Wait-Job`      |Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches soient|
|                |Remplissez.                                              |
|`Remove-Job`    |Supprime une tâche en arrière-plan.                              |
|`Invoke-Command`|Le paramètre **AsJob** crée une tâche en arrière-plan sur un  |
|                |ordinateur distant. Vous pouvez utiliser `Invoke-Command` pour exécuter   |
|                |toute commande Job à distance, y compris `Start-Job` .       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>Comment démarrer un travail sur l’ordinateur local

Pour démarrer une tâche en arrière-plan sur l’ordinateur local, utilisez l’applet de commande `Start-Job` .

Pour écrire une `Start-Job` commande, mettez-la entre guillemets doubles ( `{}` ). Utilisez le paramètre **scriptblock** pour spécifier la commande.

La commande suivante démarre une tâche en arrière-plan qui exécute une `Get-Process` commande sur l’ordinateur local.

```powershell
Start-Job -ScriptBlock {Get-Process}
```

Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, même si le travail prend une durée prolongée. Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.

La `Start-Job` commande retourne un objet qui représente le travail. L'objet de traitement retourné par Get-Job contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.

Vous pouvez enregistrer l’objet de traitement dans une variable, puis l’utiliser avec les autres applets de commande de **tâche** pour gérer la tâche en arrière-plan. La commande suivante démarre un objet de traitement et enregistre l’objet de traitement résultant dans la `$job` variable.

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

À compter de PowerShell 6,0, vous pouvez utiliser l’opérateur d’arrière-plan ( `&` ) à la fin d’un pipeline pour démarrer un travail en arrière-plan. Pour plus d’informations, consultez [opérateur d’arrière-plan](about_Operators.md#background-operator-).

L’utilisation de l’opérateur d’arrière-plan est fonctionnellement équivalente à l’utilisation `Start-Job` de l’applet de commande dans l’exemple précédent.

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a>Obtention d’objets de travail

L' `Get-Job` applet de commande retourne des objets qui représentent les tâches en arrière-plan démarrées dans la session active. Sans paramètres, `Get-Job` retourne toutes les tâches qui ont été démarrées dans la session active.

```powershell
Get-Job
```

L’objet de traitement contient l’état du travail, qui indique si le travail est terminé. L’état d’une tâche terminée est **terminé** ou **a échoué**. Un travail peut également être **bloqué** ou **en cours d’exécution**.

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

Vous pouvez enregistrer l’objet de traitement dans une variable et l’utiliser pour représenter la tâche dans une commande ultérieure. La commande suivante obtient la tâche avec l’ID 1 et l’enregistre dans la `$job` variable.

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a>Obtention des résultats d’un travail

Lorsque vous exécutez un travail en arrière-plan, les résultats n’apparaissent pas immédiatement. Pour obtenir les résultats d’une tâche en arrière-plan, utilisez l’applet de commande `Receive-Job` .

Dans l’exemple suivant, l' `Receive-Job` applet de commande obtient les résultats de la tâche à l’aide de l’objet de traitement dans la `$job` variable.

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

Vous pouvez enregistrer les résultats d’un travail dans une variable. La commande suivante enregistre les résultats de la tâche dans la variable dans la variable `$job` `$results` .

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a>Obtention et conservation des résultats de travaux partiels

L' `Receive-Job` applet de commande obtient les résultats d’une tâche en arrière-plan. Si la tâche est terminée, `Receive-Job` obtient tous les résultats de la tâche. Si le travail est toujours en cours d’exécution, `Receive-Job` obtient les résultats générés jusqu’à présent. Vous pouvez réexécuter `Receive-Job` les commandes pour obtenir les résultats restants.

Par défaut, `Receive-Job` supprime les résultats du cache où sont stockés les résultats de la tâche. Lorsque vous réexécutez `Receive-Job` , vous recevez uniquement les nouveaux résultats qui arrivent après la première exécution.

Les commandes suivantes affichent les résultats des `Receive-Job` commandes exécutées avant la fin du travail.

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

Utilisez le paramètre **Keep** pour empêcher `Receive-Job` la suppression des résultats de la tâche retournés. Les commandes suivantes montrent l’effet de l’utilisation du paramètre **Keep** sur un travail qui n’est pas encore terminé.

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a>En attente des résultats

Si vous exécutez une commande qui prend beaucoup de temps, vous pouvez utiliser les propriétés de l’objet de traitement pour déterminer à quel moment le travail est terminé. La commande suivante utilise l' `Get-Job` objet pour récupérer toutes les tâches en arrière-plan dans la session active.

```powershell
Get-Job
```

Les résultats s’affichent dans un tableau. L’état de la tâche s’affiche dans la colonne **État** .

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

Dans ce cas, la propriété **State** indique que le travail 2 est toujours en cours d’exécution. Si vous deviez utiliser l' `Receive-Job` applet de commande pour obtenir les résultats du travail maintenant, les résultats seraient incomplets. Vous pouvez utiliser l' `Receive-Job` applet de commande à plusieurs reprises pour obtenir tous les résultats. Utilisez la propriété **State** pour déterminer à quel moment le travail est terminé.

Vous pouvez également utiliser le paramètre **Wait** de l' `Receive-Job` applet de commande. Quand vous utilisez ce paramètre, l’applet de commande ne retourne pas l’invite de commandes tant que le travail n’est pas terminé et que tous les résultats sont disponibles.

Vous pouvez également utiliser l' `Wait-Job` applet de commande pour attendre un ou plusieurs des résultats de la tâche. `Wait-Job` permet d’attendre une ou plusieurs tâches spécifiques ou pour tous les travaux.
La commande suivante utilise l' `Wait-Job` applet de commande pour attendre un travail avec l' **ID**
10.

```powershell
Wait-Job -ID 10
```

Par conséquent, l’invite PowerShell est supprimée jusqu’à ce que la tâche soit terminée.

Vous pouvez également attendre une période prédéterminée. Cette commande utilise le paramètre **timeout** pour limiter l’attente à 120 secondes. Lorsque le délai expire, l’invite de commandes retourne, mais le travail continue à s’exécuter en arrière-plan.

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>Arrêt d’un travail

Pour arrêter une tâche en arrière-plan, utilisez l’applet de commande `Stop-Job` . La commande suivante démarre un travail pour obtenir chaque entrée dans le journal des événements système. Elle enregistre l’objet de traitement dans la `$job` variable.

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

La commande suivante arrête le travail. Elle utilise un opérateur de pipeline ( `|` ) pour envoyer la tâche dans la `$job` variable à `Stop-Job` .

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>Suppression d’un travail

Pour supprimer une tâche en arrière-plan, utilisez l’applet de commande `Remove-Job` . La commande suivante supprime la tâche dans la `$job` variable.

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>Examen d’un travail ayant échoué

Les travaux peuvent échouer pour de nombreuses raisons. l’objet de traitement contient une propriété **reason** qui contient des informations sur la cause de l’échec.

L’exemple suivant démarre un travail sans les informations d’identification requises.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

Inspectez la propriété **reason** pour trouver l’erreur qui a provoqué l’échec du travail.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

Dans ce cas, la tâche a échoué, car l’ordinateur distant nécessitait des informations d’identification explicites pour exécuter la commande. La propriété **reason** contient le message suivant :

> La connexion au serveur distant a échoué avec le message d’erreur suivant : « accès refusé ».

## <a name="see-also"></a>Voir aussi

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
