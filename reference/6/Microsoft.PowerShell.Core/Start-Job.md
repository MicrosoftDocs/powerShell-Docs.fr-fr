---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 69cebe735e413b226bd40539df075bf3a49bce95
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204869"
---
# <span data-ttu-id="eb7e2-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="eb7e2-103">Start-Job</span></span>

## <span data-ttu-id="eb7e2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="eb7e2-104">SYNOPSIS</span></span>
<span data-ttu-id="eb7e2-105">Démarre une tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="eb7e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eb7e2-106">SYNTAX</span></span>

### <span data-ttu-id="eb7e2-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="eb7e2-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="eb7e2-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="eb7e2-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="eb7e2-109">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="eb7e2-109">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="eb7e2-110">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="eb7e2-110">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="eb7e2-111">Description</span><span class="sxs-lookup"><span data-stu-id="eb7e2-111">DESCRIPTION</span></span>

<span data-ttu-id="eb7e2-112">L' `Start-Job` applet de commande démarre une tâche en arrière-plan PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="eb7e2-113">Une tâche en arrière-plan PowerShell exécute une commande sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="eb7e2-114">Lorsque vous démarrez une tâche en arrière-plan, un objet de tâche est retourné immédiatement, même si le travail prend une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="eb7e2-115">Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="eb7e2-116">L’objet de traitement contient des informations utiles sur le travail, mais il ne contient pas les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="eb7e2-117">Une fois le travail terminé, utilisez l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="eb7e2-118">Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="eb7e2-119">Pour exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez le paramètre **AsJob** qui est disponible sur de nombreuses applets de commande, ou utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="eb7e2-120">Pour plus d’informations, consultez [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="eb7e2-121">À compter de PowerShell 3,0, `Start-Job` peut démarrer des instances de types de tâches personnalisées, telles que les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="eb7e2-122">Pour plus d’informations sur l’utilisation `Start-Job` de pour démarrer des travaux avec des types personnalisés, consultez les documents d’aide pour la fonctionnalité de type de tâche.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="eb7e2-123">À compter de PowerShell 6,0, vous pouvez démarrer des travaux à l’aide de l' `&` opérateur d’arrière-plan esperluette ().</span><span class="sxs-lookup"><span data-stu-id="eb7e2-123">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="eb7e2-124">Les fonctionnalités de l’opérateur d’arrière-plan sont similaires à celles de `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-124">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="eb7e2-125">Les deux méthodes pour démarrer un travail créent un objet de tâche **PSRemotingJob** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-125">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="eb7e2-126">Pour plus d’informations sur l’utilisation de l’esperluette ( `&` ), consultez [about_Operators](./about/about_operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-126">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="eb7e2-127">Le répertoire de travail par défaut pour les travaux est codé en dur.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-127">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="eb7e2-128">La valeur par défaut `$HOME\Documents` de Windows est et sur Linux ou MacOS, la valeur par défaut est `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-128">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="eb7e2-129">Le code de script qui s’exécute dans la tâche en arrière-plan doit gérer le répertoire de travail en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-129">The script code running in the background job needs to manage the working directory as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="eb7e2-130">La création d’un travail en arrière-plan out-of-process avec `Start-Job` n’est pas prise en charge dans le scénario où PowerShell est hébergé dans d’autres applications, telles que les Azure Functions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-130">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="eb7e2-131">Cela est lié à la conception, car `Start-Job` dépend du `pwsh` fichier exécutable à utiliser `$PSHOME` pour démarrer un travail en arrière-plan out-of-process, mais quand une application héberge PowerShell, elle utilise directement les packages du kit SDK NuGet PowerShell et n’est pas `pwsh` livrée avec.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-131">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="eb7e2-132">Le substitut dans ce scénario provient du `Start-ThreadJob` module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-132">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)** .</span></span>

## <span data-ttu-id="eb7e2-133">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="eb7e2-133">EXAMPLES</span></span>

### <span data-ttu-id="eb7e2-134">Exemple 1 : démarrer une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="eb7e2-134">Example 1: Start a background job</span></span>

