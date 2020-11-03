---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202674"
---
# <span data-ttu-id="75e1d-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-103">Resume-Job</span></span>

## <span data-ttu-id="75e1d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="75e1d-104">SYNOPSIS</span></span>
<span data-ttu-id="75e1d-105">Redémarre une tâche suspendue.</span><span class="sxs-lookup"><span data-stu-id="75e1d-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="75e1d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75e1d-106">SYNTAX</span></span>

### <span data-ttu-id="75e1d-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="75e1d-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="75e1d-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="75e1d-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="75e1d-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="75e1d-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="75e1d-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="75e1d-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="75e1d-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="75e1d-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="75e1d-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="75e1d-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="75e1d-113">Description</span><span class="sxs-lookup"><span data-stu-id="75e1d-113">DESCRIPTION</span></span>
<span data-ttu-id="75e1d-114">L’applet de commande **Resume-Job** reprend une tâche de workflow qui a été suspendue, par exemple à l’aide de l’applet de commande Suspend-Job ou de l’activité About_Suspend-Workflow.</span><span class="sxs-lookup"><span data-stu-id="75e1d-114">The **Resume-Job** cmdlet resumes a workflow job that was suspended, such as by using the Suspend-Job cmdlet or the about_Suspend-Workflow activity.</span></span>
<span data-ttu-id="75e1d-115">Lors de la reprise d’une tâche de workflow, le moteur de tâche reconstruit l’État, les métadonnées et la sortie à partir des ressources enregistrées, telles que les points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="75e1d-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span>
<span data-ttu-id="75e1d-116">La tâche est redémarrée sans perte de données ou d’État.</span><span class="sxs-lookup"><span data-stu-id="75e1d-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="75e1d-117">L'état de la tâche est changé de **Suspended** en **Running** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-117">The job state is changed from **Suspended** to **Running** .</span></span>

<span data-ttu-id="75e1d-118">Utilisez les paramètres de **Resume-Job** pour sélectionner les travaux par nom, ID, ID d’instance ou diriger un objet de traitement, tel que celui retourné par l’applet de commande Get-Job, pour **reprendre-Job** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-118">Use the parameters of **Resume-Job** to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the Get-Job cmdlet, to **Resume-Job** .</span></span>
<span data-ttu-id="75e1d-119">Vous pouvez aussi utiliser un filtre de propriété pour sélectionner une tâche à reprendre.</span><span class="sxs-lookup"><span data-stu-id="75e1d-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="75e1d-120">Par défaut, **Resume-Job** se termine immédiatement, même si certaines tâches n'ont pas encore repris.</span><span class="sxs-lookup"><span data-stu-id="75e1d-120">By default, **Resume-Job** returns immediately, even though all jobs might not yet be resumed.</span></span>
<span data-ttu-id="75e1d-121">Pour supprimer l'invite de commandes jusqu'à ce que toutes les tâches spécifiées aient repris, utilisez le paramètre *Wait* .</span><span class="sxs-lookup"><span data-stu-id="75e1d-121">To suppress the command prompt until all specified jobs are resumed, use the *Wait* parameter.</span></span>

<span data-ttu-id="75e1d-122">L'applet de commande **Resume-Job** fonctionne seulement sur les types de tâches personnalisées, comme des tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="75e1d-122">The **Resume-Job** cmdlet works only on custom job types, such as workflow jobs.</span></span>
<span data-ttu-id="75e1d-123">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles qui sont démarrées à l’aide de l’applet de commande Start-Job.</span><span class="sxs-lookup"><span data-stu-id="75e1d-123">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>
<span data-ttu-id="75e1d-124">Si vous soumettez une tâche d'un type non pris en charge, **Resume-Job** génère une erreur avec fin d'exécution et cesse de s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="75e1d-124">If you submit a job of an unsupported type, **Resume-Job** generates a terminating error and stops running.</span></span>

