---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203005"
---
# <span data-ttu-id="28f4d-103">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-103">Get-ScheduledJob</span></span>

## <span data-ttu-id="28f4d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="28f4d-104">SYNOPSIS</span></span>
<span data-ttu-id="28f4d-105">Obtient les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="28f4d-105">Gets scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="28f4d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="28f4d-106">SYNTAX</span></span>

### <span data-ttu-id="28f4d-107">Dotée DefinitionId (par défaut)</span><span class="sxs-lookup"><span data-stu-id="28f4d-107">DefinitionId (Default)</span></span>

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="28f4d-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="28f4d-108">DefinitionName</span></span>

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="28f4d-109">Description</span><span class="sxs-lookup"><span data-stu-id="28f4d-109">DESCRIPTION</span></span>
<span data-ttu-id="28f4d-110">L'applet de commande **Get-ScheduledJob** obtient les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="28f4d-110">The **Get-ScheduledJob** cmdlet gets scheduled jobs on the local computer.</span></span>
<span data-ttu-id="28f4d-111">La commande **ScheduledJob** obtient uniquement les tâches planifiées qui sont créées par l’utilisateur actuel à l’aide de l’applet de commande Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="28f4d-111">**Get-ScheduledJob** gets only scheduled jobs that are created by the current user using the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="28f4d-112">Même si les tâches qui sont créées à l'aide de l'applet de commande **Register-ScheduledJob** s'affichent dans le Planificateur de tâches, **Get-ScheduledJob** obtient uniquement les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="28f4d-112">Although jobs that are created by using the **Register-ScheduledJob** cmdlet appear in Task Scheduler, **Get-ScheduledJob** gets only scheduled jobs.</span></span>
<span data-ttu-id="28f4d-113">Elle n'obtient pas les tâches planifiées créées dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="28f4d-113">It does not get scheduled tasks created in Task Scheduler.</span></span>

<span data-ttu-id="28f4d-114">Sans paramètres, **Get-ScheduledJob** obtient toutes les tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28f4d-114">Without parameters, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="28f4d-115">Vous pouvez utiliser les paramètres de **Get-ScheduledJob** pour obtenir les tâches planifiées par ID ou nom et les examiner ou les diriger vers d'autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="28f4d-115">You can use the parameters of **Get-ScheduledJob** to get scheduled jobs by ID or name and examine them or pipe them to other cmdlets.</span></span>

<span data-ttu-id="28f4d-116">L’applet de commande **ScheduledJob** est une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28f4d-116">**Get-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="28f4d-117">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="28f4d-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="28f4d-118">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="28f4d-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="28f4d-119">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="28f4d-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="28f4d-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="28f4d-120">EXAMPLES</span></span>

