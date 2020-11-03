---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202649"
---
# <span data-ttu-id="04908-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="04908-103">Suspend-Job</span></span>

## <span data-ttu-id="04908-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="04908-104">SYNOPSIS</span></span>
<span data-ttu-id="04908-105">Arrête temporairement les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="04908-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="04908-106">SYNTAX</span></span>

### <span data-ttu-id="04908-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="04908-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04908-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="04908-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04908-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="04908-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04908-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="04908-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04908-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="04908-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="04908-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="04908-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="04908-113">Description</span><span class="sxs-lookup"><span data-stu-id="04908-113">DESCRIPTION</span></span>
<span data-ttu-id="04908-114">L’applet **de commande suspend-Job suspend les** tâches de Workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-114">The **Suspend-Job** cmdlet suspends workflow jobs.</span></span>
<span data-ttu-id="04908-115">Suspendre signifie temporairement interrompre ou suspendre une tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span>
<span data-ttu-id="04908-116">Cette applet de commande permet aux utilisateurs qui exécutent des workflows de suspendre le workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span>
<span data-ttu-id="04908-117">Il complète l’activité suspend-Workflow https://go.microsoft.com/fwlink/?LinkId=267141 , qui est une commande dans le workflow qui suspend le Workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="04908-118">L'applet de commande **Suspend-Job** fonctionne seulement sur les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-118">The **Suspend-Job** cmdlet works only on workflow jobs.</span></span>
<span data-ttu-id="04908-119">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles qui sont démarrées à l’aide de l’applet de commande Start-Job.</span><span class="sxs-lookup"><span data-stu-id="04908-119">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="04908-120">Pour identifier une tâche de workflow, recherchez la valeur de PSWorkflowJob dans la propriété **PSJobTypeName** de la tâche.</span><span class="sxs-lookup"><span data-stu-id="04908-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="04908-121">Pour déterminer si un type particulier de tâche personnalisée prend en charge l'applet de commande **Suspend-Job** , consultez les rubriques d'aide associées à ce type.</span><span class="sxs-lookup"><span data-stu-id="04908-121">To determine whether a particular custom job type supports the **Suspend-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="04908-122">Quand vous suspendez une tâche de workflow, la tâche de workflow s'exécute jusqu'au prochain point de contrôle, se met en suspens et retourne immédiatement un objet de tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span>
<span data-ttu-id="04908-123">Pour attendre la fin de la suspension avant d’obtenir la tâche, utilisez le paramètre *Wait* de l’applet de commande **suspend-Job** ou Wait-Job.</span><span class="sxs-lookup"><span data-stu-id="04908-123">To wait for the suspension to complete before getting the job, use the *Wait* parameter of **Suspend-Job** or the Wait-Job cmdlet.</span></span>
<span data-ttu-id="04908-124">Lorsque la tâche de workflow est interrompue, la valeur de la propriété **State** du travail est suspendue.</span><span class="sxs-lookup"><span data-stu-id="04908-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="04908-125">Une mise en suspens correcte s'appuie sur les points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="04908-125">Suspending correctly relies on checkpoints.</span></span>
<span data-ttu-id="04908-126">L’état actuel de la tâche, les métadonnées et la sortie sont enregistrés dans le point de contrôle afin que la tâche de workflow puisse être reprise sans perte d’État ou de données.</span><span class="sxs-lookup"><span data-stu-id="04908-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span>
<span data-ttu-id="04908-127">Si la tâche de workflow n’a pas de points de contrôle, elle ne peut pas être suspendue correctement.</span><span class="sxs-lookup"><span data-stu-id="04908-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span>
<span data-ttu-id="04908-128">Pour ajouter des points de contrôle à un workflow que vous exécutez, utilisez le paramètre commun de workflow *PSPersist* .</span><span class="sxs-lookup"><span data-stu-id="04908-128">To add checkpoints to a workflow that you are running, use the *PSPersist* workflow common parameter.</span></span>
<span data-ttu-id="04908-129">Vous pouvez utiliser le paramètre *force* pour suspendre une tâche de workflow immédiatement et suspendre une tâche de workflow qui n’a pas de points de contrôle, mais l’action peut entraîner la perte de l’État et des données.</span><span class="sxs-lookup"><span data-stu-id="04908-129">You can use the *Force* parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="04908-130">Avant d’utiliser une applet de commande de tâche sur un type de tâche personnalisé, par exemple une tâche de workflow ( **PSWorkflowJob** ), importez le module qui prend en charge le type de tâche personnalisé, soit à l’aide de l’applet de commande Import-Module, soit à l’aide de ou de l’utilisation d’une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="04908-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the Import-Module cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="04908-131">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="04908-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="04908-132">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="04908-132">EXAMPLES</span></span>