<span data-ttu-id="75e1d-125">Pour identifier une tâche de workflow, recherchez la valeur de **PSWorkflowJob** dans la propriété **PSJobTypeName** de la tâche.</span><span class="sxs-lookup"><span data-stu-id="75e1d-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="75e1d-126">Pour déterminer si un type particulier de tâche personnalisé prend en charge l'applet de commande **Resume-Job** , consultez les rubriques d'aide associées à ce type.</span><span class="sxs-lookup"><span data-stu-id="75e1d-126">To determine whether a particular custom job type supports the **Resume-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="75e1d-127">Avant d’utiliser une applet de commande de tâche sur un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé, soit à l’aide de l’applet de commande Import-Module, soit en obtenant ou en utilisant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="75e1d-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the Import-Module cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="75e1d-128">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="75e1d-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="75e1d-129">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="75e1d-129">EXAMPLES</span></span>

### <span data-ttu-id="75e1d-130">Exemple 1 : reprendre un travail par ID</span><span class="sxs-lookup"><span data-stu-id="75e1d-130">Example 1: Resume a job by ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

<span data-ttu-id="75e1d-131">Les commandes de cet exemple vérifient que la tâche est une tâche de workflow suspendue, puis reprennent la tâche.</span><span class="sxs-lookup"><span data-stu-id="75e1d-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span>

### <span data-ttu-id="75e1d-132">Exemple 2 : reprendre une tâche par son nom</span><span class="sxs-lookup"><span data-stu-id="75e1d-132">Example 2: Resume a job by name</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

<span data-ttu-id="75e1d-133">Cette commande utilise le paramètre *Name* pour reprendre plusieurs tâches de workflow sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="75e1d-133">This command uses the *Name* parameter to resume several workflow jobs on the local computer.</span></span>

### <span data-ttu-id="75e1d-134">Exemple 3 : utiliser des valeurs de propriétés personnalisées</span><span class="sxs-lookup"><span data-stu-id="75e1d-134">Example 3: Use custom property values</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

<span data-ttu-id="75e1d-135">Cette commande utilise la valeur d'une propriété personnalisée pour identifier la tâche de workflow à reprendre.</span><span class="sxs-lookup"><span data-stu-id="75e1d-135">This command uses the value of a custom property to identify the workflow job to resume.</span></span>
<span data-ttu-id="75e1d-136">Elle utilise le paramètre *Filter* pour identifier la tâche de workflow par sa propriété **CustomID** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-136">It uses the *Filter* parameter to identify the workflow job by its **CustomID** property.</span></span>
<span data-ttu-id="75e1d-137">Elle utilise également le paramètre *State* pour vérifier que la tâche de workflow est suspendue, avant d'essayer de la reprendre.</span><span class="sxs-lookup"><span data-stu-id="75e1d-137">It also uses the *State* parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

### <span data-ttu-id="75e1d-138">Exemple 4 : reprendre toutes les tâches suspendues sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="75e1d-138">Example 4: Resume all suspended jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="75e1d-139">Cette commande reprend toutes les tâches suspendues sur l'ordinateur distant Srv01.</span><span class="sxs-lookup"><span data-stu-id="75e1d-139">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

<span data-ttu-id="75e1d-140">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur Srv01.</span><span class="sxs-lookup"><span data-stu-id="75e1d-140">The command uses the Invoke-Command cmdlet to run a command on the Srv01 computer.</span></span>
<span data-ttu-id="75e1d-141">La commande distante utilise le paramètre *State* de l’applet de commande **« obtient-Job »** pour récupérer toutes les tâches suspendues sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75e1d-141">The remote command uses the *State* parameter of the **Get-Job** cmdlet to get all suspended jobs on the computer.</span></span>
<span data-ttu-id="75e1d-142">Un opérateur de pipeline (|) envoie les tâches suspendues à l'applet de commande **Resume-Job** , qui les reprend.</span><span class="sxs-lookup"><span data-stu-id="75e1d-142">A pipeline operator (|) sends the suspended jobs to the **Resume-Job** cmdlet, which resumes them.</span></span>

