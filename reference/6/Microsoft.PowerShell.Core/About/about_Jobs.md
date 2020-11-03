---
description: Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6668e8a060c2468a4c7d98f52c7d493e1751970b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208573"
---
# <a name="about-jobs"></a>À propos des travaux

## <a name="short-description"></a>Description courte
Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.

## <a name="long-description"></a>Description longue

PowerShell exécute simultanément des commandes et des scripts par le biais de travaux. Il existe trois solutions basées sur les travaux fournies par PowerShell pour prendre en charge l’accès concurrentiel.

|Travail            |Description                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |La commande et le script s’exécutent sur un ordinateur distant.                 |
|`BackgroundJob`|Commande et script exécutés dans un processus distinct sur l’environnement local    |
|               |ordinateur virtuel.                                                     |
|`ThreadJob`    |La commande et le script s’exécutent dans un thread distinct au sein du même  |
|               |processus sur l’ordinateur local.                                |

Chaque type de tâche présente des avantages et des inconvénients. L’exécution d’un script à distance sur un ordinateur distinct ou dans un processus distinct a une grande isolation. Les erreurs n’affectent pas les travaux en cours d’exécution ou le client qui a démarré le travail. Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet. Tous les objets passés à et à partir de la session distante doivent être sérialisés puis désérialisés lorsqu’ils sont transmis entre le client et la session cible. L’opération de sérialisation peut utiliser de nombreuses ressources de calcul et de mémoire pour les objets de données complexes de grande taille.

Cette rubrique explique comment exécuter des tâches en arrière-plan dans PowerShell sur un ordinateur local. Pour plus d’informations sur l’exécution de tâches en arrière-plan sur des ordinateurs distants, consultez [about_Remote_Jobs](about_Remote_Jobs.md). Pour plus d’informations sur les travaux de thread, consultez [about_Thread_Jobs](about_Thread_Jobs.md).

Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, même si le travail prend une durée prolongée. Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.

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

La `Start-Job` commande retourne un objet qui représente le travail. L'objet de traitement retourné par Get-Job contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.

Enregistrez l’objet de traitement dans une variable, puis utilisez-le avec les autres applets de commande Job pour gérer la tâche en arrière-plan. La commande suivante démarre un objet de traitement et enregistre l’objet de traitement résultant dans la `$job` variable.

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

À compter de PowerShell 6,0, vous pouvez utiliser un amersand ( `&` ) à la fin d’un pipeline pour démarrer un travail en arrière-plan. La commande suivante est fonctionnellement équivalente à la commande ci-dessus.

```powershell
$job = Get-Process &
```

