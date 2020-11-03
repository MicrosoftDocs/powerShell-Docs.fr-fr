---
description: Décrit les tâches planifiées et explique comment utiliser et gérer les tâches planifiées dans PowerShell et dans Planificateur de tâches.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207257"
---
# <a name="about-scheduled-jobs"></a><span data-ttu-id="f27ea-104">À propos des tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="f27ea-104">About Scheduled Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="f27ea-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="f27ea-105">Short description</span></span>

<span data-ttu-id="f27ea-106">Décrit les tâches planifiées et explique comment utiliser et gérer les tâches planifiées dans PowerShell et dans Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="f27ea-106">Describes scheduled jobs and explains how to use and manage scheduled jobs in PowerShell and in Task Scheduler.</span></span>

## <a name="long-description"></a><span data-ttu-id="f27ea-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="f27ea-107">Long description</span></span>

<span data-ttu-id="f27ea-108">Les tâches planifiées PowerShell sont un hybride utile des tâches en arrière-plan PowerShell et des tâches de Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="f27ea-108">PowerShell scheduled jobs are a useful hybrid of PowerShell background jobs and Task Scheduler tasks.</span></span>

<span data-ttu-id="f27ea-109">Comme les tâches en arrière-plan PowerShell, les tâches planifiées s’exécutent de façon asynchrone en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f27ea-109">Like PowerShell background jobs, scheduled jobs run asynchronously in the background.</span></span> <span data-ttu-id="f27ea-110">Les instances de tâches planifiées qui ont été exécutées peuvent être gérées à l’aide des applets de commande Job, telles que `Start-Job` ,, `Get-Job` `Stop-Job` et `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="f27ea-110">Instances of scheduled jobs that have run can be managed by using the job cmdlets, such as `Start-Job`, `Get-Job`, `Stop-Job`, and `Receive-Job`.</span></span>

<span data-ttu-id="f27ea-111">À l’instar des tâches de Planificateur de tâches, les tâches planifiées sont enregistrées sur le disque.</span><span class="sxs-lookup"><span data-stu-id="f27ea-111">Like Task Scheduler tasks, scheduled jobs are saved to disk.</span></span> <span data-ttu-id="f27ea-112">Vous pouvez afficher et gérer les travaux dans Planificateur de tâches, les activer et les désactiver si nécessaire, les exécuter ou les utiliser en tant que modèles, établir une planification ponctuelle ou périodique pour le démarrage des travaux, ou définir des conditions sous lesquelles les travaux démarrent.</span><span class="sxs-lookup"><span data-stu-id="f27ea-112">You can view and manage the jobs in Task Scheduler, enable and disable them as needed, run them or use them as templates, establish a one-time or recurring schedules for starting the jobs, or set conditions under which the jobs start.</span></span>

<span data-ttu-id="f27ea-113">En outre, les résultats des instances de tâche planifiée sont enregistrés sur le disque dans un format facilement accessible, ce qui fournit un journal des sorties de travail.</span><span class="sxs-lookup"><span data-stu-id="f27ea-113">In addition, the results of scheduled job instances are saved to disk in an easily accessible format, providing a running log of job output.</span></span> <span data-ttu-id="f27ea-114">Les travaux planifiés sont fournis avec un ensemble personnalisé d’applets de commande pour les gérer.</span><span class="sxs-lookup"><span data-stu-id="f27ea-114">Scheduled jobs come with a customized set of cmdlets for managing them.</span></span> <span data-ttu-id="f27ea-115">Les applets de commande vous permettent de créer, modifier, gérer, désactiver et réactiver des tâches planifiées, des déclencheurs de tâche et des options de tâche.</span><span class="sxs-lookup"><span data-stu-id="f27ea-115">The cmdlets let you create, edit, manage, disable, and re-enable scheduled jobs, job triggers and job options.</span></span>

<span data-ttu-id="f27ea-116">Cet ensemble complet et flexible d’outils fait des tâches planifiées un composant essentiel de nombreuses solutions informatiques PowerShell professionnelles.</span><span class="sxs-lookup"><span data-stu-id="f27ea-116">This comprehensive and flexible set of tools make scheduled jobs an essential component of many professional PowerShell IT solutions.</span></span>

<span data-ttu-id="f27ea-117">Les applets de commande de tâche planifiée sont incluses dans le module **PSScheduledJob** qui est installé avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f27ea-117">The scheduled job cmdlets are included in the **PSScheduledJob** module that is installed with PowerShell.</span></span> <span data-ttu-id="f27ea-118">Ce module a été introduit dans PowerShell 3,0 et fonctionne dans PowerShell 3,0 et versions ultérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f27ea-118">This module was introduced in PowerShell 3.0 and works in PowerShell 3.0 and later versions of PowerShell.</span></span> <span data-ttu-id="f27ea-119">Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="f27ea-119">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