### <span data-ttu-id="75e1d-143">Exemple 5 : attendre la reprise des tâches</span><span class="sxs-lookup"><span data-stu-id="75e1d-143">Example 5: Wait for jobs to resume</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

<span data-ttu-id="75e1d-144">Cette commande utilise le paramètre *Wait* pour indiquer à **Resume-Job** de retourner uniquement une fois que toutes les tâches spécifiées ont repris.</span><span class="sxs-lookup"><span data-stu-id="75e1d-144">This command uses the *Wait* parameter to direct **Resume-Job** to return only after all specified jobs are resumed.</span></span>
<span data-ttu-id="75e1d-145">Le paramètre *Wait* est particulièrement utile dans les scripts qui supposent que les tâches soient reprises avant que le script puisse continuer.</span><span class="sxs-lookup"><span data-stu-id="75e1d-145">The *Wait* parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

### <span data-ttu-id="75e1d-146">Exemple 6 : reprendre un flux de travail qui s’interrompt</span><span class="sxs-lookup"><span data-stu-id="75e1d-146">Example 6: Resume a workflow that suspends itself</span></span>

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

<span data-ttu-id="75e1d-147">L’applet de commande **Resume-Job** vous permet de reprendre une tâche de workflow qui a été suspendue à l’aide de l’activité **suspend-Workflow** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-147">The **Resume-Job** cmdlet lets you resume a workflow job that was suspend by using the **Suspend-Workflow** activity.</span></span>
<span data-ttu-id="75e1d-148">Cette activité suspend un workflow depuis un workflow.</span><span class="sxs-lookup"><span data-stu-id="75e1d-148">This activity suspends a workflow from within a workflow.</span></span>
<span data-ttu-id="75e1d-149">Elle est valide uniquement dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="75e1d-149">It is valid only in workflows.</span></span>

<span data-ttu-id="75e1d-150">Pour plus d'informations sur Suspend-Workflow, consultez about_Suspend-Workflow.</span><span class="sxs-lookup"><span data-stu-id="75e1d-150">For information about the Suspend-Workflow, see about_Suspend-Workflow.</span></span>

## <span data-ttu-id="75e1d-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75e1d-151">PARAMETERS</span></span>

### <span data-ttu-id="75e1d-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="75e1d-152">-Filter</span></span>
<span data-ttu-id="75e1d-153">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="75e1d-153">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="75e1d-154">Cette applet de commande reprend les travaux qui satisfont à toutes les conditions de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="75e1d-154">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="75e1d-155">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="75e1d-155">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="75e1d-156">-Id</span><span class="sxs-lookup"><span data-stu-id="75e1d-156">-Id</span></span>
<span data-ttu-id="75e1d-157">Spécifie un tableau d’ID pour les travaux que cette applet de commande reprend.</span><span class="sxs-lookup"><span data-stu-id="75e1d-157">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="75e1d-158">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="75e1d-158">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="75e1d-159">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="75e1d-159">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="75e1d-160">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="75e1d-160">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="75e1d-161">Pour Rechercher l’ID d’un travail, exécutez la **tâche obtenir un travail** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-161">To find the ID of a job, run **Get-Job** .</span></span>

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

### <span data-ttu-id="75e1d-162">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="75e1d-162">-InstanceId</span></span>
<span data-ttu-id="75e1d-163">Spécifie un tableau d’ID d’instance des travaux que cette applet de commande reprend.</span><span class="sxs-lookup"><span data-stu-id="75e1d-163">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="75e1d-164">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="75e1d-164">The default is all jobs.</span></span>

<span data-ttu-id="75e1d-165">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="75e1d-165">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="75e1d-166">Pour Rechercher l’ID d’instance d’un travail, exécutez la **tâche obtenir un travail** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-166">To find the instance ID of a job, run **Get-Job** .</span></span>

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

