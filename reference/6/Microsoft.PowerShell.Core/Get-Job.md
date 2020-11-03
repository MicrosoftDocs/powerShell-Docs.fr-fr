---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: d61f1efc613b7628585e5090b9fad8d90333a291
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203813"
---
# <span data-ttu-id="d6a72-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d6a72-103">Get-Job</span></span>

## <span data-ttu-id="d6a72-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d6a72-104">SYNOPSIS</span></span>
<span data-ttu-id="d6a72-105">Obtient les tâches en arrière-plan PowerShell qui s’exécutent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="d6a72-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d6a72-106">SYNTAX</span></span>

### <span data-ttu-id="d6a72-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d6a72-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="d6a72-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d6a72-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="d6a72-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d6a72-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="d6a72-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="d6a72-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="d6a72-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="d6a72-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d6a72-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="d6a72-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="d6a72-113">Description</span><span class="sxs-lookup"><span data-stu-id="d6a72-113">DESCRIPTION</span></span>

<span data-ttu-id="d6a72-114">L'applet de commande **Get-Job** récupère les objets qui représentent les tâches en arrière-plan démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="d6a72-115">Vous pouvez utiliser l’applet de commande on **-Job** pour récupérer des tâches qui ont été démarrées à l’aide de l’applet de commande Start-Job, ou à l’aide du paramètre *AsJob* d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d6a72-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="d6a72-116">Sans paramètres, une commande **« obtenir-Job »** obtient toutes les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="d6a72-117">Vous pouvez utiliser les paramètres de **Get-Job** pour obtenir des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d6a72-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="d6a72-118">L'objet de traitement retourné par **Get-Job** contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="d6a72-119">Pour obtenir les résultats, utilisez l’applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="d6a72-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="d6a72-120">Une tâche en arrière-plan PowerShell est une commande qui s’exécute en arrière-plan sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-120">A PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="d6a72-121">En règle générale, vous utilisez une tâche en arrière-plan pour exécuter une commande complexe qui prend beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="d6a72-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="d6a72-122">Pour plus d’informations sur les tâches en arrière-plan dans PowerShell, consultez about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="d6a72-122">For more information about background jobs in PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="d6a72-123">À compter de Windows PowerShell 3.0, l'applet de commande **Get-Job** obtient également des types de tâche personnalisés, comme les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="d6a72-124">Pour rechercher le type d'une tâche, utilisez la propriété **PSJobTypeName** de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="d6a72-125">Pour permettre à la **fonction** d’obtention d’un travail d’obtenir un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une commande **obtenir-Job** , soit à l’aide de l’applet de commande Import-Module, soit en utilisant ou en obtenant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="d6a72-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="d6a72-126">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d6a72-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="d6a72-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d6a72-127">EXAMPLES</span></span>

### <span data-ttu-id="d6a72-128">Exemple 1 : récupération de toutes les tâches en arrière-plan démarrées dans la session active</span><span class="sxs-lookup"><span data-stu-id="d6a72-128">Example 1: Get all background jobs started in the current session</span></span>

```powershell
Get-Job
```

<span data-ttu-id="d6a72-129">Cette commande obtient toutes les tâches en arrière-plan démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="d6a72-130">Elle n'inclut pas les tâches créées dans d'autres sessions, même si elles s'exécutent sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6a72-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="d6a72-131">Exemple 2 : arrêter un travail à l’aide d’un ID d’instance</span><span class="sxs-lookup"><span data-stu-id="d6a72-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="d6a72-132">Ces commandes indiquent comment obtenir l'ID d'instance d'une tâche, puis l'utiliser pour arrêter une tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="d6a72-133">Contrairement au nom de la tâche, qui n'est pas unique, l'ID d'instance est unique.</span><span class="sxs-lookup"><span data-stu-id="d6a72-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

<span data-ttu-id="d6a72-134">La première commande utilise l'applet de commande **Get-Job** pour obtenir une tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-134">The first command uses the **Get-Job** cmdlet to get a job.</span></span> <span data-ttu-id="d6a72-135">Elle utilise le paramètre *Name* pour identifier le travail.</span><span class="sxs-lookup"><span data-stu-id="d6a72-135">It uses the *Name* parameter to identify the job.</span></span> <span data-ttu-id="d6a72-136">La commande stocke l'objet de traitement retourné par **Get-Job** dans la variable $j.</span><span class="sxs-lookup"><span data-stu-id="d6a72-136">The command stores the job object that **Get-Job** returns in the $j variable.</span></span> <span data-ttu-id="d6a72-137">Dans cet exemple, il existe une seule tâche ayant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6a72-137">In this example, there is only one job with the specified name.</span></span>