<span data-ttu-id="f27ea-120">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="f27ea-120">For more information about PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

<span data-ttu-id="f27ea-121">Pour plus d’informations sur Planificateur de tâches, consultez [Planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-reference).</span><span class="sxs-lookup"><span data-stu-id="f27ea-121">For more information about Task Scheduler, see [Task Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference).</span></span>

> [!NOTE]
> <span data-ttu-id="f27ea-122">Vous pouvez afficher et gérer les tâches planifiées PowerShell dans Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="f27ea-122">You can view and manage PowerShell scheduled jobs in Task Scheduler.</span></span> <span data-ttu-id="f27ea-123">Les applets de commande travaux PowerShell et tâche planifiée fonctionnent uniquement sur les tâches planifiées qui sont créées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f27ea-123">The PowerShell jobs and scheduled job cmdlets work only on scheduled jobs that are created in PowerShell.</span></span>

## <a name="quick-start"></a><span data-ttu-id="f27ea-124">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="f27ea-124">Quick start</span></span>

<span data-ttu-id="f27ea-125">Cet exemple crée une tâche planifiée qui démarre tous les jours à 3:00 AM et exécute l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="f27ea-125">This example creates a scheduled job that starts every day at 3:00 AM and runs the `Get-Process` cmdlet.</span></span> <span data-ttu-id="f27ea-126">Le travail démarre même si l’ordinateur fonctionne sur batterie.</span><span class="sxs-lookup"><span data-stu-id="f27ea-126">The job starts even if the computer is running on batteries.</span></span>

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

<span data-ttu-id="f27ea-127">L' `Get-ScheduledJob` applet de commande obtient les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f27ea-127">The `Get-ScheduledJob` cmdlet gets the scheduled jobs on the local computer.</span></span>

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

<span data-ttu-id="f27ea-128">`Get-JobTrigger` Obtient les déclencheurs de la tâche de **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="f27ea-128">`Get-JobTrigger` gets the job triggers of **ProcessJob** .</span></span> <span data-ttu-id="f27ea-129">Les paramètres d’entrée spécifient la tâche planifiée, et non le déclencheur, car les déclencheurs sont enregistrés dans une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f27ea-129">The input parameters specify the scheduled job, not the trigger, because triggers are saved in a scheduled job.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

<span data-ttu-id="f27ea-130">Cet exemple utilise le paramètre **ContinueIfGoingOnBattery** de l' `Set-ScheduledJob` applet de commande pour modifier la propriété **StopIfGoingOnBatteries** de **ProcessJob** en **false** .</span><span class="sxs-lookup"><span data-stu-id="f27ea-130">This example uses the **ContinueIfGoingOnBattery** parameter of the `Set-ScheduledJob` cmdlet to change the **StopIfGoingOnBatteries** property of **ProcessJob** to **False** .</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="f27ea-131">L' `Get-ScheduledJob` applet de commande obtient la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="f27ea-131">The `Get-ScheduledJob` cmdlet gets the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

<span data-ttu-id="f27ea-132">L' `Get-Job` applet de commande obtient toutes les instances de la tâche planifiée **ProcessJob** qui ont été exécutées jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="f27ea-132">The `Get-Job` cmdlet gets all instances of the **ProcessJob** scheduled job that have run thus far.</span></span> <span data-ttu-id="f27ea-133">L' `Get-Job` applet de commande obtient les tâches planifiées uniquement lorsque le module **PSScheduledJob** est importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f27ea-133">The `Get-Job` cmdlet gets scheduled jobs only when the **PSScheduledJob** module is imported into the current session.</span></span>

> [!TIP]
> <span data-ttu-id="f27ea-134">Notez que vous utilisez les applets de commande Job scheduled pour gérer les tâches planifiées, mais vous utilisez les applets de commande Job pour gérer les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f27ea-134">Notice that you use the scheduled job cmdlets to manage scheduled jobs, but you use the job cmdlets to manage instances of scheduled jobs.</span></span>

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

