---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202993"
---
# <span data-ttu-id="1b0ad-103">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-103">Remove-JobTrigger</span></span>

## <span data-ttu-id="1b0ad-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1b0ad-104">SYNOPSIS</span></span>
<span data-ttu-id="1b0ad-105">Supprimer les déclencheurs de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-105">Delete job triggers from scheduled jobs.</span></span>

## <span data-ttu-id="1b0ad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b0ad-106">SYNTAX</span></span>

### <span data-ttu-id="1b0ad-107">JobDefinition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1b0ad-107">JobDefinition (Default)</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### <span data-ttu-id="1b0ad-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="1b0ad-108">JobDefinitionId</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="1b0ad-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="1b0ad-109">JobDefinitionName</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="1b0ad-110">Description</span><span class="sxs-lookup"><span data-stu-id="1b0ad-110">DESCRIPTION</span></span>
<span data-ttu-id="1b0ad-111">L’applet de commande **Remove-JobTrigger** supprime les déclencheurs de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-111">The **Remove-JobTrigger** cmdlet deletes job triggers from scheduled jobs.</span></span>

<span data-ttu-id="1b0ad-112">Un déclencheur de tâche définit une planification ou des conditions récurrentes pour le démarrage d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-112">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="1b0ad-113">Pour gérer les déclencheurs de tâche, utilisez les applets de commande New-JobTrigger, Add-JobTrigger, Set-JobTrigger et Set-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-113">To manage job triggers, use the New-JobTrigger, Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJob cmdlets.</span></span>

<span data-ttu-id="1b0ad-114">Utilisez les paramètres *Name* , *ID* ou *InputObject* de **Remove-JobTrigger** pour identifier les tâches planifiées desquelles les déclencheurs sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-114">Use the *Name* , *ID* , or *InputObject* parameters of **Remove-JobTrigger** to identify the scheduled jobs from which the triggers are removed.</span></span>
<span data-ttu-id="1b0ad-115">Utilisez le paramètre *TriggerID* pour identifier les déclencheurs de tâche à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-115">Use the *TriggerID* parameter to identify the job triggers to delete.</span></span>
<span data-ttu-id="1b0ad-116">Par défaut, **Remove-JobTrigger** supprime tous les déclencheurs d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-116">By default, **Remove-JobTrigger** deletes all job triggers of a scheduled job.</span></span>

<span data-ttu-id="1b0ad-117">**Remove-JobTrigger** est une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-117">**Remove-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="1b0ad-118">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="1b0ad-119">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="1b0ad-120">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="1b0ad-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1b0ad-121">EXAMPLES</span></span>

### <span data-ttu-id="1b0ad-122">Exemple 1 : supprimer tous les déclencheurs de tâche</span><span class="sxs-lookup"><span data-stu-id="1b0ad-122">Example 1: Delete all job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

<span data-ttu-id="1b0ad-123">Cette commande supprime tous les déclencheurs des tâches planifiées dont le nom commence par test.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-123">This command deletes all job triggers from scheduled job that have names that begin with Test.</span></span>

### <span data-ttu-id="1b0ad-124">Exemple 2 : supprimer les déclencheurs de tâche sélectionnés</span><span class="sxs-lookup"><span data-stu-id="1b0ad-124">Example 2: Delete selected job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

<span data-ttu-id="1b0ad-125">Cette commande supprime uniquement le troisième déclencheur (ID = 3) de la tâche planifiée BackupArchive.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-125">This command deletes only the third trigger (ID = 3) from the BackupArchive scheduled job.</span></span>

### <span data-ttu-id="1b0ad-126">Exemple 3 : supprimer les déclencheurs de tâche AtStartup de toutes les tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="1b0ad-126">Example 3: Delete AtStartup job triggers from all scheduled jobs</span></span>

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

<span data-ttu-id="1b0ad-127">Cette fonction supprime tous les déclencheurs de tâche AtStartup de toutes les tâches sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-127">This function deletes all AtStartup job triggers from all jobs on the local computer.</span></span>
<span data-ttu-id="1b0ad-128">Pour utiliser la fonction, exécutez-la dans votre session, puis tapez `Delete-AtStartup` .</span><span class="sxs-lookup"><span data-stu-id="1b0ad-128">To use the function, run the function in your session and then type `Delete-AtStartup`.</span></span>