<span data-ttu-id="d6a72-138">La deuxième commande obtient la propriété **InstanceId** de l'objet dans la variable $j et le stocke dans la variable $ID.</span><span class="sxs-lookup"><span data-stu-id="d6a72-138">The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.</span></span>

<span data-ttu-id="d6a72-139">La troisième commande affiche la valeur de la variable $ID.</span><span class="sxs-lookup"><span data-stu-id="d6a72-139">The third command displays the value of the $ID variable.</span></span>

<span data-ttu-id="d6a72-140">La quatrième commande utilise Stop-Job applet de commande pour arrêter la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-140">The fourth command uses Stop-Job cmdlet to stop the job.</span></span> <span data-ttu-id="d6a72-141">Elle utilise le paramètre *InstanceId* pour identifier la tâche et la variable $ID afin de représenter l'ID d'instance de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-141">It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.</span></span>

### <span data-ttu-id="d6a72-142">Exemple 3 : obtenir des travaux qui incluent une commande spécifique</span><span class="sxs-lookup"><span data-stu-id="d6a72-142">Example 3: Get jobs that include a specific command</span></span>

```powershell
Get-Job -Command "*get-process*"
```

<span data-ttu-id="d6a72-143">Cette commande obtient les tâches du système qui incluent une commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="d6a72-143">This command gets the jobs on the system that include a Get-Process command.</span></span> <span data-ttu-id="d6a72-144">La commande utilise le paramètre *Command* de **Get-Job** pour limiter le nombre de tâches récupérées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-144">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span> <span data-ttu-id="d6a72-145">La commande utilise des caractères génériques (\*) pour obtenir les tâches qui incluent une commande **« obtenir un processus »** n’importe où dans la chaîne de commande.</span><span class="sxs-lookup"><span data-stu-id="d6a72-145">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="d6a72-146">Exemple 4 : obtenir des travaux qui incluent une commande spécifique à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="d6a72-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```powershell
"*get-process*" | Get-Job
```

<span data-ttu-id="d6a72-147">À l’instar de la commande dans l’exemple précédent, cette commande obtient les tâches du système qui incluent une commande **« obtenir-traiter »** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-147">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span> <span data-ttu-id="d6a72-148">La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne, entre guillemets, à l’applet de commande **« obtenir-Job »** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-148">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span> <span data-ttu-id="d6a72-149">Elle est équivalente à la commande précédente.</span><span class="sxs-lookup"><span data-stu-id="d6a72-149">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="d6a72-150">Exemple 5 : obtenir des travaux qui n’ont pas été démarrés</span><span class="sxs-lookup"><span data-stu-id="d6a72-150">Example 5: Get jobs that have not been started</span></span>

```powershell
Get-Job -State NotStarted
```

<span data-ttu-id="d6a72-151">Cette commande obtient uniquement les tâches qui ont été créées mais qui n'ont pas encore démarré.</span><span class="sxs-lookup"><span data-stu-id="d6a72-151">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="d6a72-152">Cela inclut les tâches dont l'exécution est planifiée ultérieurement et celles qui ne sont pas encore planifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="d6a72-153">Exemple 6 : obtenir des travaux auxquels aucun nom n’a été attribué</span><span class="sxs-lookup"><span data-stu-id="d6a72-153">Example 6: Get jobs that have not been assigned a name</span></span>

```powershell
Get-Job -Name Job*
```

<span data-ttu-id="d6a72-154">Cette commande obtient toutes les tâches dont le nom commence par Job.</span><span class="sxs-lookup"><span data-stu-id="d6a72-154">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="d6a72-155">Étant donné que Job \<number\> est le nom par défaut d’une tâche, cette commande obtient toutes les tâches qui n’ont pas de nom explicitement attribué.</span><span class="sxs-lookup"><span data-stu-id="d6a72-155">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="d6a72-156">Exemple 7 : utiliser un objet de traitement pour représenter la tâche dans une commande</span><span class="sxs-lookup"><span data-stu-id="d6a72-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="d6a72-157">Cet exemple illustre comment utiliser **Get-Job** pour obtenir une tâche, puis comment utiliser l'objet de traitement pour représenter la tâche dans une commande.</span><span class="sxs-lookup"><span data-stu-id="d6a72-157">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="d6a72-158">La première commande utilise l’applet de commande **Start-Job** pour démarrer une tâche en arrière-plan qui exécute une commande **« obtenir-traiter »** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6a72-158">The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer.</span></span> <span data-ttu-id="d6a72-159">La commande utilise le paramètre *Name* de **Start-Job** pour attribuer un nom convivial à la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-159">The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.</span></span>

