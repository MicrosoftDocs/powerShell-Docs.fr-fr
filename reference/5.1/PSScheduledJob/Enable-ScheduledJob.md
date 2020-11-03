---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203010"
---
# <span data-ttu-id="4b2f9-103">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-103">Enable-ScheduledJob</span></span>

## <span data-ttu-id="4b2f9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4b2f9-104">SYNOPSIS</span></span>
<span data-ttu-id="4b2f9-105">Active une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-105">Enables a scheduled job.</span></span>

## <span data-ttu-id="4b2f9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4b2f9-106">SYNTAX</span></span>

### <span data-ttu-id="4b2f9-107">Définition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4b2f9-107">Definition (Default)</span></span>

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4b2f9-108">Dotée DefinitionId</span><span class="sxs-lookup"><span data-stu-id="4b2f9-108">DefinitionId</span></span>

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4b2f9-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="4b2f9-109">DefinitionName</span></span>

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4b2f9-110">Description</span><span class="sxs-lookup"><span data-stu-id="4b2f9-110">DESCRIPTION</span></span>
<span data-ttu-id="4b2f9-111">L’applet de commande **Enable-ScheduledJob** réactive les tâches planifiées qui sont désactivées, telles que celles qui sont désactivées à l’aide de l’applet de commande Disable-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-111">The **Enable-ScheduledJob** cmdlet re-enables scheduled jobs that are disabled, such as those that are disabled by using the Disable-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="4b2f9-112">Les tâches activées s'exécutent automatiquement quand elles sont déclenchées.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-112">Enabled jobs run automatically when triggered.</span></span>

<span data-ttu-id="4b2f9-113">Pour activer une tâche planifiée, l’applet de commande **Enable-ScheduledJob** définit la propriété Enabled de la tâche planifiée sur $true.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-113">To enable a scheduled job, the **Enable-ScheduledJob** cmdlet sets the Enabled property of the scheduled job to $True.</span></span>

<span data-ttu-id="4b2f9-114">**Enabled-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-114">**Enabled-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="4b2f9-115">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-115">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="4b2f9-116">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-116">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="4b2f9-117">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4b2f9-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4b2f9-118">EXAMPLES</span></span>

### <span data-ttu-id="4b2f9-119">Exemple 1 : activer une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="4b2f9-119">Example 1: Enable a scheduled job</span></span>

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

<span data-ttu-id="4b2f9-120">Cette commande active la tâche planifiée avec l'ID 2 sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-120">This command enables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="4b2f9-121">La sortie illustre l'effet de la commande.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-121">The output shows the effect of the command.</span></span>

### <span data-ttu-id="4b2f9-122">Exemple 2 : activer toutes les tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="4b2f9-122">Example 2: Enable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

<span data-ttu-id="4b2f9-123">Cette commande active toutes les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-123">This command enables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="4b2f9-124">Elle utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées et l’applet de commande **Enable-ScheduledJob** pour les activer.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-124">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Enable-ScheduledJob** cmdlet to enable them.</span></span>

<span data-ttu-id="4b2f9-125">**Enable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous activez une tâche planifiée qui est déjà activée, ce qui vous permet d’activer toutes les tâches planifiées sans conditions.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-125">**Enable-ScheduledJob** does not generate warnings or errors if you enable a scheduled job that is already enabled, so you can enable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="4b2f9-126">Exemple 3 : activer les tâches planifiées sélectionnées</span><span class="sxs-lookup"><span data-stu-id="4b2f9-126">Example 3: Enable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

<span data-ttu-id="4b2f9-127">Cette commande active les tâches planifiées qui ne nécessitent pas de connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-127">This command enables scheduled jobs that do not require a network connection.</span></span>

<span data-ttu-id="4b2f9-128">La commande utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-128">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="4b2f9-129">Un opérateur de pipeline envoie les tâches planifiées à l’applet de commande Get-ScheduledJobOption, qui obtient les options de chaque tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-129">A pipeline operator sends the scheduled jobs to the Get-ScheduledJobOption cmdlet, which gets the job options of each scheduled job.</span></span>
<span data-ttu-id="4b2f9-130">Chaque objet d'options de tâche possède une propriété JobDefinition qui contient la tâche planifiée associée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-130">Each job options object has a JobDefinition property that contains the associated scheduled job.</span></span>
<span data-ttu-id="4b2f9-131">La propriété JobDefinition est utilisée pour terminer la commande.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-131">The JobDefinition property is used to complete the command.</span></span>

<span data-ttu-id="4b2f9-132">La commande utilise un opérateur de pipeline (|) pour envoyer les options de tâche à l’applet de commande Where-Object, qui sélectionne les objets d’options de tâche planifiés dans lesquels la propriété **RunWithoutNetwork** a la valeur True ($true).</span><span class="sxs-lookup"><span data-stu-id="4b2f9-132">The command uses a pipeline operator (|) to send the job options to the Where-Object cmdlet, which selects scheduled job option objects in which the **RunWithoutNetwork** property has a value of True ($true).</span></span>
<span data-ttu-id="4b2f9-133">Un autre opérateur de pipeline envoie les objets d’options de tâche planifiés sélectionnés à l’applet de commande ForEach-Object qui exécute une commande **Enable-ScheduledJob** sur la tâche planifiée dans la valeur de la propriété JobDefinition de chaque objet d’options de tâche.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-133">Another pipeline operator sends the selected scheduled job options objects to the ForEach-Object cmdlet which runs an **Enable-ScheduledJob** command on the scheduled job in the value of the JobDefinition property of each job options object.</span></span>

