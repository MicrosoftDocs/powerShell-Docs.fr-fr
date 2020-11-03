---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203001"
---
# <span data-ttu-id="f4514-103">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f4514-103">Get-ScheduledJobOption</span></span>

## <span data-ttu-id="f4514-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f4514-104">SYNOPSIS</span></span>
<span data-ttu-id="f4514-105">Obtient les options de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f4514-105">Gets the job options of scheduled jobs.</span></span>

## <span data-ttu-id="f4514-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f4514-106">SYNTAX</span></span>

### <span data-ttu-id="f4514-107">JobDefinition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f4514-107">JobDefinition (Default)</span></span>

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="f4514-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="f4514-108">JobDefinitionId</span></span>

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="f4514-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="f4514-109">JobDefinitionName</span></span>

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="f4514-110">Description</span><span class="sxs-lookup"><span data-stu-id="f4514-110">DESCRIPTION</span></span>
<span data-ttu-id="f4514-111">L’applet de commande **obtenir-ScheduledJobOption** obtient les options de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f4514-111">The **Get-ScheduledJobOption** cmdlet gets the job options of scheduled jobs.</span></span>
<span data-ttu-id="f4514-112">Vous pouvez utiliser cette commande pour examiner les options de tâche ou pour les diriger vers d'autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="f4514-112">You can use this command to examine the job options or to pipe the job options to other cmdlets.</span></span>

<span data-ttu-id="f4514-113">Les options de tâche ne sont pas enregistrées sur le disque de manière indépendante ; elles font partie d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-113">Job options are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="f4514-114">Pour obtenir les options d'une tâche planifiée, indiquez la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-114">To get the job options of a scheduled job, specify the scheduled job.</span></span>

<span data-ttu-id="f4514-115">Utilisez les paramètres de l'applet de commande **Get-ScheduledJobOption** pour identifier la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-115">Use the parameters of the **Get-ScheduledJobOption** cmdlet to identify the scheduled job.</span></span>
<span data-ttu-id="f4514-116">Vous pouvez identifier les tâches planifiées par leur nom ou leur numéro d’identification, ou en entrant ou en canalisant des objets **ScheduledJob** , tels que ceux retournés par l’applet de commande Get-ScheduledJob, sur **ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="f4514-116">You can identify scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-ScheduledJobOption** .</span></span>

<span data-ttu-id="f4514-117">L’applet de commande **ScheduledJobOption** est une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4514-117">**Get-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="f4514-118">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="f4514-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="f4514-119">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="f4514-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="f4514-120">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f4514-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f4514-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f4514-121">EXAMPLES</span></span>

### <span data-ttu-id="f4514-122">Exemple 1 : options d’extraction de tâche</span><span class="sxs-lookup"><span data-stu-id="f4514-122">Example 1: Get job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : False

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="f4514-123">Cette commande obtient les options de tâche des tâches planifiées dont le nom contient BackUp.</span><span class="sxs-lookup"><span data-stu-id="f4514-123">This command gets the job options of scheduled jobs that have BackUp in their names.</span></span>
<span data-ttu-id="f4514-124">Les résultats affichent l'objet d'options de tâche retourné par **Get-ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="f4514-124">The results show the job options object that **Get-ScheduledJobOption** returned.</span></span>

### <span data-ttu-id="f4514-125">Exemple 2 : récupération de toutes les options de tâche</span><span class="sxs-lookup"><span data-stu-id="f4514-125">Example 2: Get all job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

<span data-ttu-id="f4514-126">Cette commande obtient les options de toutes les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f4514-126">This command gets the job options of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="f4514-127">Elle utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f4514-127">It uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="f4514-128">Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande **ScheduledJobOption** , qui obtient les options de chaque tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-128">A pipeline operator (|) sends the scheduled jobs to the **Get-ScheduledJobOption** cmdlet, which gets the job options of each scheduled job.</span></span>

### <span data-ttu-id="f4514-129">Exemple 3 : récupérer les options de la tâche sélectionnée</span><span class="sxs-lookup"><span data-stu-id="f4514-129">Example 3: Get selected job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

<span data-ttu-id="f4514-130">Cet exemple montre comment rechercher l'objet d'options de tâche avec des valeurs particulières.</span><span class="sxs-lookup"><span data-stu-id="f4514-130">This example shows how to find job options object with particular values.</span></span>

<span data-ttu-id="f4514-131">La première commande obtient les options de travail dans lesquelles la propriété RunElevated a la valeur $True et la propriété RunWithoutNetwork a la valeur $False.</span><span class="sxs-lookup"><span data-stu-id="f4514-131">The first command gets job options in which the RunElevated property has a value of $True and the RunWithoutNetwork property has a value of $False.</span></span>
<span data-ttu-id="f4514-132">La sortie indique l’objet **JobOptions** qui a été sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f4514-132">The output shows the **JobOptions** object that was selected.</span></span>

### <span data-ttu-id="f4514-133">Exemple 4 : utiliser des options de tâche pour créer une tâche</span><span class="sxs-lookup"><span data-stu-id="f4514-133">Example 4: Use job options to create a new job</span></span>

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

