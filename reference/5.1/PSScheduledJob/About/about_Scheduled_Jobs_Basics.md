---
description: Explique comment créer et gérer des tâches planifiées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207250"
---
# <a name="about-scheduled-jobs-basics"></a><span data-ttu-id="a53cc-104">À propos des notions de base des tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="a53cc-104">About Scheduled Jobs Basics</span></span>

## <a name="short-description"></a><span data-ttu-id="a53cc-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="a53cc-105">Short description</span></span>

<span data-ttu-id="a53cc-106">Explique comment créer et gérer des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="a53cc-106">Explains how to create and manage scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="a53cc-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="a53cc-107">Long description</span></span>

<span data-ttu-id="a53cc-108">Ce document montre comment effectuer des tâches de base pour créer et gérer des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="a53cc-108">This document shows how to perform basic tasks of creating and managing scheduled jobs.</span></span> <span data-ttu-id="a53cc-109">Pour plus d’informations sur les tâches plus avancées, consultez [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="a53cc-109">For information about more advanced tasks, see [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span></span>

<span data-ttu-id="a53cc-110">Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="a53cc-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="how-to-create-a-scheduled-job"></a><span data-ttu-id="a53cc-111">Comment créer une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="a53cc-111">How to create a scheduled job</span></span>

<span data-ttu-id="a53cc-112">Pour créer une tâche planifiée, utilisez l’applet de commande `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-112">To create a scheduled job, use the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="a53cc-113">L’applet de commande requiert un nom et les commandes ou le script exécutés par la tâche.</span><span class="sxs-lookup"><span data-stu-id="a53cc-113">The cmdlet requires a name and the commands or script that the job runs.</span></span> <span data-ttu-id="a53cc-114">Vous pouvez exécuter la tâche immédiatement en ajoutant le paramètre **RunNow** , ou créer un déclencheur de tâche et définir les options de travail lorsque vous créez le travail, ou modifier un travail existant.</span><span class="sxs-lookup"><span data-stu-id="a53cc-114">You can either run the job immediately by adding the **RunNow** parameter, or create a job trigger and set job options when you create the job, or edit an existing job.</span></span>

<span data-ttu-id="a53cc-115">Pour créer un travail qui exécute un script, utilisez le paramètre **filePath** pour spécifier le chemin d’accès au fichier de script.</span><span class="sxs-lookup"><span data-stu-id="a53cc-115">To create a job that runs a script, use the **FilePath** parameter to specify the path to the script file.</span></span> <span data-ttu-id="a53cc-116">Pour créer un travail qui exécute des commandes, utilisez le paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="a53cc-116">To create a job that runs commands, use the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="a53cc-117">L' `Register-ScheduledJob` applet de commande crée le **ProcessJob** , qui exécute une `Get-Process` commande.</span><span class="sxs-lookup"><span data-stu-id="a53cc-117">The `Register-ScheduledJob` cmdlet creates the **ProcessJob** , which runs a `Get-Process` command.</span></span> <span data-ttu-id="a53cc-118">Cette tâche planifiée a les options de travail par défaut et aucun déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="a53cc-118">This scheduled job has the default job options and no job trigger.</span></span>

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a><span data-ttu-id="a53cc-119">Comment créer un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="a53cc-119">How to create a job trigger</span></span>

<span data-ttu-id="a53cc-120">Les déclencheurs de tâche démarrent automatiquement une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-120">Job triggers start a scheduled job automatically.</span></span> <span data-ttu-id="a53cc-121">Un déclencheur de tâche peut être une planification ponctuelle ou périodique, ou un événement, par exemple lorsqu’un utilisateur ouvre une session ou que Windows démarre.</span><span class="sxs-lookup"><span data-stu-id="a53cc-121">A job trigger can be one-time or recurring schedule or an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="a53cc-122">Chaque travail peut avoir zéro, un ou plusieurs déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="a53cc-122">Each job can have zero, one, or multiple job triggers.</span></span>

<span data-ttu-id="a53cc-123">Pour créer un déclencheur de tâche, utilisez l’applet de commande `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-123">To create a job trigger, use the `New-JobTrigger` cmdlet.</span></span> <span data-ttu-id="a53cc-124">La commande suivante crée un déclencheur de tâche qui démarre une tâche tous les lundis et jeudi à 5:00 AM.</span><span class="sxs-lookup"><span data-stu-id="a53cc-124">The following command creates a job trigger that starts a job every Monday and Thursday at 5:00 AM.</span></span>
<span data-ttu-id="a53cc-125">La commande enregistre le déclencheur de tâche dans la `$T` variable.</span><span class="sxs-lookup"><span data-stu-id="a53cc-125">The command saves the job trigger in the `$T` variable.</span></span>

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

<span data-ttu-id="a53cc-126">Les déclencheurs de tâche sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a53cc-126">Job triggers are optional.</span></span> <span data-ttu-id="a53cc-127">Vous pouvez démarrer une tâche planifiée à tout moment en ajoutant le paramètre **RunNow** à votre `Register-ScheduledJob` commande ou en utilisant les `Start-Job` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="a53cc-127">You can start a scheduled job at any time by adding the **RunNow** parameter to your `Register-ScheduledJob` command, or by using the `Start-Job` cmdlets.</span></span>

## <a name="how-to-add-a-job-trigger"></a><span data-ttu-id="a53cc-128">Ajout d’un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="a53cc-128">How to add a job trigger</span></span>

<span data-ttu-id="a53cc-129">Lorsque vous ajoutez un déclencheur de tâche à une tâche planifiée, le déclencheur de tâche est ajouté au fichier XML de la tâche planifiée pour la tâche planifiée et devient partie intégrante de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-129">When you add a job trigger to a scheduled job, the job trigger is added to the scheduled job XML file for the scheduled job and becomes part of the scheduled job.</span></span>

<span data-ttu-id="a53cc-130">Vous pouvez ajouter un déclencheur de tâche à une tâche planifiée lorsque vous créez la tâche planifiée, ou modifier un travail existant.</span><span class="sxs-lookup"><span data-stu-id="a53cc-130">You can add a job trigger to a scheduled job when you create the scheduled job, or edit an existing job.</span></span> <span data-ttu-id="a53cc-131">Vous pouvez modifier le déclencheur d’une tâche planifiée à tout moment.</span><span class="sxs-lookup"><span data-stu-id="a53cc-131">You can change the job trigger of a scheduled job at any time.</span></span>

<span data-ttu-id="a53cc-132">PowerShell utilise certains des déclencheurs de tâche que Planificateur de tâches utilise.</span><span class="sxs-lookup"><span data-stu-id="a53cc-132">PowerShell uses some of the same job triggers that Task Scheduler uses.</span></span> <span data-ttu-id="a53cc-133">Pour plus d’informations sur les déclencheurs de tâche, consultez la rubrique d’aide de l’applet de commande [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) .</span><span class="sxs-lookup"><span data-stu-id="a53cc-133">For detailed information about job triggers, see the help topic for the [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet.</span></span>

<span data-ttu-id="a53cc-134">L’exemple suivant utilise la projection pour créer `$JobParms` des valeurs de paramètre qui sont passées à l’applet de commande `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-134">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="a53cc-135">Pour plus d’informations, consultez [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="a53cc-135">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="a53cc-136">Le `Register-ScheduledJob` utilise `@JobParms` pour créer une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-136">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="a53cc-137">Elle utilise le paramètre **Trigger** pour spécifier le déclencheur de tâche dans la `$T` variable.</span><span class="sxs-lookup"><span data-stu-id="a53cc-137">It uses the **Trigger** parameter to specify the job trigger in the `$T` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="a53cc-138">Vous pouvez également ajouter un déclencheur de tâche à une tâche planifiée existante à tout moment.</span><span class="sxs-lookup"><span data-stu-id="a53cc-138">You can also add a job trigger to an existing scheduled job at any time.</span></span> <span data-ttu-id="a53cc-139">L' `Add-JobTrigger` applet de commande ajoute le déclencheur de tâche dans la `$T` variable à la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="a53cc-139">The `Add-JobTrigger` cmdlet adds the job trigger in the `$T` variable to the **ProcessJob** scheduled job.</span></span>

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

<span data-ttu-id="a53cc-140">Par conséquent, le déclencheur de tâche démarre automatiquement le **ProcessJob** tous les lundis et jeudi à 5:00 AM.</span><span class="sxs-lookup"><span data-stu-id="a53cc-140">As a result, the job trigger starts the **ProcessJob** automatically every Monday and Thursday at 5:00 AM.</span></span>

## <a name="how-to-get-a-job-trigger"></a><span data-ttu-id="a53cc-141">Obtention d’un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="a53cc-141">How to get a job trigger</span></span>

<span data-ttu-id="a53cc-142">Pour obtenir le déclencheur d’une tâche planifiée, utilisez l’applet de commande `Get-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-142">To get the job trigger of a scheduled job, use the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="a53cc-143">Utilisez les paramètres **Name** , **ID** et **InputObject** pour spécifier la tâche planifiée, et non le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="a53cc-143">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job trigger.</span></span>

<span data-ttu-id="a53cc-144">`Get-JobTrigger` Obtient le déclencheur de la tâche du **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="a53cc-144">`Get-JobTrigger` gets the job trigger of the **ProcessJob** .</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a><span data-ttu-id="a53cc-145">Comment créer des options de tâche</span><span class="sxs-lookup"><span data-stu-id="a53cc-145">How to create job options</span></span>

<span data-ttu-id="a53cc-146">Les options de tâche établissent des conditions de démarrage et d’exécution du travail.</span><span class="sxs-lookup"><span data-stu-id="a53cc-146">Job options establish conditions for starting and running the job.</span></span> <span data-ttu-id="a53cc-147">Chaque travail dispose des options de travail par défaut, sauf si vous les modifiez.</span><span class="sxs-lookup"><span data-stu-id="a53cc-147">Every job has the default job options unless you change them.</span></span> <span data-ttu-id="a53cc-148">Étant donné que les options de tâche peuvent empêcher l’exécution d’un travail à l’heure planifiée, il est important de comprendre les options des tâches et de les utiliser avec précaution.</span><span class="sxs-lookup"><span data-stu-id="a53cc-148">Because job options can prevent a job from running at the scheduled time, it is important to understand the job options and use them carefully.</span></span>

<span data-ttu-id="a53cc-149">PowerShell utilise les mêmes options de travail que celles que Planificateur de tâches utilise.</span><span class="sxs-lookup"><span data-stu-id="a53cc-149">PowerShell uses the same job options that Task Scheduler uses.</span></span> <span data-ttu-id="a53cc-150">Pour plus d’informations sur les options de tâche, consultez la rubrique d’aide [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span><span class="sxs-lookup"><span data-stu-id="a53cc-150">For detailed information about the job options, see the help topic for [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

<span data-ttu-id="a53cc-151">Les options de tâche sont stockées dans le fichier XML de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-151">Job options are stored in the scheduled job XML file.</span></span> <span data-ttu-id="a53cc-152">Vous pouvez définir des options de tâche lorsque vous créez une tâche planifiée ou que vous modifiez à tout moment.</span><span class="sxs-lookup"><span data-stu-id="a53cc-152">You can set job options when you create a scheduled job or change them at any time.</span></span>

<span data-ttu-id="a53cc-153">L' `New-ScheduledJobOption` applet de commande crée une option de tâche planifiée dans laquelle l’option de tâche planifiée **WakeToRun** a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="a53cc-153">The `New-ScheduledJobOption` cmdlet creates a scheduled job option in which the **WakeToRun** scheduled job option is set to True.</span></span> <span data-ttu-id="a53cc-154">L’option **WakeToRun** exécute la tâche planifiée même si l’ordinateur est en mode veille ou veille prolongée à l’heure de début planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-154">The **WakeToRun** option runs the scheduled job even if the computer is in the Sleep or Hibernate state at the scheduled start time.</span></span> <span data-ttu-id="a53cc-155">La commande enregistre les options de tâche dans la `$O` variable.</span><span class="sxs-lookup"><span data-stu-id="a53cc-155">The command saves the job options in the `$O` variable.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a><span data-ttu-id="a53cc-156">Comment récupérer des options de tâche</span><span class="sxs-lookup"><span data-stu-id="a53cc-156">How to get job options</span></span>

<span data-ttu-id="a53cc-157">Pour obtenir les options de tâche d’une tâche planifiée, utilisez l’applet de commande `Get-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-157">To get the job options of a scheduled job, use the `Get-ScheduledJobOption` cmdlet.</span></span> <span data-ttu-id="a53cc-158">Utilisez les paramètres **Name** , **ID** et **InputObject** pour spécifier la tâche planifiée, et non les options du travail.</span><span class="sxs-lookup"><span data-stu-id="a53cc-158">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job options.</span></span>

<span data-ttu-id="a53cc-159">`Get-ScheduledJobOption` Obtient les options de tâche du **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="a53cc-159">`Get-ScheduledJobOption` gets the job options of the **ProcessJob** .</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
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

## <a name="how-to-change-job-options"></a><span data-ttu-id="a53cc-160">Comment modifier les options d’un travail</span><span class="sxs-lookup"><span data-stu-id="a53cc-160">How to change job options</span></span>

<span data-ttu-id="a53cc-161">Vous pouvez modifier les options de tâche d’une tâche planifiée lorsque vous créez une tâche planifiée ou modifiez une tâche existante.</span><span class="sxs-lookup"><span data-stu-id="a53cc-161">You can change the job options of a scheduled job when you create a scheduled job or edit an existing job.</span></span>

<span data-ttu-id="a53cc-162">Le `$JobParms` projet de tâche est passé à l' `Add-JobTrigger` applet de commande pour créer le travail de processus.</span><span class="sxs-lookup"><span data-stu-id="a53cc-162">The splatted `$JobParms` are passed to the `Add-JobTrigger` cmdlet to create the process job.</span></span> <span data-ttu-id="a53cc-163">Elle utilise le paramètre **ScheduledJobOption** pour spécifier les options de tâche dans la `$O` variable.</span><span class="sxs-lookup"><span data-stu-id="a53cc-163">It uses the **ScheduledJobOption** parameter to specify the job options in the `$O` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

<span data-ttu-id="a53cc-164">Vous pouvez également modifier les options de travail en fonction d’une tâche planifiée existante à tout moment.</span><span class="sxs-lookup"><span data-stu-id="a53cc-164">You can also change the job options to an existing scheduled job at any time.</span></span>
<span data-ttu-id="a53cc-165">La commande suivante utilise l' `Set-ScheduledJobOption` applet de commande pour modifier la valeur de l’option **WakeToRun** de **ProcessJob** scheduledJob sur **true** .</span><span class="sxs-lookup"><span data-stu-id="a53cc-165">The following command uses the `Set-ScheduledJobOption` cmdlet to change the value of the **WakeToRun** option of the **ProcessJob** scheduledJob to **True** .</span></span>

<span data-ttu-id="a53cc-166">Les `Set` applets de commande du module **PSScheduledJob** , telles que l’applet de commande `Set-ScheduledJobOption` , n’ont pas de paramètres **Name** ou **ID** .</span><span class="sxs-lookup"><span data-stu-id="a53cc-166">The `Set` cmdlets in the **PSScheduledJob** module, such as the `Set-ScheduledJobOption` cmdlet, don't have **Name** or **ID** parameters.</span></span> <span data-ttu-id="a53cc-167">Vous pouvez utiliser le paramètre **InputObject** pour spécifier les options de tâche planifiée ou diriger une tâche planifiée de l' `Get-ScheduledJobOption` applet de commande vers `Set-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-167">You can use the **InputObject** parameter to specify the scheduled job options or pipe a scheduled job from `Get-ScheduledJobOption` cmdlet to `Set-ScheduledJobOption`.</span></span>

<span data-ttu-id="a53cc-168">Cet exemple utilise l' `Get-ScheduledJob` applet de commande pour récupérer ProcessJob.</span><span class="sxs-lookup"><span data-stu-id="a53cc-168">This example uses the `Get-ScheduledJob` cmdlet to get the ProcessJob.</span></span> <span data-ttu-id="a53cc-169">Elle utilise l' `Get-ScheduledJobOption` applet de commande pour récupérer les options de tâche dans le **ProcessJob** et l' `Set-ScheduledJobOption` applet de commande pour remplacer l’option de tâche **WakeToRun** dans le ProcessJob par true.</span><span class="sxs-lookup"><span data-stu-id="a53cc-169">It uses the `Get-ScheduledJobOption` cmdlet to get the job options in the **ProcessJob** and the `Set-ScheduledJobOption` cmdlet to change the **WakeToRun** job option in the ProcessJob to True.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a><span data-ttu-id="a53cc-170">Procédure d’obtention d’instances de tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="a53cc-170">How to get scheduled job instances</span></span>

<span data-ttu-id="a53cc-171">Lorsqu’une tâche planifiée est démarrée, PowerShell crée une instance de tâche similaire à une tâche en arrière-plan PowerShell standard.</span><span class="sxs-lookup"><span data-stu-id="a53cc-171">When a scheduled job is started, PowerShell creates a job instance that is similar to a standard PowerShell background job.</span></span> <span data-ttu-id="a53cc-172">Vous pouvez utiliser les applets de commande Job, telles que `Get-Job` , `Stop-Job` et `Receive-Job` pour gérer les instances de tâche.</span><span class="sxs-lookup"><span data-stu-id="a53cc-172">You can use the job cmdlets, such as `Get-Job`, `Stop-Job` and `Receive-Job` to manage the job instances.</span></span>

> [!NOTE]
> <span data-ttu-id="a53cc-173">Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session.</span><span class="sxs-lookup"><span data-stu-id="a53cc-173">To use the job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="a53cc-174">Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-174">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="a53cc-175">Pour récupérer toutes les instances de tâches planifiées PowerShell et tous les travaux standard actifs, utilisez l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-175">To get all instances of PowerShell scheduled jobs, and all active standard jobs, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="a53cc-176">L' `Import-Module` applet de commande importe le module **PSScheduledJob** et `Get-Job` obtient les tâches sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a53cc-176">The `Import-Module` cmdlet imports the **PSScheduledJob** module and `Get-Job` gets the jobs on the local computer.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job
```

<span data-ttu-id="a53cc-177">`Get-Job` obtient des instances de **ProcessJob** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a53cc-177">`Get-Job` gets instances of **ProcessJob** on the local computer.</span></span>

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

<span data-ttu-id="a53cc-178">L’affichage par défaut n’affiche pas l’heure de début, ce qui fait généralement la distinction entre les instances de la même tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-178">The default display does not show the start time, which typically distinguishes instances of the same scheduled job.</span></span>

<span data-ttu-id="a53cc-179">L' `Get-Job` applet de commande envoie des objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a53cc-179">The `Get-Job` cmdlet sends objects down the pipeline.</span></span> <span data-ttu-id="a53cc-180">L' `Format-Table` applet de commande affiche les propriétés **Name** , **ID** et **BeginTime** de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="a53cc-180">The `Format-Table` cmdlet displays the **Name** , **ID** , and **BeginTime** properties of the scheduled job.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

## <a name="get-scheduled-job-results"></a><span data-ttu-id="a53cc-181">Obtenir les résultats de la tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="a53cc-181">Get scheduled job results</span></span>

<span data-ttu-id="a53cc-182">Pour obtenir les résultats d’une instance d’une tâche planifiée, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-182">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="a53cc-183">Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session.</span><span class="sxs-lookup"><span data-stu-id="a53cc-183">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="a53cc-184">Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="a53cc-184">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="a53cc-185">Cet exemple obtient les résultats de l’instance la plus récente de la tâche planifiée **ProcessJob** (ID = 51).</span><span class="sxs-lookup"><span data-stu-id="a53cc-185">This examples gets the results of the newest instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

<span data-ttu-id="a53cc-186">Les résultats des tâches planifiées sont enregistrés sur le disque, donc le paramètre **Keep** de `Receive-Job` n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a53cc-186">The results of scheduled jobs are saved on disk, so the **Keep** parameter of `Receive-Job` is not required.</span></span> <span data-ttu-id="a53cc-187">Toutefois, sans le paramètre **Keep** , vous pouvez obtenir les résultats d’une tâche planifiée une seule fois dans chaque session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a53cc-187">However, without the **Keep** parameter, you can get the results of a scheduled job only once in each PowerShell session.</span></span> <span data-ttu-id="a53cc-188">Pour démarrer une nouvelle session PowerShell, tapez `PowerShell` ou ouvrez une nouvelle fenêtre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a53cc-188">To start a new PowerShell session, type `PowerShell` or open a new PowerShell window.</span></span>

## <a name="see-also"></a><span data-ttu-id="a53cc-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a53cc-189">See also</span></span>

[<span data-ttu-id="a53cc-190">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="a53cc-190">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="a53cc-191">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="a53cc-191">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="a53cc-192">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="a53cc-192">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="a53cc-193">about_Splatting. MD</span><span class="sxs-lookup"><span data-stu-id="a53cc-193">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="a53cc-194">Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)</span><span class="sxs-lookup"><span data-stu-id="a53cc-194">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="a53cc-195">Planificateur de tâches</span><span class="sxs-lookup"><span data-stu-id="a53cc-195">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