<span data-ttu-id="eb7e2-135">Cet exemple démarre une tâche en arrière-plan qui s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-135">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="eb7e2-136">`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Process` en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-136">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="eb7e2-137">Le paramètre **Name** spécifie de rechercher les processus PowerShell, `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-137">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="eb7e2-138">Les informations sur le travail s’affichent et PowerShell retourne à une invite pendant l’exécution de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-138">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="eb7e2-139">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-139">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="eb7e2-140">Par exemple : `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-140">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="eb7e2-141">Exemple 2 : utiliser l’opérateur d’arrière-plan pour démarrer une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="eb7e2-141">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="eb7e2-142">Cet exemple utilise l' `&` opérateur d’arrière-plan esperluette () pour démarrer une tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-142">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="eb7e2-143">Le travail obtient le même résultat que `Start-Job` dans l’exemple 1.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-143">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="eb7e2-144">`Get-Process` utilise le paramètre **Name** pour spécifier les processus PowerShell `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-144">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="eb7e2-145">La esperluette ( `&` ) exécute la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-145">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="eb7e2-146">Les informations sur le travail s’affichent et PowerShell retourne à une invite pendant l’exécution de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-146">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="eb7e2-147">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-147">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="eb7e2-148">Par exemple : `Receive-Job -Id 5`.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-148">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="eb7e2-149">Exemple 3 : démarrer un travail à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="eb7e2-149">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="eb7e2-150">Cet exemple exécute un travail sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-150">This example runs a job on multiple computers.</span></span> <span data-ttu-id="eb7e2-151">Le travail est stocké dans une variable et est exécuté à l’aide du nom de variable sur la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-151">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="eb7e2-152">Un travail qui utilise `Invoke-Command` est créé et stocké dans la `$jobWRM` variable.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-152">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="eb7e2-153">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier les ordinateurs sur lesquels le travail s’exécute.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-153">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="eb7e2-154">`Get-Content` Obtient les noms de serveur à partir du `C:\Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-154">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="eb7e2-155">Le paramètre **scriptblock** spécifie une commande qui `Get-Service` obtient le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-155">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="eb7e2-156">Le paramètre **JobName** spécifie un nom convivial pour le travail, **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-156">The **JobName** parameter specifies a friendly name for the job, **WinRM** .</span></span> <span data-ttu-id="eb7e2-157">Le paramètre **ThrottleLimit** limite le nombre de commandes simultanées à 16.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-157">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="eb7e2-158">Le paramètre **AsJob** démarre une tâche en arrière-plan qui exécute la commande sur les serveurs.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-158">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="eb7e2-159">Exemple 4 : récupérer des informations sur le travail</span><span class="sxs-lookup"><span data-stu-id="eb7e2-159">Example 4: Get job information</span></span>

<span data-ttu-id="eb7e2-160">Cet exemple obtient des informations sur un travail et affiche les résultats d’une tâche terminée qui a été exécutée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-160">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="eb7e2-161">`Start-Job` utilise le paramètre **scriptblock** pour exécuter une commande qui spécifie `Get-WinEvent` d’obtenir le journal **système** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-161">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="eb7e2-162">Le paramètre **Credential** spécifie un compte d’utilisateur de domaine autorisé à exécuter la tâche sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-162">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="eb7e2-163">L’objet de traitement est stocké dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-163">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="eb7e2-164">L’objet dans la `$j` variable est envoyé dans le pipeline à `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-164">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="eb7e2-165">Le paramètre **Property** spécifie un astérisque ( `*` ) pour afficher toutes les propriétés de l’objet de tâche.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-165">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="eb7e2-166">Exemple 5 : exécuter un script en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="eb7e2-166">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="eb7e2-167">Dans cet exemple, un script sur l’ordinateur local est exécuté en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-167">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="eb7e2-168">`Start-Job` utilise le paramètre **filePath** pour spécifier un fichier de script stocké sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-168">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="eb7e2-169">Exemple 6 : obtenir un processus à l’aide d’un travail en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="eb7e2-169">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="eb7e2-170">Cet exemple utilise une tâche en arrière-plan pour obtenir un processus spécifié par son nom.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-170">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="eb7e2-171">`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **PShellJob** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-171">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob** .</span></span> <span data-ttu-id="eb7e2-172">Le paramètre **scriptblock** spécifie `Get-Process` d’extraire les processus avec le nom **PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-172">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell** .</span></span>

