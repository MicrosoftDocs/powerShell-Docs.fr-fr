---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202654"
---
# <span data-ttu-id="846d4-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-103">Start-Job</span></span>

## <span data-ttu-id="846d4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="846d4-104">SYNOPSIS</span></span>
<span data-ttu-id="846d4-105">Démarre une tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="846d4-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="846d4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="846d4-106">SYNTAX</span></span>

### <span data-ttu-id="846d4-107">ComputerName (par défaut)</span><span class="sxs-lookup"><span data-stu-id="846d4-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="846d4-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="846d4-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="846d4-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="846d4-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="846d4-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="846d4-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="846d4-111">Description</span><span class="sxs-lookup"><span data-stu-id="846d4-111">DESCRIPTION</span></span>

<span data-ttu-id="846d4-112">L' `Start-Job` applet de commande démarre une tâche en arrière-plan PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="846d4-113">Une tâche en arrière-plan PowerShell exécute une commande sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="846d4-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="846d4-114">Lorsque vous démarrez une tâche en arrière-plan, un objet de tâche est retourné immédiatement, même si le travail prend une durée prolongée.</span><span class="sxs-lookup"><span data-stu-id="846d4-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="846d4-115">Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="846d4-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="846d4-116">L’objet de traitement contient des informations utiles sur le travail, mais il ne contient pas les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="846d4-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="846d4-117">Une fois le travail terminé, utilisez l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="846d4-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="846d4-118">Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="846d4-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="846d4-119">Pour exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez le paramètre **AsJob** qui est disponible sur de nombreuses applets de commande, ou utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="846d4-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="846d4-120">Pour plus d’informations, consultez [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="846d4-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="846d4-121">À compter de PowerShell 3,0, `Start-Job` peut démarrer des instances de types de tâches personnalisées, telles que les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="846d4-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="846d4-122">Pour plus d’informations sur l’utilisation `Start-Job` de pour démarrer des travaux avec des types personnalisés, consultez les documents d’aide pour la fonctionnalité de type de tâche.</span><span class="sxs-lookup"><span data-stu-id="846d4-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="846d4-123">Le répertoire de travail par défaut pour les travaux est codé en dur.</span><span class="sxs-lookup"><span data-stu-id="846d4-123">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="846d4-124">La valeur par défaut `$HOME\Documents` de Windows est et sur Linux ou MacOS, la valeur par défaut est `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="846d4-124">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="846d4-125">Le code de script qui s’exécute dans la tâche en arrière-plan doit gérer le répertoire de travail en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="846d4-125">The script code running in the background job needs to manage the working directory as needed.</span></span>

## <span data-ttu-id="846d4-126">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="846d4-126">EXAMPLES</span></span>

### <span data-ttu-id="846d4-127">Exemple 1 : démarrer une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="846d4-127">Example 1: Start a background job</span></span>

<span data-ttu-id="846d4-128">Cet exemple démarre une tâche en arrière-plan qui s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-128">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

<span data-ttu-id="846d4-129">`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Process` en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-129">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="846d4-130">Le paramètre **Name** spécifie de rechercher les processus PowerShell, `powershell` .</span><span class="sxs-lookup"><span data-stu-id="846d4-130">The **Name** parameter specifies to find PowerShell processes, `powershell`.</span></span> <span data-ttu-id="846d4-131">Les informations sur le travail s’affichent et PowerShell retourne à une invite pendant l’exécution de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-131">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="846d4-132">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="846d4-132">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="846d4-133">Par exemple : `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="846d4-133">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="846d4-134">Exemple 2 : démarrer un travail à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="846d4-134">Example 2: Start a job using Invoke-Command</span></span>

<span data-ttu-id="846d4-135">Cet exemple exécute un travail sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="846d4-135">This example runs a job on multiple computers.</span></span> <span data-ttu-id="846d4-136">Le travail est stocké dans une variable et est exécuté à l’aide du nom de variable sur la ligne de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="846d4-136">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="846d4-137">Un travail qui utilise `Invoke-Command` est créé et stocké dans la `$jobWRM` variable.</span><span class="sxs-lookup"><span data-stu-id="846d4-137">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="846d4-138">`Invoke-Command` utilise le paramètre **ComputerName** pour spécifier les ordinateurs sur lesquels le travail s’exécute.</span><span class="sxs-lookup"><span data-stu-id="846d4-138">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="846d4-139">`Get-Content` Obtient les noms de serveur à partir du `C:\Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="846d4-139">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="846d4-140">Le paramètre **scriptblock** spécifie une commande qui `Get-Service` obtient le service **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="846d4-140">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="846d4-141">Le paramètre **JobName** spécifie un nom convivial pour le travail, **WinRM** .</span><span class="sxs-lookup"><span data-stu-id="846d4-141">The **JobName** parameter specifies a friendly name for the job, **WinRM** .</span></span> <span data-ttu-id="846d4-142">Le paramètre **ThrottleLimit** limite le nombre de commandes simultanées à 16.</span><span class="sxs-lookup"><span data-stu-id="846d4-142">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="846d4-143">Le paramètre **AsJob** démarre une tâche en arrière-plan qui exécute la commande sur les serveurs.</span><span class="sxs-lookup"><span data-stu-id="846d4-143">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="846d4-144">Exemple 3 : récupérer des informations sur un travail</span><span class="sxs-lookup"><span data-stu-id="846d4-144">Example 3: Get job information</span></span>