<span data-ttu-id="1b0ad-129">La fonction Delete-AtStartup contient une seule commande.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-129">The Delete-AtStartup function contains a single command.</span></span>
<span data-ttu-id="1b0ad-130">La commande utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-130">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="1b0ad-131">Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande Get-JobTrigger, qui obtient tous les déclencheurs de tâche à partir de chacune des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-131">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all of the job triggers from each of the scheduled jobs.</span></span>
<span data-ttu-id="1b0ad-132">Un opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object, qui sélectionne les déclencheurs de tâche où la valeur de la propriété Frequency du déclencheur de tâche est égale à AtStartup.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-132">A pipeline operator sends the job triggers to the Where-Object cmdlet, which selects job triggers where the value of the Frequency property of the job trigger equals AtStartup.</span></span>

<span data-ttu-id="1b0ad-133">Les objets **JobTrigger** ont une propriété **JobDefinition** qui contient la tâche planifiée qu’ils déclenchent.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-133">**JobTrigger** objects have a **JobDefinition** property that contains the scheduled job that they trigger.</span></span>
<span data-ttu-id="1b0ad-134">Le reste de la commande utilise cette précieuse fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-134">The remainder of the command uses that valuable feature.</span></span>

<span data-ttu-id="1b0ad-135">Un opérateur de pipeline envoie les déclencheurs de tâche AtStartup à l’applet de commande ForEach-Object, qui exécute une commande **Remove-JobTrigger** sur chaque déclencheur AtStartup.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-135">A pipeline operator sends the AtStartup job triggers to the ForEach-Object cmdlet, which runs a **Remove-JobTrigger** command on each AtStartup trigger.</span></span>
<span data-ttu-id="1b0ad-136">La valeur du paramètre *InputObject* de **Remove-JobTrigger** est la tâche planifiée dans la propriété JobDefinition du déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-136">The value of the *InputObject* parameter of **Remove-JobTrigger** is the scheduled job in the JobDefinition property of the job trigger.</span></span>
<span data-ttu-id="1b0ad-137">La valeur du paramètre *TriggerID* est l'identificateur dans la propriété ID du déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-137">The value of the *TriggerID* parameter is the identifier in the ID property of the job trigger.</span></span>

### <span data-ttu-id="1b0ad-138">Exemple 4 : supprimer un déclencheur d’une tâche planifiée à distance</span><span class="sxs-lookup"><span data-stu-id="1b0ad-138">Example 4: Delete a job trigger from a remote scheduled job</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

<span data-ttu-id="1b0ad-139">Cette commande supprime le premier déclencheur de tâche de la tâche Inventory sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-139">This command deletes the first job trigger from the Inventory job on the Server01 computer.</span></span>

<span data-ttu-id="1b0ad-140">La commande utilise l’applet de commande **Invoke-Command** pour exécuter l’applet de commande **Remove-JobTrigger** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-140">The command uses the **Invoke-Command** cmdlet to run the **Remove-JobTrigger** cmdlet on the Server01 computer.</span></span>
<span data-ttu-id="1b0ad-141">L’applet de commande **Remove-JobTrigger** utilise le paramètre *ID* pour identifier la tâche planifiée Inventory et le paramètre *TriggerID* pour spécifier le premier déclencheur.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-141">The **Remove-JobTrigger** cmdlet uses the *ID* parameter to identify the Inventory scheduled job and the *TriggerID* parameter to specify the first trigger.</span></span>
<span data-ttu-id="1b0ad-142">Le paramètre *ID* est particulièrement utile quand plusieurs tâches planifiées ont des noms identiques ou similaires.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-142">The *ID* parameter is especially useful when multiple scheduled jobs have the same or similar names.</span></span>

## <span data-ttu-id="1b0ad-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b0ad-143">PARAMETERS</span></span>

### <span data-ttu-id="1b0ad-144">-Id</span><span class="sxs-lookup"><span data-stu-id="1b0ad-144">-Id</span></span>
<span data-ttu-id="1b0ad-145">Spécifie les numéros d'identification des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-145">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="1b0ad-146">**Remove-JobTrigger** supprime les déclencheurs des tâches planifiées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-146">**Remove-JobTrigger** deletes job triggers from the specified scheduled jobs.</span></span>

