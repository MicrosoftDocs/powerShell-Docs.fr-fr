---
external help file: ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 01/28/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: 13c78786b3dd506af9c6efa45eef4b5be20537cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205213"
---
# <span data-ttu-id="9fce5-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9fce5-102">Start-ThreadJob</span></span>

## <span data-ttu-id="9fce5-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9fce5-103">SYNOPSIS</span></span>
<span data-ttu-id="9fce5-104">Crée des travaux en arrière-plan similaires à l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9fce5-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="9fce5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9fce5-105">SYNTAX</span></span>

### <span data-ttu-id="9fce5-106">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="9fce5-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="9fce5-107">FilePath</span><span class="sxs-lookup"><span data-stu-id="9fce5-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="9fce5-108">Description</span><span class="sxs-lookup"><span data-stu-id="9fce5-108">DESCRIPTION</span></span>

<span data-ttu-id="9fce5-109">`Start-ThreadJob` crée des travaux en arrière-plan similaires à l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9fce5-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="9fce5-110">La principale différence réside dans le fait que les tâches qui sont créées s’exécutent dans des threads distincts au sein du processus local.</span><span class="sxs-lookup"><span data-stu-id="9fce5-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="9fce5-111">Par défaut, les travaux utilisent le répertoire de travail actuel de l’appelant qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="9fce5-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="9fce5-112">L’applet de commande prend également en charge un paramètre **ThrottleLimit** pour limiter le nombre de travaux en cours d’exécution en même temps.</span><span class="sxs-lookup"><span data-stu-id="9fce5-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="9fce5-113">À mesure que d’autres tâches sont démarrées, elles sont mises en file d’attente et patientent jusqu’à ce que le nombre de travaux en cours descend en dessous de la limite de limitation.</span><span class="sxs-lookup"><span data-stu-id="9fce5-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="9fce5-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9fce5-114">EXAMPLES</span></span>

### <span data-ttu-id="9fce5-115">Exemple 1 : créer des tâches en arrière-plan avec une limite de threads de 2</span><span class="sxs-lookup"><span data-stu-id="9fce5-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### <span data-ttu-id="9fce5-116">Exemple 2 : comparaison des performances des Start-Job et des Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9fce5-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="9fce5-117">Cet exemple montre la différence entre `Start-Job` et `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="9fce5-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="9fce5-118">Les tâches exécutent l' `Start-Sleep` applet de commande pendant 1 seconde.</span><span class="sxs-lookup"><span data-stu-id="9fce5-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="9fce5-119">Étant donné que les tâches s’exécutent en parallèle, le temps total d’exécution est d’environ 1 seconde, plus tout moment nécessaire pour créer les travaux.</span><span class="sxs-lookup"><span data-stu-id="9fce5-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

<span data-ttu-id="9fce5-120">Après avoir soustrait 1 seconde pour la durée d’exécution, vous pouvez constater qu' `Start-Job` environ 4,8 secondes sont nécessaires pour créer cinq travaux.</span><span class="sxs-lookup"><span data-stu-id="9fce5-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="9fce5-121">`Start-ThreadJob` est 8 fois plus rapide, ce qui prend environ 0,6 secondes pour créer cinq tâches.</span><span class="sxs-lookup"><span data-stu-id="9fce5-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="9fce5-122">Les résultats peuvent varier dans votre environnement, mais l’amélioration relative doit être la même.</span><span class="sxs-lookup"><span data-stu-id="9fce5-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="9fce5-123">Exemple 3 : créer des travaux à l’aide d’InputObject</span><span class="sxs-lookup"><span data-stu-id="9fce5-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="9fce5-124">Dans cet exemple, le bloc de script utilise la `$input` variable pour recevoir l’entrée du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="9fce5-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="9fce5-125">Pour ce faire, vous pouvez également rediriger les objets vers `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="9fce5-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

## <span data-ttu-id="9fce5-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9fce5-126">PARAMETERS</span></span>

### <span data-ttu-id="9fce5-127">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9fce5-127">-ArgumentList</span></span>

<span data-ttu-id="9fce5-128">Spécifie un tableau d’arguments, ou valeurs de paramètre, pour le script spécifié par les paramètres **filePath** ou **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="9fce5-128">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="9fce5-129">**Argumentlist** doit être le dernier paramètre sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9fce5-129">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="9fce5-130">Toutes les valeurs qui suivent le nom du paramètre sont des valeurs interprétées dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="9fce5-130">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-131">-FilePath</span><span class="sxs-lookup"><span data-stu-id="9fce5-131">-FilePath</span></span>