### <span data-ttu-id="75e1d-167">-Travail</span><span class="sxs-lookup"><span data-stu-id="75e1d-167">-Job</span></span>
<span data-ttu-id="75e1d-168">Spécifie les tâches à reprendre.</span><span class="sxs-lookup"><span data-stu-id="75e1d-168">Specifies the jobs to be resumed.</span></span>
<span data-ttu-id="75e1d-169">Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="75e1d-169">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="75e1d-170">Vous pouvez également diriger des tâches vers l'applet de commande **Resume-Job** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-170">You can also pipe jobs to the **Resume-Job** cmdlet.</span></span>

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

### <span data-ttu-id="75e1d-171">-Name</span><span class="sxs-lookup"><span data-stu-id="75e1d-171">-Name</span></span>
<span data-ttu-id="75e1d-172">Spécifie un tableau de noms conviviaux de travaux que cette applet de commande reprend.</span><span class="sxs-lookup"><span data-stu-id="75e1d-172">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="75e1d-173">Entrez un ou plusieurs noms de tâche.</span><span class="sxs-lookup"><span data-stu-id="75e1d-173">Enter one or more job names.</span></span>
<span data-ttu-id="75e1d-174">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="75e1d-174">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="75e1d-175">-État</span><span class="sxs-lookup"><span data-stu-id="75e1d-175">-State</span></span>
<span data-ttu-id="75e1d-176">Spécifie l’état des travaux à reprendre.</span><span class="sxs-lookup"><span data-stu-id="75e1d-176">Specifies the state of jobs to resume.</span></span>
<span data-ttu-id="75e1d-177">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="75e1d-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="75e1d-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="75e1d-178">NotStarted</span></span>
- <span data-ttu-id="75e1d-179">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="75e1d-179">Running</span></span>
- <span data-ttu-id="75e1d-180">Completed</span><span class="sxs-lookup"><span data-stu-id="75e1d-180">Completed</span></span>
- <span data-ttu-id="75e1d-181">Échec</span><span class="sxs-lookup"><span data-stu-id="75e1d-181">Failed</span></span>
- <span data-ttu-id="75e1d-182">Arrêté</span><span class="sxs-lookup"><span data-stu-id="75e1d-182">Stopped</span></span>
- <span data-ttu-id="75e1d-183">Bloqué</span><span class="sxs-lookup"><span data-stu-id="75e1d-183">Blocked</span></span>
- <span data-ttu-id="75e1d-184">Interrompu</span><span class="sxs-lookup"><span data-stu-id="75e1d-184">Suspended</span></span>
- <span data-ttu-id="75e1d-185">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="75e1d-185">Disconnected</span></span>
- <span data-ttu-id="75e1d-186">Suspension</span><span class="sxs-lookup"><span data-stu-id="75e1d-186">Suspending</span></span>
- <span data-ttu-id="75e1d-187">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="75e1d-187">Stopping</span></span>

<span data-ttu-id="75e1d-188">Cette applet de commande reprend uniquement les tâches dans l’état **Suspended** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-188">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="75e1d-189">Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="75e1d-189">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="75e1d-190">-Wait</span><span class="sxs-lookup"><span data-stu-id="75e1d-190">-Wait</span></span>
<span data-ttu-id="75e1d-191">Indique que cette applet de commande supprime l’invite de commandes jusqu’au redémarrage de tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="75e1d-191">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span>
<span data-ttu-id="75e1d-192">Par défaut, cette applet de commande retourne immédiatement les résultats disponibles.</span><span class="sxs-lookup"><span data-stu-id="75e1d-192">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="75e1d-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="75e1d-193">-Confirm</span></span>
<span data-ttu-id="75e1d-194">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75e1d-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="75e1d-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="75e1d-195">-WhatIf</span></span>
<span data-ttu-id="75e1d-196">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75e1d-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="75e1d-197">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="75e1d-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="75e1d-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75e1d-198">CommonParameters</span></span>
<span data-ttu-id="75e1d-199">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75e1d-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75e1d-200">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="75e1d-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75e1d-201">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="75e1d-201">INPUTS</span></span>

