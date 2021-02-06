---
description: Fournit des informations sur les travaux basés sur des threads PowerShell. Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 88880a6c58ddc02d7b35a44af7169f6c5af19a10
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603486"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="ac28c-104">À propos des travaux de thread</span><span class="sxs-lookup"><span data-stu-id="ac28c-104">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="ac28c-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="ac28c-105">Short description</span></span>

<span data-ttu-id="ac28c-106">Fournit des informations sur les travaux basés sur des threads PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac28c-106">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="ac28c-107">Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.</span><span class="sxs-lookup"><span data-stu-id="ac28c-107">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="ac28c-108">Description longue</span><span class="sxs-lookup"><span data-stu-id="ac28c-108">Long description</span></span>

<span data-ttu-id="ac28c-109">PowerShell exécute simultanément des commandes et des scripts par le biais de travaux.</span><span class="sxs-lookup"><span data-stu-id="ac28c-109">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="ac28c-110">Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="ac28c-110">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="ac28c-111">`RemoteJob` -Les commandes et les scripts s’exécutent dans une session à distance.</span><span class="sxs-lookup"><span data-stu-id="ac28c-111">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="ac28c-112">Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="ac28c-112">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="ac28c-113">`BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ac28c-113">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="ac28c-114">Pour plus d’informations, consultez [à propos des_tâches](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="ac28c-114">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="ac28c-115">`PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ac28c-115">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="ac28c-116">Les travaux basés sur les threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents.</span><span class="sxs-lookup"><span data-stu-id="ac28c-116">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="ac28c-117">Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus sont terminés.</span><span class="sxs-lookup"><span data-stu-id="ac28c-117">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="ac28c-118">Toutefois, les travaux basés sur les threads nécessitent moins de traitement.</span><span class="sxs-lookup"><span data-stu-id="ac28c-118">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="ac28c-119">Ils n’utilisent pas la couche de communication à distance ou la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="ac28c-119">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="ac28c-120">Les objets de résultats sont retournés en tant que références aux objets actifs dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ac28c-120">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="ac28c-121">Sans cette surcharge, les travaux basés sur les threads s’exécutent plus rapidement et utilisent moins de ressources que les autres types de travaux.</span><span class="sxs-lookup"><span data-stu-id="ac28c-121">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac28c-122">La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ac28c-122">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="ac28c-123">Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé.</span><span class="sxs-lookup"><span data-stu-id="ac28c-123">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="ac28c-124">Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.</span><span class="sxs-lookup"><span data-stu-id="ac28c-124">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="ac28c-125">Il existe deux façons de contourner cette situation :</span><span class="sxs-lookup"><span data-stu-id="ac28c-125">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="ac28c-126">Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="ac28c-126">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="ac28c-127">Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="ac28c-127">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="ac28c-128">Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail.</span><span class="sxs-lookup"><span data-stu-id="ac28c-128">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="ac28c-129">Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="ac28c-129">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="ac28c-130">Comment démarrer et gérer des travaux basés sur des threads</span><span class="sxs-lookup"><span data-stu-id="ac28c-130">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="ac28c-131">Il existe deux façons de démarrer des travaux basés sur des threads :</span><span class="sxs-lookup"><span data-stu-id="ac28c-131">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="ac28c-132">`Start-ThreadJob`-à partir du module **ThreadJob**</span><span class="sxs-lookup"><span data-stu-id="ac28c-132">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="ac28c-133">`ForEach-Object -Parallel -AsJob` -la fonctionnalité parallèle a été ajoutée dans PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="ac28c-133">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="ac28c-134">Utilisez les mêmes applets de commande de **tâche** que celles décrites dans [about_Jobs](about_Jobs.md) pour gérer les travaux basés sur des threads.</span><span class="sxs-lookup"><span data-stu-id="ac28c-134">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="ac28c-135">Utilisation de `Start-ThreadJob`</span><span class="sxs-lookup"><span data-stu-id="ac28c-135">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="ac28c-136">Le module **ThreadJob** a d’abord été livré avec PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="ac28c-136">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="ac28c-137">Il peut également être installé à partir du PowerShell Gallery pour Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="ac28c-137">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="ac28c-138">Pour démarrer un travail de thread sur l’ordinateur local, utilisez l' `Start-ThreadJob` applet de commande avec une commande ou un script placé entre accolades ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="ac28c-138">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="ac28c-139">L’exemple suivant démarre une tâche de thread qui exécute une `Get-Process` commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ac28c-139">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="ac28c-140">La `Start-ThreadJob` commande retourne un `ThreadJob` objet qui représente le travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac28c-140">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="ac28c-141">L’objet de traitement contient des informations utiles sur la tâche, y compris son état d’exécution actuel.</span><span class="sxs-lookup"><span data-stu-id="ac28c-141">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="ac28c-142">Il collecte les résultats du travail lors de la génération des résultats.</span><span class="sxs-lookup"><span data-stu-id="ac28c-142">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="ac28c-143">Utilisation de `ForEach-Object -Parallel -AsJob`</span><span class="sxs-lookup"><span data-stu-id="ac28c-143">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="ac28c-144">PowerShell 7,0 a ajouté un nouvel ensemble de paramètres à l’applet de commande `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ac28c-144">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="ac28c-145">Les nouveaux paramètres vous permettent d’exécuter des blocs de script dans des threads parallèles en tant que travaux PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac28c-145">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="ac28c-146">Vous pouvez diriger les données vers `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="ac28c-146">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="ac28c-147">Les données sont passées au bloc de script qui est exécuté en parallèle.</span><span class="sxs-lookup"><span data-stu-id="ac28c-147">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="ac28c-148">Le `-AsJob` paramètre crée des objets de travaux pour chacun des threads parallèles.</span><span class="sxs-lookup"><span data-stu-id="ac28c-148">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="ac28c-149">La commande suivante démarre un travail qui contient des tâches enfants pour chaque valeur d’entrée dirigée vers la commande.</span><span class="sxs-lookup"><span data-stu-id="ac28c-149">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="ac28c-150">Chaque travail enfant exécute la `Write-Output` commande avec une valeur d’entrée dirigée comme argument.</span><span class="sxs-lookup"><span data-stu-id="ac28c-150">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="ac28c-151">La `ForEach-Object -Parallel` commande retourne un `PSTaskJob` objet qui contient des tâches enfants pour chaque valeur d’entrée dirigée.</span><span class="sxs-lookup"><span data-stu-id="ac28c-151">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="ac28c-152">L’objet de traitement contient des informations utiles sur l’état d’exécution des tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="ac28c-152">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="ac28c-153">Il collecte les résultats des tâches enfants à mesure que les résultats sont générés.</span><span class="sxs-lookup"><span data-stu-id="ac28c-153">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="ac28c-154">Comment attendre qu’une tâche se termine et récupérer les résultats d’une tâche</span><span class="sxs-lookup"><span data-stu-id="ac28c-154">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="ac28c-155">Vous pouvez utiliser les applets de commande PowerShell Job, telles que `Wait-Job` et, `Receive-Job` pour attendre la fin d’un travail, puis retourner tous les résultats générés par le travail.</span><span class="sxs-lookup"><span data-stu-id="ac28c-155">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="ac28c-156">La commande suivante démarre un travail de thread qui exécute une `Get-Process` commande, puis attend la fin de la commande et retourne tous les résultats de données générés par la commande.</span><span class="sxs-lookup"><span data-stu-id="ac28c-156">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="ac28c-157">La commande suivante démarre un travail qui exécute une `Write-Output` commande pour chaque entrée dirigée, puis attend que toutes les tâches enfants soient terminées, et enfin retourne tous les résultats de données générés par les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="ac28c-157">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="ac28c-158">L' `Receive-Job` applet de commande retourne les résultats des tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="ac28c-158">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="ac28c-159">Étant donné que chaque travail enfant s’exécute en parallèle, l’ordre des résultats générés n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="ac28c-159">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="ac28c-160">Performances des travaux de thread</span><span class="sxs-lookup"><span data-stu-id="ac28c-160">Thread job performance</span></span>