### <span data-ttu-id="eb7e2-173">Exemple 7 : collecter et enregistrer des données à l’aide d’une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="eb7e2-173">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="eb7e2-174">Cet exemple démarre un travail qui collecte une grande quantité de données cartographiques, puis l’enregistre dans un `.tif` fichier.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-174">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="eb7e2-175">`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **GetMappingFiles** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-175">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles** .</span></span> <span data-ttu-id="eb7e2-176">Le paramètre **initializationScript** exécute un bloc de script qui importe le module **MapFunctions** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-176">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="eb7e2-177">Le paramètre **scriptblock** s’exécute `Get-Map` et `Set-Content` enregistre les données à l’emplacement spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-177">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="eb7e2-178">Le paramètre **RunAs32** exécute le processus comme 32 bits, même sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-178">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="eb7e2-179">Exemple 8 : passer une entrée à une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="eb7e2-179">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="eb7e2-180">Cet exemple utilise la `$input` variable Automatic pour traiter un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-180">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="eb7e2-181">Utilisez `Receive-Job` pour afficher la sortie du travail.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-181">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="eb7e2-182">`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Content` avec la `$input` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-182">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="eb7e2-183">La `$input` variable récupère des objets à partir du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-183">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="eb7e2-184">`Receive-Job` utilise le paramètre **Name** pour spécifier le travail et renvoie les résultats.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-184">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="eb7e2-185">Le paramètre **Keep** enregistre la sortie du travail afin qu’il puisse être affiché à nouveau pendant la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-185">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="eb7e2-186">Exemple 9 : utiliser le paramètre ArgumentList pour spécifier un tableau</span><span class="sxs-lookup"><span data-stu-id="eb7e2-186">Example 9: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="eb7e2-187">Cet exemple utilise le paramètre **argumentlist** pour spécifier un tableau d’arguments.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-187">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="eb7e2-188">Le tableau est une liste séparée par des virgules de noms de processus.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-188">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="eb7e2-189">L' `Start-Job` applet de commande utilise le paramètre **scriptblock** pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-189">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="eb7e2-190">`Get-Process` utilise le paramètre **Name** pour spécifier la variable automatique `$args` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-190">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="eb7e2-191">Le paramètre **argumentlist** passe le tableau de noms de processus à `$args` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-191">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="eb7e2-192">Les noms de processus PowerShell, pwsh et Notepad sont des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-192">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="eb7e2-193">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-193">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="eb7e2-194">Par exemple : `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-194">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="eb7e2-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eb7e2-195">PARAMETERS</span></span>

### <span data-ttu-id="eb7e2-196">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="eb7e2-196">-ArgumentList</span></span>

<span data-ttu-id="eb7e2-197">Spécifie un tableau d’arguments ou de valeurs de paramètre pour le script spécifié par le paramètre **filePath** ou une commande spécifiée avec le paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-197">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="eb7e2-198">Les arguments doivent être passés à **argumentlist** comme argument de tableau à une seule dimension.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-198">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="eb7e2-199">Par exemple, une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-199">For example, a comma-separated list.</span></span> <span data-ttu-id="eb7e2-200">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-200">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="eb7e2-201">-Authentification</span><span class="sxs-lookup"><span data-stu-id="eb7e2-201">-Authentication</span></span>

<span data-ttu-id="eb7e2-202">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-202">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="eb7e2-203">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb7e2-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="eb7e2-204">Default</span><span class="sxs-lookup"><span data-stu-id="eb7e2-204">Default</span></span>
- <span data-ttu-id="eb7e2-205">Basic</span><span class="sxs-lookup"><span data-stu-id="eb7e2-205">Basic</span></span>
- <span data-ttu-id="eb7e2-206">CredSSP</span><span class="sxs-lookup"><span data-stu-id="eb7e2-206">Credssp</span></span>
- <span data-ttu-id="eb7e2-207">Digest</span><span class="sxs-lookup"><span data-stu-id="eb7e2-207">Digest</span></span>
- <span data-ttu-id="eb7e2-208">Kerberos</span><span class="sxs-lookup"><span data-stu-id="eb7e2-208">Kerberos</span></span>
- <span data-ttu-id="eb7e2-209">Negotiate</span><span class="sxs-lookup"><span data-stu-id="eb7e2-209">Negotiate</span></span>
- <span data-ttu-id="eb7e2-210">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="eb7e2-210">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="eb7e2-211">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-211">The default value is Default.</span></span>

<span data-ttu-id="eb7e2-212">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-212">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="eb7e2-213">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-213">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="eb7e2-214">l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-214">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="eb7e2-215">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-215">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="eb7e2-216">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-216">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="eb7e2-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="eb7e2-217">-Credential</span></span>

