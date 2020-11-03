---
description: Décrit comment exécuter des tâches en arrière-plan sur des ordinateurs distants.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: fb2270ea5c0acdcf2c506e687787d22c73e2cb2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207730"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="8ec90-104">À propos des travaux distants</span><span class="sxs-lookup"><span data-stu-id="8ec90-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="8ec90-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="8ec90-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8ec90-106">Décrit comment exécuter des tâches en arrière-plan sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="8ec90-106">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="8ec90-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="8ec90-107">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="8ec90-108">Une tâche en arrière-plan est une commande qui s’exécute de façon asynchrone sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="8ec90-108">A background job is a command that runs asynchronously without interacting with the current session.</span></span> <span data-ttu-id="8ec90-109">L’invite de commandes s’affiche immédiatement et vous pouvez continuer à utiliser la session pendant l’exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ec90-109">The command prompt returns immediately, and you can continue to use the session while the job runs.</span></span>

<span data-ttu-id="8ec90-110">Par défaut, les travaux en arrière-plan s’exécutent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-110">By default, background jobs run on the local computer.</span></span> <span data-ttu-id="8ec90-111">Toutefois, vous pouvez utiliser différentes procédures pour exécuter des tâches en arrière-plan sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="8ec90-111">However, you can use several different procedures to run background jobs on remote computers.</span></span>

<span data-ttu-id="8ec90-112">Cette rubrique explique comment exécuter une tâche en arrière-plan sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-112">This topic explains how to run a background job on a remote computer.</span></span> <span data-ttu-id="8ec90-113">Pour plus d’informations sur la façon d’exécuter des tâches en arrière-plan sur un ordinateur local, consultez [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8ec90-113">For information about how to run background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span> <span data-ttu-id="8ec90-114">Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Job_Details](about_Job_Details.md).</span><span class="sxs-lookup"><span data-stu-id="8ec90-114">For more information about background jobs, see [about_Job_Details](about_Job_Details.md).</span></span>

## <a name="remote-background-jobs"></a><span data-ttu-id="8ec90-115">TRAVAUX EN ARRIÈRE-PLAN DISTANTS</span><span class="sxs-lookup"><span data-stu-id="8ec90-115">REMOTE BACKGROUND JOBS</span></span>

<span data-ttu-id="8ec90-116">Vous pouvez exécuter des tâches en arrière-plan sur des ordinateurs distants à l’aide de trois méthodes différentes.</span><span class="sxs-lookup"><span data-stu-id="8ec90-116">You can run background jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="8ec90-117">Démarrer une session interactive avec un ordinateur distant et démarrer un travail dans la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8ec90-117">Start an interactive session with a remote computer, and start a job in the interactive session.</span></span> <span data-ttu-id="8ec90-118">Les procédures sont les mêmes que l’exécution d’un travail local, bien que toutes les actions soient effectuées sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-118">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="8ec90-119">Exécuter une tâche en arrière-plan sur un ordinateur distant qui retourne ses résultats à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-119">Run a background job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="8ec90-120">Utilisez cette méthode lorsque vous souhaitez collecter les résultats des tâches en arrière-plan et les conserver dans un emplacement central sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-120">Use this method when you want to collect the results of background jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="8ec90-121">Exécuter une tâche en arrière-plan sur un ordinateur distant qui conserve ses résultats sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-121">Run a background job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="8ec90-122">Utilisez cette méthode lorsque les données du travail sont conservées de manière plus sécurisée sur l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="8ec90-122">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-background-job-in-an-interactive-session"></a><span data-ttu-id="8ec90-123">DÉMARRER UNE TÂCHE EN ARRIÈRE-PLAN DANS UNE SESSION INTERACTIVE</span><span class="sxs-lookup"><span data-stu-id="8ec90-123">START A BACKGROUND JOB IN AN INTERACTIVE SESSION</span></span>

<span data-ttu-id="8ec90-124">Vous pouvez démarrer une session interactive avec un ordinateur distant, puis démarrer un travail en arrière-plan pendant la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8ec90-124">You can start an interactive session with a remote computer and then start a background job during the interactive session.</span></span> <span data-ttu-id="8ec90-125">Pour plus d’informations sur les sessions interactives, consultez about_Remote, et consultez Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="8ec90-125">For more information about interactive sessions, see about_Remote, and see Enter-PSSession.</span></span>