<span data-ttu-id="d6a72-160">La deuxième commande utilise Get-Job pour obtenir la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-160">The second command uses Get-Job to get the job.</span></span> <span data-ttu-id="d6a72-161">Elle utilise le paramètre *Name* de **Get-Job** pour identifier la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-161">It uses the *Name* parameter of **Get-Job** to identify the job.</span></span> <span data-ttu-id="d6a72-162">Elle enregistre l'objet de traitement résultant dans la variable $j.</span><span class="sxs-lookup"><span data-stu-id="d6a72-162">The command saves the resulting job object in the $j variable.</span></span>

<span data-ttu-id="d6a72-163">La troisième commande affiche la valeur de l'objet de traitement dans la variable $j.</span><span class="sxs-lookup"><span data-stu-id="d6a72-163">The third command displays the value of the job object in the $j variable.</span></span> <span data-ttu-id="d6a72-164">La valeur de la propriété **State** indique que la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="d6a72-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="d6a72-165">La valeur de la propriété **HasMoreData** indique que des résultats de la tâche sont disponibles, mais qu'ils n'ont pas encore été récupérés.</span><span class="sxs-lookup"><span data-stu-id="d6a72-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span>

<span data-ttu-id="d6a72-166">La quatrième commande utilise l’applet de commande **Receive-Job** pour obtenir les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-166">The fourth command uses the **Receive-Job** cmdlet to get the results of the job.</span></span> <span data-ttu-id="d6a72-167">Elle utilise l'objet de traitement de la variable $j pour représenter la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-167">It uses the job object in the $j variable to represent the job.</span></span> <span data-ttu-id="d6a72-168">Vous pouvez également utiliser un opérateur de pipeline pour envoyer un objet de tâche au **travail de réception** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-168">You can also use a pipeline operator to send a job object to **Receive-Job** .</span></span>

### <span data-ttu-id="d6a72-169">Exemple 8 : obtenir tous les travaux, y compris les travaux démarrés par une autre méthode</span><span class="sxs-lookup"><span data-stu-id="d6a72-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="d6a72-170">Cet exemple montre que l’applet de commande **« obtient-Job »** peut récupérer toutes les tâches qui ont été démarrées dans la session active, même si elles ont été démarrées à l’aide de différentes méthodes.</span><span class="sxs-lookup"><span data-stu-id="d6a72-170">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="d6a72-171">La première commande utilise l’applet de commande **Start-Job** pour démarrer une tâche sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6a72-171">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span>

<span data-ttu-id="d6a72-172">La deuxième commande utilise le paramètre *AsJob* de l’applet de **commande Invoke-Command** pour démarrer une tâche sur l’ordinateur S1.</span><span class="sxs-lookup"><span data-stu-id="d6a72-172">The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="d6a72-173">Bien que les commandes de la tâche s'exécutent sur l'ordinateur distant, l'objet de traitement est créé sur l'ordinateur local, vous utilisez donc les commandes locales pour gérer la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span>

<span data-ttu-id="d6a72-174">La troisième commande utilise l'applet de commande **Invoke-Command** pour exécuter une commande **Start-Job** sur l'ordinateur S2.</span><span class="sxs-lookup"><span data-stu-id="d6a72-174">The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer.</span></span> <span data-ttu-id="d6a72-175">À l’aide de cette méthode, l’objet de traitement est créé sur l’ordinateur distant. vous utilisez donc des commandes à distance pour gérer le travail.</span><span class="sxs-lookup"><span data-stu-id="d6a72-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span>