<span data-ttu-id="eb7e2-218">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-218">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="eb7e2-219">Si le paramètre **Credential** n’est pas spécifié, la commande utilise les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-219">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="eb7e2-220">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-220">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="eb7e2-221">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-221">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="eb7e2-222">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-222">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="eb7e2-223">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-223">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="eb7e2-224">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="eb7e2-224">-DefinitionName</span></span>

<span data-ttu-id="eb7e2-225">Spécifie le nom de la définition du travail que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-225">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="eb7e2-226">Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un nom de définition, comme les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-226">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="eb7e2-227">Lorsque vous utilisez `Start-Job` pour démarrer une instance d’une tâche planifiée, le travail démarre immédiatement, quels que soient les déclencheurs ou les options de travail.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-227">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="eb7e2-228">L’instance de tâche qui en résulte est une tâche planifiée, mais elle n’est pas enregistrée sur le disque comme les tâches planifiées déclenchées.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-228">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="eb7e2-229">Vous ne pouvez pas utiliser le paramètre **argumentlist** de `Start-Job` pour fournir des valeurs pour les paramètres de scripts qui s’exécutent dans une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-229">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="eb7e2-230">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-230">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="eb7e2-231">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="eb7e2-231">-DefinitionPath</span></span>

<span data-ttu-id="eb7e2-232">Spécifie le chemin d’accès de la définition du travail que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-232">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="eb7e2-233">Entrez le chemin d'accès à la définition.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-233">Enter the definition path.</span></span> <span data-ttu-id="eb7e2-234">La concaténation des valeurs des paramètres **DefinitionPath** et **DefinitionName** est le chemin d’accès complet de la définition du travail.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-234">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="eb7e2-235">Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un chemin d'accès de définition, comme les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-235">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="eb7e2-236">Pour les tâches planifiées, la valeur du paramètre **DefinitionPath** est `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-236">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="eb7e2-237">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-237">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="eb7e2-238">-FilePath</span><span class="sxs-lookup"><span data-stu-id="eb7e2-238">-FilePath</span></span>

<span data-ttu-id="eb7e2-239">Spécifie un script local qui `Start-Job` s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-239">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="eb7e2-240">Entrez le chemin d’accès et le nom de fichier du script ou utilisez le pipeline pour lui envoyer un chemin d’accès de script `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-240">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="eb7e2-241">Le script doit se trouver sur l’ordinateur local ou dans un dossier accessible à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-241">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="eb7e2-242">Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script et exécute le bloc de script en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-242">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="eb7e2-243">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="eb7e2-243">-InitializationScript</span></span>

<span data-ttu-id="eb7e2-244">Spécifie les commandes à exécuter avant le début de la tâche.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-244">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="eb7e2-245">Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-245">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="eb7e2-246">Utilisez ce paramètre pour préparer la session dans laquelle la tâche s'exécute.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-246">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="eb7e2-247">Par exemple, vous pouvez l'utiliser pour ajouter des fonctions, des composants logiciels enfichables et des modules à la session.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-247">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

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

### <span data-ttu-id="eb7e2-248">-InputObject</span><span class="sxs-lookup"><span data-stu-id="eb7e2-248">-InputObject</span></span>

<span data-ttu-id="eb7e2-249">Spécifie l'entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-249">Specifies input to the command.</span></span> <span data-ttu-id="eb7e2-250">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui génère ces objets.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-250">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="eb7e2-251">Dans la valeur du paramètre **scriptblock** , utilisez la `$input` variable Automatic pour représenter les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-251">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

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

### <span data-ttu-id="eb7e2-252">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="eb7e2-252">-LiteralPath</span></span>

<span data-ttu-id="eb7e2-253">Spécifie un script local que cette applet de commande exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-253">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="eb7e2-254">Entrez le chemin d’accès d’un script sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-254">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="eb7e2-255">`Start-Job` utilise la valeur du paramètre **LiteralPath** exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-255">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="eb7e2-256">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-256">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="eb7e2-257">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-257">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="eb7e2-258">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-258">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="eb7e2-259">-Name</span><span class="sxs-lookup"><span data-stu-id="eb7e2-259">-Name</span></span>

<span data-ttu-id="eb7e2-260">Spécifie le nom convivial de la nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-260">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="eb7e2-261">Vous pouvez utiliser le nom pour identifier le travail à d’autres applets de commande de tâche, telles que l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-261">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="eb7e2-262">Le nom convivial par défaut est `Job#` , où `#` est un nombre ordinal qui est incrémenté pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-262">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

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

