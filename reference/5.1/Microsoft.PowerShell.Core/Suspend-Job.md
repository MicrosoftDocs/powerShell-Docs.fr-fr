---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388463"
---
# <span data-ttu-id="82f0b-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-103">Suspend-Job</span></span>

## <span data-ttu-id="82f0b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="82f0b-104">SYNOPSIS</span></span>
<span data-ttu-id="82f0b-105">Arrête temporairement les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="82f0b-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="82f0b-106">SYNTAX</span></span>

### <span data-ttu-id="82f0b-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="82f0b-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f0b-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="82f0b-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f0b-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="82f0b-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f0b-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="82f0b-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f0b-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="82f0b-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f0b-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="82f0b-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82f0b-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="82f0b-113">DESCRIPTION</span></span>

<span data-ttu-id="82f0b-114">L' `Suspend-Job` applet de commande suspend les tâches de Workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-114">The `Suspend-Job` cmdlet suspends workflow jobs.</span></span> <span data-ttu-id="82f0b-115">Suspendre signifie temporairement interrompre ou suspendre une tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span> <span data-ttu-id="82f0b-116">Cette applet de commande permet aux utilisateurs qui exécutent des workflows de suspendre le workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span> <span data-ttu-id="82f0b-117">Il complète l’activité suspend-Workflow https://go.microsoft.com/fwlink/?LinkId=267141 , qui est une commande dans le workflow qui suspend le Workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="82f0b-118">L' `Suspend-Job` applet de commande fonctionne uniquement sur les tâches de Workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-118">The `Suspend-Job` cmdlet works only on workflow jobs.</span></span> <span data-ttu-id="82f0b-119">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles qui sont démarrées à l’aide de l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="82f0b-119">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="82f0b-120">Pour identifier une tâche de workflow, recherchez la valeur de PSWorkflowJob dans la propriété **PSJobTypeName** de la tâche.</span><span class="sxs-lookup"><span data-stu-id="82f0b-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="82f0b-121">Pour déterminer si un type de tâche personnalisé particulier prend en charge l' `Suspend-Job` applet de commande, consultez les rubriques d’aide relatives au type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="82f0b-121">To determine whether a particular custom job type supports the `Suspend-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="82f0b-122">Quand vous suspendez une tâche de workflow, la tâche de workflow s'exécute jusqu'au prochain point de contrôle, se met en suspens et retourne immédiatement un objet de tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span> <span data-ttu-id="82f0b-123">Pour attendre la fin de la suspension avant d’obtenir la tâche, utilisez le paramètre **Wait** de `Suspend-Job` ou l’applet de commande `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="82f0b-123">To wait for the suspension to complete before getting the job, use the **Wait** parameter of `Suspend-Job` or the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="82f0b-124">Lorsque la tâche de workflow est interrompue, la valeur de la propriété **State** du travail est suspendue.</span><span class="sxs-lookup"><span data-stu-id="82f0b-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="82f0b-125">Une mise en suspens correcte s'appuie sur les points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="82f0b-125">Suspending correctly relies on checkpoints.</span></span> <span data-ttu-id="82f0b-126">L’état actuel de la tâche, les métadonnées et la sortie sont enregistrés dans le point de contrôle afin que la tâche de workflow puisse être reprise sans perte d’État ou de données.</span><span class="sxs-lookup"><span data-stu-id="82f0b-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span> <span data-ttu-id="82f0b-127">Si la tâche de workflow n’a pas de points de contrôle, elle ne peut pas être suspendue correctement.</span><span class="sxs-lookup"><span data-stu-id="82f0b-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span> <span data-ttu-id="82f0b-128">Pour ajouter des points de contrôle à un workflow que vous exécutez, utilisez le paramètre commun de workflow **PSPersist**.</span><span class="sxs-lookup"><span data-stu-id="82f0b-128">To add checkpoints to a workflow that you are running, use the **PSPersist** workflow common parameter.</span></span> <span data-ttu-id="82f0b-129">Vous pouvez utiliser le paramètre **force** pour suspendre une tâche de workflow immédiatement et suspendre une tâche de workflow qui n’a pas de points de contrôle, mais l’action peut entraîner la perte de l’État et des données.</span><span class="sxs-lookup"><span data-stu-id="82f0b-129">You can use the **Force** parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="82f0b-130">Avant d’utiliser une applet de commande de tâche sur un type de tâche personnalisé, par exemple une tâche de workflow ( **PSWorkflowJob** ), importez le module qui prend en charge le type de tâche personnalisé, soit à l’aide de l’applet de commande, soit en utilisant `Import-Module` ou en utilisant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="82f0b-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the `Import-Module` cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="82f0b-131">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="82f0b-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="82f0b-132">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="82f0b-132">EXAMPLES</span></span>