<span data-ttu-id="d6a72-176">La quatrième commande utilise **Get-Job** pour obtenir les tâches stockées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6a72-176">The fourth command uses **Get-Job** to get the jobs stored on the local computer.</span></span> <span data-ttu-id="d6a72-177">La propriété **PSJobTypeName** des travaux, introduite dans Windows PowerShell 3,0, indique que la tâche locale démarrée à l’aide de l’applet de commande **Start-Job** est une tâche en arrière-plan et que la tâche démarrée dans une session à distance à l’aide de l’applet de **commande Invoke-Command** est une tâche à distance.</span><span class="sxs-lookup"><span data-stu-id="d6a72-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.</span></span>

<span data-ttu-id="d6a72-178">La cinquième commande utilise **Invoke-Command** pour exécuter une commande **obtenir-Job** sur l’ordinateur S2. L’exemple de sortie montre les résultats de la commande Get-Job.</span><span class="sxs-lookup"><span data-stu-id="d6a72-178">The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command.</span></span> <span data-ttu-id="d6a72-179">Sur l'ordinateur S2, la tâche semble être une tâche locale.</span><span class="sxs-lookup"><span data-stu-id="d6a72-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="d6a72-180">Le nom de l’ordinateur est localhost et le type de travail est une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d6a72-180">The computer name is localhost and the job type is a background job.</span></span>

<span data-ttu-id="d6a72-181">Pour plus d’informations sur la façon d’exécuter des tâches en arrière-plan sur des ordinateurs distants, consultez about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="d6a72-181">For more information about how to run background jobs on remote computers, see about_Remote_Jobs.</span></span>

### <span data-ttu-id="d6a72-182">Exemple 9 : examiner un travail ayant échoué</span><span class="sxs-lookup"><span data-stu-id="d6a72-182">Example 9: Investigate a failed job</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

<span data-ttu-id="d6a72-183">Cette commande montre comment utiliser l’objet de traitement retourné par la **fonction-Job** pour déterminer la raison de l’échec d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-183">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="d6a72-184">Elle illustre également comment obtenir les tâches enfant de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-184">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="d6a72-185">La première commande utilise l’applet de commande **Start-Job** pour démarrer une tâche sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6a72-185">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="d6a72-186">L'objet tâche retourné par **Start-Job** indique que la tâche a échoué.</span><span class="sxs-lookup"><span data-stu-id="d6a72-186">The job object that **Start-Job** returns shows that the job failed.</span></span> <span data-ttu-id="d6a72-187">La valeur de la propriété **State** est failed.</span><span class="sxs-lookup"><span data-stu-id="d6a72-187">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="d6a72-188">La deuxième commande utilise l'applet de commande **Get-Job** pour obtenir la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-188">The second command uses the **Get-Job** cmdlet to get the job.</span></span> <span data-ttu-id="d6a72-189">La commande utilise la méthode du point pour obtenir la valeur de la propriété **JobStateInfo** de l'objet.</span><span class="sxs-lookup"><span data-stu-id="d6a72-189">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="d6a72-190">Elle utilise un opérateur de pipeline pour envoyer l’objet dans la propriété **JobStateInfo** à l’applet de commande Format-List, qui met en forme toutes les propriétés de l’objet (\*) dans une liste. Le résultat de la commande **format-list** indique que la valeur de la propriété **reason** de la tâche est vide.</span><span class="sxs-lookup"><span data-stu-id="d6a72-190">It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (\*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="d6a72-191">La troisième commande étudie davantage.</span><span class="sxs-lookup"><span data-stu-id="d6a72-191">The third command investigates more.</span></span> <span data-ttu-id="d6a72-192">Elle utilise une commande **« obtenir-Job »** pour obtenir la tâche, puis utilise un opérateur de pipeline pour envoyer l’intégralité de l’objet de traitement à l’applet de commande **format-list** , qui affiche toutes les propriétés du travail dans une liste. L’affichage de toutes les propriétés de l’objet de traitement indique que le travail contient un travail enfant nommé Job2.</span><span class="sxs-lookup"><span data-stu-id="d6a72-192">It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="d6a72-193">La quatrième commande utilise **Get-Job** pour obtenir l'objet de traitement qui représente la tâche enfant Job2.</span><span class="sxs-lookup"><span data-stu-id="d6a72-193">The fourth command uses **Get-Job** to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="d6a72-194">Il s'agit de la tâche dans laquelle a été exécutée la commande.</span><span class="sxs-lookup"><span data-stu-id="d6a72-194">This is the job in which the command actually ran.</span></span> <span data-ttu-id="d6a72-195">Elle utilise la méthode point pour avoir la propriété **reason** de la propriété **JobStateInfo** . Le résultat indique que la tâche a échoué en raison d’une erreur d’accès refusé.</span><span class="sxs-lookup"><span data-stu-id="d6a72-195">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="d6a72-196">Dans ce cas, l’utilisateur a oublié d’utiliser l’option Exécuter en tant qu’administrateur lors du démarrage de PowerShell. comme les travaux en arrière-plan utilisent les fonctionnalités de communication à distance de PowerShell, l’ordinateur doit être configuré pour que l’accès distant exécute un travail, même lorsque le travail s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d6a72-196">In this case, the user forgot to use the Run as administrator option when starting PowerShell.Because background jobs use the remoting features of PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.</span></span>