<span data-ttu-id="f27ea-135">L' `Receive-Job` applet de commande obtient les résultats de l’instance la plus récente de la tâche planifiée **PROCESSJOB** (ID = 51).</span><span class="sxs-lookup"><span data-stu-id="f27ea-135">The `Receive-Job` cmdlet gets the results of the most recent instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Receive-Job -ID 51
```

<span data-ttu-id="f27ea-136">Même si la `Receive-Job` commande n’incluait pas le paramètre **Keep** , les résultats de la tâche sont enregistrés sur le disque jusqu’à ce que vous les supprimiez ou que le nombre maximal de résultats soit dépassé.</span><span class="sxs-lookup"><span data-stu-id="f27ea-136">Even though the `Receive-Job` command did not include the **Keep** parameter, the results of the job are saved on disk until you delete them or the maximum number of results are exceeded.</span></span>

<span data-ttu-id="f27ea-137">Les résultats de la tâche ne sont plus disponibles dans cette session, mais si vous démarrez une nouvelle session ou ouvrez une nouvelle fenêtre PowerShell, les résultats du travail sont à nouveau disponibles.</span><span class="sxs-lookup"><span data-stu-id="f27ea-137">The job results are no longer available in this session, but if you start a new session or open a new PowerShell window, the results of the job are available again.</span></span>

<span data-ttu-id="f27ea-138">La commande suivante utilise le paramètre **DefinitionName** de l' `Start-Job` applet de commande pour démarrer la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="f27ea-138">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the **ProcessJob** scheduled job.</span></span>

<span data-ttu-id="f27ea-139">Les tâches démarrées à l’aide de l' `Start-Job` applet de commande sont des travaux en arrière-plan PowerShell standard, et non des instances de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f27ea-139">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="f27ea-140">Comme pour toutes les tâches en arrière-plan, ces travaux démarrent immédiatement, ils ne sont pas soumis à des options de travail ou affectés par des déclencheurs de tâche, et leur sortie n’est pas enregistrée dans le répertoire de sortie du répertoire de travail planifié.</span><span class="sxs-lookup"><span data-stu-id="f27ea-140">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers, and their output is not saved in the output directory of the scheduled job directory.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="f27ea-141">L' `Unregister-ScheduledJob` applet de commande supprime la tâche planifiée **ProcessJob** et tous les résultats enregistrés de ses instances de travail.</span><span class="sxs-lookup"><span data-stu-id="f27ea-141">The `Unregister-ScheduledJob` cmdlet deletes the **ProcessJob** scheduled job and all saved results of its job instances.</span></span>

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a><span data-ttu-id="f27ea-142">Concepts des tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="f27ea-142">Scheduled jobs concepts</span></span>

<span data-ttu-id="f27ea-143">Une tâche planifiée exécute des commandes ou un script.</span><span class="sxs-lookup"><span data-stu-id="f27ea-143">A scheduled job runs commands or a script.</span></span> <span data-ttu-id="f27ea-144">Une tâche planifiée peut inclure des déclencheurs de tâche qui démarrent les options de tâche et de travail qui définissent des conditions d’exécution du travail.</span><span class="sxs-lookup"><span data-stu-id="f27ea-144">A scheduled job can include job triggers that start the job and job options that set conditions for running the job.</span></span>

<span data-ttu-id="f27ea-145">Un déclencheur de tâche démarre automatiquement une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f27ea-145">A job trigger starts a scheduled job automatically.</span></span> <span data-ttu-id="f27ea-146">Un déclencheur de tâche peut inclure une planification ponctuelle ou périodique, ou spécifier un événement, par exemple lorsqu’un utilisateur ouvre une session ou que Windows démarre.</span><span class="sxs-lookup"><span data-stu-id="f27ea-146">A job trigger can include a one-time or recurring schedule or specify an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="f27ea-147">Une tâche planifiée peut avoir un ou plusieurs déclencheurs de tâche, et vous pouvez créer, ajouter, activer, désactiver et obtenir des déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="f27ea-147">A scheduled job can have one or more job triggers, and you can create, add, enable, disable, and get job triggers.</span></span>

<span data-ttu-id="f27ea-148">Les déclencheurs de tâche sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="f27ea-148">Job triggers are optional.</span></span> <span data-ttu-id="f27ea-149">Vous pouvez démarrer des tâches planifiées immédiatement à l’aide de l' `Start-Job cmdlet` ou en ajoutant le paramètre **RunNow** à votre `Register-ScheduledJob` commande.</span><span class="sxs-lookup"><span data-stu-id="f27ea-149">You can start scheduled jobs immediately by using the `Start-Job cmdlet`, or by adding the **RunNow** parameter to your `Register-ScheduledJob` command.</span></span>

<span data-ttu-id="f27ea-150">Les options de travail définissent les conditions d’exécution d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f27ea-150">Job options set the conditions for running a scheduled job.</span></span> <span data-ttu-id="f27ea-151">Chaque tâche planifiée a un objet d’options de tâche.</span><span class="sxs-lookup"><span data-stu-id="f27ea-151">Every scheduled job has one job options object.</span></span> <span data-ttu-id="f27ea-152">Vous pouvez créer et modifier des objets d’options de tâche et les ajouter à une ou plusieurs tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f27ea-152">You can create and edit job options objects and add them to one or more scheduled jobs.</span></span>

<span data-ttu-id="f27ea-153">Chaque fois qu’une tâche planifiée démarre, une instance de tâche est créée.</span><span class="sxs-lookup"><span data-stu-id="f27ea-153">Each time a scheduled job starts, a job instance is created.</span></span> <span data-ttu-id="f27ea-154">Utilisez les applets de commande PowerShell Job pour afficher et gérer l’instance de tâche.</span><span class="sxs-lookup"><span data-stu-id="f27ea-154">Use the PowerShell job cmdlets to view and manage the job instance.</span></span>

<span data-ttu-id="f27ea-155">Les tâches planifiées sont enregistrées sur le disque et utilisent le verbe d’applet de commande, `Register` , au lieu de `New` .</span><span class="sxs-lookup"><span data-stu-id="f27ea-155">Scheduled jobs are saved to disk and use the cmdlet verb, `Register`, instead of `New`.</span></span> <span data-ttu-id="f27ea-156">Les fichiers XML se trouvent sur l’ordinateur local dans le répertoire `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="f27ea-156">The XML files are located on the local computer in the directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