### <span data-ttu-id="82f0b-133">Exemple 1 : suspendre une tâche de workflow par nom</span><span class="sxs-lookup"><span data-stu-id="82f0b-133">Example 1: Suspend a workflow job by name</span></span>

<span data-ttu-id="82f0b-134">Cet exemple montre comment suspendre une tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-134">This example shows how to suspend a workflow job.</span></span>

<span data-ttu-id="82f0b-135">La première commande crée le `Get-SystemLog` Workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-135">The first command creates the `Get-SystemLog` workflow.</span></span> <span data-ttu-id="82f0b-136">Le workflow utilise l' `CheckPoint-Workflow` activité pour définir un point de contrôle dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="82f0b-136">The workflow uses the `CheckPoint-Workflow` activity to define a checkpoint in the workflow.</span></span>

<span data-ttu-id="82f0b-137">La deuxième commande utilise le paramètre **AsJob** qui est commun à tous les workflows pour exécuter le `Get-SystemLog` Workflow en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="82f0b-137">The second command uses the **AsJob** parameter that is common to all workflows to run the `Get-SystemLog` workflow as a background job.</span></span> <span data-ttu-id="82f0b-138">La commande utilise le paramètre commun de workflow **JobName** pour spécifier un nom convivial pour la tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-138">The command uses the **JobName** workflow common parameter to specify a friendly name for the workflow job.</span></span>

<span data-ttu-id="82f0b-139">La troisième commande utilise l' `Get-Job` applet de commande pour récupérer la `Get-SystemLogJob` tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-139">The third command uses the `Get-Job` cmdlet to get the `Get-SystemLogJob` workflow job.</span></span> <span data-ttu-id="82f0b-140">La sortie indique que la valeur de la propriété **PSJobTypeName** est PSWorkflowJob.</span><span class="sxs-lookup"><span data-stu-id="82f0b-140">The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.</span></span>

<span data-ttu-id="82f0b-141">La quatrième commande utilise l' `Suspend-Job` applet de commande pour interrompre la `Get-SystemLogJob` tâche.</span><span class="sxs-lookup"><span data-stu-id="82f0b-141">The fourth command uses the `Suspend-Job` cmdlet to suspend the `Get-SystemLogJob` job.</span></span> <span data-ttu-id="82f0b-142">La tâche s'exécute jusqu'au point de contrôle, puis se met en suspens.</span><span class="sxs-lookup"><span data-stu-id="82f0b-142">The job runs to the checkpoint and then suspends.</span></span>

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### <span data-ttu-id="82f0b-143">Exemple 2 : suspendre et reprendre une tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="82f0b-143">Example 2: Suspend and resume a workflow job</span></span>

<span data-ttu-id="82f0b-144">Cet exemple montre comment suspendre et reprendre une tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-144">This example shows how to suspend and resume a workflow job.</span></span>

<span data-ttu-id="82f0b-145">La première commande interrompt la tâche LogWorkflowJob. La commande est immédiatement retournée.</span><span class="sxs-lookup"><span data-stu-id="82f0b-145">The first command suspends the LogWorkflowJob job.The command returns immediately.</span></span> <span data-ttu-id="82f0b-146">La sortie indique que la tâche de workflow est toujours en cours d’exécution, même si elle est en cours de suspension.</span><span class="sxs-lookup"><span data-stu-id="82f0b-146">The output shows that the workflow job is still running, even though it is being suspended.</span></span>

<span data-ttu-id="82f0b-147">La deuxième commande utilise l' `Get-Job` applet de commande pour récupérer la tâche LogWorkflowJob.</span><span class="sxs-lookup"><span data-stu-id="82f0b-147">The second command uses the `Get-Job` cmdlet to get the LogWorkflowJob job.</span></span> <span data-ttu-id="82f0b-148">La sortie montre que la tâche de workflow a été suspendue.</span><span class="sxs-lookup"><span data-stu-id="82f0b-148">The output shows that the workflow job suspended successfully.</span></span>

