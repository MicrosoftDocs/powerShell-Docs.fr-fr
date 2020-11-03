---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202302"
---
# <span data-ttu-id="c407f-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-103">Get-Job</span></span>

## <span data-ttu-id="c407f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c407f-104">SYNOPSIS</span></span>
<span data-ttu-id="c407f-105">Obtient les tâches en arrière-plan PowerShell qui s’exécutent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="c407f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c407f-106">SYNTAX</span></span>

### <span data-ttu-id="c407f-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c407f-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c407f-108">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="c407f-108">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c407f-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="c407f-109">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="c407f-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="c407f-110">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c407f-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="c407f-111">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="c407f-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="c407f-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="c407f-113">Description</span><span class="sxs-lookup"><span data-stu-id="c407f-113">DESCRIPTION</span></span>

<span data-ttu-id="c407f-114">L'applet de commande **Get-Job** récupère les objets qui représentent les tâches en arrière-plan démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span>
<span data-ttu-id="c407f-115">Vous pouvez utiliser l’applet de commande on **-Job** pour récupérer des tâches qui ont été démarrées à l’aide de l’applet de commande Start-Job, ou à l’aide du paramètre *AsJob* d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c407f-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="c407f-116">Sans paramètres, une commande **« obtenir-Job »** obtient toutes les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="c407f-117">Vous pouvez utiliser les paramètres de **Get-Job** pour obtenir des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c407f-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="c407f-118">L'objet de traitement retourné par **Get-Job** contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span>
<span data-ttu-id="c407f-119">Pour obtenir les résultats, utilisez l’applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="c407f-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="c407f-120">Une tâche en arrière-plan Windows PowerShell est une commande qui s’exécute en arrière-plan sans interagir avec la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span>
<span data-ttu-id="c407f-121">En règle générale, vous utilisez une tâche en arrière-plan pour exécuter une commande complexe qui prend beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="c407f-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span>
<span data-ttu-id="c407f-122">Pour plus d'informations sur les tâches en arrière-plan, consultez about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="c407f-122">For more information about background jobs in Windows PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="c407f-123">À compter de Windows PowerShell 3.0, l'applet de commande **Get-Job** obtient également des types de tâche personnalisés, comme les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="c407f-124">Pour rechercher le type d'une tâche, utilisez la propriété **PSJobTypeName** de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="c407f-125">Pour permettre à la **fonction** d’obtention d’un travail d’obtenir un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une commande **obtenir-Job** , soit à l’aide de l’applet de commande Import-Module, soit en utilisant ou en obtenant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="c407f-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="c407f-126">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c407f-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="c407f-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c407f-127">EXAMPLES</span></span>

### <span data-ttu-id="c407f-128">Exemple 1 : récupération de toutes les tâches en arrière-plan démarrées dans la session active</span><span class="sxs-lookup"><span data-stu-id="c407f-128">Example 1: Get all background jobs started in the current session</span></span>

```
PS C:\> Get-Job
```

<span data-ttu-id="c407f-129">Cette commande obtient toutes les tâches en arrière-plan démarrées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="c407f-130">Elle n'inclut pas les tâches créées dans d'autres sessions, même si elles s'exécutent sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c407f-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="c407f-131">Exemple 2 : arrêter un travail à l’aide d’un ID d’instance</span><span class="sxs-lookup"><span data-stu-id="c407f-131">Example 2: Stop a job by using an instance ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

<span data-ttu-id="c407f-132">Ces commandes indiquent comment obtenir l'ID d'instance d'une tâche, puis l'utiliser pour arrêter une tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="c407f-133">Contrairement au nom de la tâche, qui n'est pas unique, l'ID d'instance est unique.</span><span class="sxs-lookup"><span data-stu-id="c407f-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

### <span data-ttu-id="c407f-134">Exemple 3 : obtenir des travaux qui incluent une commande spécifique</span><span class="sxs-lookup"><span data-stu-id="c407f-134">Example 3: Get jobs that include a specific command</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