### <span data-ttu-id="75e1d-202">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="75e1d-202">System.Management.Automation.Job</span></span>
<span data-ttu-id="75e1d-203">Vous pouvez diriger tous les types de travaux vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="75e1d-203">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="75e1d-204">Si **Resume-Job** obtient une tâche d’un type non pris en charge, elle retourne une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="75e1d-204">If **Resume-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="75e1d-205">SORTIES</span><span class="sxs-lookup"><span data-stu-id="75e1d-205">OUTPUTS</span></span>

### <span data-ttu-id="75e1d-206">Aucun, System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="75e1d-206">None, System.Management.Automation.Job</span></span>
<span data-ttu-id="75e1d-207">Cette applet de commande retourne les tâches qu’elle tente de reprendre, si vous utilisez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="75e1d-207">This cmdlet returns the jobs that it tries to resume, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="75e1d-208">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="75e1d-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="75e1d-209">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="75e1d-209">NOTES</span></span>

* <span data-ttu-id="75e1d-210">**RESUME : job** peut reprendre uniquement les tâches qui sont suspendues.</span><span class="sxs-lookup"><span data-stu-id="75e1d-210">**Resume-Job** can only resume jobs that are suspended.</span></span> <span data-ttu-id="75e1d-211">Si vous soumettez une tâche dans un autre état, **Resume-Job** exécute l'opération de reprise sur la tâche, mais génère un avertissement pour vous indiquer que la tâche n'a pas pu être reprise.</span><span class="sxs-lookup"><span data-stu-id="75e1d-211">If you submit a job in a different state, **Resume-Job** runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="75e1d-212">Pour supprimer l’avertissement, utilisez le paramètre commun *WarningAction* avec la valeur SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="75e1d-212">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>
* <span data-ttu-id="75e1d-213">Si un travail n’est pas d’un type qui prend en charge la reprise, par exemple une tâche de workflow ( **PSWorkflowJob** ), **Resume-Job** retourne une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="75e1d-213">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), **Resume-Job** returns a terminating error.</span></span>
* <span data-ttu-id="75e1d-214">Le mécanisme et l'emplacement pour enregistrer une tâche suspendue peuvent varier selon le type de tâche.</span><span class="sxs-lookup"><span data-stu-id="75e1d-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="75e1d-215">Par exemple, les tâches de workflow suspendues sont enregistrées par défaut dans un magasin de fichiers plats, mais elles peuvent également être enregistrées dans une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="75e1d-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
* <span data-ttu-id="75e1d-216">Quand vous reprenez une tâche, l'état de la tâche passe de **Suspended** à **Running** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-216">When you resume a job, the job state changes from **Suspended** to **Running** .</span></span> <span data-ttu-id="75e1d-217">Pour rechercher les travaux en cours d’exécution, y compris ceux qui ont été repris par cette applet de commande, utilisez le paramètre *State* de l’applet de commande **« obtenir-Job »** pour obtenir les tâches dans l’État en **cours d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="75e1d-217">To find the jobs that are running, including those that were resumed by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get jobs in the **Running** state.</span></span>
* <span data-ttu-id="75e1d-218">Certains types de tâche ont des options ou des propriétés qui empêchent Windows PowerShell de suspendre la tâche.</span><span class="sxs-lookup"><span data-stu-id="75e1d-218">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="75e1d-219">Si les tentatives d’interruption de la tâche échouent, vérifiez que les options et les propriétés du travail autorisent la suspension.</span><span class="sxs-lookup"><span data-stu-id="75e1d-219">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="75e1d-220">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="75e1d-220">RELATED LINKS</span></span>

[<span data-ttu-id="75e1d-221">Get-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-221">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="75e1d-222">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-222">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="75e1d-223">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-223">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="75e1d-224">Start-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-224">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="75e1d-225">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-225">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="75e1d-226">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-226">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="75e1d-227">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="75e1d-227">Wait-Job</span></span>](Wait-Job.md)