### <span data-ttu-id="d6a72-197">Exemple 10 : obtenir des résultats filtrés</span><span class="sxs-lookup"><span data-stu-id="d6a72-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="d6a72-198">Cet exemple indique comment utiliser le paramètre *Filter* pour obtenir une tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="d6a72-198">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="d6a72-199">Le paramètre *Filter* , introduit dans Windows PowerShell 3.0, n'est valide que sur les types de tâche personnalisé, comme les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-199">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="d6a72-200">La première commande utilise le mot clé **Workflow** pour créer le flux de travail WFProcess.</span><span class="sxs-lookup"><span data-stu-id="d6a72-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span>

<span data-ttu-id="d6a72-201">La deuxième commande utilise le paramètre *AsJob* du flux de travail WFProcess pour exécuter le workflow en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d6a72-201">The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="d6a72-202">Elle utilise le paramètre *JobName* du workflow pour spécifier un nom pour la tâche et le paramètre *PSPrivateMetadata* du workflow pour spécifier un ID personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d6a72-202">It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.</span></span>

<span data-ttu-id="d6a72-203">La troisième commande utilise le paramètre *Filter* de **Get-Job** pour obtenir la tâche par son ID personnalisé spécifié dans le paramètre *PSPrivateMetadata* .</span><span class="sxs-lookup"><span data-stu-id="d6a72-203">The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.</span></span>

### <span data-ttu-id="d6a72-204">Exemple 11 : obtenir des informations sur les tâches enfants</span><span class="sxs-lookup"><span data-stu-id="d6a72-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="d6a72-205">Cet exemple illustre l'utilisation des paramètres *IncludeChildJob* et *ChildJobState* de l'applet de commande **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-205">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="d6a72-206">La première commande obtient les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="d6a72-207">La sortie inclut une tâche en arrière-plan, une tâche à distance et plusieurs instances d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d6a72-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="d6a72-208">La tâche à distance, Job4, semble avoir échoué.</span><span class="sxs-lookup"><span data-stu-id="d6a72-208">The remote job, Job4, appears to have failed.</span></span>

<span data-ttu-id="d6a72-209">La deuxième commande utilise le paramètre *IncludeChildJob* de **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-209">The second command uses the *IncludeChildJob* parameter of **Get-Job** .</span></span> <span data-ttu-id="d6a72-210">La sortie ajoute les tâches enfants de tous les travaux qui ont des tâches enfants. Dans ce cas, la sortie révisée indique que seule la tâche enfant JOB5 de Job4 a échoué.</span><span class="sxs-lookup"><span data-stu-id="d6a72-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span>

<span data-ttu-id="d6a72-211">La troisième commande utilise le paramètre *ChildJobState* avec la valeur failed. la sortie comprend tous les travaux parents et uniquement les tâches enfants ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="d6a72-211">The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span>

<span data-ttu-id="d6a72-212">La quatrième commande utilise la propriété **JobStateInfo** des travaux et sa propriété **reason** pour découvrir la raison de l’échec de JOB5.</span><span class="sxs-lookup"><span data-stu-id="d6a72-212">The fourth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

## <span data-ttu-id="d6a72-213">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d6a72-213">PARAMETERS</span></span>

### <span data-ttu-id="d6a72-214">-Après</span><span class="sxs-lookup"><span data-stu-id="d6a72-214">-After</span></span>

<span data-ttu-id="d6a72-215">Obtient les tâches terminées après la date et l'heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-215">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="d6a72-216">Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date ou une chaîne qui peut être convertie en un objet **DateTime** , tel que `Dec 1, 2012 2:00 AM` ou `11/06` .</span><span class="sxs-lookup"><span data-stu-id="d6a72-216">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="d6a72-217">Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-217">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="d6a72-218">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-218">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="d6a72-219">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-219">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="d6a72-220">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-221">-Avant</span><span class="sxs-lookup"><span data-stu-id="d6a72-221">-Before</span></span>