<span data-ttu-id="c407f-135">Cette commande obtient les tâches du système qui incluent une commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="c407f-135">This command gets the jobs on the system that include a Get-Process command.</span></span>
<span data-ttu-id="c407f-136">La commande utilise le paramètre *Command* de **Get-Job** pour limiter le nombre de tâches récupérées.</span><span class="sxs-lookup"><span data-stu-id="c407f-136">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span>
<span data-ttu-id="c407f-137">La commande utilise des caractères génériques (\*) pour obtenir les tâches qui incluent une commande **« obtenir un processus »** n’importe où dans la chaîne de commande.</span><span class="sxs-lookup"><span data-stu-id="c407f-137">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="c407f-138">Exemple 4 : obtenir des travaux qui incluent une commande spécifique à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="c407f-138">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

<span data-ttu-id="c407f-139">À l’instar de la commande dans l’exemple précédent, cette commande obtient les tâches du système qui incluent une commande **« obtenir-traiter »** .</span><span class="sxs-lookup"><span data-stu-id="c407f-139">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span>
<span data-ttu-id="c407f-140">La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne, entre guillemets, à l’applet de commande **« obtenir-Job »** .</span><span class="sxs-lookup"><span data-stu-id="c407f-140">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span>
<span data-ttu-id="c407f-141">Elle est équivalente à la commande précédente.</span><span class="sxs-lookup"><span data-stu-id="c407f-141">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="c407f-142">Exemple 5 : obtenir des travaux qui n’ont pas été démarrés</span><span class="sxs-lookup"><span data-stu-id="c407f-142">Example 5: Get jobs that have not been started</span></span>

```
PS C:\> Get-Job -State NotStarted
```

<span data-ttu-id="c407f-143">Cette commande obtient uniquement les tâches qui ont été créées mais qui n'ont pas encore démarré.</span><span class="sxs-lookup"><span data-stu-id="c407f-143">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="c407f-144">Cela inclut les tâches dont l'exécution est planifiée ultérieurement et celles qui ne sont pas encore planifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-144">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="c407f-145">Exemple 6 : obtenir des travaux auxquels aucun nom n’a été attribué</span><span class="sxs-lookup"><span data-stu-id="c407f-145">Example 6: Get jobs that have not been assigned a name</span></span>

```
PS C:\> Get-Job -Name Job*
```

<span data-ttu-id="c407f-146">Cette commande obtient toutes les tâches dont le nom commence par Job.</span><span class="sxs-lookup"><span data-stu-id="c407f-146">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="c407f-147">Étant donné que Job \<number\> est le nom par défaut d’une tâche, cette commande obtient toutes les tâches qui n’ont pas de nom explicitement attribué.</span><span class="sxs-lookup"><span data-stu-id="c407f-147">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="c407f-148">Exemple 7 : utiliser un objet de traitement pour représenter la tâche dans une commande</span><span class="sxs-lookup"><span data-stu-id="c407f-148">Example 7: Use a job object to represent the job in a command</span></span>

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="c407f-149">Cet exemple illustre comment utiliser **Get-Job** pour obtenir une tâche, puis comment utiliser l'objet de traitement pour représenter la tâche dans une commande.</span><span class="sxs-lookup"><span data-stu-id="c407f-149">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

### <span data-ttu-id="c407f-150">Exemple 8 : obtenir tous les travaux, y compris les travaux démarrés par une autre méthode</span><span class="sxs-lookup"><span data-stu-id="c407f-150">Example 8: Get all jobs including jobs started by a different method</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="c407f-151">Cet exemple montre que l’applet de commande **« obtient-Job »** peut récupérer toutes les tâches qui ont été démarrées dans la session active, même si elles ont été démarrées à l’aide de différentes méthodes.</span><span class="sxs-lookup"><span data-stu-id="c407f-151">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

### <span data-ttu-id="c407f-152">Exemple 9 : examiner un travail ayant échoué</span><span class="sxs-lookup"><span data-stu-id="c407f-152">Example 9: Investigate a failed job</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
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

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