<span data-ttu-id="846d4-145">Cet exemple obtient des informations sur un travail et affiche les résultats d’une tâche terminée qui a été exécutée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-145">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="846d4-146">`Start-Job` utilise le paramètre **scriptblock** pour exécuter une commande qui spécifie `Get-WinEvent` d’obtenir le journal **système** .</span><span class="sxs-lookup"><span data-stu-id="846d4-146">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="846d4-147">Le paramètre **Credential** spécifie un compte d’utilisateur de domaine autorisé à exécuter la tâche sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="846d4-147">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="846d4-148">L’objet de traitement est stocké dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="846d4-148">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="846d4-149">L’objet dans la `$j` variable est envoyé dans le pipeline à `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="846d4-149">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="846d4-150">Le paramètre **Property** spécifie un astérisque ( `*` ) pour afficher toutes les propriétés de l’objet de tâche.</span><span class="sxs-lookup"><span data-stu-id="846d4-150">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="846d4-151">Exemple 4 : exécuter un script en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="846d4-151">Example 4: Run a script as a background job</span></span>

<span data-ttu-id="846d4-152">Dans cet exemple, un script sur l’ordinateur local est exécuté en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-152">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="846d4-153">`Start-Job` utilise le paramètre **filePath** pour spécifier un fichier de script stocké sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-153">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="846d4-154">Exemple 5 : obtenir un processus à l’aide d’une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="846d4-154">Example 5: Get a process using a background job</span></span>

<span data-ttu-id="846d4-155">Cet exemple utilise une tâche en arrière-plan pour obtenir un processus spécifié par son nom.</span><span class="sxs-lookup"><span data-stu-id="846d4-155">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="846d4-156">`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **PShellJob** .</span><span class="sxs-lookup"><span data-stu-id="846d4-156">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob** .</span></span> <span data-ttu-id="846d4-157">Le paramètre **scriptblock** spécifie `Get-Process` d’extraire les processus avec le nom **PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="846d4-157">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell** .</span></span>

### <span data-ttu-id="846d4-158">Exemple 6 : collecter et enregistrer des données à l’aide d’une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="846d4-158">Example 6: Collect and save data by using a background job</span></span>

<span data-ttu-id="846d4-159">Cet exemple démarre un travail qui collecte une grande quantité de données cartographiques, puis l’enregistre dans un `.tif` fichier.</span><span class="sxs-lookup"><span data-stu-id="846d4-159">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="846d4-160">`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **GetMappingFiles** .</span><span class="sxs-lookup"><span data-stu-id="846d4-160">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles** .</span></span> <span data-ttu-id="846d4-161">Le paramètre **initializationScript** exécute un bloc de script qui importe le module **MapFunctions** .</span><span class="sxs-lookup"><span data-stu-id="846d4-161">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="846d4-162">Le paramètre **scriptblock** s’exécute `Get-Map` et `Set-Content` enregistre les données à l’emplacement spécifié par le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="846d4-162">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="846d4-163">Le paramètre **RunAs32** exécute le processus comme 32 bits, même sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="846d4-163">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="846d4-164">Exemple 7 : passer une entrée à une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="846d4-164">Example 7: Pass input to a background job</span></span>

