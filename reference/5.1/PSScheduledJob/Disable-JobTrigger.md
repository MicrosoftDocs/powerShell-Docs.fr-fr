---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203033"
---
# <span data-ttu-id="fef6d-103">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-103">Disable-JobTrigger</span></span>

## <span data-ttu-id="fef6d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fef6d-104">SYNOPSIS</span></span>
<span data-ttu-id="fef6d-105">Désactive les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="fef6d-105">Disables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="fef6d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fef6d-106">SYNTAX</span></span>

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fef6d-107">Description</span><span class="sxs-lookup"><span data-stu-id="fef6d-107">DESCRIPTION</span></span>
<span data-ttu-id="fef6d-108">L'applet de commande **Disable-JobTrigger** désactive temporairement les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="fef6d-108">The **Disable-JobTrigger** cmdlet temporarily disables the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="fef6d-109">La désactivation conserve toutes les propriétés de déclencheur de tâche, mais l'empêche de démarrer la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="fef6d-109">Disabling preserves all job trigger properties, but it prevents the job trigger from starting the scheduled job.</span></span>

<span data-ttu-id="fef6d-110">Pour utiliser cette applet de commande, utilisez l’applet de commande Get-JobTrigger pour récupérer les déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="fef6d-110">To use this cmdlet, use the Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="fef6d-111">Ensuite, dirigez les déclencheurs de tâche vers **Disable-JobTrigger** ou utilisez son paramètre *InputObject* .</span><span class="sxs-lookup"><span data-stu-id="fef6d-111">Then pipe the job triggers to **Disable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="fef6d-112">Pour désactiver un déclencheur de tâche, l’applet de commande **Disable-JobTrigger** affecte la valeur $false à la propriété Enabled du déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="fef6d-112">To disable a job trigger, the **Disable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $False.</span></span>
<span data-ttu-id="fef6d-113">Pour réactiver le déclencheur de tâche, utilisez l’applet de commande Enable-JobTrigger, qui définit la propriété **Enabled** du déclencheur sur $true.</span><span class="sxs-lookup"><span data-stu-id="fef6d-113">To re-enable the job trigger, use the Enable-JobTrigger cmdlet, which sets the **Enabled** property of the job trigger to $True.</span></span>
<span data-ttu-id="fef6d-114">La désactivation d’un déclencheur de tâche ne désactive pas la tâche planifiée, comme c’est le cas par l’applet de commande Disable-ScheduledJob, mais si vous désactivez tous les déclencheurs de tâche, l’effet est identique à la désactivation de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="fef6d-114">Disabling a job trigger does not disable the scheduled job, such as is done by the Disable-ScheduledJob cmdlet, but if you disable all job triggers, the effect is the same as disabling the scheduled job.</span></span>

<span data-ttu-id="fef6d-115">Si vous désactivez une tâche planifiée ou désactivez tous les déclencheurs d’une tâche planifiée, vous pouvez toujours démarrer la tâche à l’aide de l’applet de commande Start-Job ou utiliser la tâche planifiée désactivée comme modèle.</span><span class="sxs-lookup"><span data-stu-id="fef6d-115">If you disable a scheduled job or disable all job triggers of a scheduled job, you can still start the job by using the Start-Job cmdlet or use the disabled scheduled job as a template.</span></span>

<span data-ttu-id="fef6d-116">**Disable-ScheduledJob** est une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fef6d-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="fef6d-117">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="fef6d-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="fef6d-118">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="fef6d-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="fef6d-119">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fef6d-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="fef6d-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fef6d-120">EXAMPLES</span></span>

### <span data-ttu-id="fef6d-121">Exemple 1 : désactiver un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="fef6d-121">Example 1: Disable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

<span data-ttu-id="fef6d-122">Cette commande désactive le premier déclencheur (ID=1) de la tâche planifiée Backup-Archives sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fef6d-122">This command disables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="fef6d-123">La commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="fef6d-123">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="fef6d-124">Un opérateur pipeline envoie le déclencheur de tâche à l'applet de commande **Disable-JobTrigger** , qui le désactive.</span><span class="sxs-lookup"><span data-stu-id="fef6d-124">A pipeline operator sends the job trigger to the **Disable-JobTrigger** cmdlet, which disables it.</span></span>

### <span data-ttu-id="fef6d-125">Exemple 2 : désactiver tous les déclencheurs de tâche</span><span class="sxs-lookup"><span data-stu-id="fef6d-125">Example 2: Disable all job triggers</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="fef6d-126">Ces commandes désactivent tous les déclencheurs de tâche sur deux tâches planifiées et affichent les résultats.</span><span class="sxs-lookup"><span data-stu-id="fef6d-126">These commands disable all job triggers on two scheduled jobs and display the results.</span></span>

