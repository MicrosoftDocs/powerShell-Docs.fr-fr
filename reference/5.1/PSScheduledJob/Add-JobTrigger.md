---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203034"
---
# <span data-ttu-id="57548-103">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-103">Add-JobTrigger</span></span>

## <span data-ttu-id="57548-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="57548-104">SYNOPSIS</span></span>
<span data-ttu-id="57548-105">Ajoute des déclencheurs aux tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-105">Adds job triggers to scheduled jobs.</span></span>

## <span data-ttu-id="57548-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="57548-106">SYNTAX</span></span>

### <span data-ttu-id="57548-107">JobDefinition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="57548-107">JobDefinition (Default)</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### <span data-ttu-id="57548-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="57548-108">JobDefinitionId</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="57548-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="57548-109">JobDefinitionName</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="57548-110">Description</span><span class="sxs-lookup"><span data-stu-id="57548-110">DESCRIPTION</span></span>
<span data-ttu-id="57548-111">L'applet de commande **Add-JobTrigger** ajoute des déclencheurs aux tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-111">The **Add-JobTrigger** cmdlet adds job triggers to scheduled jobs.</span></span>
<span data-ttu-id="57548-112">Vous pouvez l'utiliser pour ajouter plusieurs déclencheurs à plusieurs tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-112">You can use it to add multiple triggers to multiple scheduled jobs.</span></span>

<span data-ttu-id="57548-113">Un déclencheur de tâche démarre une tâche planifiée selon une planification ponctuelle ou périodique, ou quand un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="57548-113">A job trigger starts a scheduled job on a one-time or recurring schedule or when an event occurs.</span></span>

<span data-ttu-id="57548-114">Utilisez le paramètre *Trigger* de **Add-JobTrigger** pour identifier les déclencheurs de tâche à ajouter.</span><span class="sxs-lookup"><span data-stu-id="57548-114">Use the *Trigger* parameter of **Add-JobTrigger** to identify the job triggers to add.</span></span>
<span data-ttu-id="57548-115">Utilisez les paramètres *Name* , *ID* ou *InputObject* de **Add-JobTrigger** pour identifier la tâche planifiée à laquelle les déclencheurs sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="57548-115">Use the *Name* , *ID* , or *InputObject* parameters of **Add-JobTrigger** to identify the scheduled job to which the triggers are added.</span></span>

<span data-ttu-id="57548-116">Pour créer des déclencheurs de tâche pour la valeur du paramètre *Trigger* , utilisez l’applet de commande New-JobTrigger ou utilisez une table de hachage pour spécifier le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="57548-116">To create job triggers for the value of the *Trigger* parameter, use the New-JobTrigger cmdlet or use a hash table to specify the job trigger.</span></span>

<span data-ttu-id="57548-117">**Add-JobTrigger** fait partie d’une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57548-117">**Add-JobTrigger** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="57548-118">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="57548-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="57548-119">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="57548-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="57548-120">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="57548-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="57548-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="57548-121">EXAMPLES</span></span>

### <span data-ttu-id="57548-122">Exemple 1 : ajouter un déclencheur de tâche à une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="57548-122">Example 1: Add a job trigger to a scheduled job</span></span>

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

<span data-ttu-id="57548-123">Ces commandes ajoutent le déclencheur Daily à la tâche planifiée TestJob.</span><span class="sxs-lookup"><span data-stu-id="57548-123">These commands add the Daily job trigger to the TestJob scheduled job.</span></span>

<span data-ttu-id="57548-124">La première commande utilise l’applet de commande New-JobTrigger pour créer un déclencheur de tâche qui démarre une tâche planifiée tous les jours à 3:00 h 00.</span><span class="sxs-lookup"><span data-stu-id="57548-124">The first command uses the New-JobTrigger cmdlet to create a job trigger that starts a scheduled job every day at 3:00 a.m.</span></span>
<span data-ttu-id="57548-125">La commande enregistre le déclencheur de tâche dans la variable $Daily.</span><span class="sxs-lookup"><span data-stu-id="57548-125">The command saves the job trigger in the $Daily variable.</span></span>

<span data-ttu-id="57548-126">La deuxième commande utilise l'applet de commande **Add-JobTrigger** pour ajouter le déclencheur de tâche de la variable $Startup à la tâche planifiée TestJob.</span><span class="sxs-lookup"><span data-stu-id="57548-126">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in the $Startup variable to the TestJob scheduled job.</span></span>

### <span data-ttu-id="57548-127">Exemple 2 : ajout d’un déclencheur de tâche à plusieurs tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="57548-127">Example 2: Add a job trigger to several scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

<span data-ttu-id="57548-128">Cette commande ajoute un déclencheur de tâche AtStartup à toutes les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="57548-128">This command adds an AtStartup job trigger to all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="57548-129">Il utilise la Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="57548-129">It uses the Get-ScheduledJob to get all of the scheduled jobs on the computer.</span></span>
<span data-ttu-id="57548-130">Elle utilise un opérateur pipeline (|) pour envoyer les tâches à l'applet de commande **Add-JobTrigger** , qui ajoute le déclencheur à chacune des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-130">It uses a pipeline operator (|) to send the jobs to the **Add-JobTrigger** cmdlet, which adds the job trigger to each of the scheduled jobs.</span></span>
<span data-ttu-id="57548-131">La valeur du paramètre *Trigger* est une commande New-JobTrigger qui crée le déclencheur de tâche AtStartup.</span><span class="sxs-lookup"><span data-stu-id="57548-131">The value of the *Trigger* parameter is a New-JobTrigger command that creates the AtStartup job trigger.</span></span>