<span data-ttu-id="82f0b-149">La troisième commande utilise l' `Get-Job` applet de commande pour récupérer la tâche LogWorkflowJob et l' `Resume-Job` applet de commande pour la reprendre.</span><span class="sxs-lookup"><span data-stu-id="82f0b-149">The third command uses the `Get-Job` cmdlet to get the LogWorkflowJob job and the `Resume-Job` cmdlet to resume it.</span></span> <span data-ttu-id="82f0b-150">La sortie montre que la tâche de workflow a repris et est maintenant en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="82f0b-150">The output shows that the workflow job resumed successfully and is now running.</span></span>

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### <span data-ttu-id="82f0b-151">Exemple 3 : suspendre une tâche de workflow sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="82f0b-151">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="82f0b-152">Cette commande utilise la `Invoke-Command` cmdlet pour interrompre une tâche de workflow sur l’ordinateur distant Srv01.</span><span class="sxs-lookup"><span data-stu-id="82f0b-152">This command uses the `Invoke-Command` cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span> <span data-ttu-id="82f0b-153">La valeur du paramètre de **filtre** est une table de hachage qui spécifie une valeur CustomId.</span><span class="sxs-lookup"><span data-stu-id="82f0b-153">The value of the **Filter** parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="82f0b-154">Cet élément **CustomID** est une métadonnée de la tâche ( **PSPrivateMetadata** ).</span><span class="sxs-lookup"><span data-stu-id="82f0b-154">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="82f0b-155">Exemple 4 : attendre la suspension de la tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="82f0b-155">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="82f0b-156">Cette commande suspend la tâche de workflow VersionCheck.</span><span class="sxs-lookup"><span data-stu-id="82f0b-156">This command suspends the VersionCheck workflow job.</span></span> <span data-ttu-id="82f0b-157">La commande utilise le paramètre **Wait** pour attendre jusqu'à ce que la tâche de workflow soit suspendue.</span><span class="sxs-lookup"><span data-stu-id="82f0b-157">The command uses the **Wait** parameter to wait until the workflow job is suspended.</span></span> <span data-ttu-id="82f0b-158">Lorsque la tâche de workflow s’exécute jusqu’au point de contrôle suivant et est suspendue, la commande se termine et retourne l’objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="82f0b-158">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="82f0b-159">Exemple 5 : forcer l’interruption d’une tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="82f0b-159">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="82f0b-160">Cette commande suspend de force la tâche de workflow Maintenance.</span><span class="sxs-lookup"><span data-stu-id="82f0b-160">This command suspends the Maintenance workflow job forcibly.</span></span> <span data-ttu-id="82f0b-161">La tâche de maintenance n’a pas de points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="82f0b-161">The Maintenance job does not have checkpoints.</span></span> <span data-ttu-id="82f0b-162">Elle ne peut pas être suspendue correctement et peut ne pas reprendre correctement.</span><span class="sxs-lookup"><span data-stu-id="82f0b-162">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="82f0b-163">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="82f0b-163">PARAMETERS</span></span>

### <span data-ttu-id="82f0b-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="82f0b-164">-Filter</span></span>

<span data-ttu-id="82f0b-165">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="82f0b-165">Specifies a hash table of conditions.</span></span> <span data-ttu-id="82f0b-166">Cette applet de commande suspend les tâches qui répondent à toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="82f0b-166">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="82f0b-167">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="82f0b-167">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="82f0b-168">-Force</span><span class="sxs-lookup"><span data-stu-id="82f0b-168">-Force</span></span>

<span data-ttu-id="82f0b-169">Suspend immédiatement la tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-169">Suspends the workflow job immediately.</span></span> <span data-ttu-id="82f0b-170">Cette action peut entraîner une perte de l’État et des données.</span><span class="sxs-lookup"><span data-stu-id="82f0b-170">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="82f0b-171">Par défaut, `Suspend-Job` permet à la tâche de workflow de s’exécuter jusqu’au point de contrôle suivant, puis de l’interrompre.</span><span class="sxs-lookup"><span data-stu-id="82f0b-171">By default, `Suspend-Job` lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="82f0b-172">Vous pouvez également utiliser ce paramètre pour suspendre des tâches de workflow qui n'ont pas de points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="82f0b-172">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

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

### <span data-ttu-id="82f0b-173">-Id</span><span class="sxs-lookup"><span data-stu-id="82f0b-173">-Id</span></span>

<span data-ttu-id="82f0b-174">Spécifie les ID des travaux que cette applet de commande suspend.</span><span class="sxs-lookup"><span data-stu-id="82f0b-174">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="82f0b-175">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="82f0b-175">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="82f0b-176">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="82f0b-176">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="82f0b-177">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="82f0b-177">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="82f0b-178">Pour Rechercher l’ID d’un travail, utilisez l' `Get-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82f0b-178">To find the ID of a job, use the `Get-Job` cmdlet.</span></span>

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

