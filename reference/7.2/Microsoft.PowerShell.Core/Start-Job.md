---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 491292253578f287940490bad198698fc4b87e37
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599159"
---
# <span data-ttu-id="1d42c-102">Start-Job</span><span class="sxs-lookup"><span data-stu-id="1d42c-102">Start-Job</span></span>

## <span data-ttu-id="1d42c-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1d42c-103">SYNOPSIS</span></span>
<span data-ttu-id="1d42c-104">Démarre une tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d42c-104">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="1d42c-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1d42c-105">SYNTAX</span></span>

### <span data-ttu-id="1d42c-106">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1d42c-106">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1d42c-107">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="1d42c-107">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### <span data-ttu-id="1d42c-108">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="1d42c-108">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="1d42c-109">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="1d42c-109">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="1d42c-110">Description</span><span class="sxs-lookup"><span data-stu-id="1d42c-110">DESCRIPTION</span></span>

<span data-ttu-id="1d42c-111">L' `Start-Job` applet de commande démarre une tâche en arrière-plan PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-111">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="1d42c-112">Une tâche en arrière-plan PowerShell exécute une commande sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="1d42c-112">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="1d42c-113">Lorsque vous démarrez une tâche en arrière-plan, un objet de tâche est retourné immédiatement, même si le travail prend une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="1d42c-113">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="1d42c-114">Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="1d42c-114">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="1d42c-115">L’objet de traitement contient des informations utiles sur le travail, mais il ne contient pas les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-115">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="1d42c-116">Une fois le travail terminé, utilisez l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-116">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="1d42c-117">Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="1d42c-117">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="1d42c-118">Pour exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez le paramètre **AsJob** qui est disponible sur de nombreuses applets de commande, ou utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="1d42c-118">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="1d42c-119">Pour plus d’informations, consultez [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="1d42c-119">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="1d42c-120">À compter de PowerShell 3,0, `Start-Job` peut démarrer des instances de types de tâches personnalisées, telles que les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1d42c-120">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="1d42c-121">Pour plus d’informations sur l’utilisation `Start-Job` de pour démarrer des travaux avec des types personnalisés, consultez les documents d’aide pour la fonctionnalité de type de tâche.</span><span class="sxs-lookup"><span data-stu-id="1d42c-121">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="1d42c-122">À compter de PowerShell 6,0, vous pouvez démarrer des travaux à l’aide de l' `&` opérateur d’arrière-plan esperluette ().</span><span class="sxs-lookup"><span data-stu-id="1d42c-122">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="1d42c-123">Les fonctionnalités de l’opérateur d’arrière-plan sont similaires à celles de `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-123">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="1d42c-124">Les deux méthodes pour démarrer un travail créent un objet de tâche **PSRemotingJob** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-124">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="1d42c-125">Pour plus d’informations sur l’utilisation de l’esperluette ( `&` ), consultez [about_Operators](./about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="1d42c-125">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="1d42c-126">PowerShell 7 a introduit le paramètre **WorkingDirectory** qui spécifie le répertoire de travail initial d’un travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-126">PowerShell 7 introduced the **WorkingDirectory** parameter that specifies a background job's initial working directory.</span></span> <span data-ttu-id="1d42c-127">Si le paramètre n’est pas spécifié, `Start-Job` le répertoire de travail actuel de l’appelant qui a démarré le travail est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="1d42c-127">If the parameter isn't specified, `Start-Job` defaults to the current working directory of the caller that started the job.</span></span>

> [!NOTE]
> <span data-ttu-id="1d42c-128">La création d’un travail en arrière-plan out-of-process avec `Start-Job` n’est pas prise en charge dans le scénario où PowerShell est hébergé dans d’autres applications, telles que les Azure Functions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d42c-128">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="1d42c-129">Cela est lié à la conception, car `Start-Job` dépend du `pwsh` fichier exécutable à utiliser `$PSHOME` pour démarrer un travail en arrière-plan out-of-process, mais quand une application héberge PowerShell, elle utilise directement les packages du kit SDK NuGet PowerShell et n’est pas `pwsh` livrée avec.</span><span class="sxs-lookup"><span data-stu-id="1d42c-129">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="1d42c-130">Le substitut dans ce scénario provient du `Start-ThreadJob` module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span><span class="sxs-lookup"><span data-stu-id="1d42c-130">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.</span></span>

## <span data-ttu-id="1d42c-131">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1d42c-131">EXAMPLES</span></span>

### <span data-ttu-id="1d42c-132">Exemple 1 : démarrer une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-132">Example 1: Start a background job</span></span>

<span data-ttu-id="1d42c-133">Cet exemple démarre une tâche en arrière-plan qui s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-133">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="1d42c-134">`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Process` en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-134">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="1d42c-135">Le paramètre **Name** spécifie de rechercher les processus PowerShell, `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-135">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="1d42c-136">Les informations sur le travail s’affichent et PowerShell retourne à une invite pendant l’exécution de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-136">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="1d42c-137">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d42c-137">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="1d42c-138">Par exemple, `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="1d42c-138">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="1d42c-139">Exemple 2 : utiliser l’opérateur d’arrière-plan pour démarrer une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-139">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="1d42c-140">Cet exemple utilise l' `&` opérateur d’arrière-plan esperluette () pour démarrer une tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-140">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="1d42c-141">Le travail obtient le même résultat que `Start-Job` dans l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="1d42c-141">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="1d42c-142">`Get-Process` utilise le paramètre **Name** pour spécifier les processus PowerShell `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-142">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="1d42c-143">La esperluette ( `&` ) exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-143">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="1d42c-144">Les informations sur le travail s’affichent et PowerShell retourne à une invite pendant l’exécution de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-144">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="1d42c-145">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d42c-145">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="1d42c-146">Par exemple, `Receive-Job -Id 5`.</span><span class="sxs-lookup"><span data-stu-id="1d42c-146">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="1d42c-147">Exemple 3 : démarrer un travail à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1d42c-147">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="1d42c-148">Cet exemple exécute un travail sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="1d42c-148">This example runs a job on multiple computers.</span></span> <span data-ttu-id="1d42c-149">Le travail est stocké dans une variable et est exécuté à l’aide du nom de variable sur la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d42c-149">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="1d42c-150">Un travail qui utilise `Invoke-Command` est créé et stocké dans la `$jobWRM` variable.</span><span class="sxs-lookup"><span data-stu-id="1d42c-150">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="1d42c-151">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier les ordinateurs sur lesquels le travail s’exécute.</span><span class="sxs-lookup"><span data-stu-id="1d42c-151">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="1d42c-152">`Get-Content` Obtient les noms de serveur à partir du `C:\Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="1d42c-152">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="1d42c-153">Le paramètre **scriptblock** spécifie une commande qui `Get-Service` obtient le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-153">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="1d42c-154">Le paramètre **JobName** spécifie un nom convivial pour le travail, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="1d42c-154">The **JobName** parameter specifies a friendly name for the job, **WinRM**.</span></span> <span data-ttu-id="1d42c-155">Le paramètre **ThrottleLimit** limite le nombre de commandes simultanées à 16.</span><span class="sxs-lookup"><span data-stu-id="1d42c-155">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="1d42c-156">Le paramètre **AsJob** démarre une tâche en arrière-plan qui exécute la commande sur les serveurs.</span><span class="sxs-lookup"><span data-stu-id="1d42c-156">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="1d42c-157">Exemple 4 : récupérer des informations sur le travail</span><span class="sxs-lookup"><span data-stu-id="1d42c-157">Example 4: Get job information</span></span>