### <span data-ttu-id="04908-133">Exemple 1 : suspendre une tâche de workflow par nom</span><span class="sxs-lookup"><span data-stu-id="04908-133">Example 1: Suspend a workflow job by name</span></span>

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

<span data-ttu-id="04908-134">Cet exemple montre comment suspendre une tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-134">This example shows how to suspend a workflow job.</span></span>

### <span data-ttu-id="04908-135">Exemple 2 : suspendre et reprendre une tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="04908-135">Example 2: Suspend and resume a workflow job</span></span>

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

<span data-ttu-id="04908-136">Cet exemple montre comment suspendre et reprendre une tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-136">This example shows how to suspend and resume a workflow job.</span></span>

### <span data-ttu-id="04908-137">Exemple 3 : suspendre une tâche de workflow sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="04908-137">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="04908-138">Cette commande utilise l’applet de commande Invoke-Command pour interrompre une tâche de workflow sur l’ordinateur distant Srv01.</span><span class="sxs-lookup"><span data-stu-id="04908-138">This command uses the Invoke-Command cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span>
<span data-ttu-id="04908-139">La valeur du paramètre de *filtre* est une table de hachage qui spécifie une valeur CustomId.</span><span class="sxs-lookup"><span data-stu-id="04908-139">The value of the *Filter* parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="04908-140">Cet élément **CustomID** est une métadonnée de la tâche ( **PSPrivateMetadata** ).</span><span class="sxs-lookup"><span data-stu-id="04908-140">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="04908-141">Exemple 4 : attendre la suspension de la tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="04908-141">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="04908-142">Cette commande suspend la tâche de workflow VersionCheck.</span><span class="sxs-lookup"><span data-stu-id="04908-142">This command suspends the VersionCheck workflow job.</span></span>
<span data-ttu-id="04908-143">La commande utilise le paramètre *Wait* pour attendre jusqu'à ce que la tâche de workflow soit suspendue.</span><span class="sxs-lookup"><span data-stu-id="04908-143">The command uses the *Wait* parameter to wait until the workflow job is suspended.</span></span>
<span data-ttu-id="04908-144">Lorsque la tâche de workflow s’exécute jusqu’au point de contrôle suivant et est suspendue, la commande se termine et retourne l’objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="04908-144">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="04908-145">Exemple 5 : forcer l’interruption d’une tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="04908-145">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="04908-146">Cette commande suspend de force la tâche de workflow Maintenance.</span><span class="sxs-lookup"><span data-stu-id="04908-146">This command suspends the Maintenance workflow job forcibly.</span></span>
<span data-ttu-id="04908-147">La tâche de maintenance n’a pas de points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="04908-147">The Maintenance job does not have checkpoints.</span></span>
<span data-ttu-id="04908-148">Elle ne peut pas être suspendue correctement et peut ne pas reprendre correctement.</span><span class="sxs-lookup"><span data-stu-id="04908-148">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="04908-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="04908-149">PARAMETERS</span></span>

### <span data-ttu-id="04908-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="04908-150">-Filter</span></span>
<span data-ttu-id="04908-151">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="04908-151">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="04908-152">Cette applet de commande suspend les tâches qui répondent à toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="04908-152">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="04908-153">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="04908-153">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="04908-154">-Force</span><span class="sxs-lookup"><span data-stu-id="04908-154">-Force</span></span>
<span data-ttu-id="04908-155">Suspend immédiatement la tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-155">Suspends the workflow job immediately.</span></span>
<span data-ttu-id="04908-156">Cette action peut entraîner une perte de l’État et des données.</span><span class="sxs-lookup"><span data-stu-id="04908-156">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="04908-157">Par défaut, **Suspend-Job** permet à la tâche de workflow de s'exécuter jusqu'au point de contrôle suivant, puis la suspend.</span><span class="sxs-lookup"><span data-stu-id="04908-157">By default, **Suspend-Job** lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="04908-158">Vous pouvez également utiliser ce paramètre pour suspendre des tâches de workflow qui n'ont pas de points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="04908-158">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04908-159">-Id</span><span class="sxs-lookup"><span data-stu-id="04908-159">-Id</span></span>
<span data-ttu-id="04908-160">Spécifie les ID des travaux que cette applet de commande suspend.</span><span class="sxs-lookup"><span data-stu-id="04908-160">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="04908-161">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="04908-161">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="04908-162">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="04908-162">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="04908-163">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="04908-163">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="04908-164">Pour Rechercher l’ID d’un travail, utilisez l’applet de commande Get-Job.</span><span class="sxs-lookup"><span data-stu-id="04908-164">To find the ID of a job, use the Get-Job cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="04908-165">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="04908-165">-InstanceId</span></span>
<span data-ttu-id="04908-166">Spécifie les ID d’instance des travaux que cette applet de commande suspend.</span><span class="sxs-lookup"><span data-stu-id="04908-166">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="04908-167">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="04908-167">The default is all jobs.</span></span>

