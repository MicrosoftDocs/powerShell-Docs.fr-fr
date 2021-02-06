---
description: Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 862fbf54b927bb70c68e4b3cc43c564f178f9db5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597134"
---
# <a name="about-jobs"></a><span data-ttu-id="c11a4-103">À propos des travaux</span><span class="sxs-lookup"><span data-stu-id="c11a4-103">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="c11a4-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="c11a4-104">Short description</span></span>
<span data-ttu-id="c11a4-105">Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="c11a4-105">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="c11a4-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="c11a4-106">Long description</span></span>

<span data-ttu-id="c11a4-107">PowerShell exécute simultanément des commandes et des scripts par le biais de travaux.</span><span class="sxs-lookup"><span data-stu-id="c11a4-107">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="c11a4-108">Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="c11a4-108">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="c11a4-109">`RemoteJob` -Les commandes et les scripts s’exécutent sur une session à distance.</span><span class="sxs-lookup"><span data-stu-id="c11a4-109">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="c11a4-110">Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="c11a4-110">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="c11a4-111">`BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c11a4-111">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="c11a4-112">`PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c11a4-112">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="c11a4-113">Pour plus d’informations, consultez [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span><span class="sxs-lookup"><span data-stu-id="c11a4-113">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="c11a4-114">L’exécution de scripts à distance, sur un ordinateur distinct ou dans un processus distinct, offre une grande isolation.</span><span class="sxs-lookup"><span data-stu-id="c11a4-114">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="c11a4-115">Toutes les erreurs qui se produisent dans le travail distant n’affectent pas les autres travaux en cours d’exécution ou la session parente qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="c11a4-115">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="c11a4-116">Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c11a4-116">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="c11a4-117">Tous les objets sont sérialisés et désérialisés lorsqu’ils sont transmis entre la session parente et la session distante (travail).</span><span class="sxs-lookup"><span data-stu-id="c11a4-117">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="c11a4-118">La sérialisation d’objets de données complexes volumineux peut consommer de grandes quantités de ressources de calcul et de mémoire et transférer de grandes quantités de données sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="c11a4-118">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="c11a4-119">Les travaux basés sur les threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents.</span><span class="sxs-lookup"><span data-stu-id="c11a4-119">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="c11a4-120">Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus sont terminés.</span><span class="sxs-lookup"><span data-stu-id="c11a4-120">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="c11a4-121">Toutefois, les travaux basés sur les threads nécessitent moins de traitement.</span><span class="sxs-lookup"><span data-stu-id="c11a4-121">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="c11a4-122">Ils n’utilisent pas la couche de communication à distance ou la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="c11a4-122">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="c11a4-123">Les objets de résultats sont retournés en tant que références aux objets actifs dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c11a4-123">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="c11a4-124">Sans cette surcharge, les travaux basés sur les threads s’exécutent plus rapidement et utilisent moins de ressources que les autres types de travaux.</span><span class="sxs-lookup"><span data-stu-id="c11a4-124">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c11a4-125">La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline.</span><span class="sxs-lookup"><span data-stu-id="c11a4-125">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="c11a4-126">Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé.</span><span class="sxs-lookup"><span data-stu-id="c11a4-126">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="c11a4-127">Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.</span><span class="sxs-lookup"><span data-stu-id="c11a4-127">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="c11a4-128">Il existe deux façons de contourner cette situation :</span><span class="sxs-lookup"><span data-stu-id="c11a4-128">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="c11a4-129">Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="c11a4-129">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="c11a4-130">Pour plus d’informations, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="c11a4-130">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="c11a4-131">Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail.</span><span class="sxs-lookup"><span data-stu-id="c11a4-131">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="c11a4-132">Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="c11a4-132">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="c11a4-133">Applets de commande Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-133">The job cmdlets</span></span>

