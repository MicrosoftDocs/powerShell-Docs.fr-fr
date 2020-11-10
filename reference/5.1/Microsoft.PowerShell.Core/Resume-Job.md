---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388533"
---
# <span data-ttu-id="4f436-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-103">Resume-Job</span></span>

## <span data-ttu-id="4f436-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4f436-104">SYNOPSIS</span></span>
<span data-ttu-id="4f436-105">Redémarre une tâche suspendue.</span><span class="sxs-lookup"><span data-stu-id="4f436-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="4f436-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4f436-106">SYNTAX</span></span>

### <span data-ttu-id="4f436-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4f436-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f436-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f436-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f436-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f436-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f436-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f436-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f436-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f436-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f436-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f436-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4f436-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4f436-113">DESCRIPTION</span></span>

<span data-ttu-id="4f436-114">L' `Resume-Job` applet de commande reprend une tâche de workflow qui a été suspendue, par exemple à l’aide de l’applet de commande `Suspend-Job` ou de l’activité [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="4f436-114">The `Resume-Job` cmdlet resumes a workflow job that was suspended, such as by using the `Suspend-Job` cmdlet or the [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) activity.</span></span> <span data-ttu-id="4f436-115">Lors de la reprise d’une tâche de workflow, le moteur de tâche reconstruit l’État, les métadonnées et la sortie à partir des ressources enregistrées, telles que les points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="4f436-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span> <span data-ttu-id="4f436-116">La tâche est redémarrée sans perte de données ou d’État.</span><span class="sxs-lookup"><span data-stu-id="4f436-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="4f436-117">L'état de la tâche est changé de **Suspended** en **Running**.</span><span class="sxs-lookup"><span data-stu-id="4f436-117">The job state is changed from **Suspended** to **Running**.</span></span>

<span data-ttu-id="4f436-118">Utilisez les paramètres de `Resume-Job` pour sélectionner des travaux par nom, ID, ID d’instance ou diriger un objet de traitement, tel que celui retourné par l' `Get-Job` applet de commande, à `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="4f436-118">Use the parameters of `Resume-Job` to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the `Get-Job` cmdlet, to `Resume-Job`.</span></span> <span data-ttu-id="4f436-119">Vous pouvez aussi utiliser un filtre de propriété pour sélectionner une tâche à reprendre.</span><span class="sxs-lookup"><span data-stu-id="4f436-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="4f436-120">Par défaut, `Resume-Job` retourne immédiatement, même si tous les travaux peuvent ne pas être encore repris.</span><span class="sxs-lookup"><span data-stu-id="4f436-120">By default, `Resume-Job` returns immediately, even though all jobs might not yet be resumed.</span></span> <span data-ttu-id="4f436-121">Pour supprimer l'invite de commandes jusqu'à ce que toutes les tâches spécifiées aient repris, utilisez le paramètre **Wait**.</span><span class="sxs-lookup"><span data-stu-id="4f436-121">To suppress the command prompt until all specified jobs are resumed, use the **Wait** parameter.</span></span>

<span data-ttu-id="4f436-122">L' `Resume-Job` applet de commande fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de Workflow.</span><span class="sxs-lookup"><span data-stu-id="4f436-122">The `Resume-Job` cmdlet works only on custom job types, such as workflow jobs.</span></span> <span data-ttu-id="4f436-123">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles qui sont démarrées à l’aide de l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="4f436-123">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="4f436-124">Si vous envoyez un travail d’un type non pris en charge, `Resume-Job` génère une erreur de fin et arrête l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4f436-124">If you submit a job of an unsupported type, `Resume-Job` generates a terminating error and stops running.</span></span>

<span data-ttu-id="4f436-125">Pour identifier une tâche de workflow, recherchez la valeur de **PSWorkflowJob** dans la propriété **PSJobTypeName** de la tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="4f436-126">Pour déterminer si un type de tâche personnalisé particulier prend en charge l' `Resume-Job` applet de commande, consultez les rubriques d’aide relatives au type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4f436-126">To determine whether a particular custom job type supports the `Resume-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="4f436-127">Avant d’utiliser une applet de commande de tâche sur un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé, soit à l’aide de l’applet de commande, soit en `Import-Module` obtenant ou en utilisant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="4f436-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the `Import-Module` cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="4f436-128">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4f436-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4f436-129">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4f436-129">EXAMPLES</span></span>

