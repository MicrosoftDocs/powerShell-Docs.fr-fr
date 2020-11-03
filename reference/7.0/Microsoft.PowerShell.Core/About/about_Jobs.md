---
description: Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 838e142fe39260b759e9a44c6d69b80d3c5b293e
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208602"
---
# <a name="about-jobs"></a><span data-ttu-id="b755e-104">À propos des travaux</span><span class="sxs-lookup"><span data-stu-id="b755e-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="b755e-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="b755e-105">Short description</span></span>
<span data-ttu-id="b755e-106">Fournit des informations sur la façon dont les travaux en arrière-plan PowerShell exécutent une commande ou une expression en arrière-plan sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="b755e-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="b755e-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="b755e-107">Long description</span></span>

<span data-ttu-id="b755e-108">PowerShell exécute simultanément des commandes et des scripts par le biais de travaux.</span><span class="sxs-lookup"><span data-stu-id="b755e-108">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="b755e-109">Il existe trois solutions basées sur les travaux fournies par PowerShell pour prendre en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="b755e-109">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="b755e-110">Travail</span><span class="sxs-lookup"><span data-stu-id="b755e-110">Job</span></span>            |<span data-ttu-id="b755e-111">Description</span><span class="sxs-lookup"><span data-stu-id="b755e-111">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="b755e-112">La commande et le script s’exécutent sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b755e-112">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="b755e-113">Commande et script exécutés dans un processus distinct sur l’environnement local</span><span class="sxs-lookup"><span data-stu-id="b755e-113">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="b755e-114">ordinateur virtuel.</span><span class="sxs-lookup"><span data-stu-id="b755e-114">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="b755e-115">La commande et le script s’exécutent dans un thread distinct au sein du même</span><span class="sxs-lookup"><span data-stu-id="b755e-115">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="b755e-116">processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b755e-116">process on the local machine.</span></span>                                |

<span data-ttu-id="b755e-117">Chaque type de tâche présente des avantages et des inconvénients.</span><span class="sxs-lookup"><span data-stu-id="b755e-117">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="b755e-118">L’exécution d’un script à distance sur un ordinateur distinct ou dans un processus distinct a une grande isolation.</span><span class="sxs-lookup"><span data-stu-id="b755e-118">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="b755e-119">Les erreurs n’affectent pas les travaux en cours d’exécution ou le client qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-119">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="b755e-120">Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b755e-120">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="b755e-121">Tous les objets passés à et à partir de la session distante doivent être sérialisés puis désérialisés lorsqu’ils sont transmis entre le client et la session cible.</span><span class="sxs-lookup"><span data-stu-id="b755e-121">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="b755e-122">L’opération de sérialisation peut utiliser de nombreuses ressources de calcul et de mémoire pour les objets de données complexes de grande taille.</span><span class="sxs-lookup"><span data-stu-id="b755e-122">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

<span data-ttu-id="b755e-123">Cette rubrique explique comment exécuter des tâches en arrière-plan dans PowerShell sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b755e-123">This topic explains how to run background jobs in PowerShell on a local computer.</span></span> <span data-ttu-id="b755e-124">Pour plus d’informations sur l’exécution de tâches en arrière-plan sur des ordinateurs distants, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="b755e-124">For information about running background jobs on remote computers, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span> <span data-ttu-id="b755e-125">Pour plus d’informations sur les travaux de thread, consultez [about_Thread_Jobs](about_Thread_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="b755e-125">For more information about thread jobs, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="b755e-126">Lorsque vous démarrez une tâche en arrière-plan, l’invite de commandes est immédiatement retournée, même si le travail prend une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="b755e-126">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="b755e-127">Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b755e-127">You can continue to work in the session without interruption while the job runs.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="b755e-128">Applets de commande Job</span><span class="sxs-lookup"><span data-stu-id="b755e-128">The job cmdlets</span></span>

