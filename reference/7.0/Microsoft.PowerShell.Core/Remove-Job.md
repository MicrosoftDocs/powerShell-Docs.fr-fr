---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52db5da9057023ce9a687e1d11b0534afaabdad9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202521"
---
# <span data-ttu-id="1ce9f-103">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-103">Remove-Job</span></span>

## <span data-ttu-id="1ce9f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1ce9f-104">SYNOPSIS</span></span>
<span data-ttu-id="1ce9f-105">Supprime une tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-105">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="1ce9f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1ce9f-106">SYNTAX</span></span>

### <span data-ttu-id="1ce9f-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1ce9f-107">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1ce9f-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="1ce9f-108">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1ce9f-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="1ce9f-109">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1ce9f-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="1ce9f-110">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1ce9f-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="1ce9f-111">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1ce9f-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="1ce9f-112">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1ce9f-113">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="1ce9f-113">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1ce9f-114">Description</span><span class="sxs-lookup"><span data-stu-id="1ce9f-114">DESCRIPTION</span></span>

<span data-ttu-id="1ce9f-115">L' `Remove-Job` applet de commande supprime les tâches en arrière-plan PowerShell qui ont été démarrées par l’applet de commande `Start-Job` ou par des applets de commande telles que `Invoke-Command` qui prennent en charge le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-115">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="1ce9f-116">Vous pouvez utiliser `Remove-Job` pour supprimer tous les travaux ou supprimer les travaux sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-116">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="1ce9f-117">Les travaux sont identifiés par leur **nom** , **ID** , **ID d’instance** , **commande** ou **État** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-117">The jobs are identified by their **Name** , **ID** , **Instance ID** , **Command** , or **State** .</span></span> <span data-ttu-id="1ce9f-118">Ou un objet de traitement peut être envoyé dans le pipeline à `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-118">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="1ce9f-119">Sans paramètres ou valeurs de paramètre, n' `Remove-Job` a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-119">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="1ce9f-120">Depuis PowerShell 3,0, `Remove-Job` peut supprimer des types de tâches personnalisées, tels que les tâches planifiées et les tâches de Workflow.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-120">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="1ce9f-121">Par exemple, `Remove-Job` supprime la tâche planifiée, toutes les instances de la tâche planifiée sur le disque et les résultats de toutes les instances de tâche déclenchées.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-121">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="1ce9f-122">Si vous tentez de supprimer un travail en cours d’exécution, `Remove-Job` échoue.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-122">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="1ce9f-123">Utilisez l' `Stop-Job` applet de commande pour arrêter un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-123">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="1ce9f-124">`Remove-Job`Vous pouvez utiliser avec le paramètre **force** pour supprimer un travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-124">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="1ce9f-125">Les travaux restent dans le cache global des tâches jusqu’à ce que vous supprimiez la tâche en arrière-plan ou que vous fermiez la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-125">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="1ce9f-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1ce9f-126">EXAMPLES</span></span>