|<span data-ttu-id="c11a4-134">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="c11a4-134">Cmdlet</span></span>          |<span data-ttu-id="c11a4-135">Description</span><span class="sxs-lookup"><span data-stu-id="c11a4-135">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="c11a4-136">Démarre une tâche en arrière-plan sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c11a4-136">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="c11a4-137">Obtient les tâches en arrière-plan qui ont été démarrées dans le</span><span class="sxs-lookup"><span data-stu-id="c11a4-137">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="c11a4-138">session active.</span><span class="sxs-lookup"><span data-stu-id="c11a4-138">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="c11a4-139">Obtient les résultats des tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-139">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="c11a4-140">Arrête une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-140">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="c11a4-141">Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches soient</span><span class="sxs-lookup"><span data-stu-id="c11a4-141">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="c11a4-142">Remplissez.</span><span class="sxs-lookup"><span data-stu-id="c11a4-142">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="c11a4-143">Supprime une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-143">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="c11a4-144">Le paramètre **AsJob** crée une tâche en arrière-plan sur un</span><span class="sxs-lookup"><span data-stu-id="c11a4-144">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="c11a4-145">ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="c11a4-145">remote computer.</span></span> <span data-ttu-id="c11a4-146">Vous pouvez utiliser `Invoke-Command` pour exécuter</span><span class="sxs-lookup"><span data-stu-id="c11a4-146">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="c11a4-147">toute commande Job à distance, y compris `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-147">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="c11a4-148">Comment démarrer un travail sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="c11a4-148">How to start a job on the local computer</span></span>

<span data-ttu-id="c11a4-149">Pour démarrer une tâche en arrière-plan sur l’ordinateur local, utilisez l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-149">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="c11a4-150">Pour écrire une `Start-Job` commande, mettez-la entre guillemets doubles ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="c11a4-150">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="c11a4-151">Utilisez le paramètre **scriptblock** pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="c11a4-151">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="c11a4-152">La commande suivante démarre une tâche en arrière-plan qui exécute une `Get-Process` commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c11a4-152">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="c11a4-153">Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, même si le travail prend une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="c11a4-153">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="c11a4-154">Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c11a4-154">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="c11a4-155">La `Start-Job` commande retourne un objet qui représente le travail.</span><span class="sxs-lookup"><span data-stu-id="c11a4-155">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="c11a4-156">L'objet de traitement retourné par Get-Job contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c11a4-156">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="c11a4-157">Vous pouvez enregistrer l’objet de traitement dans une variable, puis l’utiliser avec les autres applets de commande de **tâche** pour gérer la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-157">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="c11a4-158">La commande suivante démarre un objet de traitement et enregistre l’objet de traitement résultant dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="c11a4-158">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="c11a4-159">À compter de PowerShell 6,0, vous pouvez utiliser l’opérateur d’arrière-plan ( `&` ) à la fin d’un pipeline pour démarrer un travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-159">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="c11a4-160">Pour plus d’informations, consultez [opérateur d’arrière-plan](about_Operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="c11a4-160">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="c11a4-161">L’utilisation de l’opérateur d’arrière-plan est fonctionnellement équivalente à l’utilisation `Start-Job` de l’applet de commande dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="c11a4-161">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="c11a4-162">Obtention d’objets de travail</span><span class="sxs-lookup"><span data-stu-id="c11a4-162">Getting job objects</span></span>

<span data-ttu-id="c11a4-163">L' `Get-Job` applet de commande retourne des objets qui représentent les tâches en arrière-plan démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c11a4-163">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="c11a4-164">Sans paramètres, `Get-Job` retourne toutes les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c11a4-164">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="c11a4-165">L’objet de traitement contient l’état du travail, qui indique si le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="c11a4-165">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="c11a4-166">L’état d’une tâche terminée est **terminé** ou **a échoué**.</span><span class="sxs-lookup"><span data-stu-id="c11a4-166">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="c11a4-167">Un travail peut également être **bloqué** ou **en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="c11a4-167">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="c11a4-168">Vous pouvez enregistrer l’objet de traitement dans une variable et l’utiliser pour représenter la tâche dans une commande ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c11a4-168">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="c11a4-169">La commande suivante obtient la tâche avec l’ID 1 et l’enregistre dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="c11a4-169">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="c11a4-170">Obtention des résultats d’un travail</span><span class="sxs-lookup"><span data-stu-id="c11a4-170">Getting the results of a job</span></span>

<span data-ttu-id="c11a4-171">Lorsque vous exécutez un travail en arrière-plan, les résultats n’apparaissent pas immédiatement.</span><span class="sxs-lookup"><span data-stu-id="c11a4-171">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="c11a4-172">Pour obtenir les résultats d’une tâche en arrière-plan, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-172">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="c11a4-173">Dans l’exemple suivant, l' `Receive-Job` applet de commande obtient les résultats de la tâche à l’aide de l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="c11a4-173">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

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

<span data-ttu-id="c11a4-174">Vous pouvez enregistrer les résultats d’un travail dans une variable.</span><span class="sxs-lookup"><span data-stu-id="c11a4-174">You can save the results of a job in a variable.</span></span> <span data-ttu-id="c11a4-175">La commande suivante enregistre les résultats de la tâche dans la variable dans la variable `$job` `$results` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="c11a4-176">Obtention et conservation des résultats de travaux partiels</span><span class="sxs-lookup"><span data-stu-id="c11a4-176">Getting and keeping partial job results</span></span>

<span data-ttu-id="c11a4-177">L' `Receive-Job` applet de commande obtient les résultats d’une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-177">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="c11a4-178">Si la tâche est terminée, `Receive-Job` obtient tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c11a4-178">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="c11a4-179">Si le travail est toujours en cours d’exécution, `Receive-Job` obtient les résultats générés jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="c11a4-179">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="c11a4-180">Vous pouvez réexécuter `Receive-Job` les commandes pour obtenir les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="c11a4-180">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="c11a4-181">Par défaut, `Receive-Job` supprime les résultats du cache où sont stockés les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c11a4-181">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="c11a4-182">Lorsque vous réexécutez `Receive-Job` , vous recevez uniquement les nouveaux résultats qui arrivent après la première exécution.</span><span class="sxs-lookup"><span data-stu-id="c11a4-182">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="c11a4-183">Les commandes suivantes affichent les résultats des `Receive-Job` commandes exécutées avant la fin du travail.</span><span class="sxs-lookup"><span data-stu-id="c11a4-183">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="c11a4-184">Utilisez le paramètre **Keep** pour empêcher `Receive-Job` la suppression des résultats de la tâche retournés.</span><span class="sxs-lookup"><span data-stu-id="c11a4-184">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="c11a4-185">Les commandes suivantes montrent l’effet de l’utilisation du paramètre **Keep** sur un travail qui n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="c11a4-185">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

### <a name="waiting-for-the-results"></a><span data-ttu-id="c11a4-186">En attente des résultats</span><span class="sxs-lookup"><span data-stu-id="c11a4-186">Waiting for the results</span></span>

<span data-ttu-id="c11a4-187">Si vous exécutez une commande qui prend beaucoup de temps, vous pouvez utiliser les propriétés de l’objet de traitement pour déterminer à quel moment le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="c11a4-187">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="c11a4-188">La commande suivante utilise l' `Get-Job` objet pour récupérer toutes les tâches en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c11a4-188">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="c11a4-189">Les résultats s’affichent dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="c11a4-189">The results appear in a table.</span></span> <span data-ttu-id="c11a4-190">L’état de la tâche s’affiche dans la colonne **État** .</span><span class="sxs-lookup"><span data-stu-id="c11a4-190">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="c11a4-191">Dans ce cas, la propriété **State** indique que le travail 2 est toujours en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c11a4-191">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="c11a4-192">Si vous deviez utiliser l' `Receive-Job` applet de commande pour obtenir les résultats du travail maintenant, les résultats seraient incomplets.</span><span class="sxs-lookup"><span data-stu-id="c11a4-192">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="c11a4-193">Vous pouvez utiliser l' `Receive-Job` applet de commande à plusieurs reprises pour obtenir tous les résultats.</span><span class="sxs-lookup"><span data-stu-id="c11a4-193">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="c11a4-194">Utilisez la propriété **State** pour déterminer à quel moment le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="c11a4-194">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="c11a4-195">Vous pouvez également utiliser le paramètre **Wait** de l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c11a4-195">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="c11a4-196">Quand vous utilisez ce paramètre, l’applet de commande ne retourne pas l’invite de commandes tant que le travail n’est pas terminé et que tous les résultats sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="c11a4-196">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="c11a4-197">Vous pouvez également utiliser l' `Wait-Job` applet de commande pour attendre un ou plusieurs des résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c11a4-197">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="c11a4-198">`Wait-Job` permet d’attendre une ou plusieurs tâches spécifiques ou pour tous les travaux.</span><span class="sxs-lookup"><span data-stu-id="c11a4-198">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="c11a4-199">La commande suivante utilise l' `Wait-Job` applet de commande pour attendre un travail avec l' **ID**</span><span class="sxs-lookup"><span data-stu-id="c11a4-199">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="c11a4-200">Par conséquent, l’invite PowerShell est supprimée jusqu’à ce que la tâche soit terminée.</span><span class="sxs-lookup"><span data-stu-id="c11a4-200">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="c11a4-201">Vous pouvez également attendre une période prédéterminée.</span><span class="sxs-lookup"><span data-stu-id="c11a4-201">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="c11a4-202">Cette commande utilise le paramètre **timeout** pour limiter l’attente à 120 secondes.</span><span class="sxs-lookup"><span data-stu-id="c11a4-202">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="c11a4-203">Lorsque le délai expire, l’invite de commandes retourne, mais le travail continue à s’exécuter en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="c11a4-203">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="c11a4-204">Arrêt d’un travail</span><span class="sxs-lookup"><span data-stu-id="c11a4-204">Stopping a job</span></span>

<span data-ttu-id="c11a4-205">Pour arrêter une tâche en arrière-plan, utilisez l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-205">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="c11a4-206">La commande suivante démarre un travail pour obtenir chaque entrée dans le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="c11a4-206">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="c11a4-207">Elle enregistre l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="c11a4-207">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="c11a4-208">La commande suivante arrête le travail.</span><span class="sxs-lookup"><span data-stu-id="c11a4-208">The following command stops the job.</span></span> <span data-ttu-id="c11a4-209">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer la tâche dans la `$job` variable à `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-209">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="c11a4-210">Suppression d’un travail</span><span class="sxs-lookup"><span data-stu-id="c11a4-210">Deleting a job</span></span>