<span data-ttu-id="9fce5-132">Spécifie un fichier de script à exécuter en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9fce5-132">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="9fce5-133">Entrez le chemin d’accès et le nom de fichier du script.</span><span class="sxs-lookup"><span data-stu-id="9fce5-133">Enter the path and filename of the script.</span></span> <span data-ttu-id="9fce5-134">Le script doit se trouver sur l’ordinateur local ou dans un dossier accessible à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9fce5-134">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="9fce5-135">Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script et exécute le bloc de script en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9fce5-135">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-136">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="9fce5-136">-InitializationScript</span></span>

<span data-ttu-id="9fce5-137">Spécifie les commandes à exécuter avant le début de la tâche.</span><span class="sxs-lookup"><span data-stu-id="9fce5-137">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="9fce5-138">Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="9fce5-138">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="9fce5-139">Utilisez ce paramètre pour préparer la session dans laquelle la tâche s'exécute.</span><span class="sxs-lookup"><span data-stu-id="9fce5-139">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="9fce5-140">Par exemple, vous pouvez l’utiliser pour ajouter des fonctions et des modules à la session.</span><span class="sxs-lookup"><span data-stu-id="9fce5-140">For example, you can use it to add functions and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9fce5-141">-InputObject</span></span>

<span data-ttu-id="9fce5-142">Spécifie les objets utilisés comme entrée pour le bloc de script.</span><span class="sxs-lookup"><span data-stu-id="9fce5-142">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="9fce5-143">Il permet également l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="9fce5-143">It also allows for pipeline input.</span></span> <span data-ttu-id="9fce5-144">Utilisez la `$input` variable automatique dans le bloc de script pour accéder aux objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9fce5-144">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-145">-Name</span><span class="sxs-lookup"><span data-stu-id="9fce5-145">-Name</span></span>

<span data-ttu-id="9fce5-146">Spécifie le nom convivial de la nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="9fce5-146">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="9fce5-147">Vous pouvez utiliser le nom pour identifier le travail à d’autres applets de commande de tâche, telles que l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="9fce5-147">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="9fce5-148">Le nom convivial par défaut est « Job # », où « # » est un nombre ordinal qui est incrémenté pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="9fce5-148">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-149">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="9fce5-149">-ScriptBlock</span></span>

<span data-ttu-id="9fce5-150">Spécifie les commandes à exécuter dans la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9fce5-150">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="9fce5-151">Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="9fce5-151">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="9fce5-152">Utilisez la `$Input` variable Automatic pour accéder à la valeur du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="9fce5-152">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="9fce5-153">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9fce5-153">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-154">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="9fce5-154">-StreamingHost</span></span>

<span data-ttu-id="9fce5-155">Ce paramètre fournit une méthode thread-safe pour permettre `Write-Host` à la sortie d’accéder directement à l’objet **PSHost** passé.</span><span class="sxs-lookup"><span data-stu-id="9fce5-155">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="9fce5-156">Sans celui-ci, `Write-Host` la sortie est envoyée à la collection de flux de données d’informations sur le travail et n’apparaît pas dans une console hôte jusqu’à la fin de l’exécution des travaux.</span><span class="sxs-lookup"><span data-stu-id="9fce5-156">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-157">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9fce5-157">-ThrottleLimit</span></span>

<span data-ttu-id="9fce5-158">Ce paramètre limite le nombre de travaux en cours d’exécution en même temps.</span><span class="sxs-lookup"><span data-stu-id="9fce5-158">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="9fce5-159">À mesure que les tâches sont démarrées, elles sont mises en file d’attente et attendent jusqu’à ce qu’un thread soit disponible dans le pool de threads pour exécuter le travail.</span><span class="sxs-lookup"><span data-stu-id="9fce5-159">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="9fce5-160">La limite par défaut est de 5 threads.</span><span class="sxs-lookup"><span data-stu-id="9fce5-160">The default limit is 5 threads.</span></span>

<span data-ttu-id="9fce5-161">La taille du pool de threads est globale pour la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fce5-161">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="9fce5-162">La spécification d’un **ThrottleLimit** dans un appel définit la limite pour les appels suivants dans la même session.</span><span class="sxs-lookup"><span data-stu-id="9fce5-162">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fce5-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9fce5-163">CommonParameters</span></span>

<span data-ttu-id="9fce5-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9fce5-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9fce5-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9fce5-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9fce5-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9fce5-166">INPUTS</span></span>

### <span data-ttu-id="9fce5-167">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9fce5-167">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="9fce5-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9fce5-168">OUTPUTS</span></span>

### <span data-ttu-id="9fce5-169">ThreadJob.ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9fce5-169">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="9fce5-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9fce5-170">NOTES</span></span>

## <span data-ttu-id="9fce5-171">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9fce5-171">RELATED LINKS</span></span>

[<span data-ttu-id="9fce5-172">Start-Job</span><span class="sxs-lookup"><span data-stu-id="9fce5-172">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="9fce5-173">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="9fce5-173">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="9fce5-174">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="9fce5-174">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)
