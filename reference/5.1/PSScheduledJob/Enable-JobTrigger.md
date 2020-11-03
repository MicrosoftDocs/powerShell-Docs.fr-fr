---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203009"
---
# <span data-ttu-id="e6c04-103">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-103">Enable-JobTrigger</span></span>

## <span data-ttu-id="e6c04-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e6c04-104">SYNOPSIS</span></span>
<span data-ttu-id="e6c04-105">Active les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="e6c04-105">Enables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="e6c04-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e6c04-106">SYNTAX</span></span>

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e6c04-107">Description</span><span class="sxs-lookup"><span data-stu-id="e6c04-107">DESCRIPTION</span></span>
<span data-ttu-id="e6c04-108">L’applet de commande **Enable-JobTrigger** réactive les déclencheurs des tâches planifiées, telles que celles qui ont été désactivées à l’aide de l’applet de commande Disable-JobTrigger.</span><span class="sxs-lookup"><span data-stu-id="e6c04-108">The **Enable-JobTrigger** cmdlet re-enables job triggers of scheduled jobs, such as those that were disabled by using the Disable-JobTrigger cmdlet.</span></span>
<span data-ttu-id="e6c04-109">Les déclencheurs de tâche activés et réactivés peuvent démarrer des tâches planifiées immédiatement ; il est inutile de redémarrer Windows ou Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6c04-109">Enabled and re-enabled job triggers can start scheduled jobs immediately; there is no need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="e6c04-110">Pour utiliser cette applet de commande, utilisez l’applet de commande Get-JobTrigger pour récupérer les déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="e6c04-110">To use this cmdlet, use the  Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="e6c04-111">Ensuite, dirigez les déclencheurs de tâche vers **Enable-JobTrigger** ou utilisez son paramètre *InputObject* .</span><span class="sxs-lookup"><span data-stu-id="e6c04-111">Then pipe the job triggers to **Enable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="e6c04-112">Pour activer un déclencheur de tâche, l’applet de commande **Enable-JobTrigger** affecte la valeur $true à la propriété Enabled du déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="e6c04-112">To enable a job trigger, the **Enable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $True.</span></span>

<span data-ttu-id="e6c04-113">**Enable-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6c04-113">**Enable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="e6c04-114">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="e6c04-114">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="e6c04-115">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="e6c04-115">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="e6c04-116">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e6c04-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="e6c04-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e6c04-117">EXAMPLES</span></span>

### <span data-ttu-id="e6c04-118">Exemple 1 : activer un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="e6c04-118">Example 1: Enable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

<span data-ttu-id="e6c04-119">Cette commande active le premier déclencheur (ID=1) de la tâche planifiée Backup-Archives sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e6c04-119">This command enables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="e6c04-120">La commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="e6c04-120">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="e6c04-121">Un opérateur pipeline envoie le déclencheur de tâche à l'applet de commande **Enable-JobTrigger** , qui l'active.</span><span class="sxs-lookup"><span data-stu-id="e6c04-121">A pipeline operator sends the job trigger to the **Enable-JobTrigger** cmdlet, which enables it.</span></span>

### <span data-ttu-id="e6c04-122">Exemple 2 : activer tous les déclencheurs de tâche</span><span class="sxs-lookup"><span data-stu-id="e6c04-122">Example 2: Enable all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

<span data-ttu-id="e6c04-123">La commande utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e6c04-123">The command uses the Get-ScheduledJob cmdlet to get  the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="e6c04-124">Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande Get-JobTrigger, qui obtient tous les déclencheurs de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="e6c04-124">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="e6c04-125">Un autre opérateur pipeline envoie les déclencheurs de tâche à l'applet de commande **Enable-JobTrigger** , qui les active.</span><span class="sxs-lookup"><span data-stu-id="e6c04-125">Another pipeline operator sends the job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="e6c04-126">Exemple 3 : activer le déclencheur d’une tâche planifiée sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="e6c04-126">Example 3: Enable the job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

<span data-ttu-id="e6c04-127">Cette commande réactive les déclencheurs de tâche AtLogon sur la tâche planifiée DeployPackage sur l'ordinateur distant Server01.</span><span class="sxs-lookup"><span data-stu-id="e6c04-127">This command re-enables the AtLogon job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="e6c04-128">La commande utilise l’applet de commande Invoke-Command pour exécuter les commandes sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e6c04-128">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="e6c04-129">La commande distante utilise l’applet de commande Get-JobTrigger pour recevoir les déclencheurs de la tâche planifiée DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="e6c04-129">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="e6c04-130">Un opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object qui retourne uniquement les déclencheurs de tâche AtLogon.</span><span class="sxs-lookup"><span data-stu-id="e6c04-130">A pipeline operator sends the job triggers to the Where-Object cmdlet which returns only AtLogon job triggers.</span></span>
<span data-ttu-id="e6c04-131">Un opérateur de pipeline envoie les déclencheurs de tâche AtLogon à l’applet de commande **Enable-JobTrigger** , qui les active.</span><span class="sxs-lookup"><span data-stu-id="e6c04-131">A pipeline operator sends the AtLogon job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="e6c04-132">Exemple 4 : afficher les déclencheurs de tâche désactivée</span><span class="sxs-lookup"><span data-stu-id="e6c04-132">Example 4: Display disabled job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="e6c04-133">Cette commande affiche tous les déclencheurs de tâche désactivés de toutes les tâches planifiées dans une table.</span><span class="sxs-lookup"><span data-stu-id="e6c04-133">This command displays all disabled job triggers of all scheduled jobs in a table.</span></span>
<span data-ttu-id="e6c04-134">Vous pouvez utiliser une commande similaire à celle-ci pour découvrir les déclencheurs de tâche qui doivent peut-être être activés.</span><span class="sxs-lookup"><span data-stu-id="e6c04-134">You can use a command like this one to discover job triggers that might need to be enabled.</span></span>

