---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202973"
---
# <span data-ttu-id="6e1f3-103">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-103">Unregister-ScheduledJob</span></span>

## <span data-ttu-id="6e1f3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6e1f3-104">SYNOPSIS</span></span>
<span data-ttu-id="6e1f3-105">Supprime les tâches planifiées de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-105">Deletes scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="6e1f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6e1f3-106">SYNTAX</span></span>

### <span data-ttu-id="6e1f3-107">Définition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6e1f3-107">Definition (Default)</span></span>

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="6e1f3-108">Dotée DefinitionId</span><span class="sxs-lookup"><span data-stu-id="6e1f3-108">DefinitionId</span></span>

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e1f3-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="6e1f3-109">DefinitionName</span></span>

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6e1f3-110">Description</span><span class="sxs-lookup"><span data-stu-id="6e1f3-110">DESCRIPTION</span></span>
<span data-ttu-id="6e1f3-111">L'applet de commande **Unregister-ScheduledJob** supprime les tâches planifiées de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-111">The **Unregister-ScheduledJob** cmdlet deletes scheduled jobs from the local computer.</span></span>

<span data-ttu-id="6e1f3-112">Lorsqu’il supprime ou annule l’inscription d’une tâche planifiée, **Unregister-ScheduledJob** supprime le répertoire de la tâche planifiée (dans le répertoire $home \appdata\local\microsoft\windows\powershell\scheduledjobs), qui contient le fichier XML qui définit la tâche planifiée, l’historique d’exécution du travail et tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-112">When it deletes or unregisters a scheduled job, **Unregister-ScheduledJob** deletes the directory for the scheduled job (in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory), which contains the XML file that defines the scheduled job, the job execution history, and all job results.</span></span>
<span data-ttu-id="6e1f3-113">Cette action supprime également la tâche du Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-113">This action also deletes the job from Task Scheduler.</span></span>

<span data-ttu-id="6e1f3-114">**Unregister-ScheduledJob** supprime uniquement les tâches planifiées qui sont créées à l’aide de l’applet de commande Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-114">**Unregister-ScheduledJob** deletes only the scheduled jobs that are created by using the Register-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="6e1f3-115">Elle ne supprime pas les tâches planifiées qui sont créées dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-115">It does not delete scheduled jobs that are created in Task Scheduler.</span></span>

<span data-ttu-id="6e1f3-116">Vous pouvez utiliser les paramètres de **Unregister-ScheduledJob** pour supprimer les tâches planifiées par ID ou par nom, ou les tâches planifiées de canal de Get-ScheduledJob à **Unregister-ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="6e1f3-116">You can use the parameters of **Unregister-ScheduledJob** to delete scheduled jobs by ID or name, or pipe scheduled jobs from Get-ScheduledJob to **Unregister-ScheduledJob** .</span></span>

<span data-ttu-id="6e1f3-117">**Unregister-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-117">**Unregister-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="6e1f3-118">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="6e1f3-119">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="6e1f3-120">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6e1f3-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6e1f3-121">EXAMPLES</span></span>

### <span data-ttu-id="6e1f3-122">Exemple 1 : supprimer une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="6e1f3-122">Example 1: Delete a scheduled job</span></span>

```
PS C:\> Unregister-ScheduledJob TestJob
```

<span data-ttu-id="6e1f3-123">Cette commande supprime la tâche planifiée TestJob sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-123">This command deletes the TestJob scheduled job on the local computer.</span></span>

### <span data-ttu-id="6e1f3-124">Exemple 2 : supprimer tous les travaux planifiés</span><span class="sxs-lookup"><span data-stu-id="6e1f3-124">Example 2: Delete all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

<span data-ttu-id="6e1f3-125">Cet exemple montre deux commandes différentes qui suppriment toutes les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-125">This example shows two different commands that delete all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="6e1f3-126">La première commande utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-126">The first command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="6e1f3-127">Un opérateur pipeline (|) envoie les tâches planifiées vers **Unregister-ScheduleJob** , qui les supprime.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-127">A pipeline operator (|) sends the scheduled jobs to **Unregister-ScheduleJob** , which deletes them.</span></span>

<span data-ttu-id="6e1f3-128">La deuxième commande utilise le paramètre *Name* de **Unregister-ScheduledJob** avec la valeur toutes les (\*) pour supprimer toutes les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-128">The second command uses the *Name* parameter of **Unregister-ScheduledJob** with a value of all (\*) to delete all scheduled jobs.</span></span>

<span data-ttu-id="6e1f3-129">Les deux commandes utilisent le paramètre *Force* , qui supprime une tâche planifiée, même si une instance de la tâche est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-129">Both commands use the *Force* parameter, which deletes a scheduled job even if an instance of the job is running.</span></span>

