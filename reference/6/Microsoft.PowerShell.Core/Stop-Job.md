---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 56dc7462e2625768db8b52370d3b7d38c8defafe
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387258"
---
# <span data-ttu-id="7c63c-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="7c63c-103">Stop-Job</span></span>

## <span data-ttu-id="7c63c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7c63c-104">SYNOPSIS</span></span>
<span data-ttu-id="7c63c-105">Arrête une tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c63c-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="7c63c-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="7c63c-106">SYNTAX</span></span>

### <span data-ttu-id="7c63c-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="7c63c-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c63c-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="7c63c-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c63c-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="7c63c-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c63c-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="7c63c-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c63c-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="7c63c-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7c63c-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="7c63c-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7c63c-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7c63c-113">DESCRIPTION</span></span>

<span data-ttu-id="7c63c-114">L' `Stop-Job` applet de commande arrête les tâches en arrière-plan PowerShell en cours.</span><span class="sxs-lookup"><span data-stu-id="7c63c-114">The `Stop-Job` cmdlet stops PowerShell background jobs that are in progress.</span></span> <span data-ttu-id="7c63c-115">Vous pouvez utiliser cette applet de commande pour arrêter toutes les tâches ou arrêter les tâches sélectionnées en fonction de leur nom, ID, ID d’instance ou État, ou en passant un objet de traitement à `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to `Stop-Job`.</span></span>

<span data-ttu-id="7c63c-116">Vous pouvez utiliser `Stop-Job` pour arrêter des tâches en arrière-plan, telles que celles qui ont été démarrées à l’aide `Start-Job` de l’applet de commande ou du paramètre **AsJob** d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c63c-116">You can use `Stop-Job` to stop background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span> <span data-ttu-id="7c63c-117">Lorsque vous arrêtez une tâche en arrière-plan, PowerShell termine toutes les tâches en attente dans la file d’attente de travaux, puis met fin au travail.</span><span class="sxs-lookup"><span data-stu-id="7c63c-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span> <span data-ttu-id="7c63c-118">Aucune nouvelle tâche n'est ajoutée à la file d'attente après que cette commande a été soumise.</span><span class="sxs-lookup"><span data-stu-id="7c63c-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="7c63c-119">Cette applet de commande ne supprime pas les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c63c-119">This cmdlet does not delete background jobs.</span></span> <span data-ttu-id="7c63c-120">Pour supprimer un travail, utilisez l' `Remove-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c63c-120">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="7c63c-121">À compter de Windows PowerShell 3,0, `Stop-Job` arrête également les types de tâches personnalisées, tels que les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="7c63c-121">Starting in Windows PowerShell 3.0, `Stop-Job` also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="7c63c-122">Pour permettre `Stop-Job` à d’arrêter un travail avec un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une `Stop-Job` commande, soit à l’aide de l’applet de commande, soit `Import-Module` en utilisant ou en obtenant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="7c63c-122">To enable `Stop-Job` to stop a job with custom job type, import the module that supports the custom job type into the session before you run a `Stop-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="7c63c-123">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7c63c-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="7c63c-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7c63c-124">EXAMPLES</span></span>