<span data-ttu-id="c407f-153">Cette commande montre comment utiliser l’objet de traitement retourné par la **fonction-Job** pour déterminer la raison de l’échec d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-153">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="c407f-154">Elle illustre également comment obtenir les tâches enfant de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-154">It also shows how to get the child jobs of each job.</span></span>

### <span data-ttu-id="c407f-155">Exemple 10 : obtenir des résultats filtrés</span><span class="sxs-lookup"><span data-stu-id="c407f-155">Example 10: Get filtered results</span></span>

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="c407f-156">Cet exemple indique comment utiliser le paramètre *Filter* pour obtenir une tâche de workflow.</span><span class="sxs-lookup"><span data-stu-id="c407f-156">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="c407f-157">Le paramètre *Filter* , introduit dans Windows PowerShell 3.0, n'est valide que sur les types de tâche personnalisé, comme les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-157">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

### <span data-ttu-id="c407f-158">Exemple 11 : obtenir des informations sur les tâches enfants</span><span class="sxs-lookup"><span data-stu-id="c407f-158">Example 11: Get information about child jobs</span></span>

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
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

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="c407f-159">Cet exemple illustre l'utilisation des paramètres *IncludeChildJob* et *ChildJobState* de l'applet de commande **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="c407f-159">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

## <span data-ttu-id="c407f-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c407f-160">PARAMETERS</span></span>

### <span data-ttu-id="c407f-161">-Après</span><span class="sxs-lookup"><span data-stu-id="c407f-161">-After</span></span>

<span data-ttu-id="c407f-162">Obtient les tâches terminées après la date et l'heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-162">Gets completed jobs that ended after the specified date and time.</span></span>
<span data-ttu-id="c407f-163">Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date ou une chaîne qui peut être convertie en un objet **DateTime** , tel que `Dec 1, 2012 2:00 AM` ou `11/06` .</span><span class="sxs-lookup"><span data-stu-id="c407f-163">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="c407f-164">Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** .</span><span class="sxs-lookup"><span data-stu-id="c407f-164">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="c407f-165">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c407f-165">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="c407f-166">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-166">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="c407f-167">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-167">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c407f-168">-Avant</span><span class="sxs-lookup"><span data-stu-id="c407f-168">-Before</span></span>

<span data-ttu-id="c407f-169">Obtient les tâches terminées avant la date et l'heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-169">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="c407f-170">Entrez un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="c407f-170">Enter a **DateTime** object.</span></span>

<span data-ttu-id="c407f-171">Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** .</span><span class="sxs-lookup"><span data-stu-id="c407f-171">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="c407f-172">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c407f-172">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="c407f-173">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-173">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="c407f-174">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c407f-175">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="c407f-175">-ChildJobState</span></span>

<span data-ttu-id="c407f-176">Obtient uniquement les tâches enfant dans l'état spécifié.</span><span class="sxs-lookup"><span data-stu-id="c407f-176">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="c407f-177">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c407f-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c407f-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="c407f-178">NotStarted</span></span>
- <span data-ttu-id="c407f-179">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="c407f-179">Running</span></span>
- <span data-ttu-id="c407f-180">Completed</span><span class="sxs-lookup"><span data-stu-id="c407f-180">Completed</span></span>
- <span data-ttu-id="c407f-181">Échec</span><span class="sxs-lookup"><span data-stu-id="c407f-181">Failed</span></span>
- <span data-ttu-id="c407f-182">Arrêté</span><span class="sxs-lookup"><span data-stu-id="c407f-182">Stopped</span></span>
- <span data-ttu-id="c407f-183">Bloqué</span><span class="sxs-lookup"><span data-stu-id="c407f-183">Blocked</span></span>
- <span data-ttu-id="c407f-184">Interrompu</span><span class="sxs-lookup"><span data-stu-id="c407f-184">Suspended</span></span>
- <span data-ttu-id="c407f-185">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="c407f-185">Disconnected</span></span>
- <span data-ttu-id="c407f-186">Suspension</span><span class="sxs-lookup"><span data-stu-id="c407f-186">Suspending</span></span>
- <span data-ttu-id="c407f-187">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="c407f-187">Stopping</span></span>