### <span data-ttu-id="4f436-130">Exemple 1 : reprendre un travail par ID</span><span class="sxs-lookup"><span data-stu-id="4f436-130">Example 1: Resume a job by ID</span></span>

<span data-ttu-id="4f436-131">Les commandes de cet exemple vérifient que la tâche est une tâche de workflow suspendue, puis reprennent la tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span> <span data-ttu-id="4f436-132">La première commande utilise l' `Get-Job` applet de commande pour récupérer le travail.</span><span class="sxs-lookup"><span data-stu-id="4f436-132">The first command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="4f436-133">La sortie montre que la tâche est une tâche de workflow suspendue.</span><span class="sxs-lookup"><span data-stu-id="4f436-133">The output shows that the job is a suspended workflow job.</span></span> <span data-ttu-id="4f436-134">La deuxième commande utilise le paramètre **ID** de l' `Resume-Job` applet de commande pour reprendre la tâche avec une valeur d' **ID** de 4.</span><span class="sxs-lookup"><span data-stu-id="4f436-134">The second command uses the **Id** parameter of the `Resume-Job` cmdlet to resume the job with an **Id** value of 4.</span></span>

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### <span data-ttu-id="4f436-135">Exemple 2 : reprendre une tâche par son nom</span><span class="sxs-lookup"><span data-stu-id="4f436-135">Example 2: Resume a job by name</span></span>

<span data-ttu-id="4f436-136">Cette commande utilise le paramètre **Name** pour reprendre plusieurs tâches de workflow sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4f436-136">This command uses the **Name** parameter to resume several workflow jobs on the local computer.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### <span data-ttu-id="4f436-137">Exemple 3 : utiliser des valeurs de propriétés personnalisées</span><span class="sxs-lookup"><span data-stu-id="4f436-137">Example 3: Use custom property values</span></span>

<span data-ttu-id="4f436-138">Cette commande utilise la valeur d'une propriété personnalisée pour identifier la tâche de workflow à reprendre.</span><span class="sxs-lookup"><span data-stu-id="4f436-138">This command uses the value of a custom property to identify the workflow job to resume.</span></span> <span data-ttu-id="4f436-139">Elle utilise le paramètre **Filter** pour identifier la tâche de workflow par sa propriété **CustomID**.</span><span class="sxs-lookup"><span data-stu-id="4f436-139">It uses the **Filter** parameter to identify the workflow job by its **CustomID** property.</span></span> <span data-ttu-id="4f436-140">Elle utilise également le paramètre **State** pour vérifier que la tâche de workflow est suspendue, avant d'essayer de la reprendre.</span><span class="sxs-lookup"><span data-stu-id="4f436-140">It also uses the **State** parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### <span data-ttu-id="4f436-141">Exemple 4 : reprendre toutes les tâches suspendues sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="4f436-141">Example 4: Resume all suspended jobs on a remote computer</span></span>

<span data-ttu-id="4f436-142">Cette commande reprend toutes les tâches suspendues sur l'ordinateur distant Srv01.</span><span class="sxs-lookup"><span data-stu-id="4f436-142">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="4f436-143">La commande utilise l' `Invoke-Command` applet de commande pour exécuter une commande sur l’ordinateur Srv01.</span><span class="sxs-lookup"><span data-stu-id="4f436-143">The command uses the `Invoke-Command` cmdlet to run a command on the Srv01 computer.</span></span> <span data-ttu-id="4f436-144">La commande distante utilise le paramètre **State** de l’applet de commande `Get-Job` pour récupérer toutes les tâches suspendues sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4f436-144">The remote command uses the **State** parameter of the `Get-Job` cmdlet to get all suspended jobs on the computer.</span></span> <span data-ttu-id="4f436-145">Un opérateur de pipeline ( `|` ) envoie les tâches suspendues à l’applet de commande `Resume-Job` , qui les reprend.</span><span class="sxs-lookup"><span data-stu-id="4f436-145">A pipeline operator (`|`) sends the suspended jobs to the `Resume-Job` cmdlet, which resumes them.</span></span>

### <span data-ttu-id="4f436-146">Exemple 5 : attendre la reprise des tâches</span><span class="sxs-lookup"><span data-stu-id="4f436-146">Example 5: Wait for jobs to resume</span></span>