<span data-ttu-id="1d42c-158">Cet exemple obtient des informations sur un travail et affiche les résultats d’une tâche terminée qui a été exécutée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-158">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="1d42c-159">`Start-Job` utilise le paramètre **scriptblock** pour exécuter une commande qui spécifie `Get-WinEvent` d’obtenir le journal **système** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-159">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="1d42c-160">Le paramètre **Credential** spécifie un compte d’utilisateur de domaine autorisé à exécuter la tâche sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d42c-160">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="1d42c-161">L’objet de traitement est stocké dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="1d42c-161">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="1d42c-162">L’objet dans la `$j` variable est envoyé dans le pipeline à `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-162">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="1d42c-163">Le paramètre **Property** spécifie un astérisque ( `*` ) pour afficher toutes les propriétés de l’objet de tâche.</span><span class="sxs-lookup"><span data-stu-id="1d42c-163">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="1d42c-164">Exemple 5 : exécuter un script en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-164">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="1d42c-165">Dans cet exemple, un script sur l’ordinateur local est exécuté en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-165">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="1d42c-166">`Start-Job` utilise le paramètre **filePath** pour spécifier un fichier de script stocké sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-166">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="1d42c-167">Exemple 6 : obtenir un processus à l’aide d’un travail en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-167">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="1d42c-168">Cet exemple utilise une tâche en arrière-plan pour obtenir un processus spécifié par son nom.</span><span class="sxs-lookup"><span data-stu-id="1d42c-168">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="1d42c-169">`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **PShellJob**.</span><span class="sxs-lookup"><span data-stu-id="1d42c-169">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob**.</span></span> <span data-ttu-id="1d42c-170">Le paramètre **scriptblock** spécifie `Get-Process` d’extraire les processus avec le nom **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1d42c-170">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell**.</span></span>

### <span data-ttu-id="1d42c-171">Exemple 7 : collecter et enregistrer des données à l’aide d’une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-171">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="1d42c-172">Cet exemple démarre un travail qui collecte une grande quantité de données cartographiques, puis l’enregistre dans un `.tif` fichier.</span><span class="sxs-lookup"><span data-stu-id="1d42c-172">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

<span data-ttu-id="1d42c-173">`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **GetMappingFiles**.</span><span class="sxs-lookup"><span data-stu-id="1d42c-173">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles**.</span></span> <span data-ttu-id="1d42c-174">Le paramètre **initializationScript** exécute un bloc de script qui importe le module **MapFunctions** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-174">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="1d42c-175">Le paramètre **scriptblock** s’exécute `Get-Map` et `Set-Content` enregistre les données à l’emplacement spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-175">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span>

