---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203025"
---
# <span data-ttu-id="cd8b5-103">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-103">Disable-ScheduledJob</span></span>

## <span data-ttu-id="cd8b5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cd8b5-104">SYNOPSIS</span></span>
<span data-ttu-id="cd8b5-105">Désactive une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-105">Disables a scheduled job.</span></span>

## <span data-ttu-id="cd8b5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd8b5-106">SYNTAX</span></span>

### <span data-ttu-id="cd8b5-107">Définition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="cd8b5-107">Definition (Default)</span></span>

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cd8b5-108">Dotée DefinitionId</span><span class="sxs-lookup"><span data-stu-id="cd8b5-108">DefinitionId</span></span>

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cd8b5-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="cd8b5-109">DefinitionName</span></span>

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cd8b5-110">Description</span><span class="sxs-lookup"><span data-stu-id="cd8b5-110">DESCRIPTION</span></span>
<span data-ttu-id="cd8b5-111">L'applet de commande **Disable-ScheduledJob** désactive temporairement les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-111">The **Disable-ScheduledJob** cmdlet temporarily disables scheduled jobs.</span></span>
<span data-ttu-id="cd8b5-112">La désactivation conserve toutes les propriétés des tâches et ne désactive pas les déclencheurs de tâche, mais elle empêche les tâches planifiées de démarrer automatiquement lors du déclenchement.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-112">Disabling preserves all job properties and does not disable the job triggers, but it prevents the scheduled jobs from starting automatically when triggered.</span></span>
<span data-ttu-id="cd8b5-113">Vous pouvez démarrer une tâche planifiée désactivée à l’aide de l’applet de commande Start-Job ou utiliser une tâche planifiée désactivée comme modèle.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-113">You can start a disabled scheduled job by using the Start-Job cmdlet or use a disabled scheduled job as a template.</span></span>

<span data-ttu-id="cd8b5-114">Pour désactiver une tâche planifiée, l'applet de commande **Disable-ScheduledJob** affecte à la propriété **Enabled** de la tâche planifiée la valeur False ($false).</span><span class="sxs-lookup"><span data-stu-id="cd8b5-114">To disable a scheduled job, the **Disable-ScheduledJob** cmdlet sets the **Enabled** property of the scheduled job to False ($false).</span></span>
<span data-ttu-id="cd8b5-115">Pour réactiver la tâche planifiée, utilisez l’applet de commande Enable-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-115">To re-enable the scheduled job, use the Enable-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="cd8b5-116">**Disable-ScheduledJob** est une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="cd8b5-117">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="cd8b5-118">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="cd8b5-119">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="cd8b5-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cd8b5-120">EXAMPLES</span></span>

### <span data-ttu-id="cd8b5-121">Exemple 1 : désactiver une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="cd8b5-121">Example 1: Disable a scheduled job</span></span>

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

<span data-ttu-id="cd8b5-122">Cette commande désactive la tâche planifiée avec l'ID 2 sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-122">This command disables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="cd8b5-123">La sortie illustre l'effet de la commande.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-123">The output shows the effect of the command.</span></span>

### <span data-ttu-id="cd8b5-124">Exemple 2 : désactiver toutes les tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="cd8b5-124">Example 2: Disable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

<span data-ttu-id="cd8b5-125">Cette commande désactive toutes les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-125">This command disables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="cd8b5-126">Elle utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées et l’applet de commande **Disable-ScheduledJob** pour les désactiver.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-126">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Disable-ScheduledJob** cmdlet to disable them.</span></span>

<span data-ttu-id="cd8b5-127">Vous pouvez réactiver la tâche planifiée à l’aide de l’applet de commande Enable-ScheduledJob et exécuter une tâche planifiée désactivée à l’aide de l’applet de commande Start-Job.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-127">You can re-enable scheduled job by using the Enable-ScheduledJob cmdlet and run a disabled scheduled job by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="cd8b5-128">**Disable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous désactivez une tâche planifiée qui est déjà désactivée, de sorte que vous pouvez désactiver toutes les tâches planifiées sans conditions.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-128">**Disable-ScheduledJob** does not generate warnings or errors if you disable a scheduled job that is already disabled, so you can disable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="cd8b5-129">Exemple 3 : désactiver les tâches planifiées sélectionnées</span><span class="sxs-lookup"><span data-stu-id="cd8b5-129">Example 3: Disable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

<span data-ttu-id="cd8b5-130">Cette commande désactive une tâche planifiée sans informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-130">This command disables scheduled job do not include a credential.</span></span>
<span data-ttu-id="cd8b5-131">Les tâches sans informations d'identification s'exécutent avec l'autorisation de l'utilisateur qui les a créées.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-131">Jobs without credentials run with the permission of the user who created them.</span></span>

<span data-ttu-id="cd8b5-132">La commande utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-132">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="cd8b5-133">Un opérateur de pipeline envoie les tâches planifiées à l’applet de commande Where-Object, qui sélectionne les tâches planifiées qui n’ont pas d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-133">A pipeline operator sends the scheduled jobs to the Where-Object cmdlet, which selects scheduled jobs that do not have credentials.</span></span>
<span data-ttu-id="cd8b5-134">La commande utilise l'opérateur not (!) et fait référence à la propriété Credential de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-134">The command uses the not (!) operator and references the Credential property of the scheduled job.</span></span>
<span data-ttu-id="cd8b5-135">Un autre opérateur pipeline envoie les tâches planifiées sélectionnées à l'applet de commande **Disable-ScheduledJob** , qui les désactive.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-135">Another pipeline operator sends the selected scheduled jobs to the **Disable-ScheduledJob** cmdlet, which disables them.</span></span>

### <span data-ttu-id="cd8b5-136">Exemple 4 : désactiver les tâches planifiées sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="cd8b5-136">Example 4: Disable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