<span data-ttu-id="d6a72-222">Obtient les tâches terminées avant la date et l'heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-222">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="d6a72-223">Entrez un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-223">Enter a **DateTime** object.</span></span>

<span data-ttu-id="d6a72-224">Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-224">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="d6a72-225">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-225">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="d6a72-226">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-226">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="d6a72-227">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-228">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="d6a72-228">-ChildJobState</span></span>

<span data-ttu-id="d6a72-229">Obtient uniquement les tâches enfant dans l'état spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6a72-229">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="d6a72-230">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d6a72-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d6a72-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="d6a72-231">NotStarted</span></span>
- <span data-ttu-id="d6a72-232">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="d6a72-232">Running</span></span>
- <span data-ttu-id="d6a72-233">Completed</span><span class="sxs-lookup"><span data-stu-id="d6a72-233">Completed</span></span>
- <span data-ttu-id="d6a72-234">Échec</span><span class="sxs-lookup"><span data-stu-id="d6a72-234">Failed</span></span>
- <span data-ttu-id="d6a72-235">Arrêté</span><span class="sxs-lookup"><span data-stu-id="d6a72-235">Stopped</span></span>
- <span data-ttu-id="d6a72-236">Bloqué</span><span class="sxs-lookup"><span data-stu-id="d6a72-236">Blocked</span></span>
- <span data-ttu-id="d6a72-237">Interrompu</span><span class="sxs-lookup"><span data-stu-id="d6a72-237">Suspended</span></span>
- <span data-ttu-id="d6a72-238">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="d6a72-238">Disconnected</span></span>
- <span data-ttu-id="d6a72-239">Suspension</span><span class="sxs-lookup"><span data-stu-id="d6a72-239">Suspending</span></span>
- <span data-ttu-id="d6a72-240">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="d6a72-240">Stopping</span></span>

<span data-ttu-id="d6a72-241">Par défaut, **Get-Job** n'obtient pas les tâches enfant.</span><span class="sxs-lookup"><span data-stu-id="d6a72-241">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="d6a72-242">En utilisant le paramètre *IncludeChildJob* , la **fonction « obtenir-Job »** obtient toutes les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="d6a72-242">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="d6a72-243">Si vous utilisez le paramètre *ChildJobState* , le paramètre *IncludeChildJob* n'a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="d6a72-243">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="d6a72-244">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-245">-Command</span><span class="sxs-lookup"><span data-stu-id="d6a72-245">-Command</span></span>

<span data-ttu-id="d6a72-246">Spécifie un tableau de commandes sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="d6a72-246">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="d6a72-247">Cette applet de commande obtient les tâches qui incluent les commandes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-247">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="d6a72-248">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="d6a72-248">The default is all jobs.</span></span>
<span data-ttu-id="d6a72-249">Vous pouvez utiliser des caractères génériques pour spécifier un modèle de commande.</span><span class="sxs-lookup"><span data-stu-id="d6a72-249">You can use wildcard characters to specify a command pattern.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d6a72-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="d6a72-250">-Filter</span></span>

<span data-ttu-id="d6a72-251">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="d6a72-251">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="d6a72-252">Cette applet de commande obtient les tâches qui répondent à toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="d6a72-252">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="d6a72-253">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="d6a72-253">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="d6a72-254">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="d6a72-254">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="d6a72-255">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-255">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="d6a72-256">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-256">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="d6a72-257">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d6a72-258">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="d6a72-258">-HasMoreData</span></span>