### <span data-ttu-id="4b2f9-134">Exemple 4 : activer les tâches planifiées sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="4b2f9-134">Example 4: Enable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

<span data-ttu-id="4b2f9-135">Cette commande active les tâches planifiées dont le nom contient « test » sur deux ordinateurs distants, Srv01 et Srv10.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-135">This command enables scheduled jobs that have "test" in their names on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="4b2f9-136">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande **Enable-ScheduledJob** sur les ordinateurs Srv01 et Srv10.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-136">The command uses the Invoke-Command cmdlet to run an **Enable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="4b2f9-137">La commande utilise le paramètre *Name* de **Enable-ScheduledJob** pour activer la tâche planifiée Inventory sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-137">The command uses the *Name* parameter of **Enable-ScheduledJob** to enable the Inventory scheduled job on each computer.</span></span>

## <span data-ttu-id="4b2f9-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4b2f9-138">PARAMETERS</span></span>

### <span data-ttu-id="4b2f9-139">-Id</span><span class="sxs-lookup"><span data-stu-id="4b2f9-139">-Id</span></span>
<span data-ttu-id="4b2f9-140">Active la tâche planifiée avec le numéro d'identification (ID) spécifié.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-140">Enables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="4b2f9-141">Entrez l'ID d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-141">Enter the ID of a scheduled job.</span></span>

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

### <span data-ttu-id="4b2f9-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4b2f9-142">-InputObject</span></span>
<span data-ttu-id="4b2f9-143">Spécifie la tâche planifiée à activer.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-143">Specifies the scheduled job to enable.</span></span>
<span data-ttu-id="4b2f9-144">Entrez une variable qui contient des objets **ScheduledJobDefinition** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobDefinition** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-144">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="4b2f9-145">Vous pouvez également diriger un objet **ScheduledJobDefinition** vers **Enable-ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="4b2f9-145">You can also pipe a **ScheduledJobDefinition** object to **Enable-ScheduledJob** .</span></span>

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

### <span data-ttu-id="4b2f9-146">-Name</span><span class="sxs-lookup"><span data-stu-id="4b2f9-146">-Name</span></span>
<span data-ttu-id="4b2f9-147">Active les tâches planifiées avec les noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-147">Enables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="4b2f9-148">Entrez le nom d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-148">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="4b2f9-149">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-149">Wildcards are supported.</span></span>

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

### <span data-ttu-id="4b2f9-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4b2f9-150">-PassThru</span></span>
<span data-ttu-id="4b2f9-151">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="4b2f9-152">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4b2f9-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4b2f9-153">-Confirm</span></span>
<span data-ttu-id="4b2f9-154">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4b2f9-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4b2f9-155">-WhatIf</span></span>
<span data-ttu-id="4b2f9-156">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4b2f9-157">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4b2f9-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b2f9-158">CommonParameters</span></span>
<span data-ttu-id="4b2f9-159">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b2f9-160">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4b2f9-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b2f9-161">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4b2f9-161">INPUTS</span></span>

### <span data-ttu-id="4b2f9-162">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="4b2f9-162">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="4b2f9-163">Vous pouvez diriger une tâche planifiée vers **Enable-ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="4b2f9-163">You can pipe a scheduled job to **Enable-ScheduledJob** .</span></span>

## <span data-ttu-id="4b2f9-164">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4b2f9-164">OUTPUTS</span></span>

### <span data-ttu-id="4b2f9-165">Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="4b2f9-165">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="4b2f9-166">Si vous utilisez le paramètre **Passthru** , **Enable-ScheduledJob** retourne la tâche planifiée qui a été activée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-166">If you use the **Passthru** parameter, **Enable-ScheduledJob** returns the scheduled job that was enabled.</span></span>
<span data-ttu-id="4b2f9-167">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4b2f9-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4b2f9-168">NOTES</span></span>

* <span data-ttu-id="4b2f9-169">**Enable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous l’utilisez pour activer une tâche planifiée qui est déjà activée.</span><span class="sxs-lookup"><span data-stu-id="4b2f9-169">**Enable-ScheduledJob** does not generate warnings or errors if you use it to enable a scheduled job that is already enabled.</span></span>

## <span data-ttu-id="4b2f9-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4b2f9-170">RELATED LINKS</span></span>

[<span data-ttu-id="4b2f9-171">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-171">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="4b2f9-172">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-172">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="4b2f9-173">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-173">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="4b2f9-174">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-174">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="4b2f9-175">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-175">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="4b2f9-176">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-176">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="4b2f9-177">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-177">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="4b2f9-178">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="4b2f9-178">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="4b2f9-179">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-179">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="4b2f9-180">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="4b2f9-180">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="4b2f9-181">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-181">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="4b2f9-182">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-182">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="4b2f9-183">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4b2f9-183">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="4b2f9-184">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-184">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="4b2f9-185">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="4b2f9-185">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="4b2f9-186">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4b2f9-186">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