### <span data-ttu-id="28f4d-121">Exemple 1 : récupération de tous les travaux planifiés</span><span class="sxs-lookup"><span data-stu-id="28f4d-121">Example 1: Get all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob
```

<span data-ttu-id="28f4d-122">Cette commande obtient toutes les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="28f4d-122">This command gets all scheduled jobs on the local computer.</span></span>

### <span data-ttu-id="28f4d-123">Exemple 2 : recevoir les tâches planifiées par nom</span><span class="sxs-lookup"><span data-stu-id="28f4d-123">Example 2: Get scheduled jobs by name</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

<span data-ttu-id="28f4d-124">Cette commande obtient toutes les tâches planifiées sur l’ordinateur dont les noms incluent la sauvegarde ou l’archivage.</span><span class="sxs-lookup"><span data-stu-id="28f4d-124">This command gets all scheduled jobs on the computer that have names that include Backup or Archive.</span></span>
<span data-ttu-id="28f4d-125">Ce format de commande vous permet de rechercher des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="28f4d-125">This command format lets you search for particular jobs.</span></span>

### <span data-ttu-id="28f4d-126">Exemple 3 : récupération de tâches planifiées sur des ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="28f4d-126">Example 3: Get scheduled jobs on remote computers</span></span>

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

<span data-ttu-id="28f4d-127">Cette commande obtient toutes les tâches planifiées sur les ordinateurs qui sont répertoriés dans le fichier Servers.txt.</span><span class="sxs-lookup"><span data-stu-id="28f4d-127">This command gets all scheduled jobs on the computers that are listed in the Servers.txt file.</span></span>
<span data-ttu-id="28f4d-128">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande **obtenir-ScheduleJob** sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28f4d-128">The command uses the Invoke-Command cmdlet to run a **Get-ScheduleJob** command on each computer.</span></span>

### <span data-ttu-id="28f4d-129">Exemple 4 : effectuer un canal des tâches planifiées vers d’autres applets de commande</span><span class="sxs-lookup"><span data-stu-id="28f4d-129">Example 4: Pipe scheduled jobs to other cmdlets</span></span>

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

<span data-ttu-id="28f4d-130">Cette commande obtient les déclencheurs des tâches planifiées DailyBackup et WeeklyBackup.</span><span class="sxs-lookup"><span data-stu-id="28f4d-130">This command gets the job triggers of the DailyBackup and WeeklyBackup scheduled jobs.</span></span>
<span data-ttu-id="28f4d-131">Elle utilise l’applet de commande **ScheduledJob** pour récupérer les tâches planifiées et l’applet de commande Get-JobTrigger pour recevoir les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="28f4d-131">It uses the **Get-ScheduledJob** cmdlet to get the scheduled jobs and the Get-JobTrigger cmdlet to get the job triggers of the scheduled jobs.</span></span>

## <span data-ttu-id="28f4d-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="28f4d-132">PARAMETERS</span></span>

### <span data-ttu-id="28f4d-133">-Id</span><span class="sxs-lookup"><span data-stu-id="28f4d-133">-Id</span></span>
<span data-ttu-id="28f4d-134">Obtient uniquement les tâches planifiées avec le numéro d'identification (ID) spécifié.</span><span class="sxs-lookup"><span data-stu-id="28f4d-134">Gets only the scheduled jobs with the specified identification number (ID).</span></span>
<span data-ttu-id="28f4d-135">Entrez un ou plusieurs ID de tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28f4d-135">Enter one or more IDs of scheduled jobs on the computer.</span></span>
<span data-ttu-id="28f4d-136">Par défaut, **Get-ScheduledJob** obtient toutes les tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28f4d-136">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28f4d-137">-Name</span><span class="sxs-lookup"><span data-stu-id="28f4d-137">-Name</span></span>
<span data-ttu-id="28f4d-138">Obtient uniquement les tâches planifiées avec les noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="28f4d-138">Gets only the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="28f4d-139">Entrez un ou plusieurs noms de tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28f4d-139">Enter one or more names of scheduled jobs on the computer.</span></span>
<span data-ttu-id="28f4d-140">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="28f4d-140">Wildcards are supported.</span></span>
<span data-ttu-id="28f4d-141">Par défaut, **Get-ScheduledJob** obtient toutes les tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28f4d-141">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28f4d-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28f4d-142">CommonParameters</span></span>
<span data-ttu-id="28f4d-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="28f4d-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28f4d-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="28f4d-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="28f4d-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="28f4d-145">INPUTS</span></span>

### <span data-ttu-id="28f4d-146">Aucun</span><span class="sxs-lookup"><span data-stu-id="28f4d-146">None</span></span>
<span data-ttu-id="28f4d-147">Vous ne pouvez pas diriger d’entrée vers **ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="28f4d-147">You cannot pipe input to **Get-ScheduledJob** .</span></span>

## <span data-ttu-id="28f4d-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="28f4d-148">OUTPUTS</span></span>

### <span data-ttu-id="28f4d-149">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="28f4d-149">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="28f4d-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="28f4d-150">NOTES</span></span>

* <span data-ttu-id="28f4d-151">Chaque tâche planifiée est enregistrée dans un sous-répertoire du répertoire $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="28f4d-151">Each scheduled job is saved in a subdirectory of the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the local computer.</span></span> <span data-ttu-id="28f4d-152">Le sous-répertoire est nommé pour la tâche planifiée et contient le fichier XML pour cette tâche et les enregistrements de son historique d'exécution.</span><span class="sxs-lookup"><span data-stu-id="28f4d-152">The subdirectory is named for the scheduled job and contains the XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="28f4d-153">Pour plus d'informations sur les tâches planifiées sur disque, consultez about_Scheduled_Jobs_Advanced.</span><span class="sxs-lookup"><span data-stu-id="28f4d-153">For more information about scheduled jobs on disk, see about_Scheduled_Jobs_Advanced.</span></span>
* <span data-ttu-id="28f4d-154">Les tâches planifiées que vous créez dans Windows PowerShell apparaissent dans le Planificateur de tâches dans le dossier Library\Microsoft\Windows\PowerShell\ScheduledJobs.</span><span class="sxs-lookup"><span data-stu-id="28f4d-154">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs folder.</span></span> <span data-ttu-id="28f4d-155">Vous pouvez utiliser le Planificateur de tâches pour afficher et modifier la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="28f4d-155">You can use Task Scheduler to view and edit the scheduled job.</span></span>
* <span data-ttu-id="28f4d-156">Vous pouvez utiliser le Planificateur de tâches, l'outil en ligne de commande SchTasks.exe et les applets de commande du Planificateur de tâches pour gérer les tâches planifiées que vous créez avec les applets de commande correspondantes.</span><span class="sxs-lookup"><span data-stu-id="28f4d-156">You can use Task Scheduler, the SchTasks.exe command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="28f4d-157">Toutefois, vous ne pouvez pas utiliser les applets de commande de la tâche planifiée pour gérer les tâches que vous créez dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="28f4d-157">However, you cannot use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

## <span data-ttu-id="28f4d-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="28f4d-158">RELATED LINKS</span></span>

[<span data-ttu-id="28f4d-159">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-159">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="28f4d-160">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-160">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="28f4d-161">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-161">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="28f4d-162">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-162">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="28f4d-163">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-163">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="28f4d-164">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-164">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="28f4d-165">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-165">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="28f4d-166">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="28f4d-166">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="28f4d-167">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-167">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="28f4d-168">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="28f4d-168">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="28f4d-169">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-169">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="28f4d-170">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-170">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="28f4d-171">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="28f4d-171">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="28f4d-172">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-172">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="28f4d-173">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="28f4d-173">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="28f4d-174">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="28f4d-174">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