<span data-ttu-id="d6a72-259">Indique si cette applet de commande obtient uniquement les tâches qui ont la valeur de propriété **HasMoreData** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6a72-259">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="d6a72-260">La propriété **HasMoreData** indique si tous les résultats de la tâche ont été reçus dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-260">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="d6a72-261">Pour obtenir des travaux qui ont plus de résultats, spécifiez la valeur $True.</span><span class="sxs-lookup"><span data-stu-id="d6a72-261">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="d6a72-262">Pour obtenir des travaux qui n’ont pas plus de résultats, spécifiez une valeur de $False.</span><span class="sxs-lookup"><span data-stu-id="d6a72-262">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="d6a72-263">Pour obtenir les résultats d’un travail, utilisez l’applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="d6a72-263">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="d6a72-264">Lorsque vous utilisez l’applet de commande **Receive-Job** , elle supprime de son stockage propre à la session les résultats renvoyés.</span><span class="sxs-lookup"><span data-stu-id="d6a72-264">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="d6a72-265">Lorsqu’il a retourné tous les résultats de la tâche dans la session active, il définit la valeur de la propriété **HasMoreData** du travail sur $false) pour indiquer qu’il n’a plus de résultats pour le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-265">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="d6a72-266">Utilisez le paramètre *Keep* de **Receive-Job** pour empêcher **Receive-Job** de supprimer des résultats et de modifier la valeur de la propriété **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-266">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span> <span data-ttu-id="d6a72-267">Pour plus d'informations, voir `Get-Help Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="d6a72-267">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="d6a72-268">La propriété **HasMoreData** est propre à la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-268">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="d6a72-269">Si les résultats d’un type de tâche personnalisé sont enregistrés en dehors de la session, comme le type de tâche planifiée qui enregistre les résultats du travail sur le disque, vous pouvez utiliser l’applet de commande **Receive-Job** dans une autre session pour obtenir les résultats de la tâche, même si la valeur de **HasMoreData** est $false.</span><span class="sxs-lookup"><span data-stu-id="d6a72-269">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span> <span data-ttu-id="d6a72-270">Pour plus d'informations, consultez les rubriques d'aide du type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d6a72-270">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="d6a72-271">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-272">-Id</span><span class="sxs-lookup"><span data-stu-id="d6a72-272">-Id</span></span>

<span data-ttu-id="d6a72-273">Spécifie un tableau d’ID des travaux que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="d6a72-273">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="d6a72-274">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-274">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="d6a72-275">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-275">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="d6a72-276">Vous pouvez taper un ou plusieurs ID séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d6a72-276">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="d6a72-277">Pour Rechercher l’ID d’un travail, tapez `Get-Job` sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="d6a72-277">To find the ID of a job, type `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-278">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="d6a72-278">-IncludeChildJob</span></span>

<span data-ttu-id="d6a72-279">Indique que cette applet de commande retourne des travaux enfants, en plus des travaux parents.</span><span class="sxs-lookup"><span data-stu-id="d6a72-279">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="d6a72-280">Ce paramètre est particulièrement utile pour examiner les tâches de workflow, pour lesquelles l’opération d' **extraction** de travail retourne un travail parent de conteneur et les échecs de travaux, car la raison de l’échec est enregistrée dans une propriété du travail enfant.</span><span class="sxs-lookup"><span data-stu-id="d6a72-280">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="d6a72-281">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-282">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="d6a72-282">-InstanceId</span></span>

<span data-ttu-id="d6a72-283">Spécifie un tableau d’ID d’instance des travaux que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="d6a72-283">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="d6a72-284">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="d6a72-284">The default is all jobs.</span></span>

<span data-ttu-id="d6a72-285">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d6a72-285">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="d6a72-286">Pour rechercher l'ID d'instance d'une tâche, utilisez **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-286">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="d6a72-287">-Name</span><span class="sxs-lookup"><span data-stu-id="d6a72-287">-Name</span></span>

<span data-ttu-id="d6a72-288">Spécifie un tableau de noms conviviaux d’instance des travaux que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="d6a72-288">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="d6a72-289">Entrez un nom de tâche ou utilisez des caractères génériques pour entrer un modèle de nom de tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-289">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="d6a72-290">Par défaut, **Get-Job** obtient toutes les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-290">By default, **Get-Job** gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="d6a72-291">-Plus récent</span><span class="sxs-lookup"><span data-stu-id="d6a72-291">-Newest</span></span>

<span data-ttu-id="d6a72-292">Spécifie un nombre de travaux à obtenir.</span><span class="sxs-lookup"><span data-stu-id="d6a72-292">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="d6a72-293">Cette applet de commande obtient les tâches qui ont été terminées en dernier.</span><span class="sxs-lookup"><span data-stu-id="d6a72-293">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="d6a72-294">Le paramètre *Newest* ne trie pas ni ne retourne les tâches les plus récentes selon l'heure de fin.</span><span class="sxs-lookup"><span data-stu-id="d6a72-294">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="d6a72-295">Pour trier la sortie, utilisez l’applet de commande Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="d6a72-295">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="d6a72-296">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6a72-296">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6a72-297">-État</span><span class="sxs-lookup"><span data-stu-id="d6a72-297">-State</span></span>