<span data-ttu-id="c407f-188">Par défaut, **Get-Job** n'obtient pas les tâches enfant.</span><span class="sxs-lookup"><span data-stu-id="c407f-188">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="c407f-189">En utilisant le paramètre *IncludeChildJob* , la **fonction « obtenir-Job »** obtient toutes les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="c407f-189">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="c407f-190">Si vous utilisez le paramètre *ChildJobState* , le paramètre *IncludeChildJob* n'a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="c407f-190">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="c407f-191">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c407f-192">-Command</span><span class="sxs-lookup"><span data-stu-id="c407f-192">-Command</span></span>

<span data-ttu-id="c407f-193">Spécifie un tableau de commandes sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c407f-193">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="c407f-194">Cette applet de commande obtient les tâches qui incluent les commandes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-194">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="c407f-195">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="c407f-195">The default is all jobs.</span></span>
<span data-ttu-id="c407f-196">Vous pouvez utiliser des caractères génériques pour spécifier un modèle de commande.</span><span class="sxs-lookup"><span data-stu-id="c407f-196">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="c407f-197">-Filter</span><span class="sxs-lookup"><span data-stu-id="c407f-197">-Filter</span></span>

<span data-ttu-id="c407f-198">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="c407f-198">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="c407f-199">Cette applet de commande obtient les tâches qui répondent à toutes les conditions.</span><span class="sxs-lookup"><span data-stu-id="c407f-199">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="c407f-200">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="c407f-200">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="c407f-201">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c407f-201">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="c407f-202">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c407f-202">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="c407f-203">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-203">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="c407f-204">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c407f-205">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="c407f-205">-HasMoreData</span></span>

<span data-ttu-id="c407f-206">Indique si cette applet de commande obtient uniquement les tâches qui ont la valeur de propriété **HasMoreData** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c407f-206">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="c407f-207">La propriété **HasMoreData** indique si tous les résultats de la tâche ont été reçus dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-207">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="c407f-208">Pour obtenir des travaux qui ont plus de résultats, spécifiez la valeur $True.</span><span class="sxs-lookup"><span data-stu-id="c407f-208">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="c407f-209">Pour obtenir des travaux qui n’ont pas plus de résultats, spécifiez une valeur de $False.</span><span class="sxs-lookup"><span data-stu-id="c407f-209">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="c407f-210">Pour obtenir les résultats d’un travail, utilisez l’applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="c407f-210">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="c407f-211">Lorsque vous utilisez l’applet de commande **Receive-Job** , elle supprime de son stockage propre à la session les résultats renvoyés.</span><span class="sxs-lookup"><span data-stu-id="c407f-211">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span>
<span data-ttu-id="c407f-212">Lorsqu’il a retourné tous les résultats de la tâche dans la session active, il définit la valeur de la propriété **HasMoreData** du travail sur $false) pour indiquer qu’il n’a plus de résultats pour le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-212">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span>
<span data-ttu-id="c407f-213">Utilisez le paramètre *Keep* de **Receive-Job** pour empêcher **Receive-Job** de supprimer des résultats et de modifier la valeur de la propriété **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="c407f-213">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="c407f-214">Pour plus d'informations, voir `Get-Help Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="c407f-214">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="c407f-215">La propriété **HasMoreData** est propre à la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-215">The **HasMoreData** property is specific to the current session.</span></span>
<span data-ttu-id="c407f-216">Si les résultats d’un type de tâche personnalisé sont enregistrés en dehors de la session, comme le type de tâche planifiée qui enregistre les résultats du travail sur le disque, vous pouvez utiliser l’applet de commande **Receive-Job** dans une autre session pour obtenir les résultats de la tâche, même si la valeur de **HasMoreData** est $false.</span><span class="sxs-lookup"><span data-stu-id="c407f-216">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span>
<span data-ttu-id="c407f-217">Pour plus d'informations, consultez les rubriques d'aide du type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c407f-217">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="c407f-218">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-218">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c407f-219">-Id</span><span class="sxs-lookup"><span data-stu-id="c407f-219">-Id</span></span>