<span data-ttu-id="8ec90-126">La procédure de démarrage d’une tâche en arrière-plan dans une session interactive est presque identique à la procédure de démarrage d’une tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-126">The procedure for starting a background job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="8ec90-127">Toutefois, toutes les opérations se produisent sur l’ordinateur distant, et non sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-127">However, all of the operations occur on the remote computer, not the local computer.</span></span>

#### <a name="step-1-enter-pssession"></a><span data-ttu-id="8ec90-128">ÉTAPE 1 : ENTER-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="8ec90-128">STEP 1: ENTER-PSSESSION</span></span>

<span data-ttu-id="8ec90-129">Utilisez l’applet de commande Enter-PSSession pour démarrer une session interactive avec un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-129">Use the Enter-PSSession cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="8ec90-130">Vous pouvez utiliser le paramètre ComputerName de Enter-PSSession pour établir une connexion temporaire pour la session interactive.</span><span class="sxs-lookup"><span data-stu-id="8ec90-130">You can use the ComputerName parameter of Enter-PSSession to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="8ec90-131">Vous pouvez utiliser le paramètre session pour exécuter la session interactive dans une session PowerShell (PSSession).</span><span class="sxs-lookup"><span data-stu-id="8ec90-131">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

<span data-ttu-id="8ec90-132">La commande suivante démarre une session interactive sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-132">The following command starts an interactive session on the Server01 computer.</span></span>

```powershell
C:\PS> Enter-PSSession -computername Server01
```

<span data-ttu-id="8ec90-133">L’invite de commandes change pour indiquer que vous êtes maintenant connecté à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-133">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

```
Server01\C:>
```

#### <a name="step-2-start-job"></a><span data-ttu-id="8ec90-134">ÉTAPE 2 : START-JOB</span><span class="sxs-lookup"><span data-stu-id="8ec90-134">STEP 2: START-JOB</span></span>

<span data-ttu-id="8ec90-135">Pour démarrer une tâche en arrière-plan dans la session, utilisez l’applet de commande Start-Job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-135">To start a background job in the session, use the Start-Job cmdlet.</span></span>

<span data-ttu-id="8ec90-136">La commande suivante exécute une tâche en arrière-plan qui obtient les événements dans le journal des événements Windows PowerShell sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-136">The following command runs a background job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="8ec90-137">L’applet de commande Start-Job retourne un objet qui représente la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ec90-137">The Start-Job cmdlet returns an object that represents the job.</span></span>

<span data-ttu-id="8ec90-138">Cette commande enregistre l’objet de traitement dans la \$ variable de travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-138">This command saves the job object in the \$job variable.</span></span>

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

<span data-ttu-id="8ec90-139">Pendant l’exécution de la tâche, vous pouvez utiliser la session interactive pour exécuter d’autres commandes, y compris d’autres travaux en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="8ec90-139">While the job runs, you can use the interactive session to run other commands, including other background jobs.</span></span> <span data-ttu-id="8ec90-140">Toutefois, vous devez garder la session interactive ouverte jusqu’à ce que la tâche soit terminée.</span><span class="sxs-lookup"><span data-stu-id="8ec90-140">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="8ec90-141">Si vous mettez fin à la session, le travail est interrompu et les résultats sont perdus.</span><span class="sxs-lookup"><span data-stu-id="8ec90-141">If you end the session, the job is interrupted, and the results are lost.</span></span>

#### <a name="step-3-get-job"></a><span data-ttu-id="8ec90-142">ÉTAPE 3 : OBTENIR LE TRAVAIL</span><span class="sxs-lookup"><span data-stu-id="8ec90-142">STEP 3: GET-JOB</span></span>

<span data-ttu-id="8ec90-143">Pour déterminer si la tâche est terminée, affichez la valeur de la \$ variable de tâche ou utilisez l’applet de commande Get-Job pour obtenir la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ec90-143">To find out if the job is complete, display the value of the \$job variable, or use the Get-Job cmdlet to get the job.</span></span> <span data-ttu-id="8ec90-144">La commande suivante utilise l’applet de commande Get-Job pour afficher le travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-144">The following command uses the Get-Job cmdlet to display the job.</span></span>

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

<span data-ttu-id="8ec90-145">La sortie de Get-Job indique que le travail est en cours d’exécution sur l’ordinateur « localhost », car le travail a démarré sur et s’exécute sur le même ordinateur (dans ce cas, SERVEUR01).</span><span class="sxs-lookup"><span data-stu-id="8ec90-145">The Get-Job output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