### <span data-ttu-id="fef6d-127">Exemple 3 : désactiver le déclencheur de tâche d’une tâche planifiée sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="fef6d-127">Example 3: Disable job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

<span data-ttu-id="fef6d-128">Cette commande désactive les déclencheurs de tâche quotidienne sur la tâche planifiée DeployPackage sur l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="fef6d-128">This command disables the daily job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="fef6d-129">La commande utilise l’applet de commande Invoke-Command pour exécuter les commandes sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="fef6d-129">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="fef6d-130">La commande distante utilise l’applet de commande Get-JobTrigger pour recevoir les déclencheurs de la tâche planifiée DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="fef6d-130">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="fef6d-131">Un opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object, qui retourne uniquement les déclencheurs de tâche quotidiens.</span><span class="sxs-lookup"><span data-stu-id="fef6d-131">A pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only daily job triggers.</span></span>
<span data-ttu-id="fef6d-132">Un opérateur de pipeline envoie les déclencheurs de tâche quotidienne à l’applet de commande **Disable-JobTrigger** , qui les désactive.</span><span class="sxs-lookup"><span data-stu-id="fef6d-132">A pipeline operator sends the daily job triggers to the **Disable-JobTrigger** cmdlet, which disables them.</span></span>

## <span data-ttu-id="fef6d-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fef6d-133">PARAMETERS</span></span>

### <span data-ttu-id="fef6d-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fef6d-134">-InputObject</span></span>
<span data-ttu-id="fef6d-135">Spécifie le déclencheur de tâche à désactiver.</span><span class="sxs-lookup"><span data-stu-id="fef6d-135">Specifies the job trigger to be disabled.</span></span>
<span data-ttu-id="fef6d-136">Entrez une variable qui contient des objets  **ScheduledJobTrigger** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.</span><span class="sxs-lookup"><span data-stu-id="fef6d-136">Enter a variable that contains  **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="fef6d-137">Vous pouvez également diriger un objet **ScheduledJobTrigger** vers **Disable-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="fef6d-137">You can also pipe a **ScheduledJobTrigger** object to **Disable-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fef6d-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fef6d-138">-PassThru</span></span>
<span data-ttu-id="fef6d-139">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fef6d-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="fef6d-140">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="fef6d-140">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fef6d-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fef6d-141">-Confirm</span></span>
<span data-ttu-id="fef6d-142">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fef6d-142">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fef6d-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fef6d-143">-WhatIf</span></span>
<span data-ttu-id="fef6d-144">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fef6d-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fef6d-145">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="fef6d-145">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fef6d-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fef6d-146">CommonParameters</span></span>
<span data-ttu-id="fef6d-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fef6d-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fef6d-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fef6d-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fef6d-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fef6d-149">INPUTS</span></span>

### <span data-ttu-id="fef6d-150">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-150">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="fef6d-151">Vous pouvez diriger les déclencheurs de tâche vers **Disable-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="fef6d-151">You can pipe job triggers to **Disable-JobTrigger** .</span></span>

## <span data-ttu-id="fef6d-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fef6d-152">OUTPUTS</span></span>

### <span data-ttu-id="fef6d-153">Aucun</span><span class="sxs-lookup"><span data-stu-id="fef6d-153">None</span></span>
<span data-ttu-id="fef6d-154">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="fef6d-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fef6d-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fef6d-155">NOTES</span></span>

* <span data-ttu-id="fef6d-156">**Disable-JobTrigger** ne génère pas d’erreurs ou d’avertissements si vous désactivez un déclencheur de tâche qui est déjà désactivé.</span><span class="sxs-lookup"><span data-stu-id="fef6d-156">**Disable-JobTrigger** does not generate errors or warnings if you disable a job trigger that is already disabled.</span></span>

## <span data-ttu-id="fef6d-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fef6d-157">RELATED LINKS</span></span>

[<span data-ttu-id="fef6d-158">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-158">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="fef6d-159">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-159">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="fef6d-160">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fef6d-160">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="fef6d-161">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-161">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="fef6d-162">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fef6d-162">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="fef6d-163">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-163">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="fef6d-164">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fef6d-164">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="fef6d-165">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fef6d-165">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="fef6d-166">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-166">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="fef6d-167">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fef6d-167">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="fef6d-168">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fef6d-168">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="fef6d-169">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-169">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="fef6d-170">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fef6d-170">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="fef6d-171">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fef6d-171">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="fef6d-172">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fef6d-172">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="fef6d-173">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fef6d-173">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