<span data-ttu-id="ac28c-161">Les tâches de thread sont plus rapides et plus légères que d’autres types de travaux.</span><span class="sxs-lookup"><span data-stu-id="ac28c-161">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="ac28c-162">Toutefois, elles ont toujours une surcharge qui peut être importante par rapport au travail que fait le travail.</span><span class="sxs-lookup"><span data-stu-id="ac28c-162">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="ac28c-163">PowerShell exécute des commandes et des scripts dans une session.</span><span class="sxs-lookup"><span data-stu-id="ac28c-163">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="ac28c-164">Une seule commande ou un seul script peut s’exécuter à la fois dans une session.</span><span class="sxs-lookup"><span data-stu-id="ac28c-164">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="ac28c-165">Ainsi, lors de l’exécution de plusieurs tâches, chaque travail s’exécute dans une session distincte.</span><span class="sxs-lookup"><span data-stu-id="ac28c-165">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="ac28c-166">Chaque session contribue à la surcharge.</span><span class="sxs-lookup"><span data-stu-id="ac28c-166">Each session contributes to the overhead.</span></span>

<span data-ttu-id="ac28c-167">Les travaux de thread offrent les meilleures performances lorsque le travail qu’ils effectuent est supérieur à la surcharge de la session utilisée pour exécuter le travail.</span><span class="sxs-lookup"><span data-stu-id="ac28c-167">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="ac28c-168">Il existe deux cas pour qui répondent à ces critères.</span><span class="sxs-lookup"><span data-stu-id="ac28c-168">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="ac28c-169">Calcul intensif-l’exécution d’un script sur plusieurs travaux de thread peut tirer parti de plusieurs cœurs de processeur et se terminer plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="ac28c-169">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="ac28c-170">Le travail se compose d’un script d’attente significatif, qui consacre du temps à attendre les e/s ou les résultats d’appel distant.</span><span class="sxs-lookup"><span data-stu-id="ac28c-170">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="ac28c-171">L’exécution en parallèle se termine généralement plus rapidement que si elle est exécutée de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="ac28c-171">Running in parallel usually completes quicker than if run sequentially.</span></span>

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