### <span data-ttu-id="1ce9f-127">Exemple 1 : supprimer un travail à l’aide de son nom</span><span class="sxs-lookup"><span data-stu-id="1ce9f-127">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="1ce9f-128">Cet exemple utilise une variable et le pipeline pour supprimer un travail par son nom.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-128">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="1ce9f-129">`Get-Job` utilise le paramètre **Name** pour spécifier le travail, **BatchJob** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-129">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob** .</span></span> <span data-ttu-id="1ce9f-130">L’objet de traitement est stocké dans la `$batch` variable.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-130">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="1ce9f-131">L’objet dans `$batch` est envoyé dans le pipeline à `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-131">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="1ce9f-132">Une alternative consiste à utiliser le paramètre de **tâche** , tel que `Remove-Job -Job $batch` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-132">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="1ce9f-133">Exemple 2 : supprimer tous les travaux d’une session</span><span class="sxs-lookup"><span data-stu-id="1ce9f-133">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="1ce9f-134">Dans cet exemple, toutes les tâches de la session PowerShell active sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-134">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="1ce9f-135">`Get-Job` Obtient toutes les tâches dans la session PowerShell en cours.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-135">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="1ce9f-136">Les objets de travail sont envoyés dans le pipeline à `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-136">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="1ce9f-137">Exemple 3 : supprimer des tâches NotStarted</span><span class="sxs-lookup"><span data-stu-id="1ce9f-137">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="1ce9f-138">Cet exemple supprime tous les travaux de la session PowerShell active qui n’ont pas démarré.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-138">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="1ce9f-139">`Remove-Job` utilise le paramètre **State** pour spécifier l’état du travail.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-139">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="1ce9f-140">Exemple 4 : supprimer des travaux à l’aide d’un nom convivial</span><span class="sxs-lookup"><span data-stu-id="1ce9f-140">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="1ce9f-141">Cet exemple supprime toutes les tâches de la session active avec des noms conviviaux qui se terminent par \* Batch \* \*, y compris les travaux en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-141">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="1ce9f-142">`Remove-Job` utilise le paramètre **Name** pour spécifier un modèle de nom de tâche.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-142">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="1ce9f-143">Le modèle comprend le `*` caractère générique astérisque () pour rechercher tous les noms de travail qui se terminent par **batch** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-143">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch** .</span></span> <span data-ttu-id="1ce9f-144">Le paramètre **force** supprime les travaux qui exécutent.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-144">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="1ce9f-145">Exemple 5 : supprimer un travail qui a été créé par Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1ce9f-145">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="1ce9f-146">Cet exemple supprime une tâche qui a été démarrée sur un ordinateur distant à l’aide `Invoke-Command` de avec le paramètre **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-146">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="1ce9f-147">Étant donné que l’exemple utilise le paramètre **AsJob** , l’objet de traitement est créé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-147">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="1ce9f-148">Toutefois, le travail s’exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-148">But, the job runs on a remote computer.</span></span> <span data-ttu-id="1ce9f-149">Par conséquent, vous utilisez des commandes locales pour gérer la tâche.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-149">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="1ce9f-150">`Invoke-Command` exécute un travail sur l’ordinateur **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-150">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="1ce9f-151">Le paramètre **AsJob** exécute le **scriptblock** en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-151">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="1ce9f-152">L’objet de traitement est stocké dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-152">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="1ce9f-153">L' `$job` objet variable est envoyé dans le pipeline à `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-153">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="1ce9f-154">Exemple 6 : supprimer un travail qui a été créé par Invoke-Command et Start-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-154">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="1ce9f-155">Cet exemple montre comment supprimer un travail sur un ordinateur distant qui a été démarré à l’aide `Invoke-Command` de pour exécuter `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-155">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="1ce9f-156">L’objet de traitement est créé sur l’ordinateur distant et les commandes à distance sont utilisées pour gérer le travail.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-156">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="1ce9f-157">Une connexion permanente est nécessaire lors de l’exécution d’une commande à distance `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-157">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="1ce9f-158">`New-PSSession` crée une **session PSSession** , une connexion permanente, à l’ordinateur **SERVEUR01** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-158">`New-PSSession` creates a **PSSession** , a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="1ce9f-159">La connexion est enregistrée dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-159">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="1ce9f-160">`Invoke-Command` établit une connexion à la session enregistrée dans `$S` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-160">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="1ce9f-161">Le **scriptblock** utilise `Start-Job` pour démarrer un travail distant.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-161">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="1ce9f-162">La tâche exécute une `Get-Process` commande et utilise le paramètre **Name** pour spécifier un nom de travail convivial, **MyJob** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-162">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob** .</span></span>

<span data-ttu-id="1ce9f-163">`Invoke-Command` utilise la `$S` session et s’exécute `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-163">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="1ce9f-164">Le paramètre **Name** spécifie que la tâche nommée **MyJob** est supprimée.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-164">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="1ce9f-165">Exemple 7 : supprimer un travail à l’aide de son InstanceId</span><span class="sxs-lookup"><span data-stu-id="1ce9f-165">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="1ce9f-166">Cet exemple supprime un travail en fonction de son **InstanceID** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-166">This example removes a job based on its **InstanceId** .</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="1ce9f-167">`Start-Job` démarre une tâche en arrière-plan et l’objet de traitement est enregistré dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-167">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="1ce9f-168">L’objet dans `$job` est envoyé dans le pipeline à `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-168">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="1ce9f-169">Le paramètre **Property** utilise un astérisque ( `*` ) pour spécifier que toutes les propriétés de l’objet sont affichées dans une liste.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-169">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="1ce9f-170">`Remove-Job` utilise le paramètre **InstanceID** pour spécifier la tâche à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-170">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="1ce9f-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1ce9f-171">PARAMETERS</span></span>