### <span data-ttu-id="1d42c-176">Exemple 8 : passer une entrée à une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-176">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="1d42c-177">Cet exemple utilise la `$input` variable Automatic pour traiter un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1d42c-177">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="1d42c-178">Utilisez `Receive-Job` pour afficher la sortie du travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-178">Use `Receive-Job` to view the job's output.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

<span data-ttu-id="1d42c-179">`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Content` avec la `$input` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="1d42c-179">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="1d42c-180">La `$input` variable récupère des objets à partir du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-180">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="1d42c-181">`Receive-Job` utilise le paramètre **Name** pour spécifier le travail et renvoie les résultats.</span><span class="sxs-lookup"><span data-stu-id="1d42c-181">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="1d42c-182">Le paramètre **Keep** enregistre la sortie du travail afin qu’il puisse être affiché à nouveau pendant la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d42c-182">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="1d42c-183">Exemple 9 : définir le répertoire de travail pour un travail en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="1d42c-183">Example 9: Set the working directory for a background job</span></span>

<span data-ttu-id="1d42c-184">Le **WorkingDirectory** vous permet de spécifier un autre répertoire pour un travail à partir duquel vous pouvez exécuter des scripts ou ouvrir des fichiers.</span><span class="sxs-lookup"><span data-stu-id="1d42c-184">The **WorkingDirectory** allows you to specify an alternate directory for a job from which you can run scripts or open files.</span></span> <span data-ttu-id="1d42c-185">Dans cet exemple, la tâche en arrière-plan spécifie un répertoire de travail différent de l’emplacement du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="1d42c-185">In this example, the background job specifies a working directory that's different than the current directory location.</span></span>

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