|<span data-ttu-id="b755e-129">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="b755e-129">Cmdlet</span></span>          |<span data-ttu-id="b755e-130">Description</span><span class="sxs-lookup"><span data-stu-id="b755e-130">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="b755e-131">Démarre une tâche en arrière-plan sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b755e-131">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="b755e-132">Obtient les tâches en arrière-plan qui ont été démarrées dans le</span><span class="sxs-lookup"><span data-stu-id="b755e-132">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="b755e-133">session active.</span><span class="sxs-lookup"><span data-stu-id="b755e-133">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="b755e-134">Obtient les résultats des tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-134">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="b755e-135">Arrête une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-135">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="b755e-136">Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches soient</span><span class="sxs-lookup"><span data-stu-id="b755e-136">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="b755e-137">Remplissez.</span><span class="sxs-lookup"><span data-stu-id="b755e-137">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="b755e-138">Supprime une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-138">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="b755e-139">Le paramètre **AsJob** crée une tâche en arrière-plan sur un</span><span class="sxs-lookup"><span data-stu-id="b755e-139">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="b755e-140">ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b755e-140">remote computer.</span></span> <span data-ttu-id="b755e-141">Vous pouvez utiliser `Invoke-Command` pour exécuter</span><span class="sxs-lookup"><span data-stu-id="b755e-141">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="b755e-142">toute commande Job à distance, y compris `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-142">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="b755e-143">Comment démarrer un travail sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="b755e-143">How to start a job on the local computer</span></span>