### <span data-ttu-id="eb7e2-263">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="eb7e2-263">-PSVersion</span></span>

<span data-ttu-id="eb7e2-264">Spécifie une version.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-264">Specifies a version.</span></span> <span data-ttu-id="eb7e2-265">`Start-Job` exécute la tâche avec la version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-265">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="eb7e2-266">Les valeurs acceptables pour ce paramètre sont les suivantes : `2.0` et `3.0` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-266">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="eb7e2-267">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-267">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="eb7e2-268">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="eb7e2-268">-RunAs32</span></span>

<span data-ttu-id="eb7e2-269">Indique que `Start-Job` exécute la tâche dans un processus 32 bits.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-269">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="eb7e2-270">**RunAs32** force la tâche à s’exécuter dans un processus 32 bits, même sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-270">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="eb7e2-271">Sur les versions 64 bits de Windows 7 et Windows Server 2008 R2, lorsque la `Start-Job` commande comprend le paramètre **RunAs32** , vous ne pouvez pas utiliser le paramètre **Credential** pour spécifier les informations d’identification d’un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-271">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

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

### <span data-ttu-id="eb7e2-272">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="eb7e2-272">-ScriptBlock</span></span>

<span data-ttu-id="eb7e2-273">Spécifie les commandes à exécuter dans la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-273">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="eb7e2-274">Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-274">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="eb7e2-275">Utilisez la `$input` variable Automatic pour accéder à la valeur du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-275">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="eb7e2-276">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-276">This parameter is required.</span></span>

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

### <span data-ttu-id="eb7e2-277">-Type</span><span class="sxs-lookup"><span data-stu-id="eb7e2-277">-Type</span></span>

<span data-ttu-id="eb7e2-278">Spécifie le type personnalisé pour les travaux démarrés par `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-278">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="eb7e2-279">Entrez un nom de type de tâche personnalisé, par exemple, PSScheduledJob pour les tâches planifiées ou PSWorkflowJob pour les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-279">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="eb7e2-280">Ce paramètre n’est pas valide pour les travaux en arrière-plan standard.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-280">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="eb7e2-281">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-281">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="eb7e2-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eb7e2-282">CommonParameters</span></span>

<span data-ttu-id="eb7e2-283">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eb7e2-284">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eb7e2-285">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="eb7e2-285">INPUTS</span></span>

### <span data-ttu-id="eb7e2-286">System.String</span><span class="sxs-lookup"><span data-stu-id="eb7e2-286">System.String</span></span>

<span data-ttu-id="eb7e2-287">Vous pouvez utiliser le pipeline pour envoyer un objet avec la propriété **Name** au paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-287">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="eb7e2-288">Par exemple, vous pouvez effectuer un pipeline d’un objet **FileInfo** de `Get-ChildItem` à `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-288">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="eb7e2-289">SORTIES</span><span class="sxs-lookup"><span data-stu-id="eb7e2-289">OUTPUTS</span></span>

### <span data-ttu-id="eb7e2-290">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="eb7e2-290">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="eb7e2-291">`Start-Job` retourne un objet **PSRemotingJob** qui représente le travail qu’il a démarré.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-291">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="eb7e2-292">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="eb7e2-292">NOTES</span></span>

<span data-ttu-id="eb7e2-293">Pour s’exécuter en arrière-plan, `Start-Job` s’exécute dans sa propre session dans la session active.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-293">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="eb7e2-294">Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande dans une session sur un ordinateur distant, `Start-Job` s’exécute dans une session de la session à distance.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-294">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="eb7e2-295">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="eb7e2-295">RELATED LINKS</span></span>

[<span data-ttu-id="eb7e2-296">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="eb7e2-296">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="eb7e2-297">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="eb7e2-297">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="eb7e2-298">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="eb7e2-298">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="eb7e2-299">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="eb7e2-299">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="eb7e2-300">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="eb7e2-300">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="eb7e2-301">Get-Job</span><span class="sxs-lookup"><span data-stu-id="eb7e2-301">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="eb7e2-302">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="eb7e2-302">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="eb7e2-303">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="eb7e2-303">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="eb7e2-304">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="eb7e2-304">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="eb7e2-305">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="eb7e2-305">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="eb7e2-306">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="eb7e2-306">Wait-Job</span></span>](Wait-Job.md)