<span data-ttu-id="e6c04-135">La commande utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e6c04-135">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="e6c04-136">Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande Get-JobTrigger, qui obtient tous les déclencheurs de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="e6c04-136">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="e6c04-137">Un autre opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object, qui retourne uniquement les déclencheurs de tâche qui sont désactivés, autrement dit, où la valeur de la propriété Enabled du déclencheur de tâche n’est pas ( !) true.</span><span class="sxs-lookup"><span data-stu-id="e6c04-137">Another pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only job triggers that are disabled, that is, where the value of the Enabled property of the job trigger is not (!) true.</span></span>

<span data-ttu-id="e6c04-138">Un autre opérateur de pipeline envoie les déclencheurs de tâche désactivée à l’applet de commande Format-Table, qui affiche les propriétés sélectionnées des déclencheurs de tâche dans une table.</span><span class="sxs-lookup"><span data-stu-id="e6c04-138">Another pipeline operator sends the disabled job triggers to the Format-Table cmdlet, which displays the selected properties of the job triggers in a table.</span></span>
<span data-ttu-id="e6c04-139">Les propriétés incluent une nouvelle propriété JobName qui affiche le nom de la tâche planifiée dans la propriété JobDefinition du déclencheur.</span><span class="sxs-lookup"><span data-stu-id="e6c04-139">The properties include a new JobName property that displays the name of the scheduled job in the JobDefinition property of the job trigger.</span></span>

## <span data-ttu-id="e6c04-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e6c04-140">PARAMETERS</span></span>

### <span data-ttu-id="e6c04-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e6c04-141">-InputObject</span></span>
<span data-ttu-id="e6c04-142">Spécifie le déclencheur de tâche à activer.</span><span class="sxs-lookup"><span data-stu-id="e6c04-142">Specifies the job trigger to enable.</span></span>
<span data-ttu-id="e6c04-143">Entrez une variable qui contient des objets **ScheduledJobTrigger** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.</span><span class="sxs-lookup"><span data-stu-id="e6c04-143">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="e6c04-144">Vous pouvez également diriger un objet **ScheduledJobTrigger** vers **Enable-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="e6c04-144">You can also pipe a **ScheduledJobTrigger** object to **Enable-JobTrigger** .</span></span>

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

### <span data-ttu-id="e6c04-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e6c04-145">-PassThru</span></span>
<span data-ttu-id="e6c04-146">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e6c04-146">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="e6c04-147">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="e6c04-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e6c04-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e6c04-148">-Confirm</span></span>
<span data-ttu-id="e6c04-149">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e6c04-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e6c04-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e6c04-150">-WhatIf</span></span>
<span data-ttu-id="e6c04-151">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e6c04-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e6c04-152">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="e6c04-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e6c04-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e6c04-153">CommonParameters</span></span>
<span data-ttu-id="e6c04-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e6c04-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e6c04-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e6c04-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e6c04-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e6c04-156">INPUTS</span></span>

### <span data-ttu-id="e6c04-157">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="e6c04-158">Vous pouvez diriger les déclencheurs de tâche vers **Enable-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="e6c04-158">You can pipe job triggers to **Enable-JobTrigger** .</span></span>

## <span data-ttu-id="e6c04-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e6c04-159">OUTPUTS</span></span>

### <span data-ttu-id="e6c04-160">Aucun</span><span class="sxs-lookup"><span data-stu-id="e6c04-160">None</span></span>
<span data-ttu-id="e6c04-161">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="e6c04-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e6c04-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e6c04-162">NOTES</span></span>

* <span data-ttu-id="e6c04-163">**Enable-JobTrigger** ne génère pas d’erreurs ou d’avertissements si vous activez un déclencheur de tâche qui est déjà activé.</span><span class="sxs-lookup"><span data-stu-id="e6c04-163">**Enable-JobTrigger** does not generate errors or warnings if you enable a job trigger that is already enabled.</span></span>

## <span data-ttu-id="e6c04-164">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e6c04-164">RELATED LINKS</span></span>

[<span data-ttu-id="e6c04-165">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-165">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="e6c04-166">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-166">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="e6c04-167">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e6c04-167">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="e6c04-168">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-168">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="e6c04-169">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e6c04-169">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="e6c04-170">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-170">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="e6c04-171">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e6c04-171">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="e6c04-172">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e6c04-172">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="e6c04-173">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-173">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="e6c04-174">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e6c04-174">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="e6c04-175">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e6c04-175">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="e6c04-176">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-176">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="e6c04-177">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e6c04-177">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="e6c04-178">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e6c04-178">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="e6c04-179">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e6c04-179">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="e6c04-180">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e6c04-180">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