<span data-ttu-id="1d42c-186">Le répertoire de travail actuel de cet exemple est `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-186">This example's current working directory is `C:\Test`.</span></span> <span data-ttu-id="1d42c-187">`Start-Job` utilise le paramètre **WorkingDirectory** pour spécifier le répertoire de travail du travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-187">`Start-Job` uses the **WorkingDirectory** parameter to specify the job's working directory.</span></span> <span data-ttu-id="1d42c-188">Le paramètre **scriptblock** utilise `$PWD` pour afficher le répertoire de travail du travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-188">The **ScriptBlock** parameter uses `$PWD` to display the job's working directory.</span></span> <span data-ttu-id="1d42c-189">`Receive-Job` affiche la sortie de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-189">`Receive-Job` displays the background job's output.</span></span>
<span data-ttu-id="1d42c-190">**AutoRemoveJob** supprime la tâche et **attend** la suppression de l’invite de commandes jusqu’à ce que tous les résultats soient reçus.</span><span class="sxs-lookup"><span data-stu-id="1d42c-190">**AutoRemoveJob** deletes the job and **Wait** suppresses the command prompt until all results are received.</span></span>

### <span data-ttu-id="1d42c-191">Exemple 10 : utiliser le paramètre ArgumentList pour spécifier un tableau</span><span class="sxs-lookup"><span data-stu-id="1d42c-191">Example 10: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="1d42c-192">Cet exemple utilise le paramètre **argumentlist** pour spécifier un tableau d’arguments.</span><span class="sxs-lookup"><span data-stu-id="1d42c-192">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="1d42c-193">Le tableau est une liste séparée par des virgules de noms de processus.</span><span class="sxs-lookup"><span data-stu-id="1d42c-193">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="1d42c-194">L' `Start-Job` applet de commande utilise le paramètre **scriptblock** pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="1d42c-194">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="1d42c-195">`Get-Process` utilise le paramètre **Name** pour spécifier la variable automatique `$args` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-195">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="1d42c-196">Le paramètre **argumentlist** passe le tableau de noms de processus à `$args` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-196">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="1d42c-197">Les noms de processus PowerShell, pwsh et Notepad sont des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-197">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="1d42c-198">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d42c-198">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="1d42c-199">Par exemple, `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="1d42c-199">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="1d42c-200">Exemple 11 : exécuter un travail dans un Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="1d42c-200">Example 11: Run job in a Windows PowerShell 5.1</span></span>

<span data-ttu-id="1d42c-201">Cet exemple utilise le paramètre **psversion** avec la valeur **5,1** pour exécuter le travail dans une session Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="1d42c-201">This example uses the **PSVersion** parameter with value **5.1** to run job in a Windows PowerShell 5.1 session.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## <span data-ttu-id="1d42c-202">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d42c-202">PARAMETERS</span></span>

### <span data-ttu-id="1d42c-203">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="1d42c-203">-ArgumentList</span></span>

<span data-ttu-id="1d42c-204">Spécifie un tableau d’arguments ou de valeurs de paramètre pour le script spécifié par le paramètre **filePath** ou une commande spécifiée avec le paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-204">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="1d42c-205">Les arguments doivent être passés à **argumentlist** comme argument de tableau à une seule dimension.</span><span class="sxs-lookup"><span data-stu-id="1d42c-205">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="1d42c-206">Par exemple, une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1d42c-206">For example, a comma-separated list.</span></span> <span data-ttu-id="1d42c-207">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="1d42c-207">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-208">-Authentification</span><span class="sxs-lookup"><span data-stu-id="1d42c-208">-Authentication</span></span>

<span data-ttu-id="1d42c-209">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1d42c-209">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="1d42c-210">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d42c-210">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1d42c-211">Default</span><span class="sxs-lookup"><span data-stu-id="1d42c-211">Default</span></span>
- <span data-ttu-id="1d42c-212">Basic</span><span class="sxs-lookup"><span data-stu-id="1d42c-212">Basic</span></span>
- <span data-ttu-id="1d42c-213">CredSSP</span><span class="sxs-lookup"><span data-stu-id="1d42c-213">Credssp</span></span>
- <span data-ttu-id="1d42c-214">Digest</span><span class="sxs-lookup"><span data-stu-id="1d42c-214">Digest</span></span>
- <span data-ttu-id="1d42c-215">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1d42c-215">Kerberos</span></span>
- <span data-ttu-id="1d42c-216">Negotiate</span><span class="sxs-lookup"><span data-stu-id="1d42c-216">Negotiate</span></span>
- <span data-ttu-id="1d42c-217">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="1d42c-217">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="1d42c-218">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="1d42c-218">The default value is Default.</span></span>

