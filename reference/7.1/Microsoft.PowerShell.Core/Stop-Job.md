---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: d6f1b3a719724073919930b1f1c0839250b5d2c8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204769"
---
# <span data-ttu-id="08604-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="08604-103">Stop-Job</span></span>

## <span data-ttu-id="08604-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="08604-104">SYNOPSIS</span></span>
<span data-ttu-id="08604-105">Arrête une tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08604-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="08604-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="08604-106">SYNTAX</span></span>

### <span data-ttu-id="08604-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="08604-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="08604-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="08604-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="08604-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="08604-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="08604-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="08604-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="08604-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="08604-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="08604-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="08604-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="08604-113">Description</span><span class="sxs-lookup"><span data-stu-id="08604-113">DESCRIPTION</span></span>

<span data-ttu-id="08604-114">L’applet de commande **Stop-Job** arrête les tâches en arrière-plan PowerShell en cours.</span><span class="sxs-lookup"><span data-stu-id="08604-114">The **Stop-Job** cmdlet stops PowerShell background jobs that are in progress.</span></span>
<span data-ttu-id="08604-115">Vous pouvez utiliser cette applet de commande pour arrêter toutes les tâches ou arrêter les tâches sélectionnées en fonction de leur nom, ID, ID d’instance ou État, ou en passant un objet de traitement à **Stop-Job** .</span><span class="sxs-lookup"><span data-stu-id="08604-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to **Stop-Job** .</span></span>

<span data-ttu-id="08604-116">Vous pouvez utiliser **Stop-Job** pour arrêter des tâches en arrière-plan, telles que celles qui ont été démarrées à l’aide de l’applet de commande Start-Job ou du paramètre *AsJob* d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="08604-116">You can use **Stop-Job** to stop background jobs, such as those that were started by using the Start-Job cmdlet or the *AsJob* parameter of any cmdlet.</span></span>
<span data-ttu-id="08604-117">Lorsque vous arrêtez une tâche en arrière-plan, PowerShell termine toutes les tâches en attente dans la file d’attente de travaux, puis met fin au travail.</span><span class="sxs-lookup"><span data-stu-id="08604-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span>
<span data-ttu-id="08604-118">Aucune nouvelle tâche n'est ajoutée à la file d'attente après que cette commande a été soumise.</span><span class="sxs-lookup"><span data-stu-id="08604-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="08604-119">Cette applet de commande ne supprime pas les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="08604-119">This cmdlet does not delete background jobs.</span></span>
<span data-ttu-id="08604-120">Pour supprimer un travail, utilisez l’applet de commande Remove-Job.</span><span class="sxs-lookup"><span data-stu-id="08604-120">To delete a job, use the Remove-Job cmdlet.</span></span>

<span data-ttu-id="08604-121">À compter de Windows PowerShell 3,0, **Stop-Job** arrête également les types de tâches personnalisées, tels que les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="08604-121">Starting in Windows PowerShell 3.0, **Stop-Job** also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="08604-122">Pour permettre à **Stop-Job** d’arrêter un travail avec un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une commande **Stop-Job** , soit à l’aide de l’applet de commande Import-Module, soit en utilisant ou en obtenant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="08604-122">To enable **Stop-Job** to stop a job with custom job type, import the module that supports the custom job type into the session before you run a **Stop-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="08604-123">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08604-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="08604-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="08604-124">EXAMPLES</span></span>

### <span data-ttu-id="08604-125">Exemple 1 : arrêter un travail sur un ordinateur distant à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="08604-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="08604-126">Cet exemple montre comment utiliser l'applet de commande **Stop-Job** pour arrêter une tâche qui s'exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="08604-126">This example shows how to use the **Stop-Job** cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="08604-127">Étant donné que la tâche a été démarrée à l’aide de l’applet de commande Invoke-Command pour exécuter une commande **Start-Job** à distance, l’objet de traitement est stocké sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="08604-127">Because the job was started by using the Invoke-Command cmdlet to run a **Start-Job** command remotely, the job object is stored on the remote computer.</span></span>
<span data-ttu-id="08604-128">Vous devez utiliser une autre commande **Invoke-Command** pour exécuter une commande **Stop-Job** à distance.</span><span class="sxs-lookup"><span data-stu-id="08604-128">You must use another **Invoke-Command** command to run a **Stop-Job** command remotely.</span></span>
<span data-ttu-id="08604-129">Pour plus d'informations sur les tâches distantes en arrière-plan, consultez about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="08604-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="08604-130">La première commande crée une session PowerShell ( **PSSession** ) sur l’ordinateur Serveur01, puis stocke l’objet de session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="08604-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the $s variable.</span></span>
<span data-ttu-id="08604-131">La commande utilise les informations d'identification d'un administrateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="08604-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="08604-132">La deuxième commande utilise l'applet de commande **Invoke-Command** pour exécuter une commande **Start-Job** dans la session.</span><span class="sxs-lookup"><span data-stu-id="08604-132">The second command uses the **Invoke-Command** cmdlet to run a **Start-Job** command in the session.</span></span>
<span data-ttu-id="08604-133">La commande qui figure dans la tâche obtient tous les événements du journal d'événements système.</span><span class="sxs-lookup"><span data-stu-id="08604-133">The command in the job gets all of the events in the System event log.</span></span>
<span data-ttu-id="08604-134">L'objet de traitement qui en résulte est stocké dans la variable $j.</span><span class="sxs-lookup"><span data-stu-id="08604-134">The resulting job object is stored in the $j variable.</span></span>