<span data-ttu-id="d6a72-298">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="d6a72-298">Specifies a job state.</span></span>
<span data-ttu-id="d6a72-299">Cette applet de commande obtient uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6a72-299">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="d6a72-300">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d6a72-300">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d6a72-301">NotStarted</span><span class="sxs-lookup"><span data-stu-id="d6a72-301">NotStarted</span></span>
- <span data-ttu-id="d6a72-302">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="d6a72-302">Running</span></span>
- <span data-ttu-id="d6a72-303">Completed</span><span class="sxs-lookup"><span data-stu-id="d6a72-303">Completed</span></span>
- <span data-ttu-id="d6a72-304">Échec</span><span class="sxs-lookup"><span data-stu-id="d6a72-304">Failed</span></span>
- <span data-ttu-id="d6a72-305">Arrêté</span><span class="sxs-lookup"><span data-stu-id="d6a72-305">Stopped</span></span>
- <span data-ttu-id="d6a72-306">Bloqué</span><span class="sxs-lookup"><span data-stu-id="d6a72-306">Blocked</span></span>
- <span data-ttu-id="d6a72-307">Interrompu</span><span class="sxs-lookup"><span data-stu-id="d6a72-307">Suspended</span></span>
- <span data-ttu-id="d6a72-308">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="d6a72-308">Disconnected</span></span>
- <span data-ttu-id="d6a72-309">Suspension</span><span class="sxs-lookup"><span data-stu-id="d6a72-309">Suspending</span></span>
- <span data-ttu-id="d6a72-310">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="d6a72-310">Stopping</span></span>

<span data-ttu-id="d6a72-311">Par défaut, **Get-Job** obtient toutes les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="d6a72-311">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="d6a72-312">Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="d6a72-312">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="d6a72-313">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d6a72-313">CommonParameters</span></span>

<span data-ttu-id="d6a72-314">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d6a72-314">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d6a72-315">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d6a72-315">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d6a72-316">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d6a72-316">INPUTS</span></span>

### <span data-ttu-id="d6a72-317">Aucun</span><span class="sxs-lookup"><span data-stu-id="d6a72-317">None</span></span>

<span data-ttu-id="d6a72-318">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d6a72-318">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d6a72-319">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d6a72-319">OUTPUTS</span></span>

### <span data-ttu-id="d6a72-320">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="d6a72-320">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="d6a72-321">Cette applet de commande retourne des objets qui représentent les tâches dans la session.</span><span class="sxs-lookup"><span data-stu-id="d6a72-321">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="d6a72-322">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d6a72-322">NOTES</span></span>

* <span data-ttu-id="d6a72-323">La propriété **PSJobTypeName** des tâches indique le type de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-323">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="d6a72-324">La valeur de propriété est déterminée par l'auteur du type de tâche.</span><span class="sxs-lookup"><span data-stu-id="d6a72-324">The property value is determined by the job type author.</span></span> <span data-ttu-id="d6a72-325">La liste suivante affiche les types de tâches courants.</span><span class="sxs-lookup"><span data-stu-id="d6a72-325">The following list shows common job types.</span></span>

  - <span data-ttu-id="d6a72-326">**BackgroundJob** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-326">**BackgroundJob** .</span></span>
<span data-ttu-id="d6a72-327">Tâche locale démarrée à l’aide de **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-327">Local job started by using **Start-Job** .</span></span>

  - <span data-ttu-id="d6a72-328">**RemoteJob** .</span><span class="sxs-lookup"><span data-stu-id="d6a72-328">**RemoteJob** .</span></span>
<span data-ttu-id="d6a72-329">La tâche a démarré dans une **session PSSession** à l’aide du paramètre *AsJob* de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="d6a72-329">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

## <span data-ttu-id="d6a72-330">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d6a72-330">RELATED LINKS</span></span>

[<span data-ttu-id="d6a72-331">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="d6a72-331">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="d6a72-332">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d6a72-332">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="d6a72-333">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d6a72-333">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="d6a72-334">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d6a72-334">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="d6a72-335">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d6a72-335">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="d6a72-336">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d6a72-336">Wait-Job</span></span>](Wait-Job.md)