### <span data-ttu-id="57548-132">Exemple 3 : copier un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="57548-132">Example 3: Copy a job trigger</span></span>

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

<span data-ttu-id="57548-133">Ces commandes copient le déclencheur de tâche de la tâche planifiée BackupArchives et l'ajoutent aux tâches planifiées TestBackup et BackupLogs.</span><span class="sxs-lookup"><span data-stu-id="57548-133">These commands copy the job trigger from the BackupArchives scheduled job and add it to the TestBackup and BackupLogs scheduled jobs.</span></span>

<span data-ttu-id="57548-134">La première commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de la tâche planifiée BackupArchives.</span><span class="sxs-lookup"><span data-stu-id="57548-134">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the BackupArchives scheduled job.</span></span>
<span data-ttu-id="57548-135">La commande enregistre le déclencheur dans la variable $t.</span><span class="sxs-lookup"><span data-stu-id="57548-135">The command saves the trigger in the $t variable.</span></span>

<span data-ttu-id="57548-136">La deuxième commande utilise l'applet de commande **Add-JobTrigger** pour ajouter le déclencheur de tâche dans $t aux tâches planifiées TestBackup et BackupLogs.</span><span class="sxs-lookup"><span data-stu-id="57548-136">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in $t to the TestBackup and BackupLogs scheduled jobs.</span></span>

## <span data-ttu-id="57548-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="57548-137">PARAMETERS</span></span>

### <span data-ttu-id="57548-138">-Id</span><span class="sxs-lookup"><span data-stu-id="57548-138">-Id</span></span>
<span data-ttu-id="57548-139">Spécifie les numéros d'identification des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-139">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="57548-140">**Add-JobTrigger** ajoute les déclencheurs aux tâches planifiées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-140">**Add-JobTrigger** adds the job trigger to the specified scheduled jobs.</span></span>

<span data-ttu-id="57548-141">Pour obtenir le numéro d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="57548-141">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="57548-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="57548-142">-InputObject</span></span>
<span data-ttu-id="57548-143">Spécifie les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-143">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="57548-144">Entrez une variable qui contient des objets **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="57548-144">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="57548-145">Vous pouvez également diriger les objets **ScheduledJob** vers **Add-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="57548-145">You can also pipe **ScheduledJob** objects to **Add-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="57548-146">-Name</span><span class="sxs-lookup"><span data-stu-id="57548-146">-Name</span></span>
<span data-ttu-id="57548-147">Spécifie les noms des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-147">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="57548-148">**Add-JobTrigger** ajoute les déclencheurs aux tâches planifiées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="57548-148">**Add-JobTrigger** adds the job triggers to the specified scheduled jobs.</span></span>
<span data-ttu-id="57548-149">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="57548-149">Wildcards are supported.</span></span>

<span data-ttu-id="57548-150">Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="57548-150">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="57548-151">-Déclencheur</span><span class="sxs-lookup"><span data-stu-id="57548-151">-Trigger</span></span>
<span data-ttu-id="57548-152">Spécifie les déclencheurs de tâche à ajouter.</span><span class="sxs-lookup"><span data-stu-id="57548-152">Specifies the job triggers to add.</span></span>
<span data-ttu-id="57548-153">Entrez une table de hachage qui spécifie les déclencheurs de tâche ou une variable qui contient des objets **ScheduledJobTrigger** , ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.</span><span class="sxs-lookup"><span data-stu-id="57548-153">Enter a hash table that specifies job triggers or a variable that contains **ScheduledJobTrigger** objects, or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="57548-154">Vous pouvez également diriger les objets **ScheduledJobTrigger** vers **Add-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="57548-154">You can also pipe **ScheduledJobTrigger** objects to **Add-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="57548-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57548-155">CommonParameters</span></span>
<span data-ttu-id="57548-156">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="57548-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="57548-157">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="57548-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="57548-158">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="57548-158">INPUTS</span></span>

### <span data-ttu-id="57548-159">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger, Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="57548-159">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger, Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="57548-160">Vous pouvez diriger des déclencheurs de tâche ou des tâches planifiées vers **Add-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="57548-160">You can pipe job triggers or scheduled jobs to **Add-JobTrigger** .</span></span>

## <span data-ttu-id="57548-161">SORTIES</span><span class="sxs-lookup"><span data-stu-id="57548-161">OUTPUTS</span></span>

### <span data-ttu-id="57548-162">Aucun</span><span class="sxs-lookup"><span data-stu-id="57548-162">None</span></span>
<span data-ttu-id="57548-163">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="57548-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="57548-164">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="57548-164">NOTES</span></span>

## <span data-ttu-id="57548-165">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="57548-165">RELATED LINKS</span></span>

[<span data-ttu-id="57548-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="57548-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="57548-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="57548-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="57548-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="57548-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="57548-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="57548-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="57548-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="57548-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="57548-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="57548-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="57548-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="57548-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="57548-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="57548-176">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="57548-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="57548-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="57548-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="57548-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="57548-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="57548-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="57548-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="57548-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="57548-181">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="57548-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