### <span data-ttu-id="6e1f3-130">Exemple 3 : supprimer une tâche planifiée sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="6e1f3-130">Example 3: Delete a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

<span data-ttu-id="6e1f3-131">Cette commande supprime les tâches planifiées dont le nom commence par test sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-131">This command deletes scheduled jobs with names that begin with Test on the Server01 remote computer.</span></span>
<span data-ttu-id="6e1f3-132">La commande utilise l’applet de commande Invoke-Command pour exécuter la commande **Unregister-ScheduledJob** sur l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-132">The command uses the Invoke-Command cmdlet to run the **Unregister-ScheduledJob** command on the Server02 computer.</span></span>

## <span data-ttu-id="6e1f3-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e1f3-133">PARAMETERS</span></span>

### <span data-ttu-id="6e1f3-134">-Force</span><span class="sxs-lookup"><span data-stu-id="6e1f3-134">-Force</span></span>
<span data-ttu-id="6e1f3-135">Supprime la tâche planifiée même si une instance de la tâche est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-135">Deletes the scheduled job even if an instance of the job is running.</span></span>
<span data-ttu-id="6e1f3-136">Par défaut, **Unregister-ScheduledJob** n'interrompt pas les tâches en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-136">By default, **Unregister-ScheduledJob** does not interrupt running jobs.</span></span>

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

### <span data-ttu-id="6e1f3-137">-Id</span><span class="sxs-lookup"><span data-stu-id="6e1f3-137">-Id</span></span>
<span data-ttu-id="6e1f3-138">Supprime les tâches planifiées avec les numéros d'identification (ID) spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-138">Deletes the scheduled jobs with the specified identification numbers (ID).</span></span>
<span data-ttu-id="6e1f3-139">Entrez les ID des tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-139">Enter the IDs of scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e1f3-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6e1f3-140">-InputObject</span></span>
<span data-ttu-id="6e1f3-141">Spécifie une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-141">Specifies a scheduled job.</span></span>
<span data-ttu-id="6e1f3-142">Entrez une variable qui contient des objets **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-142">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="6e1f3-143">Vous pouvez également diriger les objets **ScheduledJob** vers **Unregister-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="6e1f3-143">You can also pipe **ScheduledJob** objects to **Unregister-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6e1f3-144">-Name</span><span class="sxs-lookup"><span data-stu-id="6e1f3-144">-Name</span></span>
<span data-ttu-id="6e1f3-145">Supprime les tâches planifiées avec les noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-145">Deletes the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="6e1f3-146">Entrez le nom d'une ou de plusieurs tâches planifiées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-146">Enter the names of one or more scheduled jobs on the computer.</span></span>
<span data-ttu-id="6e1f3-147">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-147">Wildcards are supported.</span></span>

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

### <span data-ttu-id="6e1f3-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6e1f3-148">-Confirm</span></span>
<span data-ttu-id="6e1f3-149">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6e1f3-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6e1f3-150">-WhatIf</span></span>
<span data-ttu-id="6e1f3-151">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6e1f3-152">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6e1f3-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e1f3-153">CommonParameters</span></span>
<span data-ttu-id="6e1f3-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e1f3-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6e1f3-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e1f3-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6e1f3-156">INPUTS</span></span>

### <span data-ttu-id="6e1f3-157">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="6e1f3-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="6e1f3-158">Vous pouvez diriger les tâches planifiées vers Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-158">You can pipe scheduled jobs to Unregister-ScheduledJob</span></span>

## <span data-ttu-id="6e1f3-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6e1f3-159">OUTPUTS</span></span>

### <span data-ttu-id="6e1f3-160">Aucun</span><span class="sxs-lookup"><span data-stu-id="6e1f3-160">None</span></span>
<span data-ttu-id="6e1f3-161">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="6e1f3-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6e1f3-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6e1f3-162">NOTES</span></span>

## <span data-ttu-id="6e1f3-163">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6e1f3-163">RELATED LINKS</span></span>

[<span data-ttu-id="6e1f3-164">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-164">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="6e1f3-165">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-165">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="6e1f3-166">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-166">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="6e1f3-167">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-167">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="6e1f3-168">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-168">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="6e1f3-169">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-169">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="6e1f3-170">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-170">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="6e1f3-171">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6e1f3-171">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="6e1f3-172">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-172">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="6e1f3-173">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6e1f3-173">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="6e1f3-174">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-174">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="6e1f3-175">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-175">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="6e1f3-176">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6e1f3-176">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="6e1f3-177">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-177">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="6e1f3-178">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6e1f3-178">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="6e1f3-179">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6e1f3-179">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