<span data-ttu-id="4f436-147">Cette commande utilise le paramètre **Wait** pour diriger le `Resume-Job` retour uniquement après la reprise de toutes les tâches spécifiées.</span><span class="sxs-lookup"><span data-stu-id="4f436-147">This command uses the **Wait** parameter to direct `Resume-Job` to return only after all specified jobs are resumed.</span></span> <span data-ttu-id="4f436-148">Le paramètre **Wait** est particulièrement utile dans les scripts qui supposent que les tâches soient reprises avant que le script puisse continuer.</span><span class="sxs-lookup"><span data-stu-id="4f436-148">The **Wait** parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### <span data-ttu-id="4f436-149">Exemple 6 : reprendre un flux de travail qui s’interrompt</span><span class="sxs-lookup"><span data-stu-id="4f436-149">Example 6: Resume a workflow that suspends itself</span></span>

<span data-ttu-id="4f436-150">Cet exemple de code montre l' `Suspend-Workflow` activité dans un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4f436-150">This code sample shows the `Suspend-Workflow` activity in a workflow.</span></span>

<span data-ttu-id="4f436-151">`Test-Suspend`Flux de travail sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="4f436-151">The `Test-Suspend` workflow on the Server01 computer.</span></span> <span data-ttu-id="4f436-152">Lorsque vous exécutez le workflow, le workflow exécute l' `Get-Date` activité et stocke le résultat dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="4f436-152">When you run the workflow, the workflow runs the `Get-Date` activity and stores the result in the `$a` variable.</span></span> <span data-ttu-id="4f436-153">Ensuite, il exécute l' `Suspend-Workflow` activité.</span><span class="sxs-lookup"><span data-stu-id="4f436-153">Then it runs the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="4f436-154">En réponse, il prend un point de contrôle, suspend le workflow et retourne un objet de tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="4f436-154">In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.</span></span> <span data-ttu-id="4f436-155">`Suspend-Workflow` retourne un objet de tâche de workflow même si le workflow n’est pas explicitement exécuté en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-155">`Suspend-Workflow` returns a workflow job object even if the workflow is not explicitly run as a job.</span></span>

<span data-ttu-id="4f436-156">`Resume-Job` reprend le `Test-Suspend` Workflow dans Job8.</span><span class="sxs-lookup"><span data-stu-id="4f436-156">`Resume-Job` resumes the `Test-Suspend` workflow in Job8.</span></span> <span data-ttu-id="4f436-157">Elle utilise le paramètre **Wait** pour suspendre l'invite de commandes jusqu'à ce que la tâche soit reprise.</span><span class="sxs-lookup"><span data-stu-id="4f436-157">It uses the **Wait** parameter to hold the command prompt until the job is resumed.</span></span>

<span data-ttu-id="4f436-158">L' `Receive-Job` applet de commande obtient les résultats du `Test-Suspend` flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4f436-158">The `Receive-Job` cmdlet gets the results of the `Test-Suspend` workflow.</span></span> <span data-ttu-id="4f436-159">La commande finale du workflow retourne un objet **TimeSpan** qui représente le temps écoulé entre la date et l’heure actuelles et la date et l’heure qui ont été enregistrées dans la `$a` variable avant la suspension du Workflow.</span><span class="sxs-lookup"><span data-stu-id="4f436-159">The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the `$a` variable before the workflow was suspended.</span></span>

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

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

<span data-ttu-id="4f436-160">L' `Resume-Job` applet de commande vous permet de reprendre une tâche de workflow qui a été suspendue à l’aide de l' `Suspend-Workflow` activité.</span><span class="sxs-lookup"><span data-stu-id="4f436-160">The `Resume-Job` cmdlet lets you resume a workflow job that was suspend by using the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="4f436-161">Cette activité suspend un workflow depuis un workflow.</span><span class="sxs-lookup"><span data-stu-id="4f436-161">This activity suspends a workflow from within a workflow.</span></span> <span data-ttu-id="4f436-162">Elle est valide uniquement dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="4f436-162">It is valid only in workflows.</span></span>

<span data-ttu-id="4f436-163">Pour plus d’informations sur le `Suspend-Workflow` , consultez about_Suspend-Workflow] (.. /PSWorkflow/about/about_Suspend-Workflow. MD).</span><span class="sxs-lookup"><span data-stu-id="4f436-163">For information about the `Suspend-Workflow`, see about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md).</span></span>

## <span data-ttu-id="4f436-164">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="4f436-164">PARAMETERS</span></span>

### <span data-ttu-id="4f436-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="4f436-165">-Filter</span></span>

