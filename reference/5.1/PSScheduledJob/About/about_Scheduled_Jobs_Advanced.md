---
description: Décrit les rubriques avancées sur les tâches planifiées, y compris la structure de fichier sous-jacente aux tâches planifiées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207254"
---
# <a name="about-scheduled-jobs-advanced"></a><span data-ttu-id="0721e-104">À propos des tâches planifiées avancées</span><span class="sxs-lookup"><span data-stu-id="0721e-104">About Scheduled Jobs Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="0721e-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="0721e-105">Short description</span></span>

<span data-ttu-id="0721e-106">Décrit les rubriques avancées sur les tâches planifiées, y compris la structure de fichier sous-jacente aux tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="0721e-106">Explains advanced scheduled job topics, including the file structure that underlies scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="0721e-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="0721e-107">Long description</span></span>

<span data-ttu-id="0721e-108">Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="0721e-108">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="scheduled-job-directories-and-files"></a><span data-ttu-id="0721e-109">Fichiers et répertoires de travail planifiés</span><span class="sxs-lookup"><span data-stu-id="0721e-109">Scheduled job directories and files</span></span>

<span data-ttu-id="0721e-110">Les tâches planifiées PowerShell sont à la fois des travaux PowerShell et des tâches de Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="0721e-110">PowerShell scheduled jobs are both PowerShell jobs and Task Scheduler tasks.</span></span>
<span data-ttu-id="0721e-111">Chaque tâche planifiée est enregistrée dans Planificateur de tâches et enregistrée sur le disque au format XML de sérialisation Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0721e-111">Each scheduled job is registered in Task Scheduler and saved on disk in Microsoft .NET Framework Serialization XML format.</span></span>

<span data-ttu-id="0721e-112">Lorsque vous créez une tâche planifiée, PowerShell crée un répertoire pour la tâche planifiée dans le `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` Répertoire de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0721e-112">When you create a scheduled job, PowerShell creates a directory for the scheduled job in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span> <span data-ttu-id="0721e-113">Le nom du répertoire est le même que le nom du travail.</span><span class="sxs-lookup"><span data-stu-id="0721e-113">The directory name is the same as the job name.</span></span>

<span data-ttu-id="0721e-114">Voici un exemple de répertoire **ScheduledJobs** .</span><span class="sxs-lookup"><span data-stu-id="0721e-114">The following is a sample **ScheduledJobs** directory.</span></span>

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

<span data-ttu-id="0721e-115">Chaque tâche planifiée a son propre répertoire.</span><span class="sxs-lookup"><span data-stu-id="0721e-115">Each scheduled job has its own directory.</span></span> <span data-ttu-id="0721e-116">Le répertoire contient le fichier XML de la tâche planifiée et un sous-répertoire de **sortie** .</span><span class="sxs-lookup"><span data-stu-id="0721e-116">The directory contains the scheduled job XML file and an **Output** subdirectory.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

<span data-ttu-id="0721e-117">Le répertoire de **sortie** d’une tâche planifiée contient son historique d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0721e-117">The **Output** directory for a scheduled job contains its execution history.</span></span>
<span data-ttu-id="0721e-118">Chaque fois qu’un déclencheur de tâche démarre une tâche planifiée, PowerShell crée un répertoire nommé timestamp dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="0721e-118">Each time a job trigger starts a scheduled job, PowerShell creates a timestamp-named directory in the output directory.</span></span> <span data-ttu-id="0721e-119">Le répertoire horodateur contient les résultats de la tâche dans un fichier **Results.xml** et l’état du travail dans un fichier **Status.xml** .</span><span class="sxs-lookup"><span data-stu-id="0721e-119">The timestamp directory contains the results of the job in a **Results.xml** file and the job status in a **Status.xml** file.</span></span>

<span data-ttu-id="0721e-120">La commande suivante affiche les répertoires d’historique d’exécution pour la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0721e-120">The following command shows the execution history directories for the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

<span data-ttu-id="0721e-121">Vous pouvez ouvrir et examiner les fichiers **ScheduledJobDefinition.xml** , **Results.xml** et **Status.xml** ou utiliser l' `Select-XML` applet de commande pour analyser les fichiers.</span><span class="sxs-lookup"><span data-stu-id="0721e-121">You can open and examine the **ScheduledJobDefinition.xml** , **Results.xml** and **Status.xml** files or use the `Select-XML` cmdlet to parse the files.</span></span>

> [!WARNING]
> <span data-ttu-id="0721e-122">Ne modifiez pas les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="0721e-122">Do not edit the XML files.</span></span> <span data-ttu-id="0721e-123">Si un fichier XML contient du code XML non valide, PowerShell supprime la tâche planifiée et son historique d’exécution, y compris les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="0721e-123">If any XML file contains invalid XML, PowerShell deletes the scheduled job and its execution history, including job results.</span></span>