#### <a name="step-4-receive-job"></a><span data-ttu-id="8ec90-146">ÉTAPE 4 : RÉCEPTION-TRAVAIL</span><span class="sxs-lookup"><span data-stu-id="8ec90-146">STEP 4: RECEIVE-JOB</span></span>

<span data-ttu-id="8ec90-147">Pour obtenir les résultats du travail, utilisez l’applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-147">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="8ec90-148">Vous pouvez afficher les résultats dans la session interactive ou les enregistrer dans un fichier sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-148">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="8ec90-149">La commande suivante obtient les résultats du travail dans la variable $job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-149">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="8ec90-150">La commande utilise l’opérateur de redirection (>) pour enregistrer les résultats de la tâche dans le fichier PsLog.txt sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-150">The command uses the redirection operator (>) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a><span data-ttu-id="8ec90-151">ÉTAPE 5 : QUITTER-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="8ec90-151">STEP 5: EXIT-PSSESSION</span></span>

<span data-ttu-id="8ec90-152">Pour mettre fin à la session interactive, utilisez l’applet de commande Exit-PSSession.</span><span class="sxs-lookup"><span data-stu-id="8ec90-152">To end the interactive session, use the Exit-PSSession cmdlet.</span></span> <span data-ttu-id="8ec90-153">L’invite de commandes change pour indiquer que vous êtes à nouveau dans la session d’origine sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-153">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a><span data-ttu-id="8ec90-154">ÉTAPE 6 : INVOKE-COMMAND : OBTENIR-CONTENT</span><span class="sxs-lookup"><span data-stu-id="8ec90-154">STEP 6: INVOKE-COMMAND: GET-CONTENT</span></span>

<span data-ttu-id="8ec90-155">Pour afficher le contenu du fichier PsLog.txt sur l’ordinateur SERVEUR01 à tout moment, démarrez une autre session interactive ou exécutez une commande à distance.</span><span class="sxs-lookup"><span data-stu-id="8ec90-155">To view the contents of the PsLog.txt file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="8ec90-156">Ce type de commande est mieux exécuté dans une session PSSession (connexion persistante) au cas où vous souhaiteriez utiliser plusieurs commandes pour examiner et gérer les données dans le fichier PsLog.txt.</span><span class="sxs-lookup"><span data-stu-id="8ec90-156">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the PsLog.txt file.</span></span> <span data-ttu-id="8ec90-157">Pour plus d’informations sur sessions PSSession, consultez about_PSSessions.</span><span class="sxs-lookup"><span data-stu-id="8ec90-157">For more information about PSSessions, see about_PSSessions.</span></span>

<span data-ttu-id="8ec90-158">Les commandes suivantes utilisent l’applet de commande New-PSSession pour créer une session PSSession qui est connectée à l’ordinateur Serveur01, et elles utilisent l’applet de commande Invoke-Command pour exécuter une commande Get-Content dans la session PSSession afin d’afficher le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="8ec90-158">The following commands use the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer, and they use the Invoke-Command cmdlet to run a Get-Content command in the PSSession to view the contents of the file.</span></span>

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="8ec90-159">DÉMARRER une tâche distante qui renvoie les résultats à l’ordinateur LOCAL \( AsJob\)</span><span class="sxs-lookup"><span data-stu-id="8ec90-159">START A REMOTE JOB THAT RETURNS THE RESULTS TO THE LOCAL COMPUTER \(ASJOB\)</span></span>

<span data-ttu-id="8ec90-160">Pour démarrer une tâche en arrière-plan sur un ordinateur distant qui retourne les résultats de la commande à l’ordinateur local, utilisez le paramètre AsJob d’une applet de commande, telle que l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="8ec90-160">To start a background job on a remote computer that returns the command results to the local computer, use the AsJob parameter of a cmdlet such as the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="8ec90-161">Quand vous utilisez le paramètre AsJob, l’objet de traitement est réellement créé sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-161">When you use the AsJob parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="8ec90-162">Une fois le travail terminé, les résultats sont retournés à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ec90-162">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="8ec90-163">Vous pouvez utiliser les applets de commande qui contiennent le nom du travail (les applets de commande Job) pour gérer n’importe quel travail créé par une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8ec90-163">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="8ec90-164">La plupart des applets de commande qui ont des paramètres AsJob n’utilisent pas la communication à distance PowerShell. vous pouvez donc les utiliser même sur des ordinateurs qui ne sont pas configurés pour la communication à distance et qui ne satisfont pas à la configuration requise pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="8ec90-164">Many of the cmdlets that have AsJob parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