<span data-ttu-id="4f436-166">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="4f436-166">Specifies a hash table of conditions.</span></span> <span data-ttu-id="4f436-167">Cette applet de commande reprend les travaux qui satisfont à toutes les conditions de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="4f436-167">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="4f436-168">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="4f436-168">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="4f436-169">-Id</span><span class="sxs-lookup"><span data-stu-id="4f436-169">-Id</span></span>

<span data-ttu-id="4f436-170">Spécifie un tableau d’ID pour les travaux que cette applet de commande reprend.</span><span class="sxs-lookup"><span data-stu-id="4f436-170">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="4f436-171">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="4f436-171">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="4f436-172">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="4f436-172">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="4f436-173">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4f436-173">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="4f436-174">Pour Rechercher l’ID d’un travail, exécutez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="4f436-174">To find the ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="4f436-175">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4f436-175">-InstanceId</span></span>

<span data-ttu-id="4f436-176">Spécifie un tableau d’ID d’instance des travaux que cette applet de commande reprend.</span><span class="sxs-lookup"><span data-stu-id="4f436-176">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="4f436-177">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="4f436-177">The default is all jobs.</span></span>

<span data-ttu-id="4f436-178">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4f436-178">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="4f436-179">Pour Rechercher l’ID d’instance d’un travail, exécutez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="4f436-179">To find the instance ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="4f436-180">-Travail</span><span class="sxs-lookup"><span data-stu-id="4f436-180">-Job</span></span>

<span data-ttu-id="4f436-181">Spécifie les tâches à reprendre.</span><span class="sxs-lookup"><span data-stu-id="4f436-181">Specifies the jobs to be resumed.</span></span> <span data-ttu-id="4f436-182">Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="4f436-182">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="4f436-183">Vous pouvez également diriger les travaux vers l’applet de commande `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="4f436-183">You can also pipe jobs to the `Resume-Job` cmdlet.</span></span>

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

### <span data-ttu-id="4f436-184">-Name</span><span class="sxs-lookup"><span data-stu-id="4f436-184">-Name</span></span>

<span data-ttu-id="4f436-185">Spécifie un tableau de noms conviviaux de travaux que cette applet de commande reprend.</span><span class="sxs-lookup"><span data-stu-id="4f436-185">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="4f436-186">Entrez un ou plusieurs noms de tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-186">Enter one or more job names.</span></span>
<span data-ttu-id="4f436-187">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4f436-187">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4f436-188">-État</span><span class="sxs-lookup"><span data-stu-id="4f436-188">-State</span></span>

<span data-ttu-id="4f436-189">Spécifie l’état des travaux à reprendre.</span><span class="sxs-lookup"><span data-stu-id="4f436-189">Specifies the state of jobs to resume.</span></span> <span data-ttu-id="4f436-190">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="4f436-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4f436-191">NotStarted</span><span class="sxs-lookup"><span data-stu-id="4f436-191">NotStarted</span></span>
- <span data-ttu-id="4f436-192">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="4f436-192">Running</span></span>
- <span data-ttu-id="4f436-193">Completed</span><span class="sxs-lookup"><span data-stu-id="4f436-193">Completed</span></span>
- <span data-ttu-id="4f436-194">Échec</span><span class="sxs-lookup"><span data-stu-id="4f436-194">Failed</span></span>
- <span data-ttu-id="4f436-195">Arrêté</span><span class="sxs-lookup"><span data-stu-id="4f436-195">Stopped</span></span>
- <span data-ttu-id="4f436-196">Bloqué</span><span class="sxs-lookup"><span data-stu-id="4f436-196">Blocked</span></span>
- <span data-ttu-id="4f436-197">Interrompu</span><span class="sxs-lookup"><span data-stu-id="4f436-197">Suspended</span></span>
- <span data-ttu-id="4f436-198">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="4f436-198">Disconnected</span></span>
- <span data-ttu-id="4f436-199">Suspension</span><span class="sxs-lookup"><span data-stu-id="4f436-199">Suspending</span></span>
- <span data-ttu-id="4f436-200">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="4f436-200">Stopping</span></span>

<span data-ttu-id="4f436-201">Cette applet de commande reprend uniquement les tâches dans l’état **Suspended** .</span><span class="sxs-lookup"><span data-stu-id="4f436-201">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="4f436-202">Pour plus d’informations sur les États de travail, consultez [énumération JobState](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="4f436-202">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="4f436-203">-Wait</span><span class="sxs-lookup"><span data-stu-id="4f436-203">-Wait</span></span>

<span data-ttu-id="4f436-204">Indique que cette applet de commande supprime l’invite de commandes jusqu’au redémarrage de tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-204">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span> <span data-ttu-id="4f436-205">Par défaut, cette applet de commande retourne immédiatement les résultats disponibles.</span><span class="sxs-lookup"><span data-stu-id="4f436-205">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="4f436-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4f436-206">-Confirm</span></span>

<span data-ttu-id="4f436-207">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4f436-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4f436-208">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4f436-208">-WhatIf</span></span>

<span data-ttu-id="4f436-209">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4f436-209">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4f436-210">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4f436-210">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4f436-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f436-211">CommonParameters</span></span>

<span data-ttu-id="4f436-212">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f436-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f436-213">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f436-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f436-214">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4f436-214">INPUTS</span></span>

### <span data-ttu-id="4f436-215">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="4f436-215">System.Management.Automation.Job</span></span>

<span data-ttu-id="4f436-216">Vous pouvez diriger tous les types de travaux vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4f436-216">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="4f436-217">Si `Resume-Job` obtient une tâche d’un type non pris en charge, elle retourne une erreur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="4f436-217">If `Resume-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="4f436-218">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4f436-218">OUTPUTS</span></span>