<span data-ttu-id="1b0ad-147">Pour obtenir le numéro d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-147">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="1b0ad-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1b0ad-148">-InputObject</span></span>
<span data-ttu-id="1b0ad-149">Spécifie les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-149">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="1b0ad-150">Entrez une variable qui contient des objets **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-150">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="1b0ad-151">Vous pouvez également diriger les objets **ScheduledJob** vers **Remove-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="1b0ad-151">You can also pipe **ScheduledJob** objects to **Remove-JobTrigger** .</span></span>

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

### <span data-ttu-id="1b0ad-152">-Name</span><span class="sxs-lookup"><span data-stu-id="1b0ad-152">-Name</span></span>
<span data-ttu-id="1b0ad-153">Spécifie les noms des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-153">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="1b0ad-154">**Remove-JobTrigger** supprime les déclencheurs des tâches planifiées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-154">**Remove-JobTrigger** deletes the job triggers from the specified scheduled jobs.</span></span>
<span data-ttu-id="1b0ad-155">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-155">Wildcards are supported.</span></span>

<span data-ttu-id="1b0ad-156">Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-156">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="1b0ad-157">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="1b0ad-157">-TriggerId</span></span>
<span data-ttu-id="1b0ad-158">Supprime uniquement les déclencheurs de tâche spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-158">Deletes only the specified job triggers.</span></span>
<span data-ttu-id="1b0ad-159">Par défaut, **Remove-JobTrigger** supprime tous les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-159">By default, **Remove-JobTrigger** deletes all triggers from the scheduled jobs.</span></span>
<span data-ttu-id="1b0ad-160">Utilisez ce paramètre quand les tâches planifiées ont plusieurs déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-160">Use this parameter when the scheduled jobs have multiple job triggers.</span></span>

<span data-ttu-id="1b0ad-161">Entrez les ID d'un ou de plusieurs déclencheurs de tâche d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="1b0ad-162">Si vous spécifiez plusieurs tâches planifiées, **Remove-JobTrigger** supprime le déclencheur de tâche avec l’ID spécifié de toutes les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-162">If you specify multiple scheduled jobs, **Remove-JobTrigger** deletes the job trigger with the specified ID from all scheduled jobs.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b0ad-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b0ad-163">CommonParameters</span></span>
<span data-ttu-id="1b0ad-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b0ad-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1b0ad-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b0ad-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1b0ad-166">INPUTS</span></span>

### <span data-ttu-id="1b0ad-167">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="1b0ad-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="1b0ad-168">Vous pouvez diriger les tâches planifiées vers l'applet de commande **Remove-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="1b0ad-168">You can pipe scheduled jobs to the **Remove-JobTrigger** cmdlet.</span></span>

## <span data-ttu-id="1b0ad-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1b0ad-169">OUTPUTS</span></span>

### <span data-ttu-id="1b0ad-170">Aucun</span><span class="sxs-lookup"><span data-stu-id="1b0ad-170">None</span></span>
<span data-ttu-id="1b0ad-171">L'applet de commande ne génère pas de résultat.</span><span class="sxs-lookup"><span data-stu-id="1b0ad-171">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1b0ad-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1b0ad-172">NOTES</span></span>

## <span data-ttu-id="1b0ad-173">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1b0ad-173">RELATED LINKS</span></span>

[<span data-ttu-id="1b0ad-174">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-174">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="1b0ad-175">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-175">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="1b0ad-176">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1b0ad-176">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="1b0ad-177">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-177">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="1b0ad-178">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1b0ad-178">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="1b0ad-179">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-179">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="1b0ad-180">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1b0ad-180">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="1b0ad-181">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="1b0ad-181">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="1b0ad-182">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-182">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="1b0ad-183">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="1b0ad-183">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="1b0ad-184">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1b0ad-184">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="1b0ad-185">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-185">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="1b0ad-186">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1b0ad-186">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="1b0ad-187">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1b0ad-187">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="1b0ad-188">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="1b0ad-188">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="1b0ad-189">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1b0ad-189">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