<span data-ttu-id="c407f-220">Spécifie un tableau d’ID des travaux que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="c407f-220">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="c407f-221">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-221">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="c407f-222">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-222">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="c407f-223">Vous pouvez taper un ou plusieurs ID séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c407f-223">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="c407f-224">Pour Rechercher l’ID d’un travail, tapez `Get-Job` sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="c407f-224">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="c407f-225">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="c407f-225">-IncludeChildJob</span></span>

<span data-ttu-id="c407f-226">Indique que cette applet de commande retourne des travaux enfants, en plus des travaux parents.</span><span class="sxs-lookup"><span data-stu-id="c407f-226">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="c407f-227">Ce paramètre est particulièrement utile pour examiner les tâches de workflow, pour lesquelles l’opération d' **extraction** de travail retourne un travail parent de conteneur et les échecs de travaux, car la raison de l’échec est enregistrée dans une propriété du travail enfant.</span><span class="sxs-lookup"><span data-stu-id="c407f-227">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="c407f-228">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c407f-229">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="c407f-229">-InstanceId</span></span>

<span data-ttu-id="c407f-230">Spécifie un tableau d’ID d’instance des travaux que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="c407f-230">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="c407f-231">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="c407f-231">The default is all jobs.</span></span>

<span data-ttu-id="c407f-232">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c407f-232">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="c407f-233">Pour rechercher l'ID d'instance d'une tâche, utilisez **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="c407f-233">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="c407f-234">-Name</span><span class="sxs-lookup"><span data-stu-id="c407f-234">-Name</span></span>

<span data-ttu-id="c407f-235">Spécifie un tableau de noms conviviaux d’instance des travaux que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="c407f-235">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="c407f-236">Entrez un nom de tâche ou utilisez des caractères génériques pour entrer un modèle de nom de tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-236">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="c407f-237">Par défaut, **Get-Job** obtient toutes les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-237">By default, **Get-Job** gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="c407f-238">-Plus récent</span><span class="sxs-lookup"><span data-stu-id="c407f-238">-Newest</span></span>

<span data-ttu-id="c407f-239">Spécifie un nombre de travaux à obtenir.</span><span class="sxs-lookup"><span data-stu-id="c407f-239">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="c407f-240">Cette applet de commande obtient les tâches qui ont été terminées en dernier.</span><span class="sxs-lookup"><span data-stu-id="c407f-240">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="c407f-241">Le paramètre *Newest* ne trie pas ni ne retourne les tâches les plus récentes selon l'heure de fin.</span><span class="sxs-lookup"><span data-stu-id="c407f-241">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="c407f-242">Pour trier la sortie, utilisez l’applet de commande Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="c407f-242">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="c407f-243">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c407f-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c407f-244">-État</span><span class="sxs-lookup"><span data-stu-id="c407f-244">-State</span></span>