<span data-ttu-id="1d42c-219">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="1d42c-219">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="1d42c-220">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="1d42c-220">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="1d42c-221">l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="1d42c-221">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="1d42c-222">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="1d42c-222">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="1d42c-223">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="1d42c-223">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-224">-Credential</span><span class="sxs-lookup"><span data-stu-id="1d42c-224">-Credential</span></span>

<span data-ttu-id="1d42c-225">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="1d42c-225">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="1d42c-226">Si le paramètre **Credential** n’est pas spécifié, la commande utilise les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="1d42c-226">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="1d42c-227">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-227">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1d42c-228">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="1d42c-228">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="1d42c-229">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="1d42c-229">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1d42c-230">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="1d42c-230">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-231">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="1d42c-231">-DefinitionName</span></span>

<span data-ttu-id="1d42c-232">Spécifie le nom de la définition du travail que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="1d42c-232">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="1d42c-233">Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un nom de définition, comme les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1d42c-233">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="1d42c-234">Lorsque vous utilisez `Start-Job` pour démarrer une instance d’une tâche planifiée, le travail démarre immédiatement, quels que soient les déclencheurs ou les options de travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-234">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="1d42c-235">L’instance de tâche qui en résulte est une tâche planifiée, mais elle n’est pas enregistrée sur le disque comme les tâches planifiées déclenchées.</span><span class="sxs-lookup"><span data-stu-id="1d42c-235">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="1d42c-236">Vous ne pouvez pas utiliser le paramètre **argumentlist** de `Start-Job` pour fournir des valeurs pour les paramètres de scripts qui s’exécutent dans une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="1d42c-236">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="1d42c-237">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1d42c-237">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1d42c-238">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="1d42c-238">-DefinitionPath</span></span>

<span data-ttu-id="1d42c-239">Spécifie le chemin d’accès de la définition du travail que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="1d42c-239">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="1d42c-240">Entrez le chemin d'accès à la définition.</span><span class="sxs-lookup"><span data-stu-id="1d42c-240">Enter the definition path.</span></span> <span data-ttu-id="1d42c-241">La concaténation des valeurs des paramètres **DefinitionPath** et **DefinitionName** est le chemin d’accès complet de la définition du travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-241">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="1d42c-242">Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un chemin d'accès de définition, comme les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="1d42c-242">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="1d42c-243">Pour les tâches planifiées, la valeur du paramètre **DefinitionPath** est `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-243">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="1d42c-244">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1d42c-244">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-245">-FilePath</span><span class="sxs-lookup"><span data-stu-id="1d42c-245">-FilePath</span></span>

<span data-ttu-id="1d42c-246">Spécifie un script local qui `Start-Job` s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-246">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="1d42c-247">Entrez le chemin d’accès et le nom de fichier du script ou utilisez le pipeline pour lui envoyer un chemin d’accès de script `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-247">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="1d42c-248">Le script doit se trouver sur l’ordinateur local ou dans un dossier accessible à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-248">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="1d42c-249">Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script et exécute le bloc de script en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-249">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-250">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="1d42c-250">-InitializationScript</span></span>

<span data-ttu-id="1d42c-251">Spécifie les commandes à exécuter avant le début de la tâche.</span><span class="sxs-lookup"><span data-stu-id="1d42c-251">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="1d42c-252">Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="1d42c-252">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="1d42c-253">Utilisez ce paramètre pour préparer la session dans laquelle la tâche s'exécute.</span><span class="sxs-lookup"><span data-stu-id="1d42c-253">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="1d42c-254">Par exemple, vous pouvez l'utiliser pour ajouter des fonctions, des composants logiciels enfichables et des modules à la session.</span><span class="sxs-lookup"><span data-stu-id="1d42c-254">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-255">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1d42c-255">-InputObject</span></span>