#### <a name="step-1-invoke-command--asjob"></a><span data-ttu-id="8ec90-165">ÉTAPE 1 : INVOKE-COMMAND-ASJOB</span><span class="sxs-lookup"><span data-stu-id="8ec90-165">STEP 1: INVOKE-COMMAND -ASJOB</span></span>

<span data-ttu-id="8ec90-166">La commande suivante utilise le paramètre AsJob de Invoke-Command pour démarrer une tâche en arrière-plan sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-166">The following command uses the AsJob parameter of Invoke-Command to start a background job on the Server01 computer.</span></span> <span data-ttu-id="8ec90-167">La tâche exécute une commande Get-Eventlog qui obtient les événements du journal système.</span><span class="sxs-lookup"><span data-stu-id="8ec90-167">The job runs a Get-Eventlog command that gets the events in the System log.</span></span> <span data-ttu-id="8ec90-168">Vous pouvez utiliser le paramètre JobName pour attribuer un nom complet à la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ec90-168">You can use the JobName parameter to assign a display name to the job.</span></span>

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

<span data-ttu-id="8ec90-169">Les résultats de la commande ressemblent à l’exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-169">The results of the command resemble the following sample output.</span></span>

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

<span data-ttu-id="8ec90-170">Lorsque le paramètre AsJob est utilisé, Invoke-Command retourne le même type d’objet de traitement que Start-Job retourne.</span><span class="sxs-lookup"><span data-stu-id="8ec90-170">When the AsJob parameter is used, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="8ec90-171">Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une commande Get-Job pour obtenir le travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-171">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="8ec90-172">Notez que la valeur de la propriété Location indique que la tâche a été exécutée sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-172">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

#### <a name="step-2-get-job"></a><span data-ttu-id="8ec90-173">ÉTAPE 2 : OBTENIR LE TRAVAIL</span><span class="sxs-lookup"><span data-stu-id="8ec90-173">STEP 2: GET-JOB</span></span>

<span data-ttu-id="8ec90-174">Pour gérer un travail démarré à l’aide du paramètre AsJob de l’applet de commande Invoke-Command, utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-174">To manage a job started by using the AsJob parameter of the Invoke-Command cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="8ec90-175">Étant donné que l’objet de traitement qui représente le travail distant se trouve sur l’ordinateur local, vous n’avez pas besoin d’exécuter des commandes à distance pour gérer le travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-175">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

<span data-ttu-id="8ec90-176">Pour déterminer si le travail est terminé, utilisez une commande Get-Job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-176">To determine whether the job is complete, use a Get-Job command.</span></span> <span data-ttu-id="8ec90-177">La commande suivante obtient toutes les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="8ec90-177">The following command gets all of the jobs that were started in the current session.</span></span>

```powershell
get-job
```

<span data-ttu-id="8ec90-178">Étant donné que la tâche à distance a été démarrée dans la session active, une commande Get-Job locale obtient la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ec90-178">Because the remote job was started in the current session, a local Get-Job command gets the job.</span></span> <span data-ttu-id="8ec90-179">La propriété State de l’objet de traitement indique que la commande a été correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="8ec90-179">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a><span data-ttu-id="8ec90-180">ÉTAPE 3 : RÉCEPTION-TRAVAIL</span><span class="sxs-lookup"><span data-stu-id="8ec90-180">STEP 3: RECEIVE-JOB</span></span>

<span data-ttu-id="8ec90-181">Pour obtenir les résultats du travail, utilisez l’applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-181">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="8ec90-182">Étant donné que les résultats du travail sont automatiquement retournés à l’ordinateur sur lequel se trouve l’objet de traitement, vous pouvez obtenir les résultats avec une commande de Receive-Job locale.</span><span class="sxs-lookup"><span data-stu-id="8ec90-182">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local Receive-Job command.</span></span>

<span data-ttu-id="8ec90-183">La commande suivante utilise l’applet de commande Receive-Job pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-183">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="8ec90-184">Elle utilise l’ID de session pour identifier le travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-184">It uses the session ID to identify the job.</span></span> <span data-ttu-id="8ec90-185">Cette commande enregistre les résultats de la tâche dans la variable $results.</span><span class="sxs-lookup"><span data-stu-id="8ec90-185">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="8ec90-186">Vous pouvez également rediriger les résultats vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="8ec90-186">You can also redirect the results to a file.</span></span>

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="8ec90-187">DÉMARRER UN TRAVAIL DISTANT QUI CONSERVE LES RÉSULTATS SUR L’ORDINATEUR DISTANT</span><span class="sxs-lookup"><span data-stu-id="8ec90-187">START A REMOTE JOB THAT KEEPS THE RESULTS ON THE REMOTE COMPUTER</span></span>

