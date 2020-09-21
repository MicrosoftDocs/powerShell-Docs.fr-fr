---
title: Affichage de la progression lors d’un multi-threading
description: Comment utiliser Write-Progress pour plusieurs threads avec le paramètre -Parallel de Foreach-Object
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410840"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a><span data-ttu-id="21198-103">Écriture de la progression pour plusieurs threads avec le paramètre -Parallel de Foreach-Object</span><span class="sxs-lookup"><span data-stu-id="21198-103">Writing Progress across multiple threads with Foreach Parallel</span></span>

<span data-ttu-id="21198-104">À compter de PowerShell 7.0, il est possible de travailler simultanément sur plusieurs threads à l’aide du paramètre **Parallel** dans l’applet de commande [ForEach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object).</span><span class="sxs-lookup"><span data-stu-id="21198-104">Starting in PowerShell 7.0, the ability to work in multiple threads simultaneously is possible using the **Parallel** parameter in the [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet.</span></span> <span data-ttu-id="21198-105">Le fait de superviser la progression de plusieurs threads peut se révéler difficile, cela dit.</span><span class="sxs-lookup"><span data-stu-id="21198-105">Monitoring the progress of these threads can be a challenge though.</span></span> <span data-ttu-id="21198-106">Normalement, vous pouvez superviser la progression d’un processus à l’aide de [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span><span class="sxs-lookup"><span data-stu-id="21198-106">Normally, you can monitor the progress of a process using [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span></span>
<span data-ttu-id="21198-107">Toutefois, étant donné que PowerShell utilise une instance d’exécution distincte pour chaque thread lors de l’utilisation de **Parallel**, le fait d’indiquer la progression à l’hôte n’est pas aussi simple que lorsque vous utilisez `Write-Progress`.</span><span class="sxs-lookup"><span data-stu-id="21198-107">However, since PowerShell uses a separate runspace for each thread when using **Parallel**, reporting the progress back to the host isn't as straight forward as normal use of `Write-Progress`.</span></span>

## <a name="using-a-synced-hashtable-to-track-progress"></a><span data-ttu-id="21198-108">Utilisation d’une table de hachage synchronisée pour suivre la progression</span><span class="sxs-lookup"><span data-stu-id="21198-108">Using a synced hashtable to track progress</span></span>

<span data-ttu-id="21198-109">Lors de l’écriture de la progression de plusieurs threads, le suivi devient difficile, car lorsque vous exécutez des processus parallèles dans PowerShell, chaque processus a sa propre instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="21198-109">When writing the progress from multiple threads, tracking becomes difficult because when running parallel processes in PowerShell, each process has it's own runspace.</span></span> <span data-ttu-id="21198-110">Pour contourner ce problème, vous pouvez utiliser une [table de hachage synchronisée](/dotnet/api/system.collections.hashtable.synchronized).</span><span class="sxs-lookup"><span data-stu-id="21198-110">To get around this, you can use a [synchronized hashtable](/dotnet/api/system.collections.hashtable.synchronized).</span></span> <span data-ttu-id="21198-111">Une table de hachage synchronisée est une structure de données thread-safe qui peut être modifiée simultanément par plusieurs threads sans générer d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="21198-111">A synced hashtable is a thread safe data structure that can be modified by multiple threads simultaneously without throwing an error.</span></span>

### <a name="set-up"></a><span data-ttu-id="21198-112">Configurer</span><span class="sxs-lookup"><span data-stu-id="21198-112">Set up</span></span>

<span data-ttu-id="21198-113">L’un des inconvénients de cette approche est qu’elle nécessite une configuration assez complexe pour garantir que tout s’exécutera sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="21198-113">One of the downsides to this approach is it takes a, somewhat, complex set up to ensure everything runs without error.</span></span>

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

<span data-ttu-id="21198-114">Dans cette section, nous allons créer trois structures de données, à trois fins différentes.</span><span class="sxs-lookup"><span data-stu-id="21198-114">This section creates three different data structures, for three different purposes.</span></span>

<span data-ttu-id="21198-115">La variable `$dataSet` stocke un tableau de tables de hachage qui est utilisé pour coordonner les étapes suivantes sans risque de modification.</span><span class="sxs-lookup"><span data-stu-id="21198-115">The `$dataSet` variable stores an array of hashtables that is used to coordinate the next steps without the risk of being modified.</span></span> <span data-ttu-id="21198-116">Si une collection d’objets est modifiée lors de l’itération au sein de la collection, PowerShell génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="21198-116">If an object collection is modified while iterating through the collection, PowerShell throws an error.</span></span> <span data-ttu-id="21198-117">La collection d’objets de la boucle doit être séparée des objets en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="21198-117">You must keep the object collection in the loop separate from the objects being modified.</span></span> <span data-ttu-id="21198-118">La clé `Id` de chaque table de hachage sert d’identificateur pour un processus fictif.</span><span class="sxs-lookup"><span data-stu-id="21198-118">The `Id` key in each hashtable is the identifier for a mock process.</span></span> <span data-ttu-id="21198-119">La clé `Wait` simule la charge de travail de chaque processus fictif faisant l’objet d’un suivi.</span><span class="sxs-lookup"><span data-stu-id="21198-119">The `Wait` key simulates the workload of each mock process being tracked.</span></span>

<span data-ttu-id="21198-120">La variable `$origin` stocke une table de hachage imbriquée où chaque clé correspond à l’un des ID de processus fictifs.</span><span class="sxs-lookup"><span data-stu-id="21198-120">The `$origin` variable stores a nested hashtable with each key being one of the mock process id's.</span></span>
<span data-ttu-id="21198-121">Ensuite, elle est utilisée pour alimenter la table de hachage synchronisée qui est stockée dans la variable `$sync`.</span><span class="sxs-lookup"><span data-stu-id="21198-121">Then, it is used to hydrate the synchronized hashtable stored in the `$sync` variable.</span></span> <span data-ttu-id="21198-122">La variable `$sync` est chargée d’indiquer la progression à l’instance d’exécution parente, qui affiche la progression.</span><span class="sxs-lookup"><span data-stu-id="21198-122">The `$sync` variable is responsible for reporting the progress back to the parent runspace, which displays the progress.</span></span>

### <a name="running-the-processes"></a><span data-ttu-id="21198-123">Exécution des processus</span><span class="sxs-lookup"><span data-stu-id="21198-123">Running the processes</span></span>

<span data-ttu-id="21198-124">Cette section exécute les processus multithread et crée une partie de la sortie qui est utilisée pour afficher la progression.</span><span class="sxs-lookup"><span data-stu-id="21198-124">This section runs the multi-threaded processes and creates some of the output used to display progress.</span></span>

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

<span data-ttu-id="21198-125">Les processus fictifs sont envoyés à `Foreach-Object` et démarrés comme des tâches.</span><span class="sxs-lookup"><span data-stu-id="21198-125">The mock processes are sent to `Foreach-Object` and started as jobs.</span></span> <span data-ttu-id="21198-126">**ThrottleLimit** est défini sur **3** pour mettre en évidence l’exécution de plusieurs processus au sein d’une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="21198-126">The **ThrottleLimit** is set to **3** to highlight running multiple processes in a queue.</span></span> <span data-ttu-id="21198-127">Les tâches sont stockées dans la variable `$job`, ce qui nous permettra de savoir quand tous les processus seront terminés.</span><span class="sxs-lookup"><span data-stu-id="21198-127">The jobs are stored in the `$job` variable and allows us to know when all the processes have finished later on.</span></span>

<span data-ttu-id="21198-128">Lorsque vous utilisez l’instruction `using:` pour référencer une variable d’étendue parente dans PowerShell, vous ne pouvez pas utiliser d’expressions pour la rendre dynamique.</span><span class="sxs-lookup"><span data-stu-id="21198-128">When using the `using:` statement to reference a parent scope variable in PowerShell, you can't use expressions to make it dynamic.</span></span> <span data-ttu-id="21198-129">Par exemple, si vous avez essayé de créer la variable `$process` de cette façon : `$process = $using:sync.$($PSItem.id)`, vous obtiendriez une erreur indiquant que vous ne pouvez pas utiliser d’expressions à cet endroit.</span><span class="sxs-lookup"><span data-stu-id="21198-129">For example, if you tried to create the `$process` variable like this, `$process = $using:sync.$($PSItem.id)`, you would get an error stating you can't use expressions there.</span></span> <span data-ttu-id="21198-130">Nous créons donc la variable `$syncCopy` pour pouvoir référencer et modifier la variable `$sync` sans risque d’échec.</span><span class="sxs-lookup"><span data-stu-id="21198-130">So, we create the `$syncCopy` variable to be able to reference and modify the `$sync` variable without the risk of it failing.</span></span>

<span data-ttu-id="21198-131">Ensuite, nous créons une table de hachage pour représenter la progression du processus inclus actuellement dans la boucle à l’aide de la variable `$process`, en référençant les clés de la table de hachage synchronisée.</span><span class="sxs-lookup"><span data-stu-id="21198-131">Next, we build out a hashtable to represent the progress of the process currently in the loop using the `$process` variable by referencing the synchronized hashtable keys.</span></span> <span data-ttu-id="21198-132">Dans la section suivante, les clés **Activity** et **Status** sont utilisées comme valeurs de paramètre pour `Write-Progress` afin d’afficher l’état d’un processus fictif donné.</span><span class="sxs-lookup"><span data-stu-id="21198-132">The **Activity** and the **Status** keys are used as parameter values for `Write-Progress` to display the status of a given mock process in the next section.</span></span>

<span data-ttu-id="21198-133">La boucle `foreach` permet simplement de simuler le processus en cours et est randomisée selon l’`$dataSet`attribut **Wait** afin de définir `Start-Sleep` en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="21198-133">The `foreach` loop is just a way to simulate the process working and is randomized based on the `$dataSet` **Wait** attribute to set `Start-Sleep` using milliseconds.</span></span> <span data-ttu-id="21198-134">La façon dont vous calculez la progression de votre processus peut varier.</span><span class="sxs-lookup"><span data-stu-id="21198-134">How you calculate the progress of your process may vary.</span></span>

### <a name="displaying-the-progress-of-multiple-processes"></a><span data-ttu-id="21198-135">Affichage de la progression de plusieurs processus</span><span class="sxs-lookup"><span data-stu-id="21198-135">Displaying the progress of multiple processes</span></span>

<span data-ttu-id="21198-136">Maintenant que les processus fictifs s’exécutent comme des tâches, nous pouvons commencer à écrire la progression des processus dans la fenêtre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21198-136">Now that the mock processes are running as jobs, we can start to write the processes progress to the PowerShell window.</span></span>

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

<span data-ttu-id="21198-137">La variable `$job` contient la **tâche** parente, ainsi qu’une tâche **enfant** pour chacun des processus fictifs.</span><span class="sxs-lookup"><span data-stu-id="21198-137">The `$job` variable contains the parent **job** and has a child **job** for each of the mock processes.</span></span> <span data-ttu-id="21198-138">Tant que des tâches enfants sont en cours d’exécution, l’état (**State**) de la tâche parente reste « Running » (En cours d’exécution).</span><span class="sxs-lookup"><span data-stu-id="21198-138">While any of the child jobs are still running, the parent job **State** will remain "Running".</span></span> <span data-ttu-id="21198-139">Cela nous permet d’utiliser la boucle `while` pour mettre à jour continuellement la progression de chaque processus jusqu’à ce qu’ils soient tous terminés.</span><span class="sxs-lookup"><span data-stu-id="21198-139">This allows us to use the `while` loop to continually update the progress of every process until all processes are finished.</span></span>

<span data-ttu-id="21198-140">Dans la boucle while, nous parcourons en boucle chaque clé de la variable `$sync`.</span><span class="sxs-lookup"><span data-stu-id="21198-140">Within the while loop, we loop through each of the keys in the `$sync` variable.</span></span> <span data-ttu-id="21198-141">Étant donné qu’il s’agit d’une table de hachage synchronisée, celle-ci est constamment mise à jour, mais reste accessible sans générer d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="21198-141">Since this is a synchronized hashtable, it is constantly updated but can still be accessed without throwing any errors.</span></span>

<span data-ttu-id="21198-142">À l’aide de la méthode `IsNullOrEmpty()`, une vérification est effectuée pour s’assurer que le processus signalé est bien en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="21198-142">There is a check to ensure that the process being reported is actually running using the `IsNullOrEmpty()` method.</span></span> <span data-ttu-id="21198-143">Si le processus n’a pas démarré, la boucle ne le signalera pas et passera au processus suivant jusqu’à atteindre un processus qui a démarré.</span><span class="sxs-lookup"><span data-stu-id="21198-143">If the process hasn't been started, the loop won't report on it and move on to the next until it gets to a process that has been started.</span></span> <span data-ttu-id="21198-144">Si le processus a démarré, la table de hachage de la clé actuelle est utilisée pour projeter (splat) les paramètres vers `Write-Progress`.</span><span class="sxs-lookup"><span data-stu-id="21198-144">If the process is started, the hashtable from the current key is used to splat the parameters to `Write-Progress`.</span></span>

### <a name="full-example"></a><span data-ttu-id="21198-145">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="21198-145">Full example</span></span>

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

## <a name="related-links"></a><span data-ttu-id="21198-146">Liens associés</span><span class="sxs-lookup"><span data-stu-id="21198-146">Related Links</span></span>

- [<span data-ttu-id="21198-147">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="21198-147">about_Jobs</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [<span data-ttu-id="21198-148">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="21198-148">about_Scopes</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [<span data-ttu-id="21198-149">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="21198-149">about_Splatting</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