### <span data-ttu-id="1ce9f-172">-Command</span><span class="sxs-lookup"><span data-stu-id="1ce9f-172">-Command</span></span>

<span data-ttu-id="1ce9f-173">Supprime les tâches qui incluent les mots spécifiés dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-173">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="1ce9f-174">Vous pouvez entrer un tableau de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-174">You can enter a comma-separated array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1ce9f-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1ce9f-175">-Confirm</span></span>

<span data-ttu-id="1ce9f-176">Vous invite à confirmer avant l' `Remove-Job` exécution de.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-176">Prompts you for confirmation before `Remove-Job` is run.</span></span>

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

### <span data-ttu-id="1ce9f-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="1ce9f-177">-Filter</span></span>

<span data-ttu-id="1ce9f-178">Supprime les tâches qui répondent à toutes les conditions établies dans la table de hachage associée.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-178">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="1ce9f-179">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-179">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="1ce9f-180">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-180">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="1ce9f-181">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-181">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="1ce9f-182">Ce paramètre est introduit dans PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-182">This parameter is introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1ce9f-183">-Force</span><span class="sxs-lookup"><span data-stu-id="1ce9f-183">-Force</span></span>

<span data-ttu-id="1ce9f-184">Supprime un travail même si l’état de la tâche est **en cours d’exécution** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-184">Deletes a job even if the job's state is **Running** .</span></span> <span data-ttu-id="1ce9f-185">Si le paramètre **force** n’est pas spécifié, `Remove-Job` ne supprime pas les travaux en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-185">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, NameParameterSet, InstanceIdParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1ce9f-186">-Id</span><span class="sxs-lookup"><span data-stu-id="1ce9f-186">-Id</span></span>

<span data-ttu-id="1ce9f-187">Supprime les tâches en arrière-plan avec l' **ID** spécifié. Vous pouvez entrer un tableau de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-187">Deletes background jobs with the specified **Id** . You can enter a comma-separated array.</span></span> <span data-ttu-id="1ce9f-188">L' **ID** du travail est un entier unique qui identifie un travail au sein de la session active.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-188">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="1ce9f-189">Pour Rechercher l' **ID** d’un travail, utilisez `Get-Job` sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-189">To find a job's **Id** , use `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="1ce9f-190">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="1ce9f-190">-InstanceId</span></span>

<span data-ttu-id="1ce9f-191">Supprime les travaux avec l' **InstanceID** spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-191">Deletes jobs with the specified **InstanceId** .</span></span> <span data-ttu-id="1ce9f-192">Vous pouvez entrer un tableau de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-192">You can enter a comma-separated array.</span></span> <span data-ttu-id="1ce9f-193">Un **InstanceID** est un GUID unique qui identifie un travail.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-193">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="1ce9f-194">Pour Rechercher l' **InstanceID** d’un travail, utilisez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-194">To find a job's **InstanceId** , use `Get-Job`.</span></span>

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

### <span data-ttu-id="1ce9f-195">-Travail</span><span class="sxs-lookup"><span data-stu-id="1ce9f-195">-Job</span></span>

<span data-ttu-id="1ce9f-196">Spécifie les tâches à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-196">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="1ce9f-197">Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-197">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="1ce9f-198">Vous pouvez entrer un tableau de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-198">You can enter a comma-separated array.</span></span>