<span data-ttu-id="1d42c-256">Spécifie l'entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="1d42c-256">Specifies input to the command.</span></span> <span data-ttu-id="1d42c-257">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui génère ces objets.</span><span class="sxs-lookup"><span data-stu-id="1d42c-257">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="1d42c-258">Dans la valeur du paramètre **scriptblock** , utilisez la `$input` variable Automatic pour représenter les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1d42c-258">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-259">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1d42c-259">-LiteralPath</span></span>

<span data-ttu-id="1d42c-260">Spécifie un script local que cette applet de commande exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-260">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="1d42c-261">Entrez le chemin d’accès d’un script sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1d42c-261">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="1d42c-262">`Start-Job` utilise la valeur du paramètre **LiteralPath** exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="1d42c-262">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="1d42c-263">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1d42c-263">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="1d42c-264">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="1d42c-264">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1d42c-265">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="1d42c-265">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-266">-Name</span><span class="sxs-lookup"><span data-stu-id="1d42c-266">-Name</span></span>

<span data-ttu-id="1d42c-267">Spécifie le nom convivial de la nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="1d42c-267">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="1d42c-268">Vous pouvez utiliser le nom pour identifier le travail à d’autres applets de commande de tâche, telles que l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-268">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="1d42c-269">Le nom convivial par défaut est `Job#` , où `#` est un nombre ordinal qui est incrémenté pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="1d42c-269">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-270">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="1d42c-270">-PSVersion</span></span>

<span data-ttu-id="1d42c-271">Spécifie une version de PowerShell à utiliser pour exécuter le travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-271">Specifies a version of PowerShell to use for running the job.</span></span>
<span data-ttu-id="1d42c-272">Lorsque la valeur de **psversion** est **5,1** , le travail est exécuté dans une session Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="1d42c-272">When the value of **PSVersion** is **5.1** The job is run in a Windows PowerShell 5.1 session.</span></span>
<span data-ttu-id="1d42c-273">Pour toute autre valeur, la tâche est exécutée à l’aide de la version actuelle de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d42c-273">For any other value, the job is run using the current version of PowerShell.</span></span>

<span data-ttu-id="1d42c-274">Ce paramètre a été ajouté dans PowerShell 7 et fonctionne uniquement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="1d42c-274">This parameter was added in PowerShell 7 and only works on Windows.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-275">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="1d42c-275">-RunAs32</span></span>

<span data-ttu-id="1d42c-276">À partir de PowerShell 7, le paramètre **RunAs32** ne fonctionne pas sur PowerShell 64 bits ( `pwsh` ).</span><span class="sxs-lookup"><span data-stu-id="1d42c-276">Beginning with PowerShell 7, the **RunAs32** parameter doesn't work on 64-bit PowerShell (`pwsh`).</span></span>
<span data-ttu-id="1d42c-277">Si **RunAs32** est spécifié dans PowerShell 64 bits, `Start-Job` lève une erreur d’exception d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="1d42c-277">If **RunAs32** is specified in 64-bit PowerShell, `Start-Job` throws a terminating exception error.</span></span>
<span data-ttu-id="1d42c-278">Pour démarrer un processus PowerShell 32 bits ( `pwsh` ) avec **RunAs32**, le PowerShell 32 bits doit être installé.</span><span class="sxs-lookup"><span data-stu-id="1d42c-278">To start a 32-bit PowerShell (`pwsh`) process with **RunAs32**, you need to have the 32-bit PowerShell installed.</span></span>

<span data-ttu-id="1d42c-279">Dans PowerShell 32 bits, **RunAs32** force la tâche à s’exécuter dans un processus 32 bits, même sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1d42c-279">In 32-bit PowerShell, **RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="1d42c-280">Sur les versions 64 bits de Windows 7 et Windows Server 2008 R2, lorsque la `Start-Job` commande comprend le paramètre **RunAs32** , vous ne pouvez pas utiliser le paramètre **Credential** pour spécifier les informations d’identification d’un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1d42c-280">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-281">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="1d42c-281">-ScriptBlock</span></span>

