---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595737"
---
# <span data-ttu-id="f7460-102">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="f7460-102">Receive-Job</span></span>

## <span data-ttu-id="f7460-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f7460-103">SYNOPSIS</span></span>
<span data-ttu-id="f7460-104">Obtient les résultats des tâches en arrière-plan PowerShell dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f7460-104">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="f7460-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="f7460-105">SYNTAX</span></span>

### <span data-ttu-id="f7460-106">Emplacement (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f7460-106">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="f7460-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="f7460-107">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="f7460-108">Session</span><span class="sxs-lookup"><span data-stu-id="f7460-108">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="f7460-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7460-109">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f7460-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7460-110">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="f7460-111">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7460-111">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="f7460-112">Description</span><span class="sxs-lookup"><span data-stu-id="f7460-112">DESCRIPTION</span></span>

<span data-ttu-id="f7460-113">L' `Receive-Job` applet de commande obtient les résultats des travaux en arrière-plan PowerShell, tels que ceux démarrés à l’aide de l' `Start-Job` applet de commande ou du paramètre **AsJob** d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f7460-113">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="f7460-114">Vous pouvez obtenir les résultats de toutes les tâches ou identifier les tâches par leur nom, ID, ID d'instance, nom d'ordinateur, emplacement ou session, ou en envoyant un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="f7460-114">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="f7460-115">Quand vous démarrez une tâche en arrière-plan PowerShell, le travail démarre, mais les résultats n’apparaissent pas immédiatement.</span><span class="sxs-lookup"><span data-stu-id="f7460-115">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="f7460-116">À la place, la commande retourne un objet qui représente la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f7460-116">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="f7460-117">L'objet de traitement contient les informations utiles sur la tâche, mais pas les résultats.</span><span class="sxs-lookup"><span data-stu-id="f7460-117">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="f7460-118">Cette méthode vous permet de continuer à travailler dans la session pendant l’exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="f7460-118">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="f7460-119">Pour plus d’informations sur les tâches en arrière-plan dans PowerShell, consultez [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="f7460-119">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="f7460-120">L' `Receive-Job` applet de commande obtient les résultats qui ont été générés au moment de l’envoi de la `Receive-Job` commande.</span><span class="sxs-lookup"><span data-stu-id="f7460-120">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="f7460-121">Si les résultats ne sont pas encore terminés, vous pouvez exécuter des `Receive-Job` commandes supplémentaires pour obtenir les résultats restants.</span><span class="sxs-lookup"><span data-stu-id="f7460-121">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="f7460-122">Par défaut, les résultats de la tâche sont supprimés du système lorsque vous les recevez, mais vous pouvez utiliser le paramètre **Keep** pour enregistrer les résultats afin de les recevoir à nouveau.</span><span class="sxs-lookup"><span data-stu-id="f7460-122">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="f7460-123">Pour supprimer les résultats du travail, exécutez `Receive-Job` à nouveau la commande sans le paramètre **Keep** , fermez la session ou utilisez l' `Remove-Job` applet de commande pour supprimer la tâche de la session.</span><span class="sxs-lookup"><span data-stu-id="f7460-123">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="f7460-124">À compter de Windows PowerShell 3,0, `Receive-Job` obtient également les résultats des types de tâches personnalisées, tels que les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f7460-124">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="f7460-125">Pour permettre `Receive-Job` à d’obtenir les résultats d’un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une `Receive-Job` commande, soit à l’aide de l’applet de commande, soit `Import-Module` en utilisant ou en obtenant une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="f7460-125">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="f7460-126">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7460-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="f7460-127">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f7460-127">EXAMPLES</span></span>