La esperluette ( `&` ) est appelée opérateur d’arrière-plan. Pour plus d’informations, consultez [opérateur d’arrière-plan](about_Operators.md#background-operator-).

Vous pouvez également utiliser l' `Get-Job` applet de commande pour récupérer des objets qui représentent les travaux démarrés dans la session active. `Get-Job` retourne le même objet de traitement que celui `Start-Job` retourné par.

## <a name="getting-job-objects"></a>Obtention d’objets de travail

Pour récupérer l’objet qui représente les tâches en arrière-plan démarrées dans la session active, utilisez l’applet de commande `Get-Job` . Sans paramètres, `Get-Job` retourne toutes les tâches qui ont été démarrées dans la session active.

Par exemple, la commande suivante obtient les tâches de la session active.

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

Vous pouvez également enregistrer l’objet de traitement dans une variable et l’utiliser pour représenter la tâche dans une commande ultérieure. La commande suivante obtient la tâche avec l’ID 1 et l’enregistre dans la `$job` variable.

```powershell
$job = Get-Job -Id 1
```

L’objet de traitement contient l’état du travail, qui indique si le travail est terminé. L’état d’une tâche terminée est **terminé** ou **a échoué** . Un travail peut également être **bloqué** ou **en cours d’exécution** .

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a>Obtention des résultats d’un travail

Lorsque vous exécutez un travail en arrière-plan, les résultats n’apparaissent pas immédiatement. Au lieu de cela, l’applet de commande `Start-Job` retourne un objet de traitement qui représente le travail, mais il ne contient pas les résultats. Pour obtenir les résultats d’une tâche en arrière-plan, utilisez l’applet de commande `Receive-Job` .

La commande suivante utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail. Elle utilise un objet de traitement enregistré dans la `$job` variable pour identifier la tâche.

```powershell
Receive-Job -Job $job
```

L' `Receive-Job` applet de commande retourne les résultats du travail.

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

Vous pouvez également enregistrer les résultats d’un travail dans une variable. La commande suivante enregistre les résultats de la tâche dans la variable dans la variable `$job` `$results` .

```powershell
$results = Receive-Job -Job $job
```

De plus, vous pouvez enregistrer les résultats du travail dans un fichier à l’aide de l’opérateur de redirection ( `>` ) ou de l’applet de commande `Out-File` . La commande suivante utilise l’opérateur de redirection pour enregistrer les résultats de la tâche dans la `$job` variable dans le `Results.txt` fichier.

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a>Obtention et conservation des résultats de travaux partiels

L' `Receive-Job` applet de commande obtient les résultats d’une tâche en arrière-plan. Si la tâche est terminée, `Receive-Job` obtient tous les résultats de la tâche. Si le travail est toujours en cours d’exécution, `Receive-Job` obtient les résultats générés jusqu’à présent. Vous pouvez réexécuter `Receive-Job` les commandes pour obtenir les résultats restants.

Lorsque `Receive-Job` retourne les résultats, par défaut, il supprime les résultats du cache où les résultats du travail sont stockés. Si vous exécutez une autre `Receive-Job` commande, vous recevez uniquement les résultats qui n’ont pas encore été reçus.

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

Pour empêcher `Receive-Job` de supprimer les résultats du travail qu’il a renvoyés, utilisez le paramètre **Keep** . Par conséquent, `Receive-Job` retourne tous les résultats qui ont été générés jusqu’à ce moment-là.

Les commandes suivantes montrent l’effet de l’utilisation du paramètre **Keep** sur un travail qui n’est pas encore terminé.

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

## <a name="waiting-for-the-results"></a>En attente des résultats

Si vous exécutez une commande qui prend beaucoup de temps, vous pouvez utiliser les propriétés de l’objet de traitement pour déterminer à quel moment le travail est terminé. La commande suivante utilise l' `Get-Job` objet pour récupérer toutes les tâches en arrière-plan dans la session active.

```powershell
Get-Job
```

Les résultats s’affichent dans un tableau. L’état de la tâche s’affiche dans la colonne **État** .

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

Dans ce cas, la propriété State indique que le travail 2 est toujours en cours d’exécution. Si vous deviez utiliser l' `Receive-Job` applet de commande pour obtenir les résultats du travail maintenant, les résultats seraient incomplets. Vous pouvez utiliser l' `Receive-Job` applet de commande à plusieurs reprises pour obtenir tous les résultats. Par défaut, chaque fois que vous l’utilisez, vous recevez uniquement les résultats qui n’ont pas encore été reçus, mais vous pouvez utiliser le paramètre **Keep** de l’applet de commande `Receive-Job` pour conserver les résultats, même s’ils ont déjà été reçus.

Vous pouvez écrire les résultats partiels dans un fichier, puis ajouter les résultats les plus récents à mesure qu’ils arrivent, ou vous pouvez attendre et vérifier l’état du travail par la suite.

Vous pouvez utiliser le paramètre **Wait** de l' `Receive-Job` applet de commande, qui ne retourne pas l’invite de commandes jusqu’à ce que le travail soit terminé et que tous les résultats soient disponibles.

Vous pouvez également utiliser l' `Wait-Job` applet de commande pour attendre un ou plusieurs des résultats de la tâche. `Wait-Job` permet d’attendre une tâche particulière, pour tous les travaux, ou pour l’une des tâches à effectuer.

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

Pour déterminer la raison de l’échec d’un travail, utilisez la propriété **reason** de l’objet de traitement.

La commande suivante démarre un travail sans les informations d’identification requises. Elle enregistre l’objet de traitement dans la `$job` variable.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

La commande suivante utilise la propriété Reason pour trouver l’erreur qui a provoqué l’échec du travail.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

Dans ce cas, la tâche a échoué, car l’ordinateur distant nécessitait des informations d’identification explicites pour exécuter la commande. La valeur de la propriété **reason** est la suivante :

La connexion au serveur distant a échoué avec le message d’erreur suivant : « accès refusé ».

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