<span data-ttu-id="04908-168">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="04908-168">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="04908-169">Pour rechercher l'ID d'instance d'une tâche, utilisez **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="04908-169">To find the instance ID of a job, use **Get-Job** .</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="04908-170">-Travail</span><span class="sxs-lookup"><span data-stu-id="04908-170">-Job</span></span>
<span data-ttu-id="04908-171">Spécifie les tâches de workflow que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="04908-171">Specifies the workflow jobs that this cmdlet stops.</span></span>
<span data-ttu-id="04908-172">Entrez une variable qui contient les tâches de workflow ou tapez une commande permettant d'obtenir ces tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-172">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span>
<span data-ttu-id="04908-173">Vous pouvez également diriger des tâches de workflow vers l'applet de commande **Suspend-Job** .</span><span class="sxs-lookup"><span data-stu-id="04908-173">You can also pipe workflow jobs to the **Suspend-Job** cmdlet.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="04908-174">-Name</span><span class="sxs-lookup"><span data-stu-id="04908-174">-Name</span></span>
<span data-ttu-id="04908-175">Spécifie les noms conviviaux des travaux que cette applet de commande suspend.</span><span class="sxs-lookup"><span data-stu-id="04908-175">Specifies friendly names of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="04908-176">Entrez un ou plusieurs noms de tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="04908-176">Enter one or more workflow job names.</span></span>
<span data-ttu-id="04908-177">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="04908-177">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="04908-178">-État</span><span class="sxs-lookup"><span data-stu-id="04908-178">-State</span></span>
<span data-ttu-id="04908-179">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="04908-179">Specifies a job state.</span></span>
<span data-ttu-id="04908-180">Cette applet de commande arrête uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="04908-180">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="04908-181">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="04908-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="04908-182">NotStarted</span><span class="sxs-lookup"><span data-stu-id="04908-182">NotStarted</span></span>
- <span data-ttu-id="04908-183">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="04908-183">Running</span></span>
- <span data-ttu-id="04908-184">Completed</span><span class="sxs-lookup"><span data-stu-id="04908-184">Completed</span></span>
- <span data-ttu-id="04908-185">Échec</span><span class="sxs-lookup"><span data-stu-id="04908-185">Failed</span></span>
- <span data-ttu-id="04908-186">Arrêté</span><span class="sxs-lookup"><span data-stu-id="04908-186">Stopped</span></span>
- <span data-ttu-id="04908-187">Bloqué</span><span class="sxs-lookup"><span data-stu-id="04908-187">Blocked</span></span>
- <span data-ttu-id="04908-188">Interrompu</span><span class="sxs-lookup"><span data-stu-id="04908-188">Suspended</span></span>
- <span data-ttu-id="04908-189">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="04908-189">Disconnected</span></span>
- <span data-ttu-id="04908-190">Suspension</span><span class="sxs-lookup"><span data-stu-id="04908-190">Suspending</span></span>
- <span data-ttu-id="04908-191">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="04908-191">Stopping</span></span>