## <a name="start-a-scheduled-job-immediately"></a><span data-ttu-id="0721e-124">Démarrer immédiatement une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="0721e-124">Start a scheduled job immediately</span></span>

<span data-ttu-id="0721e-125">Vous pouvez démarrer une tâche planifiée immédiatement de l’une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="0721e-125">You can start a scheduled job immediately in one of two ways:</span></span>

- <span data-ttu-id="0721e-126">Exécutez l' `Start-Job` applet de commande pour démarrer une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-126">Run the `Start-Job` cmdlet to start any scheduled job.</span></span>
- <span data-ttu-id="0721e-127">Ajoutez le paramètre **RunNow** à votre `Register-ScheduledJob` commande pour démarrer le travail dès que la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="0721e-127">Add the **RunNow** parameter to your `Register-ScheduledJob` command to start the job as soon as the command is run.</span></span>

<span data-ttu-id="0721e-128">Les tâches démarrées à l’aide de l' `Start-Job` applet de commande sont des travaux en arrière-plan PowerShell standard, et non des instances de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-128">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="0721e-129">Comme pour toutes les tâches en arrière-plan, ces travaux démarrent immédiatement, ils ne sont pas soumis à des options de travail ou affectés par des déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="0721e-129">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers.</span></span> <span data-ttu-id="0721e-130">La sortie du travail n’est pas enregistrée dans le répertoire de **sortie** du répertoire de travail planifié.</span><span class="sxs-lookup"><span data-stu-id="0721e-130">The job output isn't saved in the **Output** directory of the scheduled job directory.</span></span>

<span data-ttu-id="0721e-131">La commande suivante utilise le paramètre **DefinitionName** de l' `Start-Job` applet de commande pour démarrer la tâche planifiée ProcessJob.</span><span class="sxs-lookup"><span data-stu-id="0721e-131">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the ProcessJob scheduled job.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="0721e-132">Pour gérer le travail et obtenir les résultats du travail, utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="0721e-132">To manage the job and get the job results, use the job cmdlets.</span></span> <span data-ttu-id="0721e-133">Pour plus d’informations sur les applets de commande Job, consultez [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="0721e-133">For more information about the job cmdlets, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0721e-134">Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session.</span><span class="sxs-lookup"><span data-stu-id="0721e-134">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="0721e-135">Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0721e-135">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

## <a name="rename-a-scheduled-job"></a><span data-ttu-id="0721e-136">Renommer une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="0721e-136">Rename a scheduled job</span></span>

