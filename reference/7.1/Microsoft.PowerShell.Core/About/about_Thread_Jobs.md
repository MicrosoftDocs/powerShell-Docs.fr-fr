---
description: Fournit des informations sur les travaux basés sur des threads PowerShell. Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: ba6251a195d3efdebd427b3f705386336b069211
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524839"
---
# <a name="about-thread-jobs"></a>À propos des travaux de thread

## <a name="short-description"></a>Description courte

Fournit des informations sur les travaux basés sur des threads PowerShell. Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.

## <a name="long-description"></a>Description longue

PowerShell exécute simultanément des commandes et des scripts par le biais de travaux. Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.

- `RemoteJob` -Les commandes et les scripts s’exécutent dans une session à distance. Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).
- `BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local. Pour plus d’informations, consultez [à propos des_tâches](about_Jobs.md).
- `PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local.

Les travaux basés sur les threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents. Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus sont terminés.

Toutefois, les travaux basés sur les threads nécessitent moins de traitement. Ils n’utilisent pas la couche de communication à distance ou la sérialisation. Les objets de résultats sont retournés en tant que références aux objets actifs dans la session active. Sans cette surcharge, les travaux basés sur les threads s’exécutent plus rapidement et utilisent moins de ressources que les autres types de travaux.

> [!IMPORTANT]
> La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline. Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé. Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.

Il existe deux façons de contourner cette situation :

1. Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées. Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).
1. Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail. Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).

## <a name="how-to-start-and-manage-thread-based-jobs"></a>Comment démarrer et gérer des travaux basés sur des threads

Il existe deux façons de démarrer des travaux basés sur des threads :

- `Start-ThreadJob`-à partir du module **ThreadJob**
- `ForEach-Object -Parallel -AsJob` -la fonctionnalité parallèle a été ajoutée dans PowerShell 7,0

Utilisez les mêmes applets de commande de **tâche** que celles décrites dans [about_Jobs](about_Jobs.md) pour gérer les travaux basés sur des threads.

### <a name="using-start-threadjob"></a>Utilisation de `Start-ThreadJob`

Le module **ThreadJob** a d’abord été livré avec PowerShell 6. Il peut également être installé à partir du PowerShell Gallery pour Windows PowerShell 5,1.

Pour démarrer un travail de thread sur l’ordinateur local, utilisez l' `Start-ThreadJob` applet de commande avec une commande ou un script placé entre accolades ( `{ }` ).

L’exemple suivant démarre une tâche de thread qui exécute une `Get-Process` commande sur l’ordinateur local.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

La `Start-ThreadJob` commande retourne un `ThreadJob` objet qui représente le travail en cours d’exécution. L’objet de traitement contient des informations utiles sur la tâche, y compris son état d’exécution actuel. Il collecte les résultats du travail lors de la génération des résultats.

### <a name="using-foreach-object--parallel--asjob"></a>Utilisation de `ForEach-Object -Parallel -AsJob`

PowerShell 7,0 a ajouté un nouvel ensemble de paramètres à l’applet de commande `ForEach-Object` . Les nouveaux paramètres vous permettent d’exécuter des blocs de script dans des threads parallèles en tant que travaux PowerShell.

Vous pouvez diriger les données vers `ForEach-Object -Parallel` . Les données sont passées au bloc de script qui est exécuté en parallèle. Le `-AsJob` paramètre crée des objets de travaux pour chacun des threads parallèles.

La commande suivante démarre un travail qui contient des tâches enfants pour chaque valeur d’entrée dirigée vers la commande. Chaque travail enfant exécute la `Write-Output` commande avec une valeur d’entrée dirigée comme argument.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

La `ForEach-Object -Parallel` commande retourne un `PSTaskJob` objet qui contient des tâches enfants pour chaque valeur d’entrée dirigée. L’objet de traitement contient des informations utiles sur l’état d’exécution des tâches enfants. Il collecte les résultats des tâches enfants à mesure que les résultats sont générés.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>Comment attendre qu’une tâche se termine et récupérer les résultats d’une tâche