<span data-ttu-id="8ec90-188">Pour démarrer une tâche en arrière-plan sur un ordinateur distant qui conserve les résultats de la commande sur l’ordinateur distant, utilisez l’applet de commande Invoke-Command pour exécuter une commande Start-Job sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-188">To start a background job on a remote computer that keeps the command results on the remote computer, use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span> <span data-ttu-id="8ec90-189">Vous pouvez utiliser cette méthode pour exécuter des tâches en arrière-plan sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8ec90-189">You can use this method to run background jobs on multiple computers.</span></span>

<span data-ttu-id="8ec90-190">Lorsque vous exécutez une commande Start-Job à distance, l’objet de traitement est créé sur l’ordinateur distant et les résultats de la tâche sont conservés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-190">When you run a Start-Job command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="8ec90-191">Du point de vue du travail, toutes les opérations sont locales.</span><span class="sxs-lookup"><span data-stu-id="8ec90-191">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="8ec90-192">Vous exécutez simplement des commandes à distance pour gérer un travail local sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-192">You are just running commands remotely to manage a local job on the remote computer.</span></span>

#### <a name="step-1-invoke-command-start-job"></a><span data-ttu-id="8ec90-193">ÉTAPE 1 : APPELER-COMMAND START-JOB</span><span class="sxs-lookup"><span data-stu-id="8ec90-193">STEP 1: INVOKE-COMMAND START-JOB</span></span>

<span data-ttu-id="8ec90-194">Utilisez l’applet de commande Invoke-Command pour exécuter une commande Start-Job sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-194">Use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span>

<span data-ttu-id="8ec90-195">Cette commande requiert une session PSSession (connexion persistante).</span><span class="sxs-lookup"><span data-stu-id="8ec90-195">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="8ec90-196">Si vous utilisez le paramètre ComputerName de Invoke-Command pour établir une connexion temporaire, la commande Invoke-Command est considérée comme terminée lorsque l’objet de traitement est retourné.</span><span class="sxs-lookup"><span data-stu-id="8ec90-196">If you use the ComputerName parameter of Invoke-Command to establish a temporary connection, the Invoke-Command command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="8ec90-197">Par conséquent, la connexion temporaire est fermée et le travail est annulé.</span><span class="sxs-lookup"><span data-stu-id="8ec90-197">As a result, the temporary connection is closed, and the job is canceled.</span></span>

<span data-ttu-id="8ec90-198">La commande suivante utilise l’applet de commande New-PSSession pour créer une session PSSession qui est connectée à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-198">The following command uses the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="8ec90-199">La commande enregistre la session PSSession dans la \$ variable s.</span><span class="sxs-lookup"><span data-stu-id="8ec90-199">The command saves the PSSession in the \$s variable.</span></span>

```powershell
$s = new-pssession -computername Server01
```

<span data-ttu-id="8ec90-200">La commande suivante utilise l’applet de commande Invoke-Command pour exécuter une commande Start-Job dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="8ec90-200">The next command uses the Invoke-Command cmdlet to run a Start-Job command in the PSSession.</span></span> <span data-ttu-id="8ec90-201">La commande Start-Job et la commande Get-Eventlog sont placées entre accolades.</span><span class="sxs-lookup"><span data-stu-id="8ec90-201">The Start-Job command and the Get-Eventlog command are enclosed in braces.</span></span>

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

<span data-ttu-id="8ec90-202">Les résultats ressemblent à l’exemple de sortie suivant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-202">The results resemble the following sample output.</span></span>

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

<span data-ttu-id="8ec90-203">Lorsque vous exécutez une commande Start-Job à distance, Invoke-Command retourne le même type d’objet de traitement que Start-Job retourne.</span><span class="sxs-lookup"><span data-stu-id="8ec90-203">When you run a Start-Job command remotely, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="8ec90-204">Vous pouvez enregistrer l’objet de traitement dans une variable, ou vous pouvez utiliser une commande Get-Job pour obtenir le travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-204">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="8ec90-205">Notez que la valeur de la propriété Location indique que la tâche a été exécutée sur l’ordinateur local, appelée « LocalHost », même si la tâche a été exécutée sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-205">Note that the value of the Location property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="8ec90-206">Étant donné que l’objet de traitement est créé sur l’ordinateur SERVEUR01 et que la tâche s’exécute sur le même ordinateur, il est considéré comme une tâche en arrière-plan locale.</span><span class="sxs-lookup"><span data-stu-id="8ec90-206">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