<span data-ttu-id="c11a4-211">Pour supprimer une tâche en arrière-plan, utilisez l’applet de commande `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="c11a4-211">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="c11a4-212">La commande suivante supprime la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="c11a4-212">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="c11a4-213">Examen d’un travail ayant échoué</span><span class="sxs-lookup"><span data-stu-id="c11a4-213">Investigating a failed job</span></span>

<span data-ttu-id="c11a4-214">Les travaux peuvent échouer pour de nombreuses raisons.</span><span class="sxs-lookup"><span data-stu-id="c11a4-214">Jobs can fail for many reasons.</span></span> <span data-ttu-id="c11a4-215">l’objet de traitement contient une propriété **reason** qui contient des informations sur la cause de l’échec.</span><span class="sxs-lookup"><span data-stu-id="c11a4-215">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="c11a4-216">L’exemple suivant démarre un travail sans les informations d’identification requises.</span><span class="sxs-lookup"><span data-stu-id="c11a4-216">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="c11a4-217">Inspectez la propriété **reason** pour trouver l’erreur qui a provoqué l’échec du travail.</span><span class="sxs-lookup"><span data-stu-id="c11a4-217">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="c11a4-218">Dans ce cas, la tâche a échoué, car l’ordinateur distant nécessitait des informations d’identification explicites pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="c11a4-218">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="c11a4-219">La propriété **reason** contient le message suivant :</span><span class="sxs-lookup"><span data-stu-id="c11a4-219">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="c11a4-220">La connexion au serveur distant a échoué avec le message d’erreur suivant : « accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="c11a4-220">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="c11a4-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c11a4-221">See also</span></span>

- [<span data-ttu-id="c11a4-222">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="c11a4-222">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="c11a4-223">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="c11a4-223">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="c11a4-224">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="c11a4-224">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="c11a4-225">about_Remote</span><span class="sxs-lookup"><span data-stu-id="c11a4-225">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="c11a4-226">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="c11a4-226">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="c11a4-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="c11a4-228">Get-Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="c11a4-229">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-229">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="c11a4-230">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="c11a4-231">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-231">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="c11a4-232">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="c11a4-232">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="c11a4-233">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c11a4-233">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