### <span data-ttu-id="f7460-128">Exemple 1 : obtenir les résultats d’une tâche particulière</span><span class="sxs-lookup"><span data-stu-id="f7460-128">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="f7460-129">Ces commandes utilisent le paramètre **Job** de `Receive-Job` pour obtenir les résultats d’une tâche particulière.</span><span class="sxs-lookup"><span data-stu-id="f7460-129">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="f7460-130">La première commande démarre un travail avec `Start-Job` et stocke l’objet de traitement dans la `$job` variable.</span><span class="sxs-lookup"><span data-stu-id="f7460-130">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="f7460-131">La deuxième commande utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="f7460-131">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="f7460-132">Elle utilise le paramètre **Job** pour spécifier la tâche.</span><span class="sxs-lookup"><span data-stu-id="f7460-132">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="f7460-133">Exemple 2 : utiliser le paramètre Keep</span><span class="sxs-lookup"><span data-stu-id="f7460-133">Example 2: Use the Keep parameter</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="f7460-134">Cet exemple stocke un travail dans la `$job` variable et le dirige vers l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="f7460-134">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="f7460-135">Le `-Keep` paramètre est également utilisé pour permettre la récupération de toutes les données de flux agrégées après la première vue.</span><span class="sxs-lookup"><span data-stu-id="f7460-135">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="f7460-136">Exemple 3 : obtenir les résultats de plusieurs tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="f7460-136">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="f7460-137">Quand vous utilisez le paramètre **AsJob** de `Invoke-Command` pour démarrer un travail, l’objet de traitement est créé sur l’ordinateur local, même si le travail s’exécute sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f7460-137">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="f7460-138">Par conséquent, vous utilisez des commandes locales pour gérer la tâche.</span><span class="sxs-lookup"><span data-stu-id="f7460-138">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="f7460-139">En outre, lorsque vous utilisez **AsJob**, PowerShell retourne un objet de traitement qui contient un travail enfant pour chaque travail démarré.</span><span class="sxs-lookup"><span data-stu-id="f7460-139">Also, when you use **AsJob**, PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="f7460-140">Dans ce cas, l'objet de traitement contient trois tâches enfants, une pour chaque tâche sur chaque ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f7460-140">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### <span data-ttu-id="f7460-141">Exemple 4 : obtenir les résultats des tâches en arrière-plan sur plusieurs ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="f7460-141">Example 4: Get results of background jobs on multiple remote computers</span></span>

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