<span data-ttu-id="cd8b5-137">Cette commande désactive la tâche planifiée TestJob sur deux ordinateurs distants, Srv01 et Srv10.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-137">This command disables the TestJob scheduled job on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="cd8b5-138">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande **Disable-ScheduledJob** sur les ordinateurs Srv01 et Srv10.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-138">The command uses the Invoke-Command cmdlet to run a **Disable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="cd8b5-139">La commande utilise le paramètre *Name* de **Disable-ScheduledJob** pour sélectionner la tâche planifiée TestJob sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-139">The command uses the *Name* parameter of **Disable-ScheduledJob** to select the TestJob scheduled job on each computer.</span></span>

### <span data-ttu-id="cd8b5-140">Exemple 5 : désactiver une tâche planifiée par son ID global</span><span class="sxs-lookup"><span data-stu-id="cd8b5-140">Example 5: Disable a scheduled job by its global ID</span></span>

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

<span data-ttu-id="cd8b5-141">Cet exemple montre comment désactiver une tâche planifiée à l'aide de son identificateur global.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-141">This examples shows how to disable a scheduled job by using its global identifier.</span></span>
<span data-ttu-id="cd8b5-142">La valeur de la propriété GlobalID d'une tâche planifiée est un identificateur unique (GUID).</span><span class="sxs-lookup"><span data-stu-id="cd8b5-142">The value of the GlobalID property of a scheduled job is a unique identifier (GUID).</span></span>
<span data-ttu-id="cd8b5-143">Utilisez la valeur GlobalID quand la précision est requise, par exemple quand vous désactivez des tâches planifiées sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-143">Use the GlobalID value when precision is required, such as when you are disabling scheduled jobs on multiple computers.</span></span>

## <span data-ttu-id="cd8b5-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd8b5-144">PARAMETERS</span></span>

### <span data-ttu-id="cd8b5-145">-Id</span><span class="sxs-lookup"><span data-stu-id="cd8b5-145">-Id</span></span>
<span data-ttu-id="cd8b5-146">Désactive la tâche planifiée avec le numéro d'identification (ID) spécifié.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-146">Disables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="cd8b5-147">Entrez l'ID d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-147">Enter the ID of a scheduled job.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd8b5-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cd8b5-148">-InputObject</span></span>
<span data-ttu-id="cd8b5-149">Spécifie la tâche planifiée à désactiver.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-149">Specifies the scheduled job to be disabled.</span></span>
<span data-ttu-id="cd8b5-150">Entrez une variable qui contient des objets  **ScheduledJobDefinition** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobDefinition** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-150">Enter a variable that contains  **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="cd8b5-151">Vous pouvez également diriger un objet **ScheduledJobDefinition** vers **Disable-ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="cd8b5-151">You can also pipe a **ScheduledJobDefinition** object to **Disable-ScheduledJob** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cd8b5-152">-Name</span><span class="sxs-lookup"><span data-stu-id="cd8b5-152">-Name</span></span>
<span data-ttu-id="cd8b5-153">Désactive les tâches planifiées avec les noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-153">Disables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="cd8b5-154">Entrez le nom d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-154">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="cd8b5-155">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-155">Wildcards are supported.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd8b5-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="cd8b5-156">-PassThru</span></span>
<span data-ttu-id="cd8b5-157">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-157">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="cd8b5-158">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="cd8b5-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cd8b5-159">-Confirm</span></span>
<span data-ttu-id="cd8b5-160">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cd8b5-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cd8b5-161">-WhatIf</span></span>
<span data-ttu-id="cd8b5-162">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cd8b5-163">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cd8b5-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd8b5-164">CommonParameters</span></span>
<span data-ttu-id="cd8b5-165">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd8b5-166">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cd8b5-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd8b5-167">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cd8b5-167">INPUTS</span></span>

### <span data-ttu-id="cd8b5-168">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="cd8b5-168">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="cd8b5-169">Vous pouvez acheminer par canal une tâche planifiée vers **Disable-ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="cd8b5-169">You can pipe a scheduled job to **Disable-ScheduledJob** .</span></span>

## <span data-ttu-id="cd8b5-170">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cd8b5-170">OUTPUTS</span></span>

### <span data-ttu-id="cd8b5-171">Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="cd8b5-171">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="cd8b5-172">Si vous utilisez le paramètre **Passthru** , **Disable-ScheduledJob** retourne la tâche planifiée qui a été désactivée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-172">If you use the **Passthru** parameter, **Disable-ScheduledJob** returns the scheduled job that was disabled.</span></span>
<span data-ttu-id="cd8b5-173">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cd8b5-174">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cd8b5-174">NOTES</span></span>

* <span data-ttu-id="cd8b5-175">**Disable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous l’utilisez pour désactiver une tâche planifiée qui est déjà désactivée.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-175">**Disable-ScheduledJob** does not generate warnings or errors if you use it to disable a scheduled job that is already disabled.</span></span>

## <span data-ttu-id="cd8b5-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cd8b5-176">RELATED LINKS</span></span>

[<span data-ttu-id="cd8b5-177">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-177">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="cd8b5-178">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-178">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="cd8b5-179">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-179">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="cd8b5-180">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-180">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="cd8b5-181">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-181">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="cd8b5-182">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-182">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="cd8b5-183">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-183">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="cd8b5-184">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="cd8b5-184">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="cd8b5-185">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-185">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="cd8b5-186">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="cd8b5-186">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="cd8b5-187">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-187">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="cd8b5-188">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-188">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="cd8b5-189">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="cd8b5-189">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="cd8b5-190">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-190">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="cd8b5-191">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="cd8b5-191">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="cd8b5-192">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cd8b5-192">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
