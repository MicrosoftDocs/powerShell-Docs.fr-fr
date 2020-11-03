---
description: Fournit des informations sur les travaux basés sur des threads PowerShell. Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: d3f7c2754a2e54bc1b6f9fb95d1cf6ce2fed5b9b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208582"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="3288e-105">À propos des travaux de thread</span><span class="sxs-lookup"><span data-stu-id="3288e-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="3288e-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="3288e-106">Short description</span></span>

<span data-ttu-id="3288e-107">Fournit des informations sur les travaux basés sur des threads PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3288e-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="3288e-108">Un travail de thread est un type de tâche en arrière-plan qui exécute une commande ou une expression dans un thread distinct au sein du processus de session actuel.</span><span class="sxs-lookup"><span data-stu-id="3288e-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="3288e-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="3288e-109">Long description</span></span>

<span data-ttu-id="3288e-110">Cet article explique comment exécuter des travaux de thread dans PowerShell sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3288e-110">This article explains how to run thread jobs in PowerShell on a local computer.</span></span>
<span data-ttu-id="3288e-111">Pour plus d’informations sur l’exécution de tâches en arrière-plan sur un ordinateur local, consultez [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="3288e-111">For information about running background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span>

<span data-ttu-id="3288e-112">Vous pouvez démarrer un travail de thread de l’une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3288e-112">You can start a thread job in one of two ways.</span></span>

<span data-ttu-id="3288e-113">La première consiste à utiliser l' `Start-ThreadJob` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3288e-113">The first way is with the `Start-ThreadJob` cmdlet.</span></span> <span data-ttu-id="3288e-114">Cette applet de commande est disponible dans le module **ThreadJob** fourni avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3288e-114">This cmdlet is available in the **ThreadJob** module that ships with PowerShell.</span></span> <span data-ttu-id="3288e-115">`Start-ThreadJob` retourne un objet de traitement unique qui encapsule la commande ou le script en cours d’exécution, et qui peut être utilisé avec toutes les applets de commande de manipulation de travaux PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3288e-115">`Start-ThreadJob` returns a single job object that encapsulates the running command or script, and can be used with all PowerShell job manipulating cmdlets.</span></span>

<span data-ttu-id="3288e-116">La seconde consiste à utiliser l' `ForEach-Object` applet de commande, avec l' `-Parallel` argument de bloc de script de paramètre et le commutateur de `-AsJob` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3288e-116">The second way is with the `ForEach-Object` cmdlet, with the `-Parallel` parameter script block argument along with the `-AsJob` parameter switch.</span></span> <span data-ttu-id="3288e-117">Cette applet de commande retourne un objet de traitement (parent) unique qui contient un travail enfant pour chaque entrée dirigée vers l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3288e-117">This cmdlet returns a single (parent) job object that contains a child job for each input piped to the cmdlet.</span></span> <span data-ttu-id="3288e-118">Chaque travail enfant exécute un script dans un thread distinct avec une `-ThrottleLimit` limite () sur le nombre de travaux enfants exécutés à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="3288e-118">Each child job runs script in a separate thread with a (`-ThrottleLimit`) limit to how many child jobs run at a given time.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="3288e-119">APPLETS DE COMMANDE JOB</span><span class="sxs-lookup"><span data-stu-id="3288e-119">THE JOB CMDLETS</span></span>

|<span data-ttu-id="3288e-120">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="3288e-120">Cmdlet</span></span>           |<span data-ttu-id="3288e-121">Description</span><span class="sxs-lookup"><span data-stu-id="3288e-121">Description</span></span>                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|<span data-ttu-id="3288e-122">Démarre un travail de thread sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3288e-122">Starts a thread job on a local computer.</span></span>               |
|`ForEach-Object` |<span data-ttu-id="3288e-123">Démarre les travaux de thread pour chaque objet d’entrée dirigé, lorsque</span><span class="sxs-lookup"><span data-stu-id="3288e-123">Starts thread jobs for each piped input object, when</span></span>   |
|                 |<span data-ttu-id="3288e-124">utilisé avec les paramètres-Parallel et-AsJob.</span><span class="sxs-lookup"><span data-stu-id="3288e-124">used with -Parallel and -AsJob parameters.</span></span>             |
|`Get-Job`        |<span data-ttu-id="3288e-125">Obtient les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="3288e-125">Gets the jobs that were started in the current session.</span></span>|
|`Receive-Job`    |<span data-ttu-id="3288e-126">Obtient les résultats des travaux.</span><span class="sxs-lookup"><span data-stu-id="3288e-126">Gets the results of jobs.</span></span>                              |
|`Stop-Job`       |<span data-ttu-id="3288e-127">Arrête un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3288e-127">Stops a running job.</span></span>                                   |
|`Wait-Job`       |<span data-ttu-id="3288e-128">Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches soient</span><span class="sxs-lookup"><span data-stu-id="3288e-128">Suppresses the command prompt until one or all jobs are</span></span>|
|                 |<span data-ttu-id="3288e-129">Remplissez.</span><span class="sxs-lookup"><span data-stu-id="3288e-129">complete.</span></span>                                              |
|`Remove-Job`     |<span data-ttu-id="3288e-130">Supprime un travail.</span><span class="sxs-lookup"><span data-stu-id="3288e-130">Deletes a job.</span></span>                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a><span data-ttu-id="3288e-131">Comment démarrer un travail de thread sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="3288e-131">How to start a thread job on the local computer</span></span>

<span data-ttu-id="3288e-132">Pour démarrer un travail de thread sur l’ordinateur local, utilisez l’applet de commande `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="3288e-132">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet.</span></span>

<span data-ttu-id="3288e-133">Pour écrire une `Start-ThreadJob` commande, mettez la commande ou le script en cours d’exécution entre accolades ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="3288e-133">To write a `Start-ThreadJob` command, enclose the command or script the job runs in curly braces (`{ }`).</span></span>

<span data-ttu-id="3288e-134">La commande suivante démarre un travail de thread qui exécute une `Get-Process` commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3288e-134">The following command starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="3288e-135">La `Start-ThreadJob` commande retourne un `ThreadJob` objet qui représente le travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3288e-135">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="3288e-136">L’objet de traitement contient des informations utiles sur la tâche, y compris son état d’exécution actuel.</span><span class="sxs-lookup"><span data-stu-id="3288e-136">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="3288e-137">Il collecte les résultats du travail lors de la génération des résultats.</span><span class="sxs-lookup"><span data-stu-id="3288e-137">It collects the results of the job as the results are being generated.</span></span>

<span data-ttu-id="3288e-138">Pour écrire une `ForEach-Object -Parallel` commande, dirigez les données vers la commande et encadrez la commande ou le script que la tâche exécute entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="3288e-138">To write a `ForEach-Object -Parallel` command, pipe data to the command and enclose the command or script the job runs in curly braces(`{}`).</span></span> <span data-ttu-id="3288e-139">Utilisez le `-AsJob` commutateur de paramètre pour qu’un objet de traitement soit retourné.</span><span class="sxs-lookup"><span data-stu-id="3288e-139">Use the `-AsJob` parameter switch so that a job object is returned.</span></span>

<span data-ttu-id="3288e-140">La commande suivante démarre un travail qui contient des tâches enfants pour chaque valeur d’entrée dirigée vers la commande.</span><span class="sxs-lookup"><span data-stu-id="3288e-140">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="3288e-141">Chaque travail enfant exécute la `Write-Output` commande avec une valeur d’entrée dirigée comme argument.</span><span class="sxs-lookup"><span data-stu-id="3288e-141">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="3288e-142">La `ForEach-Object -Parallel` commande retourne un `PSTaskJob` objet qui contient des tâches enfants pour chaque valeur d’entrée dirigée.</span><span class="sxs-lookup"><span data-stu-id="3288e-142">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="3288e-143">L’objet de traitement contient des informations utiles sur l’état d’exécution des tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="3288e-143">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="3288e-144">Il collecte les résultats des tâches enfants à mesure que les résultats sont générés.</span><span class="sxs-lookup"><span data-stu-id="3288e-144">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="3288e-145">Comment attendre qu’une tâche se termine et récupérer les résultats d’une tâche</span><span class="sxs-lookup"><span data-stu-id="3288e-145">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="3288e-146">Vous pouvez utiliser les applets de commande PowerShell Job, telles que `Wait-Job` et, `Receive-Job` pour attendre la fin d’un travail, puis retourner tous les résultats générés par le travail.</span><span class="sxs-lookup"><span data-stu-id="3288e-146">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="3288e-147">La commande suivante démarre un travail de thread qui exécute une `Get-Process` commande, puis attend la fin de la commande et retourne tous les résultats de données générés par la commande.</span><span class="sxs-lookup"><span data-stu-id="3288e-147">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="3288e-148">La commande suivante démarre un travail qui exécute une `Write-Output` commande pour chaque entrée dirigée, puis attend que toutes les tâches enfants soient terminées, et enfin retourne tous les résultats de données générés par les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="3288e-148">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="3288e-149">L' `Receive-Job` applet de commande retourne les résultats des tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="3288e-149">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="3288e-150">Étant donné que chaque travail enfant s’exécute en parallèle, l’ordre des résultats générés n’est pas garanti.</span><span class="sxs-lookup"><span data-stu-id="3288e-150">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="powershell-concurrency-and-jobs"></a><span data-ttu-id="3288e-151">Accès concurrentiel et travaux PowerShell</span><span class="sxs-lookup"><span data-stu-id="3288e-151">PowerShell concurrency and jobs</span></span>

<span data-ttu-id="3288e-152">PowerShell exécute simultanément des commandes et des scripts par le biais de travaux.</span><span class="sxs-lookup"><span data-stu-id="3288e-152">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="3288e-153">Il existe trois solutions basées sur les travaux fournies par PowerShell pour prendre en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="3288e-153">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="3288e-154">Travail</span><span class="sxs-lookup"><span data-stu-id="3288e-154">Job</span></span>            |<span data-ttu-id="3288e-155">Description</span><span class="sxs-lookup"><span data-stu-id="3288e-155">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="3288e-156">La commande et le script s’exécutent sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="3288e-156">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="3288e-157">Commande et script exécutés dans un processus distinct sur l’environnement local</span><span class="sxs-lookup"><span data-stu-id="3288e-157">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="3288e-158">ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="3288e-158">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="3288e-159">La commande et le script s’exécutent dans un thread distinct au sein du même</span><span class="sxs-lookup"><span data-stu-id="3288e-159">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="3288e-160">processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3288e-160">process on the local machine.</span></span>                                |

<span data-ttu-id="3288e-161">Chaque type de tâche présente des avantages et des inconvénients.</span><span class="sxs-lookup"><span data-stu-id="3288e-161">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="3288e-162">L’exécution d’un script à distance sur un ordinateur distinct ou dans un processus distinct a une grande isolation.</span><span class="sxs-lookup"><span data-stu-id="3288e-162">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="3288e-163">Les erreurs n’affectent pas les travaux en cours d’exécution ou le client qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="3288e-163">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="3288e-164">Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="3288e-164">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="3288e-165">Tous les objets passés à et à partir de la session distante doivent être sérialisés puis désérialisés lorsqu’ils sont transmis entre le client et la session cible.</span><span class="sxs-lookup"><span data-stu-id="3288e-165">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="3288e-166">L’opération de sérialisation peut utiliser de nombreuses ressources de calcul et de mémoire pour les objets de données complexes de grande taille.</span><span class="sxs-lookup"><span data-stu-id="3288e-166">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

## <a name="powershell-thread-based-jobs"></a><span data-ttu-id="3288e-167">Travaux basés sur des threads PowerShell</span><span class="sxs-lookup"><span data-stu-id="3288e-167">PowerShell thread based jobs</span></span>

<span data-ttu-id="3288e-168">Les travaux basés sur des threads ne sont pas aussi robustes que les travaux distants et en arrière-plan, car ils s’exécutent dans le même processus sur des threads différents.</span><span class="sxs-lookup"><span data-stu-id="3288e-168">Thread based jobs are not as robust as Remote and Background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="3288e-169">Si un travail a une erreur critique qui bloque le processus, alors tous les autres travaux du processus échouent également.</span><span class="sxs-lookup"><span data-stu-id="3288e-169">If one job has a critical error that crashes the process, then all other jobs in the process will also fail.</span></span>

<span data-ttu-id="3288e-170">Toutefois, les travaux basés sur les threads ont une charge de travail bien moindre.</span><span class="sxs-lookup"><span data-stu-id="3288e-170">However, thread-based jobs have much less overhead.</span></span> <span data-ttu-id="3288e-171">Ils n’ont pas besoin d’utiliser la couche de communication à distance ou la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="3288e-171">They don't need to use the remoting layer or serialization.</span></span> <span data-ttu-id="3288e-172">Le résultat est que les travaux basés sur les threads ont tendance à s’exécuter beaucoup plus rapidement et à utiliser beaucoup moins de ressources que les autres types de tâches.</span><span class="sxs-lookup"><span data-stu-id="3288e-172">The result is that thread-based jobs tend to run much faster and use far less resources than the other job types.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="3288e-173">Performances des travaux de thread</span><span class="sxs-lookup"><span data-stu-id="3288e-173">Thread job performance</span></span>

<span data-ttu-id="3288e-174">Les tâches de thread sont plus rapides et plus légères que d’autres types de travaux.</span><span class="sxs-lookup"><span data-stu-id="3288e-174">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="3288e-175">Toutefois, elles ont toujours une surcharge qui peut être importante par rapport au travail que fait le travail.</span><span class="sxs-lookup"><span data-stu-id="3288e-175">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="3288e-176">PowerShell exécute des commandes et des scripts dans une session.</span><span class="sxs-lookup"><span data-stu-id="3288e-176">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="3288e-177">Une seule commande ou un seul script peut s’exécuter à la fois dans une session.</span><span class="sxs-lookup"><span data-stu-id="3288e-177">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="3288e-178">Ainsi, lors de l’exécution de plusieurs tâches, chaque travail s’exécute dans une session distincte.</span><span class="sxs-lookup"><span data-stu-id="3288e-178">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="3288e-179">Chaque session contribue à la surcharge.</span><span class="sxs-lookup"><span data-stu-id="3288e-179">Each session contributes to the overhead.</span></span>

<span data-ttu-id="3288e-180">Les travaux de thread offrent les meilleures performances lorsque le travail qu’ils effectuent est supérieur à la surcharge de la session utilisée pour exécuter le travail.</span><span class="sxs-lookup"><span data-stu-id="3288e-180">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="3288e-181">Il existe deux cas pour qui répondent à ces critères.</span><span class="sxs-lookup"><span data-stu-id="3288e-181">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="3288e-182">Calcul intensif-l’exécution d’un script sur plusieurs travaux de thread peut tirer parti de plusieurs cœurs de processeur et se terminer plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="3288e-182">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="3288e-183">Le travail se compose d’un script d’attente significatif, qui consacre du temps à attendre les e/s ou les résultats d’appel distant.</span><span class="sxs-lookup"><span data-stu-id="3288e-183">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="3288e-184">L’exécution en parallèle se termine généralement plus rapidement que si elle est exécutée de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="3288e-184">Running in parallel usually completes quicker than if run sequentially.</span></span>

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

<span data-ttu-id="3288e-185">Le premier exemple ci-dessus illustre une boucle foreach qui crée des travaux de thread 1000 pour effectuer une écriture de chaîne simple.</span><span class="sxs-lookup"><span data-stu-id="3288e-185">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="3288e-186">En raison de la surcharge du travail, l’exécution prend plus de 33 secondes.</span><span class="sxs-lookup"><span data-stu-id="3288e-186">Due to job overhead, it takes over 33 seconds to complete.</span></span>

<span data-ttu-id="3288e-187">Le deuxième exemple exécute l' `ForEach` applet de commande pour effectuer les mêmes opérations 1000 et chaque écriture de chaîne est exécutée séquentiellement sans surcharge de travail.</span><span class="sxs-lookup"><span data-stu-id="3288e-187">The second example runs the `ForEach` cmdlet to do the same 1000 operations and each string write is executed sequentially without any job overhead.</span></span> <span data-ttu-id="3288e-188">Il se termine en une seule 25 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="3288e-188">It completes in a mere 25 milliseconds.</span></span>

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

<span data-ttu-id="3288e-189">Dans l’exemple ci-dessus, jusqu’à 5000 entrées sont collectées pour 10 journaux système distincts.</span><span class="sxs-lookup"><span data-stu-id="3288e-189">In the above example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="3288e-190">Étant donné que le script implique la lecture d’un certain nombre de journaux, il est logique d’effectuer les opérations en parallèle.</span><span class="sxs-lookup"><span data-stu-id="3288e-190">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span> <span data-ttu-id="3288e-191">Et le travail se termine plus de deux fois plus rapidement que lorsque le script est exécuté de façon séquentielle.</span><span class="sxs-lookup"><span data-stu-id="3288e-191">And the job completes over twice as fast as when the script is run sequentially.</span></span>

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

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="3288e-192">Travaux de thread et variables</span><span class="sxs-lookup"><span data-stu-id="3288e-192">Thread jobs and variables</span></span>

<span data-ttu-id="3288e-193">Les variables sont passées dans des tâches de thread de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="3288e-193">Variables are passed into thread jobs in various ways.</span></span>

<span data-ttu-id="3288e-194">`Start-ThreadJob` peut accepter des variables qui sont dirigées vers l’applet de commande, transmises au bloc de script via le `$using` mot clé ou transmises via le paramètre **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="3288e-194">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job

`ForEach-Object -Parallel` accepts piped in variables, and variables passed
directly to the script block via the `$using` keyword.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="3288e-195">Étant donné que les travaux de thread s’exécutent dans le même processus, tout type de référence de variable passé dans le travail doit être traité avec précaution.</span><span class="sxs-lookup"><span data-stu-id="3288e-195">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="3288e-196">S’il ne s’agit pas d’un objet thread-safe, il ne doit jamais être assigné à, et la méthode et les propriétés ne doivent jamais être appelées dessus.</span><span class="sxs-lookup"><span data-stu-id="3288e-196">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

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

<span data-ttu-id="3288e-197">L’exemple ci-dessus passe un objet dotNet thread-safe `ConcurrentDictionary` à toutes les tâches enfants pour collecter des objets de processus portant un nom unique.</span><span class="sxs-lookup"><span data-stu-id="3288e-197">The above example passes a thread safe dotNet `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="3288e-198">Étant donné qu’il s’agit d’un objet thread-safe, il peut être utilisé en toute sécurité pendant que les travaux s’exécutent simultanément dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3288e-198">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

## <a name="see-also"></a><span data-ttu-id="3288e-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3288e-199">See also</span></span>

- [<span data-ttu-id="3288e-200">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="3288e-200">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="3288e-201">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="3288e-201">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="3288e-202">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="3288e-202">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="3288e-203">about_Remote</span><span class="sxs-lookup"><span data-stu-id="3288e-203">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="3288e-204">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="3288e-204">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="3288e-205">Start-Job</span><span class="sxs-lookup"><span data-stu-id="3288e-205">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="3288e-206">Get-Job</span><span class="sxs-lookup"><span data-stu-id="3288e-206">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="3288e-207">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="3288e-207">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="3288e-208">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="3288e-208">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="3288e-209">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3288e-209">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="3288e-210">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="3288e-210">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