<span data-ttu-id="f27ea-157">PowerShell crée un répertoire pour chaque tâche planifiée et enregistre les commandes de travail, les déclencheurs de tâche, les options de tâche et les résultats de travail dans le répertoire de travail planifié.</span><span class="sxs-lookup"><span data-stu-id="f27ea-157">PowerShell creates a directory for each scheduled job and saves the job commands, job triggers, job options and job results in the scheduled job directory.</span></span> <span data-ttu-id="f27ea-158">Les déclencheurs de tâche et les options de tâche ne sont pas enregistrés sur le disque indépendamment.</span><span class="sxs-lookup"><span data-stu-id="f27ea-158">Job triggers and job options aren't saved to disk independently.</span></span>
<span data-ttu-id="f27ea-159">Elles sont enregistrées dans le fichier XML de tâches planifiées de chaque tâche planifiée à laquelle elles sont associées.</span><span class="sxs-lookup"><span data-stu-id="f27ea-159">They are saved in the scheduled job XML of each scheduled job with which they are associated.</span></span>

<span data-ttu-id="f27ea-160">Les tâches planifiées, les déclencheurs de tâche et les options de tâche s’affichent dans PowerShell en tant qu’objets.</span><span class="sxs-lookup"><span data-stu-id="f27ea-160">Scheduled jobs, job triggers, and job options appear in PowerShell as objects.</span></span>
<span data-ttu-id="f27ea-161">Les objets sont liés entre eux, ce qui facilite leur découverte et leur utilisation dans les commandes et les scripts.</span><span class="sxs-lookup"><span data-stu-id="f27ea-161">The objects are interlinked, which makes them easy to discover and use in commands and scripts.</span></span>

<span data-ttu-id="f27ea-162">Les tâches planifiées apparaissent en tant qu’objets **ScheduledJobDefinition** .</span><span class="sxs-lookup"><span data-stu-id="f27ea-162">Scheduled jobs appear as **ScheduledJobDefinition** objects.</span></span> <span data-ttu-id="f27ea-163">L’objet **ScheduledJobDefinition** a une propriété **JobTriggers** qui contient les déclencheurs de la tâche planifiée et une propriété **options** qui contient les options du travail.</span><span class="sxs-lookup"><span data-stu-id="f27ea-163">The **ScheduledJobDefinition** object has a **JobTriggers** property that contains the job triggers of the scheduled job and an **Options** property that contains the job options.</span></span> <span data-ttu-id="f27ea-164">Les objets **ScheduledJobTriggers** et **ScheduledJobOptions** qui représentent les déclencheurs de tâche et les options de tâche, respectivement, ont chacun une propriété **JobDefinition** qui contient la tâche planifiée à laquelle ils sont associés.</span><span class="sxs-lookup"><span data-stu-id="f27ea-164">The **ScheduledJobTriggers** and **ScheduledJobOptions** objects that represent job triggers and job options, respectively, each have a **JobDefinition** property that contains the scheduled job with which they are associated.</span></span> <span data-ttu-id="f27ea-165">Cette interconnexion récursive permet de trouver facilement les déclencheurs et les options d’une tâche planifiée, ainsi que de rechercher, de générer un script et d’afficher la tâche planifiée à laquelle n’importe quel déclencheur de tâche ou option de travail est associé.</span><span class="sxs-lookup"><span data-stu-id="f27ea-165">This recursive interconnection makes it easy to find the triggers and options of a scheduled job and to find, script, and display the scheduled job to which any job trigger or job option is associated.</span></span>

## <a name="see-also"></a><span data-ttu-id="f27ea-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f27ea-166">See also</span></span>

[<span data-ttu-id="f27ea-167">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="f27ea-167">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="f27ea-168">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="f27ea-168">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="f27ea-169">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="f27ea-169">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

<span data-ttu-id="f27ea-170">Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)</span><span class="sxs-lookup"><span data-stu-id="f27ea-170">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="f27ea-171">Planificateur de tâches</span><span class="sxs-lookup"><span data-stu-id="f27ea-171">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