<span data-ttu-id="ac28c-172">Le premier exemple ci-dessus illustre une boucle foreach qui crée des travaux de thread 1000 pour effectuer une écriture de chaîne simple.</span><span class="sxs-lookup"><span data-stu-id="ac28c-172">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="ac28c-173">En raison de la surcharge du travail, l’exécution prend plus de 36 secondes.</span><span class="sxs-lookup"><span data-stu-id="ac28c-173">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="ac28c-174">Le deuxième exemple exécute l' `ForEach` applet de commande pour effectuer les mêmes opérations 1000.</span><span class="sxs-lookup"><span data-stu-id="ac28c-174">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="ac28c-175">Cette fois, `ForEach-Object` s’exécute de manière séquentielle, sur un seul thread, sans surcharge de travail.</span><span class="sxs-lookup"><span data-stu-id="ac28c-175">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="ac28c-176">Il se termine en une seule sept millisecondes.</span><span class="sxs-lookup"><span data-stu-id="ac28c-176">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="ac28c-177">Dans l’exemple suivant, jusqu’à 5000 entrées sont collectées pour 10 journaux système distincts.</span><span class="sxs-lookup"><span data-stu-id="ac28c-177">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="ac28c-178">Étant donné que le script implique la lecture d’un certain nombre de journaux, il est logique d’effectuer les opérations en parallèle.</span><span class="sxs-lookup"><span data-stu-id="ac28c-178">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

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

<span data-ttu-id="ac28c-179">Le script se termine dans la moitié de l’heure à laquelle les travaux sont exécutés en parallèle.</span><span class="sxs-lookup"><span data-stu-id="ac28c-179">The script completes in half the time when the jobs are run in parallel.</span></span>

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

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="ac28c-180">Travaux de thread et variables</span><span class="sxs-lookup"><span data-stu-id="ac28c-180">Thread jobs and variables</span></span>

<span data-ttu-id="ac28c-181">Il existe plusieurs façons de passer des valeurs dans les travaux basés sur des threads.</span><span class="sxs-lookup"><span data-stu-id="ac28c-181">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="ac28c-182">`Start-ThreadJob` peut accepter des variables qui sont dirigées vers l’applet de commande, transmises au bloc de script via le `$using` mot clé ou transmises via le paramètre **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="ac28c-182">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="ac28c-183">`ForEach-Object -Parallel` accepte les variables redirigées et les variables transmises directement au bloc de script via le `$using` mot clé.</span><span class="sxs-lookup"><span data-stu-id="ac28c-183">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="ac28c-184">Étant donné que les travaux de thread s’exécutent dans le même processus, tout type de référence de variable passé dans le travail doit être traité avec précaution.</span><span class="sxs-lookup"><span data-stu-id="ac28c-184">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="ac28c-185">S’il ne s’agit pas d’un objet thread-safe, il ne doit jamais être assigné à, et la méthode et les propriétés ne doivent jamais être appelées dessus.</span><span class="sxs-lookup"><span data-stu-id="ac28c-185">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="ac28c-186">L’exemple suivant passe un objet .NET thread-safe `ConcurrentDictionary` à toutes les tâches enfants pour collecter des objets de processus portant un nom unique.</span><span class="sxs-lookup"><span data-stu-id="ac28c-186">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="ac28c-187">Étant donné qu’il s’agit d’un objet thread-safe, il peut être utilisé en toute sécurité pendant que les travaux s’exécutent simultanément dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ac28c-187">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ac28c-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac28c-188">See also</span></span>

- [<span data-ttu-id="ac28c-189">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="ac28c-189">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="ac28c-190">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="ac28c-190">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="ac28c-191">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="ac28c-191">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="ac28c-192">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ac28c-192">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="ac28c-193">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ac28c-193">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="ac28c-194">Start-Job</span><span class="sxs-lookup"><span data-stu-id="ac28c-194">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="ac28c-195">Get-Job</span><span class="sxs-lookup"><span data-stu-id="ac28c-195">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="ac28c-196">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="ac28c-196">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="ac28c-197">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="ac28c-197">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="ac28c-198">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="ac28c-198">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="ac28c-199">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="ac28c-199">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
