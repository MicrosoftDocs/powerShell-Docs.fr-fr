---
description: Fournit des informations sur les travaux basés sur des threads PowerShell. Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 4951ac2c14c0685fbf2ead16bc52c64096231260
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208585"
---
# <a name="about-thread-jobs"></a>À propos des travaux de thread

## <a name="short-description"></a>Description courte

Fournit des informations sur les travaux basés sur des threads PowerShell. Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.

## <a name="long-description"></a>Description longue

Cet article explique comment exécuter des travaux de thread dans PowerShell sur un ordinateur local.
Pour plus d’informations sur l’exécution de tâches en arrière-plan sur un ordinateur local, consultez [about_Jobs](about_Jobs.md).

Démarrez un travail de thread à l’aide de l’applet de commande `Start-ThreadJob` . Cette applet de commande est disponible dans le module **ThreadJob** fourni avec PowerShell.
`Start-ThreadJob` retourne un objet de traitement unique qui encapsule la commande ou le script en cours d’exécution, et qui peut être utilisé avec toutes les applets de commande de manipulation de travaux PowerShell.

## <a name="the-job-cmdlets"></a>Applets de commande Job

|Applet de commande           |Description                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|Démarre un travail de thread sur un ordinateur local.               |
|`Get-Job`        |Obtient les tâches qui ont été démarrées dans la session active.|
|`Receive-Job`    |Obtient les résultats des travaux.                              |
|`Stop-Job`       |Arrête un travail en cours d’exécution.                                   |
|`Wait-Job`       |Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches soient|
|                 |Remplissez.                                              |
|`Remove-Job`     |Supprime un travail.                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a>Comment démarrer un travail de thread sur l’ordinateur local

Pour démarrer un travail de thread sur l’ordinateur local, utilisez l’applet de commande `Start-ThreadJob` .

Pour écrire une `Start-ThreadJob` commande, mettez la commande ou le script en cours d’exécution entre accolades ( `{ }` ).

La commande suivante démarre un travail de thread qui exécute une `Get-Process` commande sur l’ordinateur local.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

La `Start-ThreadJob` commande retourne un `ThreadJob` objet qui représente le travail en cours d’exécution. L’objet de traitement contient des informations utiles sur la tâche, y compris son état d’exécution actuel. Il collecte les résultats du travail lors de la génération des résultats.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>Comment attendre qu’une tâche se termine et récupérer les résultats d’une tâche

Vous pouvez utiliser les applets de commande PowerShell Job, telles que `Wait-Job` et, `Receive-Job` pour attendre la fin d’un travail, puis retourner tous les résultats générés par le travail.

La commande suivante démarre un travail de thread qui exécute une `Get-Process` commande, puis attend la fin de la commande et retourne tous les résultats de données générés par la commande.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

## <a name="powershell-concurrency-and-jobs"></a>Accès concurrentiel et travaux PowerShell

PowerShell exécute simultanément des commandes et des scripts par le biais de travaux. Il existe trois solutions basées sur les travaux fournies par PowerShell pour prendre en charge l’accès concurrentiel.

|Travail            |Description                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |La commande et le script s’exécutent sur un ordinateur distant.                 |
|`BackgroundJob`|Commande et script exécutés dans un processus distinct sur l’environnement local    |
|               |ordinateur virtuel.                                                     |
|`ThreadJob`    |La commande et le script s’exécutent dans un thread distinct au sein du même  |
|               |processus sur l’ordinateur local.                                |

Chaque type de tâche présente des avantages et des inconvénients. L’exécution d’un script à distance sur un ordinateur distinct ou dans un processus distinct a une grande isolation. Les erreurs n’affectent pas les travaux en cours d’exécution ou le client qui a démarré le travail. Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet. Tous les objets passés à et à partir de la session distante doivent être sérialisés puis désérialisés lorsqu’ils sont transmis entre le client et la session cible. L’opération de sérialisation peut utiliser de nombreuses ressources de calcul et de mémoire pour les objets de données complexes de grande taille.

## <a name="powershell-thread-based-jobs"></a>Travaux basés sur des threads PowerShell

Les travaux basés sur des threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents. Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus échouent également.

Toutefois, les travaux basés sur les threads ont une charge de travail bien moindre. Ils n’ont pas besoin d’utiliser la couche de communication à distance ou la sérialisation. Le résultat est que les travaux basés sur les threads ont tendance à s’exécuter beaucoup plus rapidement et à utiliser beaucoup moins de ressources que les autres types de tâches.

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
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

Le premier exemple ci-dessus illustre une boucle foreach qui crée des travaux de thread 1000 pour effectuer une écriture de chaîne simple. En raison de la surcharge du travail, l’exécution prend plus de 33 secondes.

Le deuxième exemple exécute l' `ForEach` applet de commande pour effectuer les mêmes opérations 1000 et chaque écriture de chaîne est exécutée séquentiellement sans surcharge de travail. Il se termine en une seule 25 millisecondes.

```powershell
$logNames.count
10

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

Dans l’exemple ci-dessus, jusqu’à 5000 entrées sont collectées pour 10 journaux système distincts. Étant donné que le script implique la lecture d’un certain nombre de journaux, il est logique d’effectuer les opérations en parallèle. Et le travail se termine plus de deux fois plus rapidement que lorsque le script est exécuté de façon séquentielle.

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>Travaux de thread et variables

Les variables sont passées dans des tâches de thread de différentes façons.

`Start-ThreadJob` peut accepter des variables qui sont dirigées vers l’applet de commande, transmises au bloc de script via le `$using` mot clé ou transmises via le paramètre **argumentlist** .

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

Étant donné que les travaux de thread s’exécutent dans le même processus, tout type de référence de variable passé dans le travail doit être traité avec précaution. S’il ne s’agit pas d’un objet thread-safe, il ne doit jamais être assigné à, et la méthode et les propriétés ne doivent jamais être appelées dessus.

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

L’exemple ci-dessus passe un objet dotNet thread-safe `ConcurrentDictionary` à toutes les tâches enfants pour collecter des objets de processus portant un nom unique. Étant donné qu’il s’agit d’un objet thread-safe, il peut être utilisé en toute sécurité pendant que les travaux s’exécutent simultanément dans le processus.

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