<span data-ttu-id="c407f-245">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="c407f-245">Specifies a job state.</span></span>
<span data-ttu-id="c407f-246">Cette applet de commande obtient uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="c407f-246">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="c407f-247">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c407f-247">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c407f-248">NotStarted</span><span class="sxs-lookup"><span data-stu-id="c407f-248">NotStarted</span></span>
- <span data-ttu-id="c407f-249">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="c407f-249">Running</span></span>
- <span data-ttu-id="c407f-250">Completed</span><span class="sxs-lookup"><span data-stu-id="c407f-250">Completed</span></span>
- <span data-ttu-id="c407f-251">Échec</span><span class="sxs-lookup"><span data-stu-id="c407f-251">Failed</span></span>
- <span data-ttu-id="c407f-252">Arrêté</span><span class="sxs-lookup"><span data-stu-id="c407f-252">Stopped</span></span>
- <span data-ttu-id="c407f-253">Bloqué</span><span class="sxs-lookup"><span data-stu-id="c407f-253">Blocked</span></span>
- <span data-ttu-id="c407f-254">Interrompu</span><span class="sxs-lookup"><span data-stu-id="c407f-254">Suspended</span></span>
- <span data-ttu-id="c407f-255">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="c407f-255">Disconnected</span></span>
- <span data-ttu-id="c407f-256">Suspension</span><span class="sxs-lookup"><span data-stu-id="c407f-256">Suspending</span></span>
- <span data-ttu-id="c407f-257">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="c407f-257">Stopping</span></span>

<span data-ttu-id="c407f-258">Par défaut, **Get-Job** obtient toutes les tâches de la session active.</span><span class="sxs-lookup"><span data-stu-id="c407f-258">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="c407f-259">Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="c407f-259">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="c407f-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c407f-260">CommonParameters</span></span>

<span data-ttu-id="c407f-261">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c407f-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c407f-262">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c407f-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c407f-263">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c407f-263">INPUTS</span></span>

### <span data-ttu-id="c407f-264">Aucun</span><span class="sxs-lookup"><span data-stu-id="c407f-264">None</span></span>

<span data-ttu-id="c407f-265">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c407f-265">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c407f-266">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c407f-266">OUTPUTS</span></span>

### <span data-ttu-id="c407f-267">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="c407f-267">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="c407f-268">Cette applet de commande retourne des objets qui représentent les tâches dans la session.</span><span class="sxs-lookup"><span data-stu-id="c407f-268">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="c407f-269">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c407f-269">NOTES</span></span>

* <span data-ttu-id="c407f-270">La propriété **PSJobTypeName** des tâches indique le type de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-270">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="c407f-271">La valeur de propriété est déterminée par l'auteur du type de tâche.</span><span class="sxs-lookup"><span data-stu-id="c407f-271">The property value is determined by the job type author.</span></span> <span data-ttu-id="c407f-272">La liste suivante affiche les types de tâches courants.</span><span class="sxs-lookup"><span data-stu-id="c407f-272">The following list shows common job types.</span></span>

  - <span data-ttu-id="c407f-273">**BackgroundJob** .</span><span class="sxs-lookup"><span data-stu-id="c407f-273">**BackgroundJob** .</span></span>
<span data-ttu-id="c407f-274">Tâche locale démarrée à l’aide de **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c407f-274">Local job started by using **Start-Job** .</span></span>

  - <span data-ttu-id="c407f-275">**RemoteJob** .</span><span class="sxs-lookup"><span data-stu-id="c407f-275">**RemoteJob** .</span></span>
<span data-ttu-id="c407f-276">La tâche a démarré dans une **session PSSession** à l’aide du paramètre *AsJob* de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="c407f-276">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="c407f-277">**PSWorkflowJob** .</span><span class="sxs-lookup"><span data-stu-id="c407f-277">**PSWorkflowJob** .</span></span>
<span data-ttu-id="c407f-278">tâche démarrée à l'aide du paramètre *AsJob* commun des workflows.</span><span class="sxs-lookup"><span data-stu-id="c407f-278">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="c407f-279">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c407f-279">RELATED LINKS</span></span>

[<span data-ttu-id="c407f-280">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c407f-280">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="c407f-281">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-281">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="c407f-282">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-282">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="c407f-283">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-283">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="c407f-284">Start-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-284">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="c407f-285">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-285">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="c407f-286">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-286">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="c407f-287">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="c407f-287">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="c407f-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="c407f-288">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="c407f-289">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="c407f-289">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="c407f-290">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="c407f-290">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="c407f-291">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="c407f-291">about_Scheduled_Jobs</span></span>](../PSScheduledJob/About/about_Scheduled_Jobs.md)