### <span data-ttu-id="4f436-219">Aucun, System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="4f436-219">None, System.Management.Automation.Job</span></span>

<span data-ttu-id="4f436-220">Cette applet de commande retourne les tâches qu’elle tente de reprendre, si vous utilisez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="4f436-220">This cmdlet returns the jobs that it tries to resume, if you use the **PassThru** parameter.</span></span>
<span data-ttu-id="4f436-221">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="4f436-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4f436-222">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4f436-222">NOTES</span></span>

- <span data-ttu-id="4f436-223">`Resume-Job` peut reprendre uniquement les tâches qui sont suspendues.</span><span class="sxs-lookup"><span data-stu-id="4f436-223">`Resume-Job` can only resume jobs that are suspended.</span></span> <span data-ttu-id="4f436-224">Si vous soumettez un travail dans un état différent, `Resume-Job` exécute l’opération de reprise sur le travail, mais génère un avertissement pour vous informer que le travail n’a pas pu être repris.</span><span class="sxs-lookup"><span data-stu-id="4f436-224">If you submit a job in a different state, `Resume-Job` runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="4f436-225">Pour supprimer l’avertissement, utilisez le paramètre commun **WarningAction** avec la valeur SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="4f436-225">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>
- <span data-ttu-id="4f436-226">Si un travail n’est pas d’un type qui prend en charge la reprise, par exemple une tâche de workflow ( **PSWorkflowJob** ), `Resume-Job` retourne une erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="4f436-226">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), `Resume-Job` returns a terminating error.</span></span>
- <span data-ttu-id="4f436-227">Le mécanisme et l'emplacement pour enregistrer une tâche suspendue peuvent varier selon le type de tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-227">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="4f436-228">Par exemple, les tâches de workflow suspendues sont enregistrées par défaut dans un magasin de fichiers plats, mais elles peuvent également être enregistrées dans une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="4f436-228">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
- <span data-ttu-id="4f436-229">Quand vous reprenez une tâche, l'état de la tâche passe de **Suspended** à **Running**.</span><span class="sxs-lookup"><span data-stu-id="4f436-229">When you resume a job, the job state changes from **Suspended** to **Running**.</span></span> <span data-ttu-id="4f436-230">Pour rechercher les travaux en cours d’exécution, y compris ceux qui ont été repris par cette applet de commande, utilisez le paramètre **State** de l’applet de commande `Get-Job` pour obtenir les tâches dans l’État en **cours d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="4f436-230">To find the jobs that are running, including those that were resumed by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get jobs in the **Running** state.</span></span>
- <span data-ttu-id="4f436-231">Certains types de tâche ont des options ou des propriétés qui empêchent Windows PowerShell de suspendre la tâche.</span><span class="sxs-lookup"><span data-stu-id="4f436-231">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="4f436-232">Si les tentatives d’interruption de la tâche échouent, vérifiez que les options et les propriétés du travail autorisent la suspension.</span><span class="sxs-lookup"><span data-stu-id="4f436-232">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="4f436-233">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4f436-233">RELATED LINKS</span></span>

[<span data-ttu-id="4f436-234">Get-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="4f436-235">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-235">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="4f436-236">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-236">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="4f436-237">Start-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-237">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="4f436-238">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-238">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="4f436-239">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-239">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="4f436-240">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="4f436-240">Wait-Job</span></span>](Wait-Job.md)
