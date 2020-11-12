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
# <a name="about-jobs"></a><span data-ttu-id="5826a-104">À propos des travaux</span><span class="sxs-lookup"><span data-stu-id="5826a-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="5826a-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="5826a-105">Short description</span></span>
<span data-ttu-id="5826a-106">Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="5826a-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="5826a-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="5826a-107">Long description</span></span>

<span data-ttu-id="5826a-108">PowerShell exécute simultanément des commandes et des scripts par le biais de travaux.</span><span class="sxs-lookup"><span data-stu-id="5826a-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="5826a-109">Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="5826a-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="5826a-110">`RemoteJob` -Les commandes et les scripts s’exécutent sur une session à distance.</span><span class="sxs-lookup"><span data-stu-id="5826a-110">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="5826a-111">Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="5826a-111">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="5826a-112">`BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5826a-112">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="5826a-113">`PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5826a-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="5826a-114">Pour plus d’informations, consultez [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span><span class="sxs-lookup"><span data-stu-id="5826a-114">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="5826a-115">L’exécution de scripts à distance, sur un ordinateur distinct ou dans un processus distinct, offre une grande isolation.</span><span class="sxs-lookup"><span data-stu-id="5826a-115">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="5826a-116">Toutes les erreurs qui se produisent dans le travail distant n’affectent pas les autres travaux en cours d’exécution ou la session parente qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="5826a-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="5826a-117">Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="5826a-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="5826a-118">Tous les objets sont sérialisés et désérialisés lorsqu’ils sont transmis entre la session parente et la session distante (travail).</span><span class="sxs-lookup"><span data-stu-id="5826a-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="5826a-119">La sérialisation d’objets de données complexes volumineux peut consommer de grandes quantités de ressources de calcul et de mémoire et transférer de grandes quantités de données sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="5826a-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="5826a-120">Les travaux basés sur les threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents.</span><span class="sxs-lookup"><span data-stu-id="5826a-120">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="5826a-121">Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus sont terminés.</span><span class="sxs-lookup"><span data-stu-id="5826a-121">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="5826a-122">Toutefois, les travaux basés sur les threads nécessitent moins de traitement.</span><span class="sxs-lookup"><span data-stu-id="5826a-122">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="5826a-123">Ils n’utilisent pas la couche de communication à distance ou la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="5826a-123">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="5826a-124">Les objets de résultats sont retournés en tant que références aux objets actifs dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5826a-124">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="5826a-125">Sans cette surcharge, les travaux basés sur les threads s’exécutent plus rapidement et utilisent moins de ressources que les autres types de travaux.</span><span class="sxs-lookup"><span data-stu-id="5826a-125">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5826a-126">La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5826a-126">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="5826a-127">Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé.</span><span class="sxs-lookup"><span data-stu-id="5826a-127">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="5826a-128">Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.</span><span class="sxs-lookup"><span data-stu-id="5826a-128">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="5826a-129">Il existe deux façons de contourner cette limitation :</span><span class="sxs-lookup"><span data-stu-id="5826a-129">There are two ways work around this limitation:</span></span>

1. <span data-ttu-id="5826a-130">Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="5826a-130">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="5826a-131">Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="5826a-131">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="5826a-132">Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail.</span><span class="sxs-lookup"><span data-stu-id="5826a-132">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="5826a-133">Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="5826a-133">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="5826a-134">Applets de commande Job</span><span class="sxs-lookup"><span data-stu-id="5826a-134">The job cmdlets</span></span>

|<span data-ttu-id="5826a-135">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="5826a-135">Cmdlet</span></span>          |<span data-ttu-id="5826a-136">Description</span><span class="sxs-lookup"><span data-stu-id="5826a-136">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="5826a-137">Démarre une tâche en arrière-plan sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5826a-137">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="5826a-138">Obtient les tâches en arrière-plan qui ont été démarrées dans le</span><span class="sxs-lookup"><span data-stu-id="5826a-138">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="5826a-139">session active.</span><span class="sxs-lookup"><span data-stu-id="5826a-139">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="5826a-140">Obtient les résultats des tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-140">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="5826a-141">Arrête une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-141">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="5826a-142">Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches soient</span><span class="sxs-lookup"><span data-stu-id="5826a-142">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="5826a-143">Remplissez.</span><span class="sxs-lookup"><span data-stu-id="5826a-143">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="5826a-144">Supprime une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-144">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="5826a-145">Le paramètre **AsJob** crée une tâche en arrière-plan sur un</span><span class="sxs-lookup"><span data-stu-id="5826a-145">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="5826a-146">ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5826a-146">remote computer.</span></span> <span data-ttu-id="5826a-147">Vous pouvez utiliser `Invoke-Command` pour exécuter</span><span class="sxs-lookup"><span data-stu-id="5826a-147">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="5826a-148">toute commande Job à distance, y compris `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="5826a-148">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="5826a-149">Comment démarrer un travail sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="5826a-149">How to start a job on the local computer</span></span>

<span data-ttu-id="5826a-150">Pour démarrer une tâche en arrière-plan sur l’ordinateur local, utilisez l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="5826a-150">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="5826a-151">Pour écrire une `Start-Job` commande, mettez-la entre guillemets doubles ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="5826a-151">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="5826a-152">Utilisez le paramètre **scriptblock** pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="5826a-152">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="5826a-153">La commande suivante démarre une tâche en arrière-plan qui exécute une `Get-Process` commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5826a-153">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="5826a-154">Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, même si le travail prend une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="5826a-154">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="5826a-155">Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="5826a-155">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="5826a-156">La `Start-Job` commande retourne un objet qui représente le travail.</span><span class="sxs-lookup"><span data-stu-id="5826a-156">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="5826a-157">L'objet de traitement retourné par Get-Job contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="5826a-157">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="5826a-158">Vous pouvez enregistrer l’objet de traitement dans une variable, puis l’utiliser avec les autres applets de commande de **tâche** pour gérer la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-158">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="5826a-159">La commande suivante démarre un objet de traitement et enregistre l’objet de traitement résultant dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="5826a-159">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="5826a-160">À compter de PowerShell 6,0, vous pouvez utiliser l’opérateur d’arrière-plan ( `&` ) à la fin d’un pipeline pour démarrer un travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-160">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="5826a-161">Pour plus d’informations, consultez [opérateur d’arrière-plan](about_Operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="5826a-161">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="5826a-162">L’utilisation de l’opérateur d’arrière-plan est fonctionnellement équivalente à l’utilisation `Start-Job` de l’applet de commande dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="5826a-162">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="5826a-163">Obtention d’objets de travail</span><span class="sxs-lookup"><span data-stu-id="5826a-163">Getting job objects</span></span>

<span data-ttu-id="5826a-164">L' `Get-Job` applet de commande retourne des objets qui représentent les tâches en arrière-plan démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5826a-164">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="5826a-165">Sans paramètres, `Get-Job` retourne toutes les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5826a-165">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="5826a-166">L’objet de traitement contient l’état du travail, qui indique si le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="5826a-166">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="5826a-167">L’état d’une tâche terminée est **terminé** ou **a échoué**.</span><span class="sxs-lookup"><span data-stu-id="5826a-167">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="5826a-168">Un travail peut également être **bloqué** ou **en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="5826a-168">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="5826a-169">Vous pouvez enregistrer l’objet de traitement dans une variable et l’utiliser pour représenter la tâche dans une commande ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5826a-169">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="5826a-170">La commande suivante obtient la tâche avec l’ID 1 et l’enregistre dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="5826a-170">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="5826a-171">Obtention des résultats d’un travail</span><span class="sxs-lookup"><span data-stu-id="5826a-171">Getting the results of a job</span></span>

<span data-ttu-id="5826a-172">Lorsque vous exécutez un travail en arrière-plan, les résultats n’apparaissent pas immédiatement.</span><span class="sxs-lookup"><span data-stu-id="5826a-172">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="5826a-173">Pour obtenir les résultats d’une tâche en arrière-plan, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="5826a-173">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="5826a-174">Dans l’exemple suivant, l' `Receive-Job` applet de commande obtient les résultats de la tâche à l’aide de l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="5826a-174">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

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

<span data-ttu-id="5826a-175">Vous pouvez enregistrer les résultats d’un travail dans une variable.</span><span class="sxs-lookup"><span data-stu-id="5826a-175">You can save the results of a job in a variable.</span></span> <span data-ttu-id="5826a-176">La commande suivante enregistre les résultats de la tâche dans la variable dans la variable `$job` `$results` .</span><span class="sxs-lookup"><span data-stu-id="5826a-176">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="5826a-177">Obtention et conservation des résultats de travaux partiels</span><span class="sxs-lookup"><span data-stu-id="5826a-177">Getting and keeping partial job results</span></span>

<span data-ttu-id="5826a-178">L' `Receive-Job` applet de commande obtient les résultats d’une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-178">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="5826a-179">Si la tâche est terminée, `Receive-Job` obtient tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="5826a-179">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="5826a-180">Si le travail est toujours en cours d’exécution, `Receive-Job` obtient les résultats générés jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="5826a-180">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="5826a-181">Vous pouvez réexécuter `Receive-Job` les commandes pour obtenir les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="5826a-181">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="5826a-182">Par défaut, `Receive-Job` supprime les résultats du cache où sont stockés les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="5826a-182">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="5826a-183">Lorsque vous réexécutez `Receive-Job` , vous recevez uniquement les nouveaux résultats qui arrivent après la première exécution.</span><span class="sxs-lookup"><span data-stu-id="5826a-183">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="5826a-184">Les commandes suivantes affichent les résultats des `Receive-Job` commandes exécutées avant la fin du travail.</span><span class="sxs-lookup"><span data-stu-id="5826a-184">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="5826a-185">Utilisez le paramètre **Keep** pour empêcher `Receive-Job` la suppression des résultats de la tâche retournés.</span><span class="sxs-lookup"><span data-stu-id="5826a-185">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="5826a-186">Les commandes suivantes montrent l’effet de l’utilisation du paramètre **Keep** sur un travail qui n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="5826a-186">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

### <a name="waiting-for-the-results"></a><span data-ttu-id="5826a-187">En attente des résultats</span><span class="sxs-lookup"><span data-stu-id="5826a-187">Waiting for the results</span></span>

<span data-ttu-id="5826a-188">Si vous exécutez une commande qui prend beaucoup de temps, vous pouvez utiliser les propriétés de l’objet de traitement pour déterminer à quel moment le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="5826a-188">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="5826a-189">La commande suivante utilise l' `Get-Job` objet pour récupérer toutes les tâches en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5826a-189">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="5826a-190">Les résultats s’affichent dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="5826a-190">The results appear in a table.</span></span> <span data-ttu-id="5826a-191">L’état de la tâche s’affiche dans la colonne **État** .</span><span class="sxs-lookup"><span data-stu-id="5826a-191">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="5826a-192">Dans ce cas, la propriété **State** indique que le travail 2 est toujours en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5826a-192">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="5826a-193">Si vous deviez utiliser l' `Receive-Job` applet de commande pour obtenir les résultats du travail maintenant, les résultats seraient incomplets.</span><span class="sxs-lookup"><span data-stu-id="5826a-193">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="5826a-194">Vous pouvez utiliser l' `Receive-Job` applet de commande à plusieurs reprises pour obtenir tous les résultats.</span><span class="sxs-lookup"><span data-stu-id="5826a-194">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="5826a-195">Utilisez la propriété **State** pour déterminer à quel moment le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="5826a-195">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="5826a-196">Vous pouvez également utiliser le paramètre **Wait** de l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5826a-196">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="5826a-197">Quand vous utilisez ce paramètre, l’applet de commande ne retourne pas l’invite de commandes tant que le travail n’est pas terminé et que tous les résultats sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="5826a-197">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="5826a-198">Vous pouvez également utiliser l' `Wait-Job` applet de commande pour attendre un ou plusieurs des résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="5826a-198">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="5826a-199">`Wait-Job` permet d’attendre une ou plusieurs tâches spécifiques ou pour tous les travaux.</span><span class="sxs-lookup"><span data-stu-id="5826a-199">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="5826a-200">La commande suivante utilise l' `Wait-Job` applet de commande pour attendre un travail avec l' **ID**</span><span class="sxs-lookup"><span data-stu-id="5826a-200">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="5826a-201">Par conséquent, l’invite PowerShell est supprimée jusqu’à ce que la tâche soit terminée.</span><span class="sxs-lookup"><span data-stu-id="5826a-201">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="5826a-202">Vous pouvez également attendre une période prédéterminée.</span><span class="sxs-lookup"><span data-stu-id="5826a-202">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="5826a-203">Cette commande utilise le paramètre **timeout** pour limiter l’attente à 120 secondes.</span><span class="sxs-lookup"><span data-stu-id="5826a-203">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="5826a-204">Lorsque le délai expire, l’invite de commandes retourne, mais le travail continue à s’exécuter en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5826a-204">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="5826a-205">Arrêt d’un travail</span><span class="sxs-lookup"><span data-stu-id="5826a-205">Stopping a job</span></span>

<span data-ttu-id="5826a-206">Pour arrêter une tâche en arrière-plan, utilisez l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="5826a-206">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="5826a-207">La commande suivante démarre un travail pour obtenir chaque entrée dans le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="5826a-207">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="5826a-208">Elle enregistre l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="5826a-208">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="5826a-209">La commande suivante arrête le travail.</span><span class="sxs-lookup"><span data-stu-id="5826a-209">The following command stops the job.</span></span> <span data-ttu-id="5826a-210">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer la tâche dans la `$job` variable à `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="5826a-210">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="5826a-211">Suppression d’un travail</span><span class="sxs-lookup"><span data-stu-id="5826a-211">Deleting a job</span></span>

<span data-ttu-id="5826a-212">Pour supprimer une tâche en arrière-plan, utilisez l’applet de commande `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="5826a-212">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="5826a-213">La commande suivante supprime la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="5826a-213">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="5826a-214">Examen d’un travail ayant échoué</span><span class="sxs-lookup"><span data-stu-id="5826a-214">Investigating a failed job</span></span>

<span data-ttu-id="5826a-215">Les travaux peuvent échouer pour de nombreuses raisons.</span><span class="sxs-lookup"><span data-stu-id="5826a-215">Jobs can fail for many reasons.</span></span> <span data-ttu-id="5826a-216">l’objet de traitement contient une propriété **reason** qui contient des informations sur la cause de l’échec.</span><span class="sxs-lookup"><span data-stu-id="5826a-216">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="5826a-217">L’exemple suivant démarre un travail sans les informations d’identification requises.</span><span class="sxs-lookup"><span data-stu-id="5826a-217">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="5826a-218">Inspectez la propriété **reason** pour trouver l’erreur qui a provoqué l’échec du travail.</span><span class="sxs-lookup"><span data-stu-id="5826a-218">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="5826a-219">Dans ce cas, la tâche a échoué, car l’ordinateur distant nécessitait des informations d’identification explicites pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="5826a-219">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="5826a-220">La propriété **reason** contient le message suivant :</span><span class="sxs-lookup"><span data-stu-id="5826a-220">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="5826a-221">La connexion au serveur distant a échoué avec le message d’erreur suivant : « accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="5826a-221">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="5826a-222">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5826a-222">See also</span></span>

- [<span data-ttu-id="5826a-223">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="5826a-223">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="5826a-224">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="5826a-224">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="5826a-225">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="5826a-225">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="5826a-226">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5826a-226">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="5826a-227">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5826a-227">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="5826a-228">Start-Job</span><span class="sxs-lookup"><span data-stu-id="5826a-228">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="5826a-229">Get-Job</span><span class="sxs-lookup"><span data-stu-id="5826a-229">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="5826a-230">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="5826a-230">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="5826a-231">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="5826a-231">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="5826a-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="5826a-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="5826a-233">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="5826a-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="5826a-234">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="5826a-234">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