<span data-ttu-id="846d4-165">Cet exemple utilise la `$input` variable Automatic pour traiter un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="846d4-165">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="846d4-166">Utilisez `Receive-Job` pour afficher la sortie du travail.</span><span class="sxs-lookup"><span data-stu-id="846d4-166">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="846d4-167">`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Content` avec la `$input` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="846d4-167">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="846d4-168">La `$input` variable récupère des objets à partir du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="846d4-168">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="846d4-169">`Receive-Job` utilise le paramètre **Name** pour spécifier le travail et renvoie les résultats.</span><span class="sxs-lookup"><span data-stu-id="846d4-169">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="846d4-170">Le paramètre **Keep** enregistre la sortie du travail afin qu’il puisse être affiché à nouveau pendant la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="846d4-170">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="846d4-171">Exemple 8 : utiliser le paramètre ArgumentList pour spécifier un tableau</span><span class="sxs-lookup"><span data-stu-id="846d4-171">Example 8: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="846d4-172">Cet exemple utilise le paramètre **argumentlist** pour spécifier un tableau d’arguments.</span><span class="sxs-lookup"><span data-stu-id="846d4-172">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="846d4-173">Le tableau est une liste séparée par des virgules de noms de processus.</span><span class="sxs-lookup"><span data-stu-id="846d4-173">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="846d4-174">L' `Start-Job` applet de commande utilise le paramètre **scriptblock** pour exécuter une commande.</span><span class="sxs-lookup"><span data-stu-id="846d4-174">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="846d4-175">`Get-Process` utilise le paramètre **Name** pour spécifier la variable automatique `$args` .</span><span class="sxs-lookup"><span data-stu-id="846d4-175">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="846d4-176">Le paramètre **argumentlist** passe le tableau de noms de processus à `$args` .</span><span class="sxs-lookup"><span data-stu-id="846d4-176">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="846d4-177">Les noms de processus PowerShell, pwsh et Notepad sont des processus en cours d’exécution sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-177">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="846d4-178">Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="846d4-178">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="846d4-179">Par exemple : `Receive-Job -Id 1`.</span><span class="sxs-lookup"><span data-stu-id="846d4-179">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="846d4-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="846d4-180">PARAMETERS</span></span>

### <span data-ttu-id="846d4-181">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="846d4-181">-ArgumentList</span></span>

<span data-ttu-id="846d4-182">Spécifie un tableau d’arguments ou de valeurs de paramètre pour le script spécifié par le paramètre **filePath** ou une commande spécifiée avec le paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="846d4-182">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="846d4-183">Les arguments doivent être passés à **argumentlist** comme argument de tableau à une seule dimension.</span><span class="sxs-lookup"><span data-stu-id="846d4-183">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="846d4-184">Par exemple, une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="846d4-184">For example, a comma-separated list.</span></span> <span data-ttu-id="846d4-185">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="846d4-185">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-186">-Authentification</span><span class="sxs-lookup"><span data-stu-id="846d4-186">-Authentication</span></span>

<span data-ttu-id="846d4-187">Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="846d4-187">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="846d4-188">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="846d4-188">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="846d4-189">Default</span><span class="sxs-lookup"><span data-stu-id="846d4-189">Default</span></span>
- <span data-ttu-id="846d4-190">Basic</span><span class="sxs-lookup"><span data-stu-id="846d4-190">Basic</span></span>
- <span data-ttu-id="846d4-191">CredSSP</span><span class="sxs-lookup"><span data-stu-id="846d4-191">Credssp</span></span>
- <span data-ttu-id="846d4-192">Digest</span><span class="sxs-lookup"><span data-stu-id="846d4-192">Digest</span></span>
- <span data-ttu-id="846d4-193">Kerberos</span><span class="sxs-lookup"><span data-stu-id="846d4-193">Kerberos</span></span>
- <span data-ttu-id="846d4-194">Negotiate</span><span class="sxs-lookup"><span data-stu-id="846d4-194">Negotiate</span></span>
- <span data-ttu-id="846d4-195">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="846d4-195">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="846d4-196">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="846d4-196">The default value is Default.</span></span>

<span data-ttu-id="846d4-197">L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="846d4-197">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="846d4-198">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="846d4-198">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="846d4-199">l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="846d4-199">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="846d4-200">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="846d4-200">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="846d4-201">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="846d4-201">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-202">-Credential</span><span class="sxs-lookup"><span data-stu-id="846d4-202">-Credential</span></span>

<span data-ttu-id="846d4-203">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="846d4-203">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="846d4-204">Si le paramètre **Credential** n’est pas spécifié, la commande utilise les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="846d4-204">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="846d4-205">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="846d4-205">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="846d4-206">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="846d4-206">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="846d4-207">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="846d4-207">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="846d4-208">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="846d4-208">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-209">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="846d4-209">-DefinitionName</span></span>