<span data-ttu-id="b755e-144">Pour démarrer une tâche en arrière-plan sur l’ordinateur local, utilisez l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-144">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="b755e-145">Pour écrire une `Start-Job` commande, mettez-la entre guillemets doubles ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="b755e-145">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="b755e-146">Utilisez le paramètre **scriptblock** pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="b755e-146">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="b755e-147">La commande suivante démarre une tâche en arrière-plan qui exécute une `Get-Process` commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b755e-147">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="b755e-148">La `Start-Job` commande retourne un objet qui représente le travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-148">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="b755e-149">L'objet de traitement retourné par Get-Job contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b755e-149">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="b755e-150">Enregistrez l’objet de traitement dans une variable, puis utilisez-le avec les autres applets de commande Job pour gérer la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-150">Save the job object in a variable, and then use it with the other Job cmdlets to manage the background job.</span></span> <span data-ttu-id="b755e-151">La commande suivante démarre un objet de traitement et enregistre l’objet de traitement résultant dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="b755e-151">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="b755e-152">À compter de PowerShell 6,0, vous pouvez utiliser un amersand ( `&` ) à la fin d’un pipeline pour démarrer un travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-152">Beginning in PowerShell 6.0, you can use an amersand (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="b755e-153">La commande suivante est fonctionnellement équivalente à la commande ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b755e-153">The following command is functionally equivalent to the command above.</span></span>

```powershell
$job = Get-Process &
```

<span data-ttu-id="b755e-154">La esperluette ( `&` ) est appelée opérateur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-154">The ampersand (`&`) is called the background operator.</span></span> <span data-ttu-id="b755e-155">Pour plus d’informations, consultez [opérateur d’arrière-plan](about_Operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="b755e-155">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="b755e-156">Vous pouvez également utiliser l' `Get-Job` applet de commande pour récupérer des objets qui représentent les travaux démarrés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b755e-156">You can also use the `Get-Job` cmdlet to get objects that represent the jobs started in the current session.</span></span> <span data-ttu-id="b755e-157">`Get-Job` retourne le même objet de traitement que celui `Start-Job` retourné par.</span><span class="sxs-lookup"><span data-stu-id="b755e-157">`Get-Job` returns the same job object that `Start-Job` returns.</span></span>

## <a name="getting-job-objects"></a><span data-ttu-id="b755e-158">Obtention d’objets de travail</span><span class="sxs-lookup"><span data-stu-id="b755e-158">Getting job objects</span></span>

<span data-ttu-id="b755e-159">Pour récupérer l’objet qui représente les tâches en arrière-plan démarrées dans la session active, utilisez l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-159">To get object that represent the background jobs that were started in the current session, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="b755e-160">Sans paramètres, `Get-Job` retourne toutes les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b755e-160">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

<span data-ttu-id="b755e-161">Par exemple, la commande suivante obtient les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="b755e-161">For example, the following command gets the jobs in the current session.</span></span>

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

<span data-ttu-id="b755e-162">Vous pouvez également enregistrer l’objet de traitement dans une variable et l’utiliser pour représenter la tâche dans une commande ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b755e-162">You can also save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="b755e-163">La commande suivante obtient la tâche avec l’ID 1 et l’enregistre dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="b755e-163">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

<span data-ttu-id="b755e-164">L’objet de traitement contient l’état du travail, qui indique si le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="b755e-164">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="b755e-165">L’état d’une tâche terminée est **terminé** ou **a échoué** .</span><span class="sxs-lookup"><span data-stu-id="b755e-165">A finished job has a state of **Complete** or **Failed** .</span></span> <span data-ttu-id="b755e-166">Un travail peut également être **bloqué** ou **en cours d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="b755e-166">A job might also be **blocked** or **running** .</span></span>

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="b755e-167">Obtention des résultats d’un travail</span><span class="sxs-lookup"><span data-stu-id="b755e-167">Getting the results of a job</span></span>

<span data-ttu-id="b755e-168">Lorsque vous exécutez un travail en arrière-plan, les résultats n’apparaissent pas immédiatement.</span><span class="sxs-lookup"><span data-stu-id="b755e-168">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="b755e-169">Au lieu de cela, l’applet de commande `Start-Job` retourne un objet de traitement qui représente le travail, mais il ne contient pas les résultats.</span><span class="sxs-lookup"><span data-stu-id="b755e-169">Instead, the `Start-Job` cmdlet returns a job object that represents the job, but it does not contain the results.</span></span> <span data-ttu-id="b755e-170">Pour obtenir les résultats d’une tâche en arrière-plan, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-170">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="b755e-171">La commande suivante utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-171">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="b755e-172">Elle utilise un objet de traitement enregistré dans la `$job` variable pour identifier la tâche.</span><span class="sxs-lookup"><span data-stu-id="b755e-172">It uses a job object saved in the `$job` variable to identify the job.</span></span>

```powershell
Receive-Job -Job $job
```

<span data-ttu-id="b755e-173">L' `Receive-Job` applet de commande retourne les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-173">The `Receive-Job` cmdlet returns the results of the job.</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

<span data-ttu-id="b755e-174">Vous pouvez également enregistrer les résultats d’un travail dans une variable.</span><span class="sxs-lookup"><span data-stu-id="b755e-174">You can also save the results of a job in a variable.</span></span> <span data-ttu-id="b755e-175">La commande suivante enregistre les résultats de la tâche dans la variable dans la variable `$job` `$results` .</span><span class="sxs-lookup"><span data-stu-id="b755e-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

<span data-ttu-id="b755e-176">De plus, vous pouvez enregistrer les résultats du travail dans un fichier à l’aide de l’opérateur de redirection ( `>` ) ou de l’applet de commande `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="b755e-176">And, you can save the results of the job in a file by using the redirection operator (`>`) or the `Out-File` cmdlet.</span></span> <span data-ttu-id="b755e-177">La commande suivante utilise l’opérateur de redirection pour enregistrer les résultats de la tâche dans la `$job` variable dans le `Results.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="b755e-177">The following command uses the redirection operator to save the results of the job in the `$job` variable in the `Results.txt` file.</span></span>

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="b755e-178">Obtention et conservation des résultats de travaux partiels</span><span class="sxs-lookup"><span data-stu-id="b755e-178">Getting and keeping partial job results</span></span>

<span data-ttu-id="b755e-179">L' `Receive-Job` applet de commande obtient les résultats d’une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-179">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="b755e-180">Si la tâche est terminée, `Receive-Job` obtient tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b755e-180">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="b755e-181">Si le travail est toujours en cours d’exécution, `Receive-Job` obtient les résultats générés jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="b755e-181">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="b755e-182">Vous pouvez réexécuter `Receive-Job` les commandes pour obtenir les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="b755e-182">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="b755e-183">Lorsque `Receive-Job` retourne les résultats, par défaut, il supprime les résultats du cache où les résultats du travail sont stockés.</span><span class="sxs-lookup"><span data-stu-id="b755e-183">When `Receive-Job` returns results, by default, it deletes those results from the cache where job results are stored.</span></span> <span data-ttu-id="b755e-184">Si vous exécutez une autre `Receive-Job` commande, vous recevez uniquement les résultats qui n’ont pas encore été reçus.</span><span class="sxs-lookup"><span data-stu-id="b755e-184">If you run another `Receive-Job` command, you get only the results that are not yet received.</span></span>

<span data-ttu-id="b755e-185">Les commandes suivantes affichent les résultats des `Receive-Job` commandes exécutées avant la fin du travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-185">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="b755e-186">Pour empêcher `Receive-Job` de supprimer les résultats du travail qu’il a renvoyés, utilisez le paramètre **Keep** .</span><span class="sxs-lookup"><span data-stu-id="b755e-186">To prevent `Receive-Job` from deleting the job results that it has returned, use the **Keep** parameter.</span></span> <span data-ttu-id="b755e-187">Par conséquent, `Receive-Job` retourne tous les résultats qui ont été générés jusqu’à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="b755e-187">As a result, `Receive-Job` returns all of the results that have been generated until that time.</span></span>

<span data-ttu-id="b755e-188">Les commandes suivantes montrent l’effet de l’utilisation du paramètre **Keep** sur un travail qui n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="b755e-188">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

## <a name="waiting-for-the-results"></a><span data-ttu-id="b755e-189">En attente des résultats</span><span class="sxs-lookup"><span data-stu-id="b755e-189">Waiting for the results</span></span>

<span data-ttu-id="b755e-190">Si vous exécutez une commande qui prend beaucoup de temps, vous pouvez utiliser les propriétés de l’objet de traitement pour déterminer à quel moment le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="b755e-190">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="b755e-191">La commande suivante utilise l' `Get-Job` objet pour récupérer toutes les tâches en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b755e-191">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="b755e-192">Les résultats s’affichent dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="b755e-192">The results appear in a table.</span></span> <span data-ttu-id="b755e-193">L’état de la tâche s’affiche dans la colonne **État** .</span><span class="sxs-lookup"><span data-stu-id="b755e-193">The status of the job appears in the **State** column.</span></span>

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="b755e-194">Dans ce cas, la propriété State indique que le travail 2 est toujours en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b755e-194">In this case, the State property reveals that Job 2 is still running.</span></span> <span data-ttu-id="b755e-195">Si vous deviez utiliser l' `Receive-Job` applet de commande pour obtenir les résultats du travail maintenant, les résultats seraient incomplets.</span><span class="sxs-lookup"><span data-stu-id="b755e-195">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="b755e-196">Vous pouvez utiliser l' `Receive-Job` applet de commande à plusieurs reprises pour obtenir tous les résultats.</span><span class="sxs-lookup"><span data-stu-id="b755e-196">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="b755e-197">Par défaut, chaque fois que vous l’utilisez, vous recevez uniquement les résultats qui n’ont pas encore été reçus, mais vous pouvez utiliser le paramètre **Keep** de l’applet de commande `Receive-Job` pour conserver les résultats, même s’ils ont déjà été reçus.</span><span class="sxs-lookup"><span data-stu-id="b755e-197">By default, each time you use it, you get only the results that were not already received, but you can use the **Keep** parameter of the `Receive-Job` cmdlet to retain the results, even though they were already received.</span></span>

<span data-ttu-id="b755e-198">Vous pouvez écrire les résultats partiels dans un fichier, puis ajouter les résultats les plus récents à mesure qu’ils arrivent, ou vous pouvez attendre et vérifier l’état du travail par la suite.</span><span class="sxs-lookup"><span data-stu-id="b755e-198">You can write the partial results to a file and then append newer results as they arrive or you can wait and check the state of the job later.</span></span>

<span data-ttu-id="b755e-199">Vous pouvez utiliser le paramètre **Wait** de l' `Receive-Job` applet de commande, qui ne retourne pas l’invite de commandes jusqu’à ce que le travail soit terminé et que tous les résultats soient disponibles.</span><span class="sxs-lookup"><span data-stu-id="b755e-199">You can use the **Wait** parameter of the `Receive-Job` cmdlet, which does not return the command prompt until the job is complete and all results are available.</span></span>

<span data-ttu-id="b755e-200">Vous pouvez également utiliser l' `Wait-Job` applet de commande pour attendre un ou plusieurs des résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="b755e-200">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="b755e-201">`Wait-Job` permet d’attendre une tâche particulière, pour tous les travaux, ou pour l’une des tâches à effectuer.</span><span class="sxs-lookup"><span data-stu-id="b755e-201">`Wait-Job` lets you wait for a particular job, for all jobs, or for any of the jobs to be completed.</span></span>

<span data-ttu-id="b755e-202">La commande suivante utilise l' `Wait-Job` applet de commande pour attendre un travail avec l' **ID**</span><span class="sxs-lookup"><span data-stu-id="b755e-202">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="b755e-203">Par conséquent, l’invite PowerShell est supprimée jusqu’à ce que la tâche soit terminée.</span><span class="sxs-lookup"><span data-stu-id="b755e-203">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="b755e-204">Vous pouvez également attendre une période prédéterminée.</span><span class="sxs-lookup"><span data-stu-id="b755e-204">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="b755e-205">Cette commande utilise le paramètre **timeout** pour limiter l’attente à 120 secondes.</span><span class="sxs-lookup"><span data-stu-id="b755e-205">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="b755e-206">Lorsque le délai expire, l’invite de commandes retourne, mais le travail continue à s’exécuter en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b755e-206">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="b755e-207">Arrêt d’un travail</span><span class="sxs-lookup"><span data-stu-id="b755e-207">Stopping a job</span></span>

<span data-ttu-id="b755e-208">Pour arrêter une tâche en arrière-plan, utilisez l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-208">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="b755e-209">La commande suivante démarre un travail pour obtenir chaque entrée dans le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="b755e-209">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="b755e-210">Elle enregistre l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="b755e-210">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="b755e-211">La commande suivante arrête le travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-211">The following command stops the job.</span></span> <span data-ttu-id="b755e-212">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer la tâche dans la `$job` variable à `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-212">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="b755e-213">Suppression d’un travail</span><span class="sxs-lookup"><span data-stu-id="b755e-213">Deleting a job</span></span>

<span data-ttu-id="b755e-214">Pour supprimer une tâche en arrière-plan, utilisez l’applet de commande `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="b755e-214">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="b755e-215">La commande suivante supprime la tâche dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="b755e-215">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="b755e-216">Examen d’un travail ayant échoué</span><span class="sxs-lookup"><span data-stu-id="b755e-216">Investigating a failed job</span></span>

<span data-ttu-id="b755e-217">Pour déterminer la raison de l’échec d’un travail, utilisez la propriété **reason** de l’objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="b755e-217">To find out why a job failed, use the **Reason** property of the job object.</span></span>

<span data-ttu-id="b755e-218">La commande suivante démarre un travail sans les informations d’identification requises.</span><span class="sxs-lookup"><span data-stu-id="b755e-218">The following command starts a job without the required credentials.</span></span> <span data-ttu-id="b755e-219">Elle enregistre l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="b755e-219">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="b755e-220">La commande suivante utilise la propriété Reason pour trouver l’erreur qui a provoqué l’échec du travail.</span><span class="sxs-lookup"><span data-stu-id="b755e-220">The following command uses the Reason property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="b755e-221">Dans ce cas, la tâche a échoué, car l’ordinateur distant nécessitait des informations d’identification explicites pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="b755e-221">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="b755e-222">La valeur de la propriété **reason** est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b755e-222">The value of the **Reason** property is:</span></span>

<span data-ttu-id="b755e-223">La connexion au serveur distant a échoué avec le message d’erreur suivant : « accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="b755e-223">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="b755e-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b755e-224">See also</span></span>

- [<span data-ttu-id="b755e-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="b755e-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="b755e-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="b755e-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="b755e-227">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="b755e-227">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="b755e-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="b755e-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="b755e-229">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b755e-229">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="b755e-230">Start-Job</span><span class="sxs-lookup"><span data-stu-id="b755e-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="b755e-231">Get-Job</span><span class="sxs-lookup"><span data-stu-id="b755e-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="b755e-232">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="b755e-232">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="b755e-233">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="b755e-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="b755e-234">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="b755e-234">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="b755e-235">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="b755e-235">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="b755e-236">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b755e-236">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