### <span data-ttu-id="82f0b-179">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="82f0b-179">-InstanceId</span></span>

<span data-ttu-id="82f0b-180">Spécifie les ID d’instance des travaux que cette applet de commande suspend.</span><span class="sxs-lookup"><span data-stu-id="82f0b-180">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="82f0b-181">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="82f0b-181">The default is all jobs.</span></span>

<span data-ttu-id="82f0b-182">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="82f0b-182">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="82f0b-183">Pour Rechercher l’ID d’instance d’un travail, utilisez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="82f0b-183">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="82f0b-184">-Travail</span><span class="sxs-lookup"><span data-stu-id="82f0b-184">-Job</span></span>

<span data-ttu-id="82f0b-185">Spécifie les tâches de workflow que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="82f0b-185">Specifies the workflow jobs that this cmdlet stops.</span></span> <span data-ttu-id="82f0b-186">Entrez une variable qui contient les tâches de workflow ou tapez une commande permettant d'obtenir ces tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-186">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span> <span data-ttu-id="82f0b-187">Vous pouvez également diriger les tâches de workflow vers l’applet de commande `Suspend-Job` .</span><span class="sxs-lookup"><span data-stu-id="82f0b-187">You can also pipe workflow jobs to the `Suspend-Job` cmdlet.</span></span>

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

### <span data-ttu-id="82f0b-188">-Name</span><span class="sxs-lookup"><span data-stu-id="82f0b-188">-Name</span></span>

<span data-ttu-id="82f0b-189">Spécifie les noms conviviaux des travaux que cette applet de commande suspend.</span><span class="sxs-lookup"><span data-stu-id="82f0b-189">Specifies friendly names of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="82f0b-190">Entrez un ou plusieurs noms de tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="82f0b-190">Enter one or more workflow job names.</span></span>
<span data-ttu-id="82f0b-191">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="82f0b-191">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="82f0b-192">-État</span><span class="sxs-lookup"><span data-stu-id="82f0b-192">-State</span></span>

<span data-ttu-id="82f0b-193">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="82f0b-193">Specifies a job state.</span></span> <span data-ttu-id="82f0b-194">Cette applet de commande arrête uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="82f0b-194">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="82f0b-195">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="82f0b-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82f0b-196">NotStarted</span><span class="sxs-lookup"><span data-stu-id="82f0b-196">NotStarted</span></span>
- <span data-ttu-id="82f0b-197">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="82f0b-197">Running</span></span>
- <span data-ttu-id="82f0b-198">Completed</span><span class="sxs-lookup"><span data-stu-id="82f0b-198">Completed</span></span>
- <span data-ttu-id="82f0b-199">Échec</span><span class="sxs-lookup"><span data-stu-id="82f0b-199">Failed</span></span>
- <span data-ttu-id="82f0b-200">Arrêté</span><span class="sxs-lookup"><span data-stu-id="82f0b-200">Stopped</span></span>
- <span data-ttu-id="82f0b-201">Bloqué</span><span class="sxs-lookup"><span data-stu-id="82f0b-201">Blocked</span></span>
- <span data-ttu-id="82f0b-202">Interrompu</span><span class="sxs-lookup"><span data-stu-id="82f0b-202">Suspended</span></span>
- <span data-ttu-id="82f0b-203">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="82f0b-203">Disconnected</span></span>
- <span data-ttu-id="82f0b-204">Suspension</span><span class="sxs-lookup"><span data-stu-id="82f0b-204">Suspending</span></span>
- <span data-ttu-id="82f0b-205">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="82f0b-205">Stopping</span></span>