<span data-ttu-id="0721e-137">Pour renommer une tâche planifiée, utilisez le paramètre Name de l’applet de commande `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0721e-137">To rename a scheduled job, use the Name parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="0721e-138">Lorsque vous renommez une tâche planifiée, PowerShell modifie le nom de la tâche planifiée et le répertoire de travail planifié.</span><span class="sxs-lookup"><span data-stu-id="0721e-138">When you rename a scheduled job, PowerShell changes the name of the scheduled job and the scheduled job directory.</span></span> <span data-ttu-id="0721e-139">Toutefois, il ne modifie pas les noms des instances de la tâche planifiée qui ont déjà été exécutées.</span><span class="sxs-lookup"><span data-stu-id="0721e-139">However, it doesn't change the names of instances of the scheduled job that have already run.</span></span>

## <a name="get-start-and-end-times"></a><span data-ttu-id="0721e-140">Obtenez des heures de début et de fin</span><span class="sxs-lookup"><span data-stu-id="0721e-140">Get start and end times</span></span>

<span data-ttu-id="0721e-141">Pour obtenir les dates et heures de début et de fin des instances de tâche, utilisez les propriétés **PSBeginTime** et **PSEndTime** de l’objet ScheduledJob qui `Get-Job` retourne pour les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="0721e-141">To get the dates and times that job instances started and ended, use the **PSBeginTime** and **PSEndTime** properties of the ScheduledJob object that `Get-Job` returns for scheduled jobs.</span></span>

<span data-ttu-id="0721e-142">L’exemple suivant utilise le paramètre **Property** de l' `Format-Table` applet de commande pour afficher les propriétés **PSBeginTime** et **PSEndTime** de chaque instance de tâche dans une table.</span><span class="sxs-lookup"><span data-stu-id="0721e-142">The following example uses the **Property** parameter of the `Format-Table` cmdlet to display the **PSBeginTime** and **PSEndTime** properties of each job instance in a table.</span></span> <span data-ttu-id="0721e-143">Une propriété calculée nommée **label** affiche le temps écoulé de chaque instance de tâche.</span><span class="sxs-lookup"><span data-stu-id="0721e-143">A calculated property named **Label** displays the elapsed time of each job instance.</span></span>

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a><span data-ttu-id="0721e-144">Gérer l’historique d’exécution</span><span class="sxs-lookup"><span data-stu-id="0721e-144">Manage execution history</span></span>

<span data-ttu-id="0721e-145">Vous pouvez déterminer le nombre de résultats d’instance de tâche qui sont enregistrés pour chaque tâche planifiée et supprimer l’historique d’exécution et les résultats de travail enregistrés d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-145">You can determine the number of job instance results that are saved for each scheduled job and delete the execution history and saved job results of any scheduled job.</span></span>

<span data-ttu-id="0721e-146">La propriété **ExecutionHistoryLength** d’une tâche planifiée détermine le nombre de résultats d’instance de tâche qui sont enregistrés pour la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-146">The **ExecutionHistoryLength** property of a scheduled job determines how many job instance results are saved for the scheduled job.</span></span> <span data-ttu-id="0721e-147">Lorsque le nombre de résultats enregistrés dépasse la valeur de la propriété **ExecutionHistoryLength** , PowerShell supprime les résultats de l’instance la plus ancienne pour libérer de l’espace pour les résultats de l’instance la plus récente.</span><span class="sxs-lookup"><span data-stu-id="0721e-147">When the number of saved results exceeds the value of the **ExecutionHistoryLength** property, PowerShell deletes the results of the oldest instance to make room for the results of the newest instance.</span></span>

<span data-ttu-id="0721e-148">Par défaut, PowerShell enregistre l’historique d’exécution et les résultats des instances 32 de chaque tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-148">By default, PowerShell saves the execution history and results of 32 instances of each scheduled job.</span></span> <span data-ttu-id="0721e-149">Pour modifier cette valeur, utilisez les paramètres **MaxResultCount** des applets de commande `Register-ScheduledJob` ou `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0721e-149">To change that value, use the **MaxResultCount** parameters of the `Register-ScheduledJob` or `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="0721e-150">Pour supprimer l’historique d’exécution et tous les résultats d’une tâche planifiée, utilisez le paramètre **ClearExecutionHistory** de l’applet de commande `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0721e-150">To delete the execution history and all results for a scheduled job, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="0721e-151">La suppression de cet historique d’exécution n’empêche pas PowerShell d’enregistrer les résultats des nouvelles instances de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-151">Deleting this execution history does not prevent PowerShell from saving the results of new instances of the scheduled job.</span></span>

<span data-ttu-id="0721e-152">L’exemple suivant utilise la projection pour créer `$JobParms` des valeurs de paramètre qui sont passées à l’applet de commande `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0721e-152">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="0721e-153">Pour plus d’informations, consultez [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="0721e-153">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="0721e-154">Le `Register-ScheduledJob` utilise `@JobParms` pour créer une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-154">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="0721e-155">La commande utilise le paramètre **MaxResultCount** avec la valeur 12 pour enregistrer uniquement les 12 résultats les plus récents de l’instance de tâche de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0721e-155">The command uses the **MaxResultCount** parameter with a value of 12 to save only the 12 newest job instance results of the scheduled job.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="0721e-156">La commande suivante utilise le paramètre **MaxResultCount** de l' `Set-ScheduledJob` applet de commande pour augmenter le nombre de résultats d’instance enregistrés à</span><span class="sxs-lookup"><span data-stu-id="0721e-156">The following command uses the **MaxResultCount** parameter of the `Set-ScheduledJob` cmdlet to increase the number of saved instance results to</span></span>
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

<span data-ttu-id="0721e-157">La commande suivante supprime l’historique d’exécution et les résultats actuellement enregistrés de la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0721e-157">The following command deletes the execution history and the current saved results of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="0721e-158">La commande suivante obtient les valeurs des propriétés Name et **ExecutionHistoryLength** de toutes les tâches planifiées sur l’ordinateur et les affiche dans une table.</span><span class="sxs-lookup"><span data-stu-id="0721e-158">The following command gets the values of the name and **ExecutionHistoryLength** properties of all scheduled jobs on the computer and displays them in a table.</span></span>

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a><span data-ttu-id="0721e-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0721e-159">See also</span></span>

[<span data-ttu-id="0721e-160">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="0721e-160">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="0721e-161">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="0721e-161">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="0721e-162">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="0721e-162">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="0721e-163">about_Splatting. MD</span><span class="sxs-lookup"><span data-stu-id="0721e-163">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="0721e-164">Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)</span><span class="sxs-lookup"><span data-stu-id="0721e-164">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="0721e-165">Planificateur de tâches</span><span class="sxs-lookup"><span data-stu-id="0721e-165">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
