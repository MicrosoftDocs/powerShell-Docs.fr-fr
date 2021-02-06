---
description: Décrit comment exécuter des travaux sur des ordinateurs distants.
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 93e1d3aba1f4037cc3c5c18386488bf321fc2a64
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595706"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="8a6d2-103">À propos des travaux distants</span><span class="sxs-lookup"><span data-stu-id="8a6d2-103">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="8a6d2-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="8a6d2-104">Short Description</span></span>
<span data-ttu-id="8a6d2-105">Décrit comment exécuter des tâches en arrière-plan sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-105">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="8a6d2-106">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="8a6d2-106">Detailed Description</span></span>

<span data-ttu-id="8a6d2-107">PowerShell exécute simultanément des commandes et des scripts par le biais de travaux.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-107">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="8a6d2-108">Il existe trois types de travaux fournis par PowerShell pour prendre en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-108">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="8a6d2-109">`RemoteJob` -Les commandes et les scripts s’exécutent dans une session à distance.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-109">`RemoteJob` - Commands and scripts run in a remote session.</span></span>
- <span data-ttu-id="8a6d2-110">`BackgroundJob` -Les commandes et les scripts s’exécutent dans un processus distinct sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-110">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="8a6d2-111">Pour plus d’informations, consultez [à propos des_tâches](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-111">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="8a6d2-112">`PSTaskJob` ou `ThreadJob` -les commandes et les scripts s’exécutent dans un thread distinct au sein du même processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-112">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="8a6d2-113">Pour plus d’informations, consultez [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-113">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="8a6d2-114">L’exécution de scripts à distance, sur un ordinateur distinct ou dans un processus distinct, offre une grande isolation.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-114">Running scripts remotely, on a separate machine or in a separate process, provide great isolation.</span></span> <span data-ttu-id="8a6d2-115">Toutes les erreurs qui se produisent dans le travail distant n’affectent pas les autres travaux en cours d’exécution ou la session parente qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-115">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="8a6d2-116">Toutefois, la couche de communication à distance ajoute de la surcharge, y compris la sérialisation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-116">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="8a6d2-117">Tous les objets sont sérialisés et désérialisés lorsqu’ils sont transmis entre la session parente et la session distante (travail).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-117">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="8a6d2-118">La sérialisation d’objets de données complexes volumineux peut consommer de grandes quantités de ressources de calcul et de mémoire et transférer de grandes quantités de données sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-118">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a6d2-119">La session parente qui a créé le travail surveille également l’état du travail et collecte des données de pipeline.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-119">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="8a6d2-120">Le processus enfant du travail est terminé par le processus parent une fois que le travail atteint un état terminé.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-120">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="8a6d2-121">Si la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-121">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="8a6d2-122">Il existe deux façons de contourner cette situation :</span><span class="sxs-lookup"><span data-stu-id="8a6d2-122">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="8a6d2-123">Utilisez `Invoke-Command` pour créer des travaux qui s’exécutent dans des sessions déconnectées.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-123">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="8a6d2-124">Consultez la section [processus détachés](#how-to-run-as-a-detached-process) de cet article.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-124">See the [detached processes](#how-to-run-as-a-detached-process) section of this article.</span></span>
1. <span data-ttu-id="8a6d2-125">Utilisez `Start-Process` pour créer un nouveau processus plutôt qu’un travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-125">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="8a6d2-126">Pour plus d’informations, consultez [start-process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-126">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="remote-jobs"></a><span data-ttu-id="8a6d2-127">Travaux distants</span><span class="sxs-lookup"><span data-stu-id="8a6d2-127">Remote Jobs</span></span>

<span data-ttu-id="8a6d2-128">Vous pouvez exécuter des travaux sur des ordinateurs distants à l’aide de trois méthodes différentes.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-128">You can run jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="8a6d2-129">Démarrer une session interactive sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-129">Start an interactive session on a remote computer.</span></span> <span data-ttu-id="8a6d2-130">Démarrez ensuite un travail dans la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-130">Then start a job in the interactive session.</span></span> <span data-ttu-id="8a6d2-131">Les procédures sont les mêmes que l’exécution d’un travail local, bien que toutes les actions soient effectuées sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-131">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="8a6d2-132">Exécuter une tâche sur un ordinateur distant qui retourne ses résultats à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-132">Run a job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="8a6d2-133">Utilisez cette méthode lorsque vous souhaitez collecter les résultats des travaux et les conserver dans un emplacement central sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-133">Use this method when you want to collect the results of jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="8a6d2-134">Exécutez un travail sur un ordinateur distant qui conserve ses résultats sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-134">Run a job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="8a6d2-135">Utilisez cette méthode lorsque les données du travail sont conservées de manière plus sécurisée sur l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-135">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-job-in-an-interactive-session"></a><span data-ttu-id="8a6d2-136">Démarrer un travail dans une session interactive</span><span class="sxs-lookup"><span data-stu-id="8a6d2-136">Start a job in an interactive session</span></span>

<span data-ttu-id="8a6d2-137">Vous pouvez démarrer une session interactive avec un ordinateur distant, puis démarrer un travail pendant la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-137">You can start an interactive session with a remote computer and then start a job during the interactive session.</span></span> <span data-ttu-id="8a6d2-138">Pour plus d’informations sur les sessions interactives, consultez about_Remote et `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="8a6d2-138">For more information about interactive sessions, see about_Remote, and see `Enter-PSSession`.</span></span>

<span data-ttu-id="8a6d2-139">La procédure de démarrage d’un travail dans une session interactive est presque identique à la procédure de démarrage d’une tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-139">The procedure for starting a job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="8a6d2-140">Toutefois, toutes les opérations se produisent sur l’ordinateur distant, et non sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-140">However, all of the operations occur on the remote computer, not the local computer.</span></span>

1. <span data-ttu-id="8a6d2-141">Utilisez l' `Enter-PSSession` applet de commande pour démarrer une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-141">Use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="8a6d2-142">Vous pouvez utiliser le paramètre ComputerName de `Enter-PSSession` pour établir une connexion temporaire pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-142">You can use the ComputerName parameter of `Enter-PSSession` to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="8a6d2-143">Vous pouvez utiliser le paramètre session pour exécuter la session interactive dans une session PowerShell (PSSession).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-143">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

   <span data-ttu-id="8a6d2-144">La commande suivante démarre une session interactive sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-144">The following command starts an interactive session on the Server01 computer.</span></span>

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   <span data-ttu-id="8a6d2-145">L’invite de commandes change pour indiquer que vous êtes maintenant connecté à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-145">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

   ```
   Server01\C:>
   ```

1. <span data-ttu-id="8a6d2-146">Pour démarrer un travail distant dans la session, utilisez l' `Start-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-146">To start a remote job in the session, use the `Start-Job` cmdlet.</span></span> <span data-ttu-id="8a6d2-147">La commande suivante exécute une tâche distante qui obtient les événements dans le journal des événements Windows PowerShell sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-147">The following command runs a remote job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="8a6d2-148">L' `Start-Job` applet de commande retourne un objet qui représente la tâche.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-148">The `Start-Job` cmdlet returns an object that represents the job.</span></span>

   <span data-ttu-id="8a6d2-149">Cette commande enregistre l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-149">This command saves the job object in the `$job` variable.</span></span>

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   <span data-ttu-id="8a6d2-150">Pendant l’exécution de la tâche, vous pouvez utiliser la session interactive pour exécuter d’autres commandes, y compris d’autres travaux.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-150">While the job runs, you can use the interactive session to run other commands, including other jobs.</span></span> <span data-ttu-id="8a6d2-151">Toutefois, vous devez garder la session interactive ouverte jusqu’à ce que la tâche soit terminée.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-151">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="8a6d2-152">Si vous mettez fin à la session, le travail est interrompu et les résultats sont perdus.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-152">If you end the session, the job is interrupted, and the results are lost.</span></span>

1. <span data-ttu-id="8a6d2-153">Pour déterminer si la tâche est terminée, affichez la valeur de la `$job` variable ou utilisez l' `Get-Job` applet de commande pour obtenir la tâche.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-153">To find out if the job is complete, display the value of the `$job` variable, or use the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="8a6d2-154">La commande suivante utilise l' `Get-Job` applet de commande pour afficher le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-154">The following command uses the `Get-Job` cmdlet to display the job.</span></span>

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   <span data-ttu-id="8a6d2-155">La `Get-Job` sortie indique que la tâche est en cours d’exécution sur l’ordinateur « localhost », car le travail a démarré sur le même ordinateur (dans le cas présent, SERVEUR01).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-155">The `Get-Job` output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

1. <span data-ttu-id="8a6d2-156">Pour obtenir les résultats du travail, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="8a6d2-156">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="8a6d2-157">Vous pouvez afficher les résultats dans la session interactive ou les enregistrer dans un fichier sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-157">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="8a6d2-158">La commande suivante obtient les résultats du travail dans la variable $job.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-158">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="8a6d2-159">La commande utilise l’opérateur de redirection ( `>` ) pour enregistrer les résultats de la tâche dans le fichier PsLog.txt sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-159">The command uses the redirection operator (`>`) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. <span data-ttu-id="8a6d2-160">Pour mettre fin à la session interactive, utilisez l’applet de commande `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="8a6d2-160">To end the interactive session, use the `Exit-PSSession` cmdlet.</span></span> <span data-ttu-id="8a6d2-161">L’invite de commandes change pour indiquer que vous êtes à nouveau dans la session d’origine sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-161">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. <span data-ttu-id="8a6d2-162">Pour afficher le contenu du `PsLog.txt` fichier sur l’ordinateur SERVEUR01 à tout moment, démarrez une autre session interactive ou exécutez une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-162">To view the contents of the `PsLog.txt` file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="8a6d2-163">Ce type de commande est mieux exécuté dans une session PSSession (connexion persistante) au cas où vous souhaiteriez utiliser plusieurs commandes pour examiner et gérer les données dans le `PsLog.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-163">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the `PsLog.txt` file.</span></span> <span data-ttu-id="8a6d2-164">Pour plus d’informations sur sessions PSSession, consultez [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-164">For more information about PSSessions, see [about_PSSessions](about_PSSessions.md).</span></span>

   <span data-ttu-id="8a6d2-165">Les commandes suivantes utilisent l' `New-PSSession` applet de commande pour créer une **session PSSession** qui est connectée à l’ordinateur Serveur01, et elles utilisent l' `Invoke-Command` applet de commande pour exécuter une `Get-Content` commande dans la session PSSession afin d’afficher le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-165">The following commands use the `New-PSSession` cmdlet to create a **PSSession** that is connected to the Server01 computer, and they use the `Invoke-Command` cmdlet to run a `Get-Content` command in the PSSession to view the contents of the file.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="8a6d2-166">Démarrer une tâche distante qui retourne les résultats à l’ordinateur local (AsJob)</span><span class="sxs-lookup"><span data-stu-id="8a6d2-166">Start a remote job that returns the results to the local computer (AsJob)</span></span>

<span data-ttu-id="8a6d2-167">Pour démarrer un travail sur un ordinateur distant qui retourne les résultats de la commande à l’ordinateur local, utilisez le paramètre **AsJob** d’une applet de commande, telle que l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="8a6d2-167">To start a job on a remote computer that returns the command results to the local computer, use the **AsJob** parameter of a cmdlet such as the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="8a6d2-168">Quand vous utilisez le paramètre **AsJob** , l’objet de traitement est réellement créé sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-168">When you use the **AsJob** parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="8a6d2-169">Une fois le travail terminé, les résultats sont retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-169">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="8a6d2-170">Vous pouvez utiliser les applets de commande qui contiennent le nom du travail (les applets de commande Job) pour gérer n’importe quel travail créé par une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-170">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="8a6d2-171">La plupart des applets de commande qui ont des paramètres **AsJob** n’utilisent pas la communication à distance PowerShell. vous pouvez donc les utiliser même sur des ordinateurs qui ne sont pas configurés pour la communication à distance et qui ne satisfont pas à la configuration requise pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-171">Many of the cmdlets that have **AsJob** parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

1. <span data-ttu-id="8a6d2-172">La commande suivante utilise le paramètre **AsJob** de `Invoke-Command` pour démarrer un travail sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-172">The following command uses the **AsJob** parameter of `Invoke-Command` to start a job on the Server01 computer.</span></span> <span data-ttu-id="8a6d2-173">La tâche exécute une `Get-Eventlog` commande qui obtient les événements dans le journal système.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-173">The job runs a `Get-Eventlog` command that gets the events in the System log.</span></span> <span data-ttu-id="8a6d2-174">Vous pouvez utiliser le paramètre JobName pour attribuer un nom complet à la tâche.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-174">You can use the JobName parameter to assign a display name to the job.</span></span>

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   <span data-ttu-id="8a6d2-175">Les résultats de la commande ressemblent à l’exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-175">The results of the command resemble the following sample output.</span></span>

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   <span data-ttu-id="8a6d2-176">Lorsque le paramètre **AsJob** est utilisé, `Invoke-Command` retourne le même type d’objet de traitement que celui `Start-Job` retourné par.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-176">When the **AsJob** parameter is used, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="8a6d2-177">Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une `Get-Job` commande pour obtenir le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-177">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="8a6d2-178">Notez que la valeur de la propriété Location indique que la tâche a été exécutée sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-178">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

1. <span data-ttu-id="8a6d2-179">Pour gérer un travail démarré à l’aide du paramètre **AsJob** de l’applet de commande `Invoke-Command` , utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-179">To manage a job started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="8a6d2-180">Étant donné que l’objet de traitement qui représente le travail distant se trouve sur l’ordinateur local, vous n’avez pas besoin d’exécuter des commandes à distance pour gérer le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-180">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

   <span data-ttu-id="8a6d2-181">Pour déterminer si le travail est terminé, utilisez une `Get-Job` commande.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-181">To determine whether the job is complete, use a `Get-Job` command.</span></span> <span data-ttu-id="8a6d2-182">La commande suivante obtient toutes les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-182">The following command gets all of the jobs that were started in the current session.</span></span>

   ```powershell
   Get-Job
   ```

   <span data-ttu-id="8a6d2-183">Étant donné que la tâche à distance a été démarrée dans la session active, une `Get-Job` commande locale obtient la tâche.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-183">Because the remote job was started in the current session, a local `Get-Job` command gets the job.</span></span> <span data-ttu-id="8a6d2-184">La propriété State de l’objet de traitement indique que la commande a été correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-184">The State property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. <span data-ttu-id="8a6d2-185">Pour obtenir les résultats du travail, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="8a6d2-185">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="8a6d2-186">Étant donné que les résultats du travail sont automatiquement retournés à l’ordinateur sur lequel se trouve l’objet de traitement, vous pouvez obtenir les résultats avec une `Receive-Job` commande locale.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-186">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local `Receive-Job` command.</span></span>

   <span data-ttu-id="8a6d2-187">La commande suivante utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-187">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="8a6d2-188">Elle utilise l’ID de session pour identifier le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-188">It uses the session ID to identify the job.</span></span> <span data-ttu-id="8a6d2-189">Cette commande enregistre les résultats de la tâche dans la variable $results.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-189">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="8a6d2-190">Vous pouvez également rediriger les résultats vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-190">You can also redirect the results to a file.</span></span>

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="8a6d2-191">Démarrer un travail distant qui conserve les résultats sur l’ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="8a6d2-191">Start a remote job that keeps the results on the remote computer</span></span>

<span data-ttu-id="8a6d2-192">Pour démarrer un travail sur un ordinateur distant qui conserve les résultats de la commande sur l’ordinateur distant, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-192">To start a job on a remote computer that keeps the command results on the remote computer, use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="8a6d2-193">Vous pouvez utiliser cette méthode pour exécuter des travaux sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-193">You can use this method to run jobs on multiple computers.</span></span>

<span data-ttu-id="8a6d2-194">Lorsque vous exécutez une `Start-Job` commande à distance, l’objet de traitement est créé sur l’ordinateur distant et les résultats de la tâche sont conservés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-194">When you run a `Start-Job` command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="8a6d2-195">Du point de vue du travail, toutes les opérations sont locales.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-195">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="8a6d2-196">Vous exécutez simplement des commandes à distance pour gérer un travail local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-196">You are just running commands remotely to manage a local job on the remote computer.</span></span>

1. <span data-ttu-id="8a6d2-197">Utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-197">Use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span>

   <span data-ttu-id="8a6d2-198">Cette commande requiert une session PSSession (connexion persistante).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-198">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="8a6d2-199">Si vous utilisez le paramètre ComputerName de `Invoke-Command` pour établir une connexion temporaire, la `Invoke-Command` commande est considérée comme terminée lorsque l’objet de traitement est retourné.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-199">If you use the ComputerName parameter of `Invoke-Command` to establish a temporary connection, the `Invoke-Command` command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="8a6d2-200">Par conséquent, la connexion temporaire est fermée et le travail est annulé.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-200">As a result, the temporary connection is closed, and the job is canceled.</span></span>

   <span data-ttu-id="8a6d2-201">La commande suivante utilise l' `New-PSSession` applet de commande pour créer une session PSSession qui est connectée à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-201">The following command uses the `New-PSSession` cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="8a6d2-202">La commande enregistre la session PSSession dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-202">The command saves the PSSession in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   <span data-ttu-id="8a6d2-203">La commande suivante utilise l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-203">The next command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the PSSession.</span></span> <span data-ttu-id="8a6d2-204">La `Start-Job` commande et la `Get-Eventlog` commande sont placées entre accolades.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-204">The `Start-Job` command and the `Get-Eventlog` command are enclosed in braces.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   <span data-ttu-id="8a6d2-205">Les résultats ressemblent à l’exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-205">The results resemble the following sample output.</span></span>

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   <span data-ttu-id="8a6d2-206">Lorsque vous exécutez une `Start-Job` commande à distance, `Invoke-Command` retourne le même type d’objet de traitement que celui `Start-Job` retourné par.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-206">When you run a `Start-Job` command remotely, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="8a6d2-207">Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une `Get-Job` commande pour obtenir le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-207">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="8a6d2-208">Notez que la valeur de la propriété **location** indique que la tâche a été exécutée sur l’ordinateur local, appelée « localhost », même si la tâche a été exécutée sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-208">Note that the value of the **Location** property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="8a6d2-209">Étant donné que l’objet de traitement est créé sur l’ordinateur SERVEUR01 et que la tâche s’exécute sur le même ordinateur, il est considéré comme une tâche en arrière-plan locale.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-209">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

1. <span data-ttu-id="8a6d2-210">Pour gérer un travail distant, utilisez les applets de commande **Job** .</span><span class="sxs-lookup"><span data-stu-id="8a6d2-210">To manage a remote job, use the **Job** cmdlets.</span></span> <span data-ttu-id="8a6d2-211">Étant donné que l’objet de traitement se trouve sur l’ordinateur distant, vous devez exécuter des commandes à distance pour obtenir, arrêter, attendre ou récupérer les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-211">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

   <span data-ttu-id="8a6d2-212">Pour voir si le travail est terminé, utilisez une `Invoke-Command` commande pour exécuter une `Get-Job` commande dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-212">To see if the job is complete, use an `Invoke-Command` command to run a `Get-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   <span data-ttu-id="8a6d2-213">La commande retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-213">The command returns a job object.</span></span> <span data-ttu-id="8a6d2-214">La propriété **State** de l’objet de traitement indique que la commande a été correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-214">The **State** property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. <span data-ttu-id="8a6d2-215">Pour obtenir les résultats du travail, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-215">To get the results of the job, use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   <span data-ttu-id="8a6d2-216">La commande suivante utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-216">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="8a6d2-217">Elle utilise l’ID de session pour identifier le travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-217">It uses the session ID to identify the job.</span></span> <span data-ttu-id="8a6d2-218">Cette commande enregistre les résultats de la tâche dans la `$results` variable.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-218">This command saves the job results in the `$results` variable.</span></span> <span data-ttu-id="8a6d2-219">Elle utilise le paramètre Keep de `Receive-Job` pour conserver le résultat dans le cache de travaux sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-219">It uses the Keep parameter of `Receive-Job` to keep the result in the job cache on the remote computer.</span></span>

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   <span data-ttu-id="8a6d2-220">Vous pouvez également rediriger les résultats vers un fichier sur l’ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-220">You can also redirect the results to a file on the local or remote computer.</span></span>
   <span data-ttu-id="8a6d2-221">La commande suivante utilise un opérateur de redirection pour enregistrer les résultats dans un fichier sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-221">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a><span data-ttu-id="8a6d2-222">Comment exécuter en tant que processus détaché</span><span class="sxs-lookup"><span data-stu-id="8a6d2-222">How to run as a detached process</span></span>

<span data-ttu-id="8a6d2-223">Comme mentionné précédemment, lorsque la session parente est terminée, toutes les tâches enfants en cours d’exécution sont terminées en même temps que leurs processus enfants.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-223">As previously mentioned, when the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span> <span data-ttu-id="8a6d2-224">Vous pouvez utiliser la communication à distance sur l’ordinateur local pour exécuter des tâches qui ne sont pas attachées à la session PowerShell en cours.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-224">You can use remoting on the local machine to run jobs that are not attached to the current PowerShell session.</span></span>

<span data-ttu-id="8a6d2-225">Créez une nouvelle session PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-225">Create a new PowerShell session on the local machine.</span></span> <span data-ttu-id="8a6d2-226">Utilisé `Invoke-Command` pour démarrer un travail dans cette session.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-226">The use `Invoke-Command` to start a job in this session.</span></span> <span data-ttu-id="8a6d2-227">`Invoke-Command` vous permet de déconnecter une session à distance et de mettre fin à la session parente.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-227">`Invoke-Command` allows you to disconnect a remote session and terminate the parent session.</span></span> <span data-ttu-id="8a6d2-228">Plus tard, vous pouvez démarrer une nouvelle session PowerShell et vous connecter à la session précédemment déconnectée pour reprendre la surveillance du travail.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-228">Later, you can start a new PowerShell session and connect to the previously disconnected session to resume monitoring the job.</span></span> <span data-ttu-id="8a6d2-229">Toutefois, toutes les données qui ont été retournées à la session PowerShell d’origine sont perdues lorsque cette session est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-229">However, any data that was returned to the original PowerShell session is lost when that session is terminated.</span></span> <span data-ttu-id="8a6d2-230">Seuls les nouveaux objets de données générés après la déconnexion sont retournés lors de la reconnexion.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-230">Only new data objects generated after the disconnect are returned when re-connected.</span></span>

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

<span data-ttu-id="8a6d2-231">Pour cet exemple, les travaux sont toujours attachés à une session PowerShell parente.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-231">For this example, the jobs are still attached to a parent PowerShell session.</span></span>
<span data-ttu-id="8a6d2-232">Toutefois, la session parente n’est pas la session PowerShell d’origine où `Invoke-Command` a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-232">However, the parent session is not the original PowerShell session where `Invoke-Command` was run.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a6d2-233">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a6d2-233">See also</span></span>

- [<span data-ttu-id="8a6d2-234">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="8a6d2-234">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="8a6d2-235">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="8a6d2-235">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="8a6d2-236">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8a6d2-236">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="8a6d2-237">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="8a6d2-237">about_Remote_Variables</span></span>](about_Remote_Variables.md)
- [<span data-ttu-id="8a6d2-238">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8a6d2-238">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="8a6d2-239">Start-Job</span><span class="sxs-lookup"><span data-stu-id="8a6d2-239">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="8a6d2-240">Get-Job</span><span class="sxs-lookup"><span data-stu-id="8a6d2-240">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="8a6d2-241">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="8a6d2-241">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="8a6d2-242">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="8a6d2-242">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="8a6d2-243">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="8a6d2-243">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="8a6d2-244">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8a6d2-244">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="8a6d2-245">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="8a6d2-245">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="8a6d2-246">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="8a6d2-246">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)