<span data-ttu-id="08604-135">La troisième commande arrête la tâche.</span><span class="sxs-lookup"><span data-stu-id="08604-135">The third command stops the job.</span></span>
<span data-ttu-id="08604-136">Elle utilise l’applet de **commande Invoke-Command** pour exécuter une commande **Stop-Job** dans la **session PSSession** sur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="08604-136">It uses the **Invoke-Command** cmdlet to run a **Stop-Job** command in the **PSSession** on Server01.</span></span>
<span data-ttu-id="08604-137">Comme les objets de traitement sont stockés dans $j, qui est une variable sur l'ordinateur local, la commande utilise le modificateur d'étendue Using pour identifier $j comme une variable locale.</span><span class="sxs-lookup"><span data-stu-id="08604-137">Because the job objects are stored in $j, which is a variable on the local computer, the command uses the Using scope modifier to identify $j as a local variable.</span></span>
<span data-ttu-id="08604-138">Pour plus d’informations sur le modificateur d’étendue using, consultez [about_Remote_Variables](about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="08604-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="08604-139">Une fois la commande terminée, la tâche est arrêtée et la **session PSSession** dans $s peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="08604-139">When the command finishes, the job is stopped and the **PSSession** in $s is available for use.</span></span>

### <span data-ttu-id="08604-140">Exemple 2 : arrêter une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="08604-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="08604-141">Cette commande arrête la tâche en arrière-plan Job1.</span><span class="sxs-lookup"><span data-stu-id="08604-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="08604-142">Exemple 3 : arrêter plusieurs tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="08604-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="08604-143">Cette commande arrête trois tâches.</span><span class="sxs-lookup"><span data-stu-id="08604-143">This command stops three jobs.</span></span>
<span data-ttu-id="08604-144">Elle les identifie par leurs ID.</span><span class="sxs-lookup"><span data-stu-id="08604-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="08604-145">Exemple 4 : arrêter toutes les tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="08604-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="08604-146">Cette commande arrête toutes les tâches en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="08604-147">Exemple 5 : arrêter toutes les tâches en arrière-plan bloquées</span><span class="sxs-lookup"><span data-stu-id="08604-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="08604-148">Cette commande arrête toutes les tâches qui sont bloquées.</span><span class="sxs-lookup"><span data-stu-id="08604-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="08604-149">Exemple 6 : arrêter un travail à l’aide d’un ID d’instance</span><span class="sxs-lookup"><span data-stu-id="08604-149">Example 6: Stop a job by using an instance ID</span></span>

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

<span data-ttu-id="08604-150">Ces commandes montrent comment arrêter une tâche sur la base de son ID d'instance.</span><span class="sxs-lookup"><span data-stu-id="08604-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="08604-151">La première commande utilise l’applet de commande Get-Job pour récupérer les tâches dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-151">The first command uses the Get-Job cmdlet to get the jobs in the current session.</span></span>
<span data-ttu-id="08604-152">La commande utilise un opérateur de pipeline (|) pour envoyer les tâches à une commande Format-Table, qui affiche une table des propriétés spécifiées de chaque travail.</span><span class="sxs-lookup"><span data-stu-id="08604-152">The command uses a pipeline operator (|) to send the jobs to a Format-Table command, which displays a table of the specified properties of each job.</span></span>
<span data-ttu-id="08604-153">Cette table inclut l'ID d'instance de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="08604-153">The table includes the Instance ID of each job.</span></span>
<span data-ttu-id="08604-154">Elle utilise une propriété calculée pour afficher l'état de la tâche.</span><span class="sxs-lookup"><span data-stu-id="08604-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="08604-155">La deuxième commande utilise une commande **Stop-Job** qui a le paramètre *InstanceID* pour arrêter un travail sélectionné.</span><span class="sxs-lookup"><span data-stu-id="08604-155">The second command uses a **Stop-Job** command that has the *InstanceID* parameter to stop a selected job.</span></span>

### <span data-ttu-id="08604-156">Exemple 7 : arrêter un travail sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="08604-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="08604-157">Cet exemple montre comment utiliser l'applet de commande **Stop-Job** pour arrêter une tâche qui s'exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="08604-157">This example shows how to use the **Stop-Job** cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="08604-158">Étant donné que la tâche a été démarrée à l’aide du paramètre *AsJob* de l’applet de **commande Invoke-Command** , l’objet de traitement se trouve sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="08604-158">Because the job was started by using the *AsJob* parameter of the **Invoke-Command** cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span>
<span data-ttu-id="08604-159">Par conséquent, vous pouvez utiliser une commande **Stop-Job** locale pour arrêter la tâche.</span><span class="sxs-lookup"><span data-stu-id="08604-159">Therefore, you can use a local **Stop-Job** command to stop the job.</span></span>

<span data-ttu-id="08604-160">La première commande utilise l'applet de commande **Invoke-Command** pour démarrer une tâche en arrière-plan sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="08604-160">The first command uses the **Invoke-Command** cmdlet to start a background job on the Server01 computer.</span></span>
<span data-ttu-id="08604-161">La commande utilise le paramètre *AsJob* pour exécuter la commande distante en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="08604-161">The command uses the *AsJob* parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="08604-162">Cette commande retourne un objet de traitement, qui est le même objet de traitement que celui retourné par l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="08604-162">This command returns a job object, which is the same job object that the **Start-Job** cmdlet returns.</span></span>
<span data-ttu-id="08604-163">La commande enregistre l'objet de traitement dans la variable $j.</span><span class="sxs-lookup"><span data-stu-id="08604-163">The command saves the job object in the $j variable.</span></span>

<span data-ttu-id="08604-164">La deuxième commande utilise un opérateur de pipeline pour envoyer la tâche figurant dans la variable $j à Stop-Job.</span><span class="sxs-lookup"><span data-stu-id="08604-164">The second command uses a pipeline operator to send the job in the $j variable to Stop-Job.</span></span>
<span data-ttu-id="08604-165">La commande utilise le paramètre *PassThru* pour indiquer à **Stop-Job** de retourner un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="08604-165">The command uses the *PassThru* parameter to direct **Stop-Job** to return a job object.</span></span>
<span data-ttu-id="08604-166">L’affichage de l’objet de traitement confirme que l’état du travail est arrêté.</span><span class="sxs-lookup"><span data-stu-id="08604-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="08604-167">Pour plus d'informations sur les tâches distantes en arrière-plan, consultez about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="08604-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="08604-168">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="08604-168">PARAMETERS</span></span>

### <span data-ttu-id="08604-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="08604-169">-Filter</span></span>

<span data-ttu-id="08604-170">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="08604-170">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="08604-171">Cette applet de commande arrête les travaux qui remplissent toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="08604-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="08604-172">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="08604-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="08604-173">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="08604-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="08604-174">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="08604-174">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="08604-175">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="08604-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="08604-176">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="08604-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="08604-177">-Id</span><span class="sxs-lookup"><span data-stu-id="08604-177">-Id</span></span>

<span data-ttu-id="08604-178">Spécifie les ID des travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="08604-178">Specifies the IDs of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="08604-179">La valeur par défaut est toutes les tâches dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="08604-180">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="08604-181">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="08604-182">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="08604-182">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="08604-183">Pour Rechercher l’ID d’un travail, tapez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="08604-183">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="08604-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="08604-184">-InstanceId</span></span>

<span data-ttu-id="08604-185">Spécifie les ID d’instance des travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="08604-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="08604-186">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="08604-186">The default is all jobs.</span></span>

<span data-ttu-id="08604-187">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="08604-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="08604-188">Pour rechercher l'ID d'instance d'une tâche, utilisez Get-Job.</span><span class="sxs-lookup"><span data-stu-id="08604-188">To find the instance ID of a job, use Get-Job.</span></span>

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

### <span data-ttu-id="08604-189">-Travail</span><span class="sxs-lookup"><span data-stu-id="08604-189">-Job</span></span>

<span data-ttu-id="08604-190">Spécifie les travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="08604-190">Specifies the jobs that this cmdlet stops.</span></span>
<span data-ttu-id="08604-191">Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="08604-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="08604-192">Vous pouvez également utiliser un opérateur de pipeline pour envoyer des travaux à l’applet de commande **Stop-Job** .</span><span class="sxs-lookup"><span data-stu-id="08604-192">You can also use a pipeline operator to submit jobs to the **Stop-Job** cmdlet.</span></span>
<span data-ttu-id="08604-193">Par défaut, **Stop-Job** supprime toutes les tâches qui ont été démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-193">By default, **Stop-Job** deletes all jobs that were started in the current session.</span></span>

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

### <span data-ttu-id="08604-194">-Name</span><span class="sxs-lookup"><span data-stu-id="08604-194">-Name</span></span>

<span data-ttu-id="08604-195">Spécifie les noms conviviaux des travaux que cette applet de commande arrête.</span><span class="sxs-lookup"><span data-stu-id="08604-195">Specifies friendly names of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="08604-196">Entrez les noms de tâches dans une liste séparée par des virgules ou utilisez des caractères génériques (\*) pour entrer un modèle de nom de tâche.</span><span class="sxs-lookup"><span data-stu-id="08604-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span>
<span data-ttu-id="08604-197">Par défaut, **Stop-Job** arrête toutes les tâches créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="08604-197">By default, **Stop-Job** stops all jobs created in the current session.</span></span>

<span data-ttu-id="08604-198">Étant donné que le nom convivial n’est pas forcément unique, utilisez les paramètres *WhatIf* et *Confirm* lors de l’arrêt des tâches par nom.</span><span class="sxs-lookup"><span data-stu-id="08604-198">Because the friendly name is not guaranteed to be unique, use the *WhatIf* and *Confirm* parameters when stopping jobs by name.</span></span>

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

### <span data-ttu-id="08604-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="08604-199">-PassThru</span></span>

<span data-ttu-id="08604-200">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="08604-200">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="08604-201">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="08604-201">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="08604-202">-État</span><span class="sxs-lookup"><span data-stu-id="08604-202">-State</span></span>

<span data-ttu-id="08604-203">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="08604-203">Specifies a job state.</span></span>
<span data-ttu-id="08604-204">Cette applet de commande arrête uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="08604-204">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="08604-205">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="08604-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="08604-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="08604-206">NotStarted</span></span>
- <span data-ttu-id="08604-207">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="08604-207">Running</span></span>
- <span data-ttu-id="08604-208">Completed</span><span class="sxs-lookup"><span data-stu-id="08604-208">Completed</span></span>
- <span data-ttu-id="08604-209">Échec</span><span class="sxs-lookup"><span data-stu-id="08604-209">Failed</span></span>
- <span data-ttu-id="08604-210">Arrêté</span><span class="sxs-lookup"><span data-stu-id="08604-210">Stopped</span></span>
- <span data-ttu-id="08604-211">Bloqué</span><span class="sxs-lookup"><span data-stu-id="08604-211">Blocked</span></span>
- <span data-ttu-id="08604-212">Interrompu</span><span class="sxs-lookup"><span data-stu-id="08604-212">Suspended</span></span>
- <span data-ttu-id="08604-213">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="08604-213">Disconnected</span></span>
- <span data-ttu-id="08604-214">Suspension</span><span class="sxs-lookup"><span data-stu-id="08604-214">Suspending</span></span>
- <span data-ttu-id="08604-215">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="08604-215">Stopping</span></span>

<span data-ttu-id="08604-216">Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="08604-216">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="08604-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="08604-217">-Confirm</span></span>

<span data-ttu-id="08604-218">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="08604-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="08604-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="08604-219">-WhatIf</span></span>

<span data-ttu-id="08604-220">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="08604-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="08604-221">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="08604-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="08604-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="08604-222">CommonParameters</span></span>

<span data-ttu-id="08604-223">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="08604-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="08604-224">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="08604-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="08604-225">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="08604-225">INPUTS</span></span>

### <span data-ttu-id="08604-226">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="08604-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="08604-227">Vous pouvez diriger un objet de traitement vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="08604-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="08604-228">SORTIES</span><span class="sxs-lookup"><span data-stu-id="08604-228">OUTPUTS</span></span>

### <span data-ttu-id="08604-229">Aucun, System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="08604-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="08604-230">Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="08604-230">This cmdlet returns a job object, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="08604-231">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="08604-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="08604-232">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="08604-232">NOTES</span></span>

## <span data-ttu-id="08604-233">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="08604-233">RELATED LINKS</span></span>

[<span data-ttu-id="08604-234">Get-Job</span><span class="sxs-lookup"><span data-stu-id="08604-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="08604-235">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="08604-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="08604-236">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="08604-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="08604-237">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="08604-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="08604-238">Start-Job</span><span class="sxs-lookup"><span data-stu-id="08604-238">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="08604-239">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="08604-239">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="08604-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="08604-240">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="08604-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="08604-241">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="08604-242">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="08604-242">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="08604-243">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="08604-243">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="08604-244">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="08604-244">about_Scopes</span></span>](About/about_scopes.md)