### <span data-ttu-id="7c63c-125">Exemple 1 : arrêter un travail sur un ordinateur distant à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7c63c-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="7c63c-126">Cet exemple montre comment utiliser l' `Stop-Job` applet de commande pour arrêter un travail qui s’exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7c63c-126">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="7c63c-127">Étant donné que la tâche a été démarrée à l’aide `Invoke-Command` de l’applet de commande pour exécuter une `Start-Job` commande à distance, l’objet de traitement est stocké sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7c63c-127">Because the job was started by using the `Invoke-Command` cmdlet to run a `Start-Job` command remotely, the job object is stored on the remote computer.</span></span> <span data-ttu-id="7c63c-128">Vous devez utiliser une autre `Invoke-Command` commande pour exécuter une `Stop-Job` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="7c63c-128">You must use another `Invoke-Command` command to run a `Stop-Job` command remotely.</span></span> <span data-ttu-id="7c63c-129">Pour plus d'informations sur les tâches distantes en arrière-plan, consultez about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="7c63c-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="7c63c-130">La première commande crée une session PowerShell ( **PSSession** ) sur l’ordinateur Serveur01, puis stocke l’objet de session dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="7c63c-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the `$s` variable.</span></span> <span data-ttu-id="7c63c-131">La commande utilise les informations d'identification d'un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="7c63c-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="7c63c-132">La deuxième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande dans la session.</span><span class="sxs-lookup"><span data-stu-id="7c63c-132">The second command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the session.</span></span> <span data-ttu-id="7c63c-133">La commande qui figure dans la tâche obtient tous les événements du journal d'événements système.</span><span class="sxs-lookup"><span data-stu-id="7c63c-133">The command in the job gets all of the events in the System event log.</span></span> <span data-ttu-id="7c63c-134">L’objet de traitement résultant est stocké dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="7c63c-134">The resulting job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="7c63c-135">La troisième commande arrête la tâche.</span><span class="sxs-lookup"><span data-stu-id="7c63c-135">The third command stops the job.</span></span> <span data-ttu-id="7c63c-136">Elle utilise l' `Invoke-Command` applet de commande pour exécuter une `Stop-Job` commande dans la **session PSSession** sur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7c63c-136">It uses the `Invoke-Command` cmdlet to run a `Stop-Job` command in the **PSSession** on Server01.</span></span> <span data-ttu-id="7c63c-137">Étant donné que les objets de traitement sont stockés dans `$j` , qui est une variable sur l’ordinateur local, la commande utilise le modificateur d’étendue using pour identifier `$j` une variable locale.</span><span class="sxs-lookup"><span data-stu-id="7c63c-137">Because the job objects are stored in `$j`, which is a variable on the local computer, the command uses the Using scope modifier to identify `$j` as a local variable.</span></span>
<span data-ttu-id="7c63c-138">Pour plus d’informations sur le modificateur d’étendue using, consultez [about_Remote_Variables](about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="7c63c-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="7c63c-139">Quand la commande se termine, la tâche est arrêtée et la **session PSSession** dans `$s` peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="7c63c-139">When the command finishes, the job is stopped and the **PSSession** in `$s` is available for use.</span></span>

### <span data-ttu-id="7c63c-140">Exemple 2 : arrêter une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7c63c-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="7c63c-141">Cette commande arrête la tâche en arrière-plan Job1.</span><span class="sxs-lookup"><span data-stu-id="7c63c-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="7c63c-142">Exemple 3 : arrêter plusieurs tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7c63c-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="7c63c-143">Cette commande arrête trois tâches.</span><span class="sxs-lookup"><span data-stu-id="7c63c-143">This command stops three jobs.</span></span>
<span data-ttu-id="7c63c-144">Elle les identifie par leurs ID.</span><span class="sxs-lookup"><span data-stu-id="7c63c-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="7c63c-145">Exemple 4 : arrêter toutes les tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7c63c-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="7c63c-146">Cette commande arrête toutes les tâches en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="7c63c-147">Exemple 5 : arrêter toutes les tâches en arrière-plan bloquées</span><span class="sxs-lookup"><span data-stu-id="7c63c-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="7c63c-148">Cette commande arrête toutes les tâches qui sont bloquées.</span><span class="sxs-lookup"><span data-stu-id="7c63c-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="7c63c-149">Exemple 6 : arrêter un travail à l’aide d’un ID d’instance</span><span class="sxs-lookup"><span data-stu-id="7c63c-149">Example 6: Stop a job by using an instance ID</span></span>

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

<span data-ttu-id="7c63c-150">Ces commandes montrent comment arrêter une tâche sur la base de son ID d'instance.</span><span class="sxs-lookup"><span data-stu-id="7c63c-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="7c63c-151">La première commande utilise l' `Get-Job` applet de commande pour récupérer les tâches dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-151">The first command uses the `Get-Job` cmdlet to get the jobs in the current session.</span></span> <span data-ttu-id="7c63c-152">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les tâches à une `Format-Table` commande, qui affiche une table des propriétés spécifiées de chaque travail.</span><span class="sxs-lookup"><span data-stu-id="7c63c-152">The command uses a pipeline operator (`|`) to send the jobs to a `Format-Table` command, which displays a table of the specified properties of each job.</span></span> <span data-ttu-id="7c63c-153">Cette table inclut l'ID d'instance de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="7c63c-153">The table includes the Instance ID of each job.</span></span> <span data-ttu-id="7c63c-154">Elle utilise une propriété calculée pour afficher l'état de la tâche.</span><span class="sxs-lookup"><span data-stu-id="7c63c-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="7c63c-155">La deuxième commande utilise une `Stop-Job` commande qui a le paramètre **InstanceID** pour arrêter un travail sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7c63c-155">The second command uses a `Stop-Job` command that has the **InstanceID** parameter to stop a selected job.</span></span>

### <span data-ttu-id="7c63c-156">Exemple 7 : arrêter un travail sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="7c63c-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="7c63c-157">Cet exemple montre comment utiliser l' `Stop-Job` applet de commande pour arrêter un travail qui s’exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7c63c-157">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="7c63c-158">Étant donné que la tâche a été démarrée à l’aide du paramètre **AsJob** de l' `Invoke-Command` applet de commande, l’objet de traitement se trouve sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7c63c-158">Because the job was started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span> <span data-ttu-id="7c63c-159">Par conséquent, vous pouvez utiliser une `Stop-Job` commande locale pour arrêter le travail.</span><span class="sxs-lookup"><span data-stu-id="7c63c-159">Therefore, you can use a local `Stop-Job` command to stop the job.</span></span>

<span data-ttu-id="7c63c-160">La première commande utilise l' `Invoke-Command` applet de commande pour démarrer une tâche en arrière-plan sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7c63c-160">The first command uses the `Invoke-Command` cmdlet to start a background job on the Server01 computer.</span></span> <span data-ttu-id="7c63c-161">La commande utilise le paramètre **AsJob** pour exécuter la commande distante en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c63c-161">The command uses the **AsJob** parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="7c63c-162">Cette commande retourne un objet de traitement, qui est le même objet de traitement que celui retourné par l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-162">This command returns a job object, which is the same job object that the `Start-Job` cmdlet returns.</span></span>
<span data-ttu-id="7c63c-163">La commande enregistre l’objet de traitement dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="7c63c-163">The command saves the job object in the `$j` variable.</span></span>

<span data-ttu-id="7c63c-164">La deuxième commande utilise un opérateur de pipeline pour envoyer la tâche dans la `$j` variable à `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-164">The second command uses a pipeline operator to send the job in the `$j` variable to `Stop-Job`.</span></span> <span data-ttu-id="7c63c-165">La commande utilise le paramètre **PassThru** pour demander `Stop-Job` à de retourner un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="7c63c-165">The command uses the **PassThru** parameter to direct `Stop-Job` to return a job object.</span></span> <span data-ttu-id="7c63c-166">L’affichage de l’objet de traitement confirme que l’état du travail est arrêté.</span><span class="sxs-lookup"><span data-stu-id="7c63c-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="7c63c-167">Pour plus d'informations sur les tâches distantes en arrière-plan, consultez about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="7c63c-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="7c63c-168">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="7c63c-168">PARAMETERS</span></span>

### <span data-ttu-id="7c63c-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="7c63c-169">-Filter</span></span>

<span data-ttu-id="7c63c-170">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="7c63c-170">Specifies a hash table of conditions.</span></span> <span data-ttu-id="7c63c-171">Cette applet de commande arrête les travaux qui remplissent toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="7c63c-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="7c63c-172">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="7c63c-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="7c63c-173">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="7c63c-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="7c63c-174">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-174">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="7c63c-175">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="7c63c-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="7c63c-176">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="7c63c-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="7c63c-177">-Id</span><span class="sxs-lookup"><span data-stu-id="7c63c-177">-Id</span></span>

<span data-ttu-id="7c63c-178">Spécifie les ID des travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="7c63c-178">Specifies the IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="7c63c-179">La valeur par défaut est toutes les tâches dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="7c63c-180">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-180">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="7c63c-181">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="7c63c-182">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7c63c-182">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="7c63c-183">Pour Rechercher l’ID d’un travail, tapez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-183">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7c63c-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="7c63c-184">-InstanceId</span></span>

<span data-ttu-id="7c63c-185">Spécifie les ID d’instance des travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="7c63c-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="7c63c-186">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="7c63c-186">The default is all jobs.</span></span>

<span data-ttu-id="7c63c-187">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7c63c-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="7c63c-188">Pour Rechercher l’ID d’instance d’un travail, utilisez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-188">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7c63c-189">-Travail</span><span class="sxs-lookup"><span data-stu-id="7c63c-189">-Job</span></span>

<span data-ttu-id="7c63c-190">Spécifie les travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="7c63c-190">Specifies the jobs that this cmdlet stops.</span></span> <span data-ttu-id="7c63c-191">Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="7c63c-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="7c63c-192">Vous pouvez également utiliser un opérateur de pipeline pour envoyer des travaux à l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="7c63c-192">You can also use a pipeline operator to submit jobs to the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="7c63c-193">Par défaut, `Stop-Job` supprime tous les travaux qui ont été démarrés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-193">By default, `Stop-Job` deletes all jobs that were started in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7c63c-194">-Name</span><span class="sxs-lookup"><span data-stu-id="7c63c-194">-Name</span></span>

<span data-ttu-id="7c63c-195">Spécifie les noms conviviaux des travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="7c63c-195">Specifies friendly names of jobs that this cmdlet stops.</span></span> <span data-ttu-id="7c63c-196">Entrez les noms de tâches dans une liste séparée par des virgules ou utilisez des caractères génériques (\*) pour entrer un modèle de nom de tâche.</span><span class="sxs-lookup"><span data-stu-id="7c63c-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span> <span data-ttu-id="7c63c-197">Par défaut, `Stop-Job` arrête tous les travaux créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c63c-197">By default, `Stop-Job` stops all jobs created in the current session.</span></span>

<span data-ttu-id="7c63c-198">Étant donné que le nom convivial n’est pas forcément unique, utilisez les paramètres **WhatIf** et **Confirm** lors de l’arrêt des tâches par nom.</span><span class="sxs-lookup"><span data-stu-id="7c63c-198">Because the friendly name is not guaranteed to be unique, use the **WhatIf** and **Confirm** parameters when stopping jobs by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7c63c-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7c63c-199">-PassThru</span></span>

<span data-ttu-id="7c63c-200">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="7c63c-200">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="7c63c-201">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="7c63c-201">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c63c-202">-État</span><span class="sxs-lookup"><span data-stu-id="7c63c-202">-State</span></span>

<span data-ttu-id="7c63c-203">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="7c63c-203">Specifies a job state.</span></span> <span data-ttu-id="7c63c-204">Cette applet de commande arrête uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="7c63c-204">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="7c63c-205">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="7c63c-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7c63c-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="7c63c-206">NotStarted</span></span>
- <span data-ttu-id="7c63c-207">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="7c63c-207">Running</span></span>
- <span data-ttu-id="7c63c-208">Completed</span><span class="sxs-lookup"><span data-stu-id="7c63c-208">Completed</span></span>
- <span data-ttu-id="7c63c-209">Échec</span><span class="sxs-lookup"><span data-stu-id="7c63c-209">Failed</span></span>
- <span data-ttu-id="7c63c-210">Arrêté</span><span class="sxs-lookup"><span data-stu-id="7c63c-210">Stopped</span></span>
- <span data-ttu-id="7c63c-211">Bloqué</span><span class="sxs-lookup"><span data-stu-id="7c63c-211">Blocked</span></span>
- <span data-ttu-id="7c63c-212">Interrompu</span><span class="sxs-lookup"><span data-stu-id="7c63c-212">Suspended</span></span>
- <span data-ttu-id="7c63c-213">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="7c63c-213">Disconnected</span></span>
- <span data-ttu-id="7c63c-214">Suspension</span><span class="sxs-lookup"><span data-stu-id="7c63c-214">Suspending</span></span>
- <span data-ttu-id="7c63c-215">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="7c63c-215">Stopping</span></span>

<span data-ttu-id="7c63c-216">Pour plus d’informations sur les États de travail, consultez [énumération JobState](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="7c63c-216">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7c63c-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7c63c-217">-Confirm</span></span>

<span data-ttu-id="7c63c-218">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c63c-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7c63c-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7c63c-219">-WhatIf</span></span>

<span data-ttu-id="7c63c-220">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c63c-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7c63c-221">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="7c63c-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7c63c-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c63c-222">CommonParameters</span></span>

<span data-ttu-id="7c63c-223">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c63c-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c63c-224">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7c63c-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c63c-225">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7c63c-225">INPUTS</span></span>

### <span data-ttu-id="7c63c-226">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="7c63c-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="7c63c-227">Vous pouvez diriger un objet de traitement vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c63c-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="7c63c-228">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7c63c-228">OUTPUTS</span></span>

### <span data-ttu-id="7c63c-229">Aucun, System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="7c63c-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="7c63c-230">Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="7c63c-230">This cmdlet returns a job object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="7c63c-231">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="7c63c-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7c63c-232">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7c63c-232">NOTES</span></span>

## <span data-ttu-id="7c63c-233">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7c63c-233">RELATED LINKS</span></span>

[<span data-ttu-id="7c63c-234">Get-Job</span><span class="sxs-lookup"><span data-stu-id="7c63c-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="7c63c-235">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7c63c-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="7c63c-236">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="7c63c-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="7c63c-237">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="7c63c-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="7c63c-238">Start-Job</span><span class="sxs-lookup"><span data-stu-id="7c63c-238">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="7c63c-239">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="7c63c-239">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="7c63c-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="7c63c-240">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="7c63c-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="7c63c-241">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="7c63c-242">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="7c63c-242">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="7c63c-243">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="7c63c-243">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="7c63c-244">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="7c63c-244">about_Scopes</span></span>](About/about_scopes.md)
