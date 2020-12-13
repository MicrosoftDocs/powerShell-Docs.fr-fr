---
title: Affichage de la progression lors d’un multi-threading
description: Comment utiliser Write-Progress pour plusieurs threads avec le paramètre -Parallel de Foreach-Object
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "89410840"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a>Écriture de la progression pour plusieurs threads avec le paramètre -Parallel de Foreach-Object

À compter de PowerShell 7.0, il est possible de travailler simultanément sur plusieurs threads à l’aide du paramètre **Parallel** dans l’applet de commande [ForEach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object). Le fait de superviser la progression de plusieurs threads peut se révéler difficile, cela dit. Normalement, vous pouvez superviser la progression d’un processus à l’aide de [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).
Toutefois, étant donné que PowerShell utilise une instance d’exécution distincte pour chaque thread lors de l’utilisation de **Parallel**, le fait d’indiquer la progression à l’hôte n’est pas aussi simple que lorsque vous utilisez `Write-Progress`.

## <a name="using-a-synced-hashtable-to-track-progress"></a>Utilisation d’une table de hachage synchronisée pour suivre la progression

Lors de l’écriture de la progression de plusieurs threads, le suivi devient difficile, car lorsque vous exécutez des processus parallèles dans PowerShell, chaque processus a sa propre instance d’exécution. Pour contourner ce problème, vous pouvez utiliser une [table de hachage synchronisée](/dotnet/api/system.collections.hashtable.synchronized). Une table de hachage synchronisée est une structure de données thread-safe qui peut être modifiée simultanément par plusieurs threads sans générer d’erreurs.

### <a name="set-up"></a>Configurer

L’un des inconvénients de cette approche est qu’elle nécessite une configuration assez complexe pour garantir que tout s’exécutera sans erreurs.

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

Dans cette section, nous allons créer trois structures de données, à trois fins différentes.

La variable `$dataSet` stocke un tableau de tables de hachage qui est utilisé pour coordonner les étapes suivantes sans risque de modification. Si une collection d’objets est modifiée lors de l’itération au sein de la collection, PowerShell génère une erreur. La collection d’objets de la boucle doit être séparée des objets en cours de modification. La clé `Id` de chaque table de hachage sert d’identificateur pour un processus fictif. La clé `Wait` simule la charge de travail de chaque processus fictif faisant l’objet d’un suivi.

La variable `$origin` stocke une table de hachage imbriquée où chaque clé correspond à l’un des ID de processus fictifs.
Ensuite, elle est utilisée pour alimenter la table de hachage synchronisée qui est stockée dans la variable `$sync`. La variable `$sync` est chargée d’indiquer la progression à l’instance d’exécution parente, qui affiche la progression.

### <a name="running-the-processes"></a>Exécution des processus

Cette section exécute les processus multithread et crée une partie de la sortie qui est utilisée pour afficher la progression.

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

Les processus fictifs sont envoyés à `Foreach-Object` et démarrés comme des tâches. **ThrottleLimit** est défini sur **3** pour mettre en évidence l’exécution de plusieurs processus au sein d’une file d’attente. Les tâches sont stockées dans la variable `$job`, ce qui nous permettra de savoir quand tous les processus seront terminés.

Lorsque vous utilisez l’instruction `using:` pour référencer une variable d’étendue parente dans PowerShell, vous ne pouvez pas utiliser d’expressions pour la rendre dynamique. Par exemple, si vous avez essayé de créer la variable `$process` de cette façon : `$process = $using:sync.$($PSItem.id)`, vous obtiendriez une erreur indiquant que vous ne pouvez pas utiliser d’expressions à cet endroit. Nous créons donc la variable `$syncCopy` pour pouvoir référencer et modifier la variable `$sync` sans risque d’échec.

Ensuite, nous créons une table de hachage pour représenter la progression du processus inclus actuellement dans la boucle à l’aide de la variable `$process`, en référençant les clés de la table de hachage synchronisée. Dans la section suivante, les clés **Activity** et **Status** sont utilisées comme valeurs de paramètre pour `Write-Progress` afin d’afficher l’état d’un processus fictif donné.

La boucle `foreach` permet simplement de simuler le processus en cours et est randomisée selon l’`$dataSet`attribut **Wait** afin de définir `Start-Sleep` en millisecondes. La façon dont vous calculez la progression de votre processus peut varier.

### <a name="displaying-the-progress-of-multiple-processes"></a>Affichage de la progression de plusieurs processus

Maintenant que les processus fictifs s’exécutent comme des tâches, nous pouvons commencer à écrire la progression des processus dans la fenêtre PowerShell.

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

La variable `$job` contient la **tâche** parente, ainsi qu’une tâche **enfant** pour chacun des processus fictifs. Tant que des tâches enfants sont en cours d’exécution, l’état (**State**) de la tâche parente reste « Running » (En cours d’exécution). Cela nous permet d’utiliser la boucle `while` pour mettre à jour continuellement la progression de chaque processus jusqu’à ce qu’ils soient tous terminés.

Dans la boucle while, nous parcourons en boucle chaque clé de la variable `$sync`. Étant donné qu’il s’agit d’une table de hachage synchronisée, celle-ci est constamment mise à jour, mais reste accessible sans générer d’erreurs.

À l’aide de la méthode `IsNullOrEmpty()`, une vérification est effectuée pour s’assurer que le processus signalé est bien en cours d’exécution. Si le processus n’a pas démarré, la boucle ne le signalera pas et passera au processus suivant jusqu’à atteindre un processus qui a démarré. Si le processus a démarré, la table de hachage de la clé actuelle est utilisée pour projeter (splat) les paramètres vers `Write-Progress`.

### <a name="full-example"></a>Exemple complet

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a>Liens associés

- [about_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [about_Scopes](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [about_Splatting](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