<span data-ttu-id="04908-192">**Suspend : le travail** suspend uniquement les tâches de workflow dans l’État en **cours d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="04908-192">**Suspend-Job** suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="04908-193">Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="04908-193">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="04908-194">-Wait</span><span class="sxs-lookup"><span data-stu-id="04908-194">-Wait</span></span>
<span data-ttu-id="04908-195">Indique que cette applet de commande supprime l’invite de commandes jusqu’à ce que la tâche de workflow soit dans l’état suspendu.</span><span class="sxs-lookup"><span data-stu-id="04908-195">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span>
<span data-ttu-id="04908-196">Par défaut, **suspend-Job** est retourné immédiatement, même si la tâche de workflow n’est pas encore dans l’État Suspended.</span><span class="sxs-lookup"><span data-stu-id="04908-196">By default, **Suspend-Job** returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="04908-197">Le paramètre *Wait* équivaut à diriger une commande **suspend-Job** vers l’applet de commande **Wait-Job** .</span><span class="sxs-lookup"><span data-stu-id="04908-197">The *Wait* parameter is equivalent to piping a **Suspend-Job** command to the **Wait-Job** cmdlet.</span></span>

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

### <span data-ttu-id="04908-198">-Confirm</span><span class="sxs-lookup"><span data-stu-id="04908-198">-Confirm</span></span>
<span data-ttu-id="04908-199">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="04908-199">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="04908-200">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="04908-200">-WhatIf</span></span>
<span data-ttu-id="04908-201">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="04908-201">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="04908-202">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="04908-202">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="04908-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="04908-203">CommonParameters</span></span>
<span data-ttu-id="04908-204">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="04908-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="04908-205">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="04908-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="04908-206">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="04908-206">INPUTS</span></span>

### <span data-ttu-id="04908-207">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="04908-207">System.Management.Automation.Job</span></span>
<span data-ttu-id="04908-208">Vous pouvez diriger tous les types de travaux vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="04908-208">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="04908-209">Toutefois, si **suspend-Job** obtient une tâche d’un type non pris en charge, elle retourne une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="04908-209">However, if **Suspend-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="04908-210">SORTIES</span><span class="sxs-lookup"><span data-stu-id="04908-210">OUTPUTS</span></span>

### <span data-ttu-id="04908-211">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="04908-211">System.Management.Automation.Job</span></span>
<span data-ttu-id="04908-212">Cette applet de commande retourne les tâches qu’elle a suspendues.</span><span class="sxs-lookup"><span data-stu-id="04908-212">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="04908-213">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="04908-213">NOTES</span></span>

* <span data-ttu-id="04908-214">Le mécanisme et l'emplacement pour enregistrer une tâche suspendue peuvent varier selon le type de tâche.</span><span class="sxs-lookup"><span data-stu-id="04908-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="04908-215">Par exemple, les tâches de workflow suspendues sont enregistrées par défaut dans un magasin de fichiers plats, mais elles peuvent également être enregistrées dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="04908-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
* <span data-ttu-id="04908-216">Si vous soumettez une tâche de workflow qui n'est pas dans l'état Running, **Suspend-Job** affiche un message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="04908-216">If you submit a workflow job that is not in the Running state, **Suspend-Job** displays a warning message.</span></span> <span data-ttu-id="04908-217">Pour supprimer l’avertissement, utilisez le paramètre commun *WarningAction* avec la valeur SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="04908-217">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="04908-218">Si un travail n’est pas d’un type qui prend en charge la suspension, **suspend-Job** retourne une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="04908-218">If a job is not of a type that supports suspending, **Suspend-Job** returns a terminating error.</span></span>

* <span data-ttu-id="04908-219">Pour rechercher les tâches de workflow qui sont suspendues, y compris celles qui ont été suspendues par cette applet de commande, utilisez le paramètre *State* de l’applet de commande **obtenir-Job** pour obtenir les tâches de workflow dans l’État Suspended.</span><span class="sxs-lookup"><span data-stu-id="04908-219">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get workflow jobs in the Suspended state.</span></span>
* <span data-ttu-id="04908-220">Certains types de tâche ont des options ou des propriétés qui empêchent Windows PowerShell de suspendre la tâche.</span><span class="sxs-lookup"><span data-stu-id="04908-220">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="04908-221">Si les tentatives d’interruption de la tâche échouent, vérifiez que les options et les propriétés du travail autorisent la suspension.</span><span class="sxs-lookup"><span data-stu-id="04908-221">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="04908-222">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="04908-222">RELATED LINKS</span></span>

[<span data-ttu-id="04908-223">Get-Job</span><span class="sxs-lookup"><span data-stu-id="04908-223">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="04908-224">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="04908-224">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="04908-225">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="04908-225">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="04908-226">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="04908-226">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="04908-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="04908-227">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="04908-228">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="04908-228">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="04908-229">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="04908-229">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="04908-230">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="04908-230">Wait-Job</span></span>](Wait-Job.md)