<span data-ttu-id="82f0b-206">`Suspend-Job` suspend uniquement les tâches de workflow dans l’état **en cours d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="82f0b-206">`Suspend-Job` suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="82f0b-207">Pour plus d’informations sur les États de travail, consultez [énumération JobState](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="82f0b-207">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="82f0b-208">-Wait</span><span class="sxs-lookup"><span data-stu-id="82f0b-208">-Wait</span></span>

<span data-ttu-id="82f0b-209">Indique que cette applet de commande supprime l’invite de commandes jusqu’à ce que la tâche de workflow soit dans l’état suspendu.</span><span class="sxs-lookup"><span data-stu-id="82f0b-209">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span> <span data-ttu-id="82f0b-210">Par défaut, `Suspend-Job` retourne immédiatement, même si la tâche de workflow n’est pas encore dans l’État Suspended.</span><span class="sxs-lookup"><span data-stu-id="82f0b-210">By default, `Suspend-Job` returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="82f0b-211">Le paramètre **Wait** équivaut à diriger une `Suspend-Job` commande vers l’applet de commande `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="82f0b-211">The **Wait** parameter is equivalent to piping a `Suspend-Job` command to the `Wait-Job` cmdlet.</span></span>

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

### <span data-ttu-id="82f0b-212">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82f0b-212">-Confirm</span></span>

<span data-ttu-id="82f0b-213">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82f0b-213">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="82f0b-214">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82f0b-214">-WhatIf</span></span>

<span data-ttu-id="82f0b-215">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82f0b-215">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="82f0b-216">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="82f0b-216">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="82f0b-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82f0b-217">CommonParameters</span></span>

<span data-ttu-id="82f0b-218">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82f0b-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82f0b-219">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82f0b-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82f0b-220">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="82f0b-220">INPUTS</span></span>

### <span data-ttu-id="82f0b-221">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="82f0b-221">System.Management.Automation.Job</span></span>

<span data-ttu-id="82f0b-222">Vous pouvez diriger tous les types de travaux vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82f0b-222">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="82f0b-223">Toutefois, si `Suspend-Job` obtient une tâche d’un type non pris en charge, elle retourne une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="82f0b-223">However, if `Suspend-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="82f0b-224">SORTIES</span><span class="sxs-lookup"><span data-stu-id="82f0b-224">OUTPUTS</span></span>

### <span data-ttu-id="82f0b-225">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="82f0b-225">System.Management.Automation.Job</span></span>
<span data-ttu-id="82f0b-226">Cette applet de commande retourne les tâches qu’elle a suspendues.</span><span class="sxs-lookup"><span data-stu-id="82f0b-226">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="82f0b-227">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="82f0b-227">NOTES</span></span>

- <span data-ttu-id="82f0b-228">Le mécanisme et l'emplacement pour enregistrer une tâche suspendue peuvent varier selon le type de tâche.</span><span class="sxs-lookup"><span data-stu-id="82f0b-228">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="82f0b-229">Par exemple, les tâches de workflow suspendues sont enregistrées par défaut dans un magasin de fichiers plats, mais elles peuvent également être enregistrées dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="82f0b-229">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
- <span data-ttu-id="82f0b-230">Si vous soumettez une tâche de workflow qui n’est pas à l’État en cours d’exécution, `Suspend-Job` affiche un message d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="82f0b-230">If you submit a workflow job that is not in the Running state, `Suspend-Job` displays a warning message.</span></span> <span data-ttu-id="82f0b-231">Pour supprimer l’avertissement, utilisez le paramètre commun **WarningAction** avec la valeur SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="82f0b-231">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="82f0b-232">Si un travail n’est pas d’un type qui prend en charge la suspension, `Suspend-Job` retourne une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="82f0b-232">If a job is not of a type that supports suspending, `Suspend-Job` returns a terminating error.</span></span>

- <span data-ttu-id="82f0b-233">Pour rechercher les tâches de workflow suspendues, y compris celles qui ont été suspendues par cette applet de commande, utilisez le paramètre **State** de l’applet de commande `Get-Job` pour obtenir les tâches de workflow dans l’État Suspended.</span><span class="sxs-lookup"><span data-stu-id="82f0b-233">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get workflow jobs in the Suspended state.</span></span>
- <span data-ttu-id="82f0b-234">Certains types de tâche ont des options ou des propriétés qui empêchent Windows PowerShell de suspendre la tâche.</span><span class="sxs-lookup"><span data-stu-id="82f0b-234">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="82f0b-235">Si les tentatives d’interruption de la tâche échouent, vérifiez que les options et les propriétés du travail autorisent la suspension.</span><span class="sxs-lookup"><span data-stu-id="82f0b-235">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="82f0b-236">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="82f0b-236">RELATED LINKS</span></span>

[<span data-ttu-id="82f0b-237">Get-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-237">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="82f0b-238">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-238">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="82f0b-239">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-239">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="82f0b-240">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-240">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="82f0b-241">Start-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-241">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="82f0b-242">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-242">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="82f0b-243">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-243">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="82f0b-244">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="82f0b-244">Wait-Job</span></span>](Wait-Job.md)