#### <a name="step-2-invoke-command-get-job"></a><span data-ttu-id="8ec90-207">ÉTAPE 2 : INVOKE-COMMAND, OBTENIR-JOB</span><span class="sxs-lookup"><span data-stu-id="8ec90-207">STEP 2: INVOKE-COMMAND GET-JOB</span></span>

<span data-ttu-id="8ec90-208">Pour gérer un travail en arrière-plan distant, utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="8ec90-208">To manage a remote background job, use the Job cmdlets.</span></span> <span data-ttu-id="8ec90-209">Étant donné que l’objet de traitement se trouve sur l’ordinateur distant, vous devez exécuter des commandes à distance pour obtenir, arrêter, attendre ou récupérer les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="8ec90-209">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

<span data-ttu-id="8ec90-210">Pour voir si le travail est terminé, utilisez une commande Invoke-Command pour exécuter une commande Get-Job dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-210">To see if the job is complete, use an Invoke-Command command to run a Get-Job command in the PSSession that is connected to the Server01 computer.</span></span>

```powershell
invoke-command -session $s -scriptblock {get-job}
```

<span data-ttu-id="8ec90-211">La commande retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="8ec90-211">The command returns a job object.</span></span> <span data-ttu-id="8ec90-212">La propriété State de l’objet de traitement indique que la commande a été correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="8ec90-212">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a><span data-ttu-id="8ec90-213">ÉTAPE 3 : APPELER-COMMAND RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="8ec90-213">STEP 3: INVOKE-COMMAND RECEIVE-JOB</span></span>

<span data-ttu-id="8ec90-214">Pour obtenir les résultats du travail, utilisez l’applet de commande Invoke-Command pour exécuter une commande Receive-Job dans la session PSSession qui est connectée à l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-214">To get the results of the job, use the Invoke-Command cmdlet to run a Receive-Job command in the PSSession that is connected to the Server01 computer.</span></span>

<span data-ttu-id="8ec90-215">La commande suivante utilise l’applet de commande Receive-Job pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-215">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="8ec90-216">Elle utilise l’ID de session pour identifier le travail.</span><span class="sxs-lookup"><span data-stu-id="8ec90-216">It uses the session ID to identify the job.</span></span> <span data-ttu-id="8ec90-217">Cette commande enregistre les résultats de la tâche dans la \$ variable results.</span><span class="sxs-lookup"><span data-stu-id="8ec90-217">This command saves the job results in the \$results variable.</span></span> <span data-ttu-id="8ec90-218">Elle utilise le paramètre Keep de Receive-Job pour conserver le résultat dans le cache de travaux sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-218">It uses the Keep parameter of Receive-Job to keep the result in the job cache on the remote computer.</span></span>

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

<span data-ttu-id="8ec90-219">Vous pouvez également rediriger les résultats vers un fichier sur l’ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="8ec90-219">You can also redirect the results to a file on the local or remote computer.</span></span>
<span data-ttu-id="8ec90-220">La commande suivante utilise un opérateur de redirection pour enregistrer les résultats dans un fichier sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="8ec90-220">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a><span data-ttu-id="8ec90-221">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="8ec90-221">SEE ALSO</span></span>

[<span data-ttu-id="8ec90-222">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="8ec90-222">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="8ec90-223">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="8ec90-223">about_Job_Details</span></span>](about_Job_Details.md)

[<span data-ttu-id="8ec90-224">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8ec90-224">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="8ec90-225">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="8ec90-225">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="8ec90-226">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8ec90-226">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="8ec90-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="8ec90-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)

[<span data-ttu-id="8ec90-228">Get-Job</span><span class="sxs-lookup"><span data-stu-id="8ec90-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)

[<span data-ttu-id="8ec90-229">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="8ec90-229">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)

[<span data-ttu-id="8ec90-230">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="8ec90-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)

[<span data-ttu-id="8ec90-231">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="8ec90-231">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)

[<span data-ttu-id="8ec90-232">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ec90-232">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="8ec90-233">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ec90-233">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="8ec90-234">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ec90-234">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