<span data-ttu-id="1d42c-282">Spécifie les commandes à exécuter dans la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-282">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="1d42c-283">Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="1d42c-283">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="1d42c-284">Utilisez la `$input` variable Automatic pour accéder à la valeur du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-284">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="1d42c-285">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1d42c-285">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-286">-Type</span><span class="sxs-lookup"><span data-stu-id="1d42c-286">-Type</span></span>

<span data-ttu-id="1d42c-287">Spécifie le type personnalisé pour les travaux démarrés par `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-287">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="1d42c-288">Entrez un nom de type de tâche personnalisé, par exemple, PSScheduledJob pour les tâches planifiées ou PSWorkflowJob pour les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="1d42c-288">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="1d42c-289">Ce paramètre n’est pas valide pour les travaux en arrière-plan standard.</span><span class="sxs-lookup"><span data-stu-id="1d42c-289">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="1d42c-290">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1d42c-290">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-291">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="1d42c-291">-WorkingDirectory</span></span>

<span data-ttu-id="1d42c-292">Spécifie le répertoire de travail initial du travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1d42c-292">Specifies the initial working directory of the background job.</span></span> <span data-ttu-id="1d42c-293">Si le paramètre n’est pas spécifié, la tâche est exécutée à partir de l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="1d42c-293">If the parameter isn't specified, the job runs from the default location.</span></span> <span data-ttu-id="1d42c-294">L’emplacement par défaut est le répertoire de travail actuel de l’appelant qui a démarré le travail.</span><span class="sxs-lookup"><span data-stu-id="1d42c-294">The default location is the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="1d42c-295">Ce paramètre a été introduit dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="1d42c-295">This parameter was introduced in PowerShell 7.</span></span>

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d42c-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d42c-296">CommonParameters</span></span>

<span data-ttu-id="1d42c-297">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1d42c-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d42c-298">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1d42c-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d42c-299">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1d42c-299">INPUTS</span></span>

### <span data-ttu-id="1d42c-300">System.String</span><span class="sxs-lookup"><span data-stu-id="1d42c-300">System.String</span></span>

<span data-ttu-id="1d42c-301">Vous pouvez utiliser le pipeline pour envoyer un objet avec la propriété **Name** au paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="1d42c-301">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="1d42c-302">Par exemple, vous pouvez effectuer un pipeline d’un objet **FileInfo** de `Get-ChildItem` à `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1d42c-302">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="1d42c-303">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1d42c-303">OUTPUTS</span></span>

### <span data-ttu-id="1d42c-304">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="1d42c-304">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="1d42c-305">`Start-Job` retourne un objet **PSRemotingJob** qui représente le travail qu’il a démarré.</span><span class="sxs-lookup"><span data-stu-id="1d42c-305">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="1d42c-306">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1d42c-306">NOTES</span></span>

<span data-ttu-id="1d42c-307">Pour s’exécuter en arrière-plan, `Start-Job` s’exécute dans sa propre session dans la session active.</span><span class="sxs-lookup"><span data-stu-id="1d42c-307">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="1d42c-308">Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande dans une session sur un ordinateur distant, `Start-Job` s’exécute dans une session de la session à distance.</span><span class="sxs-lookup"><span data-stu-id="1d42c-308">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="1d42c-309">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1d42c-309">RELATED LINKS</span></span>

[<span data-ttu-id="1d42c-310">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="1d42c-310">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="1d42c-311">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1d42c-311">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="1d42c-312">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="1d42c-312">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="1d42c-313">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="1d42c-313">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="1d42c-314">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="1d42c-314">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="1d42c-315">Get-Job</span><span class="sxs-lookup"><span data-stu-id="1d42c-315">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="1d42c-316">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1d42c-316">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="1d42c-317">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="1d42c-317">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="1d42c-318">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="1d42c-318">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="1d42c-319">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="1d42c-319">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="1d42c-320">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="1d42c-320">Wait-Job</span></span>](Wait-Job.md)