Vous pouvez utiliser les applets de commande PowerShell Job, telles que `Wait-Job` et, `Receive-Job` pour attendre la fin d’un travail, puis retourner tous les résultats générés par le travail.

La commande suivante démarre un travail de thread qui exécute une `Get-Process` commande, puis attend la fin de la commande et retourne tous les résultats de données générés par la commande.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

La commande suivante démarre un travail qui exécute une `Write-Output` commande pour chaque entrée dirigée, puis attend que toutes les tâches enfants soient terminées, et enfin retourne tous les résultats de données générés par les tâches enfants.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

L' `Receive-Job` applet de commande retourne les résultats des tâches enfants.

```powershell
1
3
2
4
5
```

Étant donné que chaque travail enfant s’exécute en parallèle, l’ordre des résultats générés n’est pas garanti.

## <a name="thread-job-performance"></a>Performances des travaux de thread

Les tâches de thread sont plus rapides et plus légères que d’autres types de travaux. Toutefois, elles ont toujours une surcharge qui peut être importante par rapport au travail que fait le travail.

PowerShell exécute des commandes et des scripts dans une session. Une seule commande ou un seul script peut s’exécuter à la fois dans une session. Ainsi, lors de l’exécution de plusieurs tâches, chaque travail s’exécute dans une session distincte. Chaque session contribue à la surcharge.

Les travaux de thread offrent les meilleures performances lorsque le travail qu’ils effectuent est supérieur à la surcharge de la session utilisée pour exécuter le travail. Il existe deux cas pour qui répondent à ces critères.

- Calcul intensif-l’exécution d’un script sur plusieurs travaux de thread peut tirer parti de plusieurs cœurs de processeur et se terminer plus rapidement.

- Le travail se compose d’un script d’attente significatif, qui consacre du temps à attendre les e/s ou les résultats d’appel distant. L’exécution en parallèle se termine généralement plus rapidement que si elle est exécutée de manière séquentielle.

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

Le premier exemple ci-dessus illustre une boucle foreach qui crée des travaux de thread 1000 pour effectuer une écriture de chaîne simple. En raison de la surcharge du travail, l’exécution prend plus de 36 secondes.

Le deuxième exemple exécute l' `ForEach` applet de commande pour effectuer les mêmes opérations 1000.
Cette fois, `ForEach-Object` s’exécute de manière séquentielle, sur un seul thread, sans surcharge de travail. Il se termine en une seule sept millisecondes.

Dans l’exemple suivant, jusqu’à 5000 entrées sont collectées pour 10 journaux système distincts. Étant donné que le script implique la lecture d’un certain nombre de journaux, il est logique d’effectuer les opérations en parallèle.

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

Le script se termine dans la moitié de l’heure à laquelle les travaux sont exécutés en parallèle.

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>Travaux de thread et variables

Il existe plusieurs façons de passer des valeurs dans les travaux basés sur des threads.

`Start-ThreadJob` peut accepter des variables qui sont dirigées vers l’applet de commande, transmises au bloc de script via le `$using` mot clé ou transmises via le paramètre **argumentlist** .

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

`ForEach-Object -Parallel` accepte les variables redirigées et les variables transmises directement au bloc de script via le `$using` mot clé.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

Étant donné que les travaux de thread s’exécutent dans le même processus, tout type de référence de variable passé dans le travail doit être traité avec précaution. S’il ne s’agit pas d’un objet thread-safe, il ne doit jamais être assigné à, et la méthode et les propriétés ne doivent jamais être appelées dessus.

L’exemple suivant passe un objet .NET thread-safe `ConcurrentDictionary` à toutes les tâches enfants pour collecter des objets de processus portant un nom unique. Étant donné qu’il s’agit d’un objet thread-safe, il peut être utilisé en toute sécurité pendant que les travaux s’exécutent simultanément dans le processus.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

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