<span data-ttu-id="846d4-210">Spécifie le nom de la définition du travail que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="846d4-210">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="846d4-211">Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un nom de définition, comme les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="846d4-211">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="846d4-212">Lorsque vous utilisez `Start-Job` pour démarrer une instance d’une tâche planifiée, le travail démarre immédiatement, quels que soient les déclencheurs ou les options de travail.</span><span class="sxs-lookup"><span data-stu-id="846d4-212">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="846d4-213">L’instance de tâche qui en résulte est une tâche planifiée, mais elle n’est pas enregistrée sur le disque comme les tâches planifiées déclenchées.</span><span class="sxs-lookup"><span data-stu-id="846d4-213">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="846d4-214">Vous ne pouvez pas utiliser le paramètre **argumentlist** de `Start-Job` pour fournir des valeurs pour les paramètres de scripts qui s’exécutent dans une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="846d4-214">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span> <span data-ttu-id="846d4-215">Pour plus d’informations, consultez [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="846d4-215">For more information, see [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span></span>

<span data-ttu-id="846d4-216">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="846d4-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="846d4-217">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="846d4-217">-DefinitionPath</span></span>

<span data-ttu-id="846d4-218">Spécifie le chemin d’accès de la définition du travail que cette applet de commande démarre.</span><span class="sxs-lookup"><span data-stu-id="846d4-218">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="846d4-219">Entrez le chemin d'accès à la définition.</span><span class="sxs-lookup"><span data-stu-id="846d4-219">Enter the definition path.</span></span> <span data-ttu-id="846d4-220">La concaténation des valeurs des paramètres **DefinitionPath** et **DefinitionName** est le chemin d’accès complet de la définition du travail.</span><span class="sxs-lookup"><span data-stu-id="846d4-220">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="846d4-221">Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un chemin d'accès de définition, comme les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="846d4-221">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="846d4-222">Pour les tâches planifiées, la valeur du paramètre **DefinitionPath** est `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="846d4-222">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="846d4-223">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="846d4-223">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="846d4-224">-FilePath</span><span class="sxs-lookup"><span data-stu-id="846d4-224">-FilePath</span></span>

<span data-ttu-id="846d4-225">Spécifie un script local qui `Start-Job` s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-225">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="846d4-226">Entrez le chemin d’accès et le nom de fichier du script ou utilisez le pipeline pour lui envoyer un chemin d’accès de script `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="846d4-226">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="846d4-227">Le script doit se trouver sur l’ordinateur local ou dans un dossier accessible à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-227">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="846d4-228">Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script et exécute le bloc de script en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-228">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="846d4-229">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="846d4-229">-InitializationScript</span></span>

<span data-ttu-id="846d4-230">Spécifie les commandes à exécuter avant le début de la tâche.</span><span class="sxs-lookup"><span data-stu-id="846d4-230">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="846d4-231">Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="846d4-231">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="846d4-232">Utilisez ce paramètre pour préparer la session dans laquelle la tâche s'exécute.</span><span class="sxs-lookup"><span data-stu-id="846d4-232">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="846d4-233">Par exemple, vous pouvez l'utiliser pour ajouter des fonctions, des composants logiciels enfichables et des modules à la session.</span><span class="sxs-lookup"><span data-stu-id="846d4-233">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-234">-InputObject</span><span class="sxs-lookup"><span data-stu-id="846d4-234">-InputObject</span></span>

<span data-ttu-id="846d4-235">Spécifie l'entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="846d4-235">Specifies input to the command.</span></span> <span data-ttu-id="846d4-236">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui génère ces objets.</span><span class="sxs-lookup"><span data-stu-id="846d4-236">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="846d4-237">Dans la valeur du paramètre **scriptblock** , utilisez la `$input` variable Automatic pour représenter les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="846d4-237">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-238">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="846d4-238">-LiteralPath</span></span>

<span data-ttu-id="846d4-239">Spécifie un script local que cette applet de commande exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-239">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="846d4-240">Entrez le chemin d’accès d’un script sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="846d4-240">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="846d4-241">`Start-Job` utilise la valeur du paramètre **LiteralPath** exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="846d4-241">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="846d4-242">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="846d4-242">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="846d4-243">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="846d4-243">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="846d4-244">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="846d4-244">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-245">-Name</span><span class="sxs-lookup"><span data-stu-id="846d4-245">-Name</span></span>

<span data-ttu-id="846d4-246">Spécifie le nom convivial de la nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="846d4-246">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="846d4-247">Vous pouvez utiliser le nom pour identifier le travail à d’autres applets de commande de tâche, telles que l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="846d4-247">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="846d4-248">Le nom convivial par défaut est `Job#` , où `#` est un nombre ordinal qui est incrémenté pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="846d4-248">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-249">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="846d4-249">-PSVersion</span></span>

<span data-ttu-id="846d4-250">Spécifie une version.</span><span class="sxs-lookup"><span data-stu-id="846d4-250">Specifies a version.</span></span> <span data-ttu-id="846d4-251">`Start-Job` exécute la tâche avec la version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="846d4-251">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="846d4-252">Les valeurs acceptables pour ce paramètre sont les suivantes : `2.0` et `3.0` .</span><span class="sxs-lookup"><span data-stu-id="846d4-252">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="846d4-253">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="846d4-253">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-254">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="846d4-254">-RunAs32</span></span>

<span data-ttu-id="846d4-255">Indique que `Start-Job` exécute la tâche dans un processus 32 bits.</span><span class="sxs-lookup"><span data-stu-id="846d4-255">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="846d4-256">**RunAs32** force la tâche à s’exécuter dans un processus 32 bits, même sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="846d4-256">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="846d4-257">Sur les versions 64 bits de Windows 7 et Windows Server 2008 R2, lorsque la `Start-Job` commande comprend le paramètre **RunAs32** , vous ne pouvez pas utiliser le paramètre **Credential** pour spécifier les informations d’identification d’un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="846d4-257">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="846d4-258">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="846d4-258">-ScriptBlock</span></span>

<span data-ttu-id="846d4-259">Spécifie les commandes à exécuter dans la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="846d4-259">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="846d4-260">Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="846d4-260">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="846d4-261">Utilisez la `$input` variable Automatic pour accéder à la valeur du paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="846d4-261">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="846d4-262">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="846d4-262">This parameter is required.</span></span>

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

### <span data-ttu-id="846d4-263">-Type</span><span class="sxs-lookup"><span data-stu-id="846d4-263">-Type</span></span>

<span data-ttu-id="846d4-264">Spécifie le type personnalisé pour les travaux démarrés par `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="846d4-264">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="846d4-265">Entrez un nom de type de tâche personnalisé, par exemple, PSScheduledJob pour les tâches planifiées ou PSWorkflowJob pour les tâches de workflow.</span><span class="sxs-lookup"><span data-stu-id="846d4-265">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="846d4-266">Ce paramètre n’est pas valide pour les travaux en arrière-plan standard.</span><span class="sxs-lookup"><span data-stu-id="846d4-266">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="846d4-267">Ce paramètre a été introduit dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="846d4-267">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="846d4-268">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="846d4-268">CommonParameters</span></span>

<span data-ttu-id="846d4-269">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="846d4-269">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="846d4-270">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="846d4-270">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="846d4-271">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="846d4-271">INPUTS</span></span>

### <span data-ttu-id="846d4-272">System.String</span><span class="sxs-lookup"><span data-stu-id="846d4-272">System.String</span></span>

<span data-ttu-id="846d4-273">Vous pouvez utiliser le pipeline pour envoyer un objet avec la propriété **Name** au paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="846d4-273">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="846d4-274">Par exemple, vous pouvez effectuer un pipeline d’un objet **FileInfo** de `Get-ChildItem` à `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="846d4-274">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="846d4-275">SORTIES</span><span class="sxs-lookup"><span data-stu-id="846d4-275">OUTPUTS</span></span>

### <span data-ttu-id="846d4-276">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="846d4-276">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="846d4-277">`Start-Job` retourne un objet **PSRemotingJob** qui représente le travail qu’il a démarré.</span><span class="sxs-lookup"><span data-stu-id="846d4-277">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="846d4-278">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="846d4-278">NOTES</span></span>

<span data-ttu-id="846d4-279">Pour s’exécuter en arrière-plan, `Start-Job` s’exécute dans sa propre session dans la session active.</span><span class="sxs-lookup"><span data-stu-id="846d4-279">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="846d4-280">Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande dans une session sur un ordinateur distant, `Start-Job` s’exécute dans une session de la session à distance.</span><span class="sxs-lookup"><span data-stu-id="846d4-280">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="846d4-281">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="846d4-281">RELATED LINKS</span></span>

[<span data-ttu-id="846d4-282">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="846d4-282">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="846d4-283">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="846d4-283">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="846d4-284">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="846d4-284">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="846d4-285">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="846d4-285">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="846d4-286">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="846d4-286">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="846d4-287">Get-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-287">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="846d4-288">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="846d4-288">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="846d4-289">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-289">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="846d4-290">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-290">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="846d4-291">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-291">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="846d4-292">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-292">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="846d4-293">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-293">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="846d4-294">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="846d4-294">Wait-Job</span></span>](Wait-Job.md)