<span data-ttu-id="f7460-142">Cet exemple montre comment obtenir les résultats des tâches en arrière-plan exécutées sur trois ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f7460-142">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="f7460-143">Contrairement à l’exemple précédent, l’utilisation `Invoke-Command` de pour exécuter la `Start-Job` commande a fait démarrer trois tâches indépendantes sur chacun des trois ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f7460-143">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="f7460-144">Par conséquent, la commande a retourné trois objets de travail représentant trois tâches exécutées localement sur trois ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="f7460-144">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="f7460-145">Dans la dernière commande, étant donné que `$j` est une variable locale, le bloc de script utilise le modificateur d’étendue **using** pour identifier la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="f7460-145">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="f7460-146">Pour plus d’informations sur le modificateur d’étendue **using** , consultez [about_Remote_Variables](./About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f7460-146">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="f7460-147">Exemple 5 : accéder aux tâches enfants</span><span class="sxs-lookup"><span data-stu-id="f7460-147">Example 5: Access child jobs</span></span>

<span data-ttu-id="f7460-148">Le `-Keep` paramètre conserve l’état des flux agrégés d’un travail afin qu’il puisse être affiché à nouveau.</span><span class="sxs-lookup"><span data-stu-id="f7460-148">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="f7460-149">Sans ce paramètre, toutes les données de flux agrégées sont effacées lors de la réception du travail.</span><span class="sxs-lookup"><span data-stu-id="f7460-149">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="f7460-150">Pour plus d’informations, consultez [about_Job_Details](About/about_Job_Details.md#child-jobs)</span><span class="sxs-lookup"><span data-stu-id="f7460-150">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="f7460-151">Les flux agrégés incluent les flux de toutes les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="f7460-151">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="f7460-152">Vous pouvez toujours atteindre les flux de données individuels via l’objet de tâche et les objets de travail enfants.</span><span class="sxs-lookup"><span data-stu-id="f7460-152">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="f7460-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7460-153">PARAMETERS</span></span>

### <span data-ttu-id="f7460-154">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="f7460-154">-AutoRemoveJob</span></span>

<span data-ttu-id="f7460-155">Indique que cette applet de commande supprime le travail après avoir retourné les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="f7460-155">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="f7460-156">Si le travail a plus de résultats, le travail est toujours supprimé, mais `Receive-Job` affiche un message.</span><span class="sxs-lookup"><span data-stu-id="f7460-156">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="f7460-157">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f7460-157">This parameter works only on custom job types.</span></span>
<span data-ttu-id="f7460-158">Il est conçu pour les instances de types de tâches qui enregistrent la tâche ou le type en dehors de la session, telles que les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="f7460-158">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="f7460-159">Ce paramètre ne peut pas être utilisé sans le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="f7460-159">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="f7460-160">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f7460-160">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f7460-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f7460-161">-ComputerName</span></span>

<span data-ttu-id="f7460-162">Spécifie un tableau de noms d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f7460-162">Specifies an array of names of computers.</span></span>

<span data-ttu-id="f7460-163">Ce paramètre procède à une sélection parmi les résultats des tâches stockés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f7460-163">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="f7460-164">Il n’obtient pas de données pour les travaux exécutés sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f7460-164">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="f7460-165">Pour obtenir des résultats de travail stockés sur des ordinateurs distants, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="f7460-165">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f7460-166">-Force</span><span class="sxs-lookup"><span data-stu-id="f7460-166">-Force</span></span>

<span data-ttu-id="f7460-167">Indique que cette applet de commande continue à attendre si les tâches sont dans l’état **Suspended** ou **Disconnected** .</span><span class="sxs-lookup"><span data-stu-id="f7460-167">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="f7460-168">Par défaut, le paramètre **Wait** de `Receive-Job` retourne ou met fin à l’attente, lorsque les tâches sont dans l’un des États suivants :</span><span class="sxs-lookup"><span data-stu-id="f7460-168">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="f7460-169">Completed</span><span class="sxs-lookup"><span data-stu-id="f7460-169">Completed</span></span>
- <span data-ttu-id="f7460-170">Échec</span><span class="sxs-lookup"><span data-stu-id="f7460-170">Failed</span></span>
- <span data-ttu-id="f7460-171">Arrêté</span><span class="sxs-lookup"><span data-stu-id="f7460-171">Stopped</span></span>
- <span data-ttu-id="f7460-172">Interrompu</span><span class="sxs-lookup"><span data-stu-id="f7460-172">Suspended</span></span>
- <span data-ttu-id="f7460-173">Déconnecté.</span><span class="sxs-lookup"><span data-stu-id="f7460-173">Disconnected.</span></span>

<span data-ttu-id="f7460-174">Le paramètre **Force** n'est valide que lorsque le paramètre **Wait** est également utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="f7460-174">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="f7460-175">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f7460-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f7460-176">-Id</span><span class="sxs-lookup"><span data-stu-id="f7460-176">-Id</span></span>

<span data-ttu-id="f7460-177">Spécifie un tableau d'ID.</span><span class="sxs-lookup"><span data-stu-id="f7460-177">Specifies an array of IDs.</span></span>
<span data-ttu-id="f7460-178">Cette applet de commande obtient les résultats des tâches avec les ID spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f7460-178">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="f7460-179">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f7460-179">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="f7460-180">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f7460-180">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="f7460-181">Vous pouvez taper un ou plusieurs ID séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f7460-181">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="f7460-182">Pour Rechercher l’ID d’un travail, utilisez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f7460-182">To find the ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="f7460-183">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f7460-183">-InstanceId</span></span>

<span data-ttu-id="f7460-184">Spécifie un tableau d’ID d’instance.</span><span class="sxs-lookup"><span data-stu-id="f7460-184">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="f7460-185">Cette applet de commande obtient les résultats des tâches avec les ID d’instance spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f7460-185">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="f7460-186">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f7460-186">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="f7460-187">Pour Rechercher l’ID d’instance d’un travail, utilisez l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f7460-187">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f7460-188">-Travail</span><span class="sxs-lookup"><span data-stu-id="f7460-188">-Job</span></span>

<span data-ttu-id="f7460-189">Spécifie la tâche pour laquelle les résultats sont récupérés.</span><span class="sxs-lookup"><span data-stu-id="f7460-189">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="f7460-190">Entrez une variable qui contient la tâche ou une commande qui obtient la tâche.</span><span class="sxs-lookup"><span data-stu-id="f7460-190">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="f7460-191">Vous pouvez également diriger un objet de traitement vers `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="f7460-191">You can also pipe a job object to `Receive-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f7460-192">-Conserver</span><span class="sxs-lookup"><span data-stu-id="f7460-192">-Keep</span></span>

<span data-ttu-id="f7460-193">Indique que cette applet de commande enregistre les données de flux agrégées dans le système, même après que vous les avez reçues.</span><span class="sxs-lookup"><span data-stu-id="f7460-193">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="f7460-194">Par défaut, les données de flux agrégées sont effacées après leur affichage avec `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="f7460-194">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="f7460-195">La fermeture de la session ou la suppression de la tâche avec l’applet de commande `Remove-Job` supprime également les données de flux agrégées.</span><span class="sxs-lookup"><span data-stu-id="f7460-195">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

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

### <span data-ttu-id="f7460-196">-Location</span><span class="sxs-lookup"><span data-stu-id="f7460-196">-Location</span></span>

<span data-ttu-id="f7460-197">Spécifie un tableau d’emplacements.</span><span class="sxs-lookup"><span data-stu-id="f7460-197">Specifies an array of locations.</span></span>
<span data-ttu-id="f7460-198">Cette applet de commande obtient uniquement les résultats des tâches aux emplacements spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f7460-198">This cmdlet gets only the results of jobs in the specified locations.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7460-199">-Name</span><span class="sxs-lookup"><span data-stu-id="f7460-199">-Name</span></span>

<span data-ttu-id="f7460-200">Spécifie un tableau de noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="f7460-200">Specifies an array of friendly names.</span></span>
<span data-ttu-id="f7460-201">Cette applet de commande obtient les résultats des tâches qui ont les noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f7460-201">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="f7460-202">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f7460-202">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="f7460-203">-Norécurrent</span><span class="sxs-lookup"><span data-stu-id="f7460-203">-NoRecurse</span></span>

<span data-ttu-id="f7460-204">Indique que cette applet de commande obtient les résultats uniquement à partir du travail spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7460-204">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="f7460-205">Par défaut, `Receive-Job` obtient également les résultats de toutes les tâches enfants du travail spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7460-205">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

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

### <span data-ttu-id="f7460-206">-Session</span><span class="sxs-lookup"><span data-stu-id="f7460-206">-Session</span></span>

<span data-ttu-id="f7460-207">Spécifie un tableau de sessions.</span><span class="sxs-lookup"><span data-stu-id="f7460-207">Specifies an array of sessions.</span></span>
<span data-ttu-id="f7460-208">Cette applet de commande obtient les résultats des tâches qui ont été exécutées dans la session PowerShell spécifiée (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="f7460-208">This cmdlet gets the results of jobs that were run in the specified PowerShell session (**PSSession**).</span></span>
<span data-ttu-id="f7460-209">Entrez une variable qui contient la **session PSSession** ou une commande qui obtient la **session PSSession**, telle qu’une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="f7460-209">Enter a variable that contains the **PSSession** or a command that gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f7460-210">-Wait</span><span class="sxs-lookup"><span data-stu-id="f7460-210">-Wait</span></span>

<span data-ttu-id="f7460-211">Indique que cette applet de commande supprime l’invite de commandes jusqu’à ce que tous les résultats de la tâche soient reçus.</span><span class="sxs-lookup"><span data-stu-id="f7460-211">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="f7460-212">Par défaut, `Receive-Job` retourne immédiatement les résultats disponibles.</span><span class="sxs-lookup"><span data-stu-id="f7460-212">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="f7460-213">Par défaut, le paramètre **Wait** attend jusqu'à ce que la tâche soit dans l'un des états suivants :</span><span class="sxs-lookup"><span data-stu-id="f7460-213">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="f7460-214">Completed</span><span class="sxs-lookup"><span data-stu-id="f7460-214">Completed</span></span>
- <span data-ttu-id="f7460-215">Échec</span><span class="sxs-lookup"><span data-stu-id="f7460-215">Failed</span></span>
- <span data-ttu-id="f7460-216">Arrêté</span><span class="sxs-lookup"><span data-stu-id="f7460-216">Stopped</span></span>
- <span data-ttu-id="f7460-217">Interrompu</span><span class="sxs-lookup"><span data-stu-id="f7460-217">Suspended</span></span>
- <span data-ttu-id="f7460-218">Déconnecté.</span><span class="sxs-lookup"><span data-stu-id="f7460-218">Disconnected.</span></span>

<span data-ttu-id="f7460-219">Pour indiquer au paramètre **Wait** de continuer à attendre si l’état du travail est Suspended ou Disconnected, utilisez le paramètre **force** avec le paramètre **Wait** .</span><span class="sxs-lookup"><span data-stu-id="f7460-219">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="f7460-220">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f7460-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f7460-221">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="f7460-221">-WriteEvents</span></span>

<span data-ttu-id="f7460-222">Indique que cette applet de commande signale les modifications de l’état du travail pendant qu’elle attend la fin du travail.</span><span class="sxs-lookup"><span data-stu-id="f7460-222">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="f7460-223">Ce paramètre est valide uniquement quand le paramètre **Wait** est utilisé dans la commande et que le paramètre **Keep** est omis.</span><span class="sxs-lookup"><span data-stu-id="f7460-223">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="f7460-224">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f7460-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f7460-225">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="f7460-225">-WriteJobInResults</span></span>

<span data-ttu-id="f7460-226">Indique que cette applet de commande retourne l’objet de traitement suivi des résultats.</span><span class="sxs-lookup"><span data-stu-id="f7460-226">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="f7460-227">Ce paramètre est valide uniquement quand le paramètre **Wait** est utilisé dans la commande et que le paramètre **Keep** est omis.</span><span class="sxs-lookup"><span data-stu-id="f7460-227">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="f7460-228">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f7460-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f7460-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7460-229">CommonParameters</span></span>

<span data-ttu-id="f7460-230">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7460-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7460-231">Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="f7460-231">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f7460-232">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f7460-232">INPUTS</span></span>

### <span data-ttu-id="f7460-233">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="f7460-233">System.Management.Automation.Job</span></span>

<span data-ttu-id="f7460-234">Vous pouvez diriger les objets de travail vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f7460-234">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="f7460-235">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f7460-235">OUTPUTS</span></span>

### <span data-ttu-id="f7460-236">PSObject</span><span class="sxs-lookup"><span data-stu-id="f7460-236">PSObject</span></span>

<span data-ttu-id="f7460-237">Cette applet de commande retourne les résultats des commandes dans le travail.</span><span class="sxs-lookup"><span data-stu-id="f7460-237">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="f7460-238">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f7460-238">NOTES</span></span>

## <span data-ttu-id="f7460-239">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f7460-239">RELATED LINKS</span></span>

[<span data-ttu-id="f7460-240">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f7460-240">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="f7460-241">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f7460-241">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f7460-242">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f7460-242">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f7460-243">Start-Job</span><span class="sxs-lookup"><span data-stu-id="f7460-243">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f7460-244">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f7460-244">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="f7460-245">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f7460-245">Wait-Job</span></span>](Wait-Job.md)