<span data-ttu-id="f4514-134">Cet exemple montre comment utiliser les options de tâche que Get-ScheduledJobOption obtient dans une nouvelle tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-134">This example shows how to use the job options that Get-ScheduledJobOption gets in a new scheduled job.</span></span>

<span data-ttu-id="f4514-135">La première commande utilise la commande **ScheduledJobOption** pour accéder aux options de tâches de la tâche planifiée BackupTestLogs.</span><span class="sxs-lookup"><span data-stu-id="f4514-135">The first command uses **Get-ScheduledJobOption** to get the jobs options of the BackupTestLogs scheduled job.</span></span>
<span data-ttu-id="f4514-136">La commande enregistre les options dans la variable $Opts.</span><span class="sxs-lookup"><span data-stu-id="f4514-136">The command saves the options in the $Opts variable.</span></span>

<span data-ttu-id="f4514-137">La deuxième commande utilise Register-ScheduledJob applet de commande pour créer une nouvelle tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-137">The second command uses Register-ScheduledJob cmdlet to create a new scheduled job.</span></span>
<span data-ttu-id="f4514-138">La valeur du paramètre *ScheduledJobOption* est l'objet d'options dans la variable $Opts.</span><span class="sxs-lookup"><span data-stu-id="f4514-138">The value of the *ScheduledJobOption* parameter is the options object in the $Opts variable.</span></span>

### <span data-ttu-id="f4514-139">Exemple 5 : obtenir les options d’un travail à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="f4514-139">Example 5: Get job options from a remote computer</span></span>

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

<span data-ttu-id="f4514-140">Cette commande utilise l’applet de commande Invoke-Command pour accéder aux options de tâche planifiée de la tâche DataDemon sur l’ordinateur Srv01.</span><span class="sxs-lookup"><span data-stu-id="f4514-140">This command uses the Invoke-Command cmdlet to get the scheduled job options of the DataDemon job on the Srv01 computer.</span></span>
<span data-ttu-id="f4514-141">La commande enregistre les options dans la variable $O.</span><span class="sxs-lookup"><span data-stu-id="f4514-141">The command saves the options in the $O variable.</span></span>

## <span data-ttu-id="f4514-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4514-142">PARAMETERS</span></span>

### <span data-ttu-id="f4514-143">-Id</span><span class="sxs-lookup"><span data-stu-id="f4514-143">-Id</span></span>
<span data-ttu-id="f4514-144">Spécifie le numéro d'identification d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-144">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="f4514-145">**Get-ScheduledJobOption** obtient les options de la tâche planifiée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-145">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>

<span data-ttu-id="f4514-146">Pour obtenir les numéros d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="f4514-146">To get the identification numbers of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4514-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f4514-147">-InputObject</span></span>
<span data-ttu-id="f4514-148">Spécifie une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-148">Specifies a scheduled job.</span></span>
<span data-ttu-id="f4514-149">Entrez une variable qui contient un objet **ScheduledJob** ou tapez une commande ou une expression qui obtient un objet **ScheduledJob** , tel qu’une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="f4514-149">Enter a variable that contains a **ScheduledJob** object or type a command or expression that gets a **ScheduledJob** object, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="f4514-150">Vous pouvez également acheminer par canal un objet **ScheduledJob** vers **Get-ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="f4514-150">You can also pipe a **ScheduledJob** object to **Get-ScheduledJobOption** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4514-151">-Name</span><span class="sxs-lookup"><span data-stu-id="f4514-151">-Name</span></span>
<span data-ttu-id="f4514-152">Spécifie les noms des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f4514-152">Specifies the names of scheduled jobs.</span></span>
<span data-ttu-id="f4514-153">**Get-ScheduledJobOption** obtient les options de la tâche planifiée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f4514-153">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>
<span data-ttu-id="f4514-154">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f4514-154">Wildcards are supported.</span></span>

<span data-ttu-id="f4514-155">Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="f4514-155">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4514-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4514-156">CommonParameters</span></span>
<span data-ttu-id="f4514-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4514-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4514-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f4514-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4514-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f4514-159">INPUTS</span></span>

### <span data-ttu-id="f4514-160">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="f4514-160">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="f4514-161">Vous pouvez diriger une tâche planifiée à partir de Get-ScheduledJob vers **ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="f4514-161">You can pipe a scheduled job from Get-ScheduledJob to **Get-ScheduledJobOption** .</span></span>

## <span data-ttu-id="f4514-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f4514-162">OUTPUTS</span></span>

### <span data-ttu-id="f4514-163">Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="f4514-163">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="f4514-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f4514-164">NOTES</span></span>

## <span data-ttu-id="f4514-165">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f4514-165">RELATED LINKS</span></span>

[<span data-ttu-id="f4514-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="f4514-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="f4514-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f4514-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="f4514-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="f4514-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f4514-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="f4514-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="f4514-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f4514-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="f4514-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f4514-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="f4514-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="f4514-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f4514-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="f4514-176">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f4514-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="f4514-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="f4514-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f4514-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="f4514-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f4514-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="f4514-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f4514-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="f4514-181">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f4514-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