<span data-ttu-id="1ce9f-199">Vous pouvez envoyer des objets de travail vers le dessous du pipeline `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-199">You can send job objects down the pipeline to `Remove-Job`.</span></span>

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

### <span data-ttu-id="1ce9f-200">-Name</span><span class="sxs-lookup"><span data-stu-id="1ce9f-200">-Name</span></span>

<span data-ttu-id="1ce9f-201">Supprime uniquement les tâches avec le nom convivial spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-201">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="1ce9f-202">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-202">Wildcards are permitted.</span></span> <span data-ttu-id="1ce9f-203">Vous pouvez entrer un tableau de valeurs séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-203">You can enter a comma-separated array.</span></span>

<span data-ttu-id="1ce9f-204">Il n’est pas garanti que les noms conviviaux des travaux soient uniques, même au sein d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-204">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="1ce9f-205">Utilisez les paramètres **WhatIf** et **Confirm** lorsque vous supprimez des fichiers par nom.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-205">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1ce9f-206">-État</span><span class="sxs-lookup"><span data-stu-id="1ce9f-206">-State</span></span>

<span data-ttu-id="1ce9f-207">Supprime uniquement les tâches avec l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-207">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="1ce9f-208">Pour supprimer des travaux avec un état **en cours d’exécution** , utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-208">To delete jobs with a state of **Running** , use the **Force** parameter.</span></span>

<span data-ttu-id="1ce9f-209">Valeurs acceptées :</span><span class="sxs-lookup"><span data-stu-id="1ce9f-209">Accepted values:</span></span>

- <span data-ttu-id="1ce9f-210">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1ce9f-210">AtBreakpoint</span></span>
- <span data-ttu-id="1ce9f-211">Bloqué</span><span class="sxs-lookup"><span data-stu-id="1ce9f-211">Blocked</span></span>
- <span data-ttu-id="1ce9f-212">Effectué</span><span class="sxs-lookup"><span data-stu-id="1ce9f-212">Completed</span></span>
- <span data-ttu-id="1ce9f-213">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="1ce9f-213">Disconnected</span></span>
- <span data-ttu-id="1ce9f-214">Échec</span><span class="sxs-lookup"><span data-stu-id="1ce9f-214">Failed</span></span>
- <span data-ttu-id="1ce9f-215">NotStarted</span><span class="sxs-lookup"><span data-stu-id="1ce9f-215">NotStarted</span></span>
- <span data-ttu-id="1ce9f-216">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="1ce9f-216">Running</span></span>
- <span data-ttu-id="1ce9f-217">Arrêté</span><span class="sxs-lookup"><span data-stu-id="1ce9f-217">Stopped</span></span>
- <span data-ttu-id="1ce9f-218">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="1ce9f-218">Stopping</span></span>
- <span data-ttu-id="1ce9f-219">Interrompu</span><span class="sxs-lookup"><span data-stu-id="1ce9f-219">Suspended</span></span>
- <span data-ttu-id="1ce9f-220">Suspension</span><span class="sxs-lookup"><span data-stu-id="1ce9f-220">Suspending</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1ce9f-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1ce9f-221">-WhatIf</span></span>

<span data-ttu-id="1ce9f-222">Montre ce qui se passe si `Remove-Job` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-222">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="1ce9f-223">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-223">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1ce9f-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ce9f-224">CommonParameters</span></span>

<span data-ttu-id="1ce9f-225">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-225">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ce9f-226">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1ce9f-226">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1ce9f-227">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1ce9f-227">INPUTS</span></span>

### <span data-ttu-id="1ce9f-228">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-228">System.Management.Automation.Job</span></span>

<span data-ttu-id="1ce9f-229">Vous pouvez envoyer un objet de traitement vers le dessous du pipeline `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="1ce9f-229">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="1ce9f-230">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1ce9f-230">OUTPUTS</span></span>

### <span data-ttu-id="1ce9f-231">Aucun</span><span class="sxs-lookup"><span data-stu-id="1ce9f-231">None</span></span>

<span data-ttu-id="1ce9f-232">`Remove-Job` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-232">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="1ce9f-233">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1ce9f-233">NOTES</span></span>

<span data-ttu-id="1ce9f-234">Un travail PowerShell crée un nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-234">A PowerShell job creates a new process.</span></span> <span data-ttu-id="1ce9f-235">Une fois le travail terminé, le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-235">When the job completes, the process exits.</span></span> <span data-ttu-id="1ce9f-236">Lorsque `Remove-Job` est exécuté, l’état du travail est supprimé.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-236">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="1ce9f-237">Si un travail s’arrête avant la fin et que son processus n’a pas quitté, le processus est arrêté de force.</span><span class="sxs-lookup"><span data-stu-id="1ce9f-237">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="1ce9f-238">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1ce9f-238">RELATED LINKS</span></span>

[<span data-ttu-id="1ce9f-239">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="1ce9f-239">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="1ce9f-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="1ce9f-240">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="1ce9f-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="1ce9f-241">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="1ce9f-242">Get-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-242">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="1ce9f-243">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1ce9f-243">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="1ce9f-244">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-244">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="1ce9f-245">Start-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-245">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="1ce9f-246">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-246">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="1ce9f-247">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="1ce9f-247">Wait-Job</span></span>](Wait-Job.md)
