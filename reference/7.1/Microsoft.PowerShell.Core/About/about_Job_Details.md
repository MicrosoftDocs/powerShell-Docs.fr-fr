---
description: Fournit des détails sur les tâches en arrière-plan sur les ordinateurs locaux et distants.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: e334d71951808265a82e1cd7c7e973e7ea67771c
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208581"
---
# <a name="about-job-details"></a><span data-ttu-id="2ad31-104">À propos des détails de la tâche</span><span class="sxs-lookup"><span data-stu-id="2ad31-104">About Job Details</span></span>

## <a name="short-description"></a><span data-ttu-id="2ad31-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="2ad31-105">Short description</span></span>
<span data-ttu-id="2ad31-106">Fournit des détails sur les tâches en arrière-plan sur les ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-106">Provides details about background jobs on local and remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="2ad31-107">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="2ad31-107">Detailed description</span></span>

<span data-ttu-id="2ad31-108">Cette rubrique explique le concept de tâche en arrière-plan et fournit des informations techniques sur le fonctionnement des tâches en arrière-plan dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ad31-108">This topic explains the concept of a background job and provides technical information about how background jobs work in PowerShell.</span></span>

<span data-ttu-id="2ad31-109">Cette rubrique est un complément des rubriques [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md)et [about_Remote_Jobs](about_Remote_Jobs.md) .</span><span class="sxs-lookup"><span data-stu-id="2ad31-109">This topic is a supplement to the [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md), and [about_Remote_Jobs](about_Remote_Jobs.md) topics.</span></span>

### <a name="about-background-jobs"></a><span data-ttu-id="2ad31-110">À propos des tâches en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="2ad31-110">About background jobs</span></span>

<span data-ttu-id="2ad31-111">Une tâche en arrière-plan exécute une commande ou une expression de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="2ad31-111">A background job runs a command or expression asynchronously.</span></span> <span data-ttu-id="2ad31-112">Il peut exécuter une applet de commande, une fonction, un script ou toute autre tâche basée sur une commande.</span><span class="sxs-lookup"><span data-stu-id="2ad31-112">It might run a cmdlet, a function, a script, or any other command-based task.</span></span> <span data-ttu-id="2ad31-113">Il est conçu pour exécuter des commandes qui prennent un certain temps, mais vous pouvez l’utiliser pour exécuter n’importe quelle commande en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2ad31-113">It is designed to run commands that take an extended period of time, but you can use it to run any command in the background.</span></span>

<span data-ttu-id="2ad31-114">Lorsqu’une commande synchrone s’exécute, l’invite de commandes PowerShell est supprimée jusqu’à ce que la commande soit terminée.</span><span class="sxs-lookup"><span data-stu-id="2ad31-114">When a synchronous command runs, the PowerShell command prompt is suppressed until the command is complete.</span></span> <span data-ttu-id="2ad31-115">Toutefois, un travail en arrière-plan ne supprime pas l’invite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ad31-115">But a background job does not suppress the PowerShell prompt.</span></span> <span data-ttu-id="2ad31-116">Une commande permettant de démarrer une tâche en arrière-plan retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="2ad31-116">A command to start a background job returns a job object.</span></span>
<span data-ttu-id="2ad31-117">L’invite s’affiche immédiatement pour vous permettre de travailler sur d’autres tâches pendant l’exécution de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="2ad31-117">The prompt returns immediately so you can work on other tasks while the background job runs.</span></span>

<span data-ttu-id="2ad31-118">Toutefois, lorsque vous démarrez une tâche en arrière-plan, vous ne recevez pas les résultats immédiatement, même si le travail s’exécute très rapidement.</span><span class="sxs-lookup"><span data-stu-id="2ad31-118">However, when you start a background job, you do not get the results immediately even if the job runs very quickly.</span></span> <span data-ttu-id="2ad31-119">L’objet de traitement retourné contient des informations utiles sur la tâche, mais elle ne contient pas les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="2ad31-119">The job object that is returned contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="2ad31-120">Vous devez exécuter une commande distincte pour obtenir les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="2ad31-120">You must run a separate command to get the job results.</span></span> <span data-ttu-id="2ad31-121">Vous pouvez également exécuter des commandes pour arrêter la tâche, attendre la fin de la tâche et supprimer la tâche.</span><span class="sxs-lookup"><span data-stu-id="2ad31-121">You can also run commands to stop the job, to wait for the job to be completed, and to delete the job.</span></span>

<span data-ttu-id="2ad31-122">Pour effectuer la synchronisation d’un travail en arrière-plan indépendamment d’autres commandes, chaque travail en arrière-plan s’exécute dans sa propre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ad31-122">To make the timing of a background job independent of other commands, each background job runs in its own PowerShell session.</span></span> <span data-ttu-id="2ad31-123">Toutefois, il peut s’agir d’une connexion temporaire qui est créée uniquement pour exécuter le travail et qui est ensuite détruite, ou il peut s’agir d’une **session PSSession** permanente que vous pouvez utiliser pour exécuter plusieurs tâches ou commandes associées.</span><span class="sxs-lookup"><span data-stu-id="2ad31-123">However, this can be a temporary connection that is created only to run the job and is then destroyed, or it can be a persistent **PSSession** that you can use to run several related jobs or commands.</span></span>

### <a name="using-the-job-cmdlets"></a><span data-ttu-id="2ad31-124">Utilisation des applets de commande Job</span><span class="sxs-lookup"><span data-stu-id="2ad31-124">Using the job cmdlets</span></span>

<span data-ttu-id="2ad31-125">Utilisez une `Start-Job` commande pour démarrer une tâche en arrière-plan sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2ad31-125">Use a `Start-Job` command to start a background job on a local computer.</span></span>
<span data-ttu-id="2ad31-126">`Start-Job` retourne un objet de traitement.</span><span class="sxs-lookup"><span data-stu-id="2ad31-126">`Start-Job` returns a job object.</span></span> <span data-ttu-id="2ad31-127">Vous pouvez également récupérer des objets représentant les tâches qui ont été démarrées sur l’ordinateur local à l’aide de l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-127">You can also get objects representing the jobs that were started on the local computer using the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="2ad31-128">Pour obtenir les résultats du travail, utilisez une `Receive-Job` commande.</span><span class="sxs-lookup"><span data-stu-id="2ad31-128">To get the job results, use a `Receive-Job` command.</span></span> <span data-ttu-id="2ad31-129">Si la tâche n’est pas terminée, `Receive-Job` retourne des résultats partiels.</span><span class="sxs-lookup"><span data-stu-id="2ad31-129">If the job is not complete, `Receive-Job` returns partial results.</span></span> <span data-ttu-id="2ad31-130">Vous pouvez également utiliser l' `Wait-Job` applet de commande pour supprimer l’invite de commandes jusqu’à ce qu’une ou toutes les tâches démarrées dans la session soient terminées.</span><span class="sxs-lookup"><span data-stu-id="2ad31-130">You can also use the `Wait-Job` cmdlet to suppress the command prompt until one or all of the jobs that were started in the session are complete.</span></span>

<span data-ttu-id="2ad31-131">Pour arrêter une tâche en arrière-plan, utilisez l’applet de commande `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-131">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="2ad31-132">Pour supprimer un travail, utilisez l' `Remove-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2ad31-132">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="2ad31-133">Pour plus d’informations sur le fonctionnement des applets de commande, consultez la rubrique d’aide pour chaque applet de commande et consultez [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2ad31-133">For more information about how the cmdlets work, see the Help topic for each cmdlet, and see [about_Jobs](about_Jobs.md).</span></span>

### <a name="starting-background-jobs-on-remote-computers"></a><span data-ttu-id="2ad31-134">Démarrage des tâches en arrière-plan sur des ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="2ad31-134">Starting background jobs on remote computers</span></span>

<span data-ttu-id="2ad31-135">Vous pouvez créer et gérer des tâches en arrière-plan sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="2ad31-135">You can create and manage background jobs on a local or remote computer.</span></span> <span data-ttu-id="2ad31-136">Pour exécuter une tâche en arrière-plan à distance, utilisez le paramètre **AsJob** d’une applet de commande telle que `Invoke-Command` , ou utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="2ad31-136">To run a background job remotely, use the **AsJob** parameter of a cmdlet such as `Invoke-Command`, or use the `Invoke-Command` cmdlet to run a `Start-Job` command remotely.</span></span> <span data-ttu-id="2ad31-137">Vous pouvez également démarrer une tâche en arrière-plan dans une session interactive.</span><span class="sxs-lookup"><span data-stu-id="2ad31-137">You can also start a background job in an interactive session.</span></span>

<span data-ttu-id="2ad31-138">Pour plus d’informations sur les travaux en arrière-plan distants, consultez [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2ad31-138">For more information about remote background jobs, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>

### <a name="child-jobs"></a><span data-ttu-id="2ad31-139">Travaux enfants</span><span class="sxs-lookup"><span data-stu-id="2ad31-139">Child jobs</span></span>

<span data-ttu-id="2ad31-140">Chaque travail en arrière-plan est constitué d’un travail parent et d’un ou plusieurs travaux enfants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-140">Each background job consists of a parent job and one or more child jobs.</span></span> <span data-ttu-id="2ad31-141">Dans les tâches démarrées à l’aide `Start-Job` de ou du paramètre **AsJob** de `Invoke-Command` , le travail parent est un dirigeant.</span><span class="sxs-lookup"><span data-stu-id="2ad31-141">In jobs started using `Start-Job` or the **AsJob** parameter of `Invoke-Command`, the parent job is an executive.</span></span> <span data-ttu-id="2ad31-142">Elle n’exécute aucune commande et ne retourne aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="2ad31-142">It does not run any commands or return any results.</span></span> <span data-ttu-id="2ad31-143">Les commandes sont exécutées en fait par les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-143">The commands are actually run by the child jobs.</span></span> <span data-ttu-id="2ad31-144">Les travaux démarrés à l’aide d’autres applets de commande peuvent fonctionner différemment.</span><span class="sxs-lookup"><span data-stu-id="2ad31-144">Jobs started using other cmdlets might work differently.</span></span>

<span data-ttu-id="2ad31-145">Les tâches enfants sont stockées dans la propriété **ChildJobs** de l’objet de tâche parent.</span><span class="sxs-lookup"><span data-stu-id="2ad31-145">The child jobs are stored in the **ChildJobs** property of the parent job object.</span></span> <span data-ttu-id="2ad31-146">La propriété **ChildJobs** peut contenir un ou plusieurs objets de tâche enfants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-146">The **ChildJobs** property can contain one or many child job objects.</span></span>
<span data-ttu-id="2ad31-147">Les objets de travail enfants ont un **nom** , un **ID** et un **InstanceID** qui diffèrent du travail parent, ce qui vous permet de gérer les travaux parent et enfant individuellement ou en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="2ad31-147">The child job objects have a **Name** , **ID** , and **InstanceId** that differ from the parent job so that you can manage the parent and child jobs individually or as a unit.</span></span>

<span data-ttu-id="2ad31-148">Pour obtenir les tâches parent et enfant d’un travail, utilisez le paramètre **IncludeChildJobs** de l' `Get-Job` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2ad31-148">To get the parent and child jobs of a job, use the **IncludeChildJobs** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="2ad31-149">Le paramètre **IncludeChildJob** a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ad31-149">The **IncludeChildJob** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="2ad31-150">Pour obtenir le travail parent et uniquement les tâches enfants avec une valeur d' **État** particulière, utilisez le paramètre **ChildJobState** de l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-150">To get the parent job and only the child jobs with a particular **State** value, use the **ChildJobState** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="2ad31-151">Le paramètre **ChildJobState** a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ad31-151">The **ChildJobState** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="2ad31-152">Pour obtenir les tâches enfants d’un travail sur toutes les versions de PowerShell, utilisez la propriété **ChildJob** de la tâche parente.</span><span class="sxs-lookup"><span data-stu-id="2ad31-152">To get the child jobs of a job on all versions of PowerShell, use the **ChildJob** property of the parent job.</span></span>

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="2ad31-153">Vous pouvez également utiliser une `Get-Job` commande sur le travail enfant, comme indiqué dans la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2ad31-153">You can also use a `Get-Job` command on the child job, as shown in the following command:</span></span>

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="2ad31-154">La configuration du travail enfant dépend de la commande que vous utilisez pour démarrer le travail.</span><span class="sxs-lookup"><span data-stu-id="2ad31-154">The configuration of the child job depends on the command that you use to start the job.</span></span>

- <span data-ttu-id="2ad31-155">Lorsque vous utilisez `Start-Job` pour démarrer un travail sur un ordinateur local, le travail se compose d’un travail parent exécutif et d’un travail enfant qui exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="2ad31-155">When you use `Start-Job` to start a job on a local computer, the job consists of an executive parent job and a child job that runs the command.</span></span>

- <span data-ttu-id="2ad31-156">Quand vous utilisez le paramètre **AsJob** de `Invoke-Command` pour démarrer un travail sur un ou plusieurs ordinateurs, le travail se compose d’un travail parent et d’un travail enfant pour chaque travail exécuté sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ad31-156">When you use the **AsJob** parameter of `Invoke-Command` to start a job on one or more computers, the job consists of an executive parent job and a child job for each job run on each computer.</span></span>

- <span data-ttu-id="2ad31-157">Lorsque vous utilisez `Invoke-Command` pour exécuter une `Start-Job` commande sur un ou plusieurs ordinateurs distants, le résultat est le même qu’une commande locale exécutée sur chaque ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2ad31-157">When you use `Invoke-Command` to run a `Start-Job` command on one or more remote computers, the result is the same as a local command run on each remote computer.</span></span> <span data-ttu-id="2ad31-158">La commande retourne un objet de traitement pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ad31-158">The command returns a job object for each computer.</span></span> <span data-ttu-id="2ad31-159">L’objet de traitement est constitué d’un travail parent et d’un travail enfant qui exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="2ad31-159">The job object consists of an executive parent job and one child job that runs the command.</span></span>

<span data-ttu-id="2ad31-160">La tâche parente représente toutes les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-160">The parent job represents all of the child jobs.</span></span> <span data-ttu-id="2ad31-161">Lorsque vous gérez un travail parent, vous gérez également les tâches enfants associées.</span><span class="sxs-lookup"><span data-stu-id="2ad31-161">When you manage a parent job, you also manage the associated child jobs.</span></span> <span data-ttu-id="2ad31-162">Par exemple, si vous arrêtez un travail parent, toutes les tâches enfants sont arrêtées.</span><span class="sxs-lookup"><span data-stu-id="2ad31-162">For example, if you stop a parent job, all child jobs are stopped.</span></span> <span data-ttu-id="2ad31-163">Si vous récupérez les résultats d’une tâche parente, vous pouvez obtenir les résultats de toutes les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-163">If you get the results of a parent job, you get the results of all child jobs.</span></span>

<span data-ttu-id="2ad31-164">Toutefois, vous pouvez également gérer les tâches enfants individuellement.</span><span class="sxs-lookup"><span data-stu-id="2ad31-164">However, you can also manage child jobs individually.</span></span> <span data-ttu-id="2ad31-165">Cela est très utile lorsque vous souhaitez examiner un problème lié à un travail ou obtenir les résultats d’un seul nombre de travaux enfants démarrés à l’aide du paramètre **AsJob** de `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-165">This is most useful when you want to investigate a problem with a job or get the results of only one of a number of child jobs started using the **AsJob** parameter of `Invoke-Command`.</span></span>

<span data-ttu-id="2ad31-166">La commande suivante utilise le paramètre **AsJob** de `Invoke-Command` pour démarrer des tâches en arrière-plan sur l’ordinateur local et sur deux ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="2ad31-166">The following command uses the **AsJob** parameter of `Invoke-Command` to start background jobs on the local computer and two remote computers.</span></span> <span data-ttu-id="2ad31-167">La commande enregistre la tâche dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="2ad31-167">The command saves the job in the `$j` variable.</span></span>

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

<span data-ttu-id="2ad31-168">Lorsque vous affichez les propriétés Name et **ChildJob** de la tâche dans `$j` , elle indique que la commande a retourné un objet de traitement avec trois tâches enfants, une pour chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ad31-168">When you display the Name and **ChildJob** properties of the job in `$j`, it shows that the command returned a job object with three child jobs, one for each computer.</span></span>

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

<span data-ttu-id="2ad31-169">Lorsque vous affichez le travail parent, il indique que le travail a échoué.</span><span class="sxs-lookup"><span data-stu-id="2ad31-169">When you display the parent job, it shows that the job failed.</span></span>

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

<span data-ttu-id="2ad31-170">Toutefois, lorsque vous exécutez une `Get-Job` commande qui obtient les tâches enfants, la sortie indique qu’une seule tâche enfant a échoué.</span><span class="sxs-lookup"><span data-stu-id="2ad31-170">But when you run a `Get-Job` command that gets the child jobs, the output shows that only one child job failed.</span></span>

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

<span data-ttu-id="2ad31-171">Pour obtenir les résultats de toutes les tâches enfants, utilisez l' `Receive-Job` applet de commande pour obtenir les résultats de la tâche parente.</span><span class="sxs-lookup"><span data-stu-id="2ad31-171">To get the results of all child jobs, use the `Receive-Job` cmdlet to get the results of the parent job.</span></span> <span data-ttu-id="2ad31-172">Toutefois, vous pouvez également obtenir les résultats d’un travail enfant particulier, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2ad31-172">But you can also get the results of a particular child job, as shown in the following command.</span></span>

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

<span data-ttu-id="2ad31-173">La fonctionnalité tâches enfants des tâches en arrière-plan PowerShell vous donne davantage de contrôle sur les tâches que vous exécutez.</span><span class="sxs-lookup"><span data-stu-id="2ad31-173">The child jobs feature of PowerShell background jobs gives you more control over the jobs that you run.</span></span>

### <a name="job-types"></a><span data-ttu-id="2ad31-174">Types de travaux</span><span class="sxs-lookup"><span data-stu-id="2ad31-174">Job types</span></span>

<span data-ttu-id="2ad31-175">PowerShell prend en charge différents types de tâches pour différentes tâches.</span><span class="sxs-lookup"><span data-stu-id="2ad31-175">PowerShell supports different types of jobs for different tasks.</span></span> <span data-ttu-id="2ad31-176">À compter de Windows PowerShell 3,0, les développeurs peuvent écrire des « adaptateurs de source de tâche » qui ajoutent de nouveaux types de travaux à PowerShell et incluent les adaptateurs de source de travail dans les modules.</span><span class="sxs-lookup"><span data-stu-id="2ad31-176">Beginning in Windows PowerShell 3.0, developers can write "job source adapters" that add new job types to PowerShell and include the job source adapters in modules.</span></span>
<span data-ttu-id="2ad31-177">Lorsque vous importez le module, vous pouvez utiliser le nouveau type de travail dans votre session.</span><span class="sxs-lookup"><span data-stu-id="2ad31-177">When you import the module, you can use the new job type in your session.</span></span>

<span data-ttu-id="2ad31-178">Par exemple, le module PSScheduledJob ajoute des tâches planifiées et le module PSWorkflow ajoute des tâches de Workflow.</span><span class="sxs-lookup"><span data-stu-id="2ad31-178">For example, the PSScheduledJob module adds scheduled jobs and the PSWorkflow module adds workflow jobs.</span></span>

<span data-ttu-id="2ad31-179">Les types de tâches personnalisées peuvent différer considérablement des tâches en arrière-plan PowerShell standard.</span><span class="sxs-lookup"><span data-stu-id="2ad31-179">Custom jobs types might differ significantly from standard PowerShell background jobs.</span></span> <span data-ttu-id="2ad31-180">Par exemple, les tâches planifiées sont enregistrées sur le disque. ils n’existent pas uniquement dans une session particulière.</span><span class="sxs-lookup"><span data-stu-id="2ad31-180">For example, scheduled jobs are saved on disk; they do not exist only in a particular session.</span></span> <span data-ttu-id="2ad31-181">Les tâches de workflow peuvent être suspendues et reprises.</span><span class="sxs-lookup"><span data-stu-id="2ad31-181">Workflow jobs can be suspended and resumed.</span></span>

<span data-ttu-id="2ad31-182">Les applets de commande que vous utilisez pour gérer les tâches personnalisées dépendent du type de travail.</span><span class="sxs-lookup"><span data-stu-id="2ad31-182">The cmdlets that you use to manage custom jobs depend on the job type.</span></span> <span data-ttu-id="2ad31-183">Pour certains, vous utilisez les applets de commande de tâche standard, telles que `Get-Job` et `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-183">For some, you use the standard job cmdlets, such as `Get-Job` and `Start-Job`.</span></span> <span data-ttu-id="2ad31-184">D’autres sont fournies avec des applets de commande spécialisées qui gèrent uniquement un type particulier de tâche.</span><span class="sxs-lookup"><span data-stu-id="2ad31-184">Others come with specialized cmdlets that manage only a particular type of job.</span></span> <span data-ttu-id="2ad31-185">Pour plus d’informations sur les types de tâches personnalisés, consultez les rubriques d’aide sur le type de travail.</span><span class="sxs-lookup"><span data-stu-id="2ad31-185">For detailed information about custom job types, see the help topics about the job type.</span></span>

<span data-ttu-id="2ad31-186">Pour rechercher le type de tâche d’un travail, utilisez l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-186">To find the job type of a job, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="2ad31-187">`Get-Job` Retourne différents objets de travail pour différents types de travaux.</span><span class="sxs-lookup"><span data-stu-id="2ad31-187">`Get-Job` returns different job objects for different types of jobs.</span></span> <span data-ttu-id="2ad31-188">La valeur de la propriété **PSJobTypeName** des objets de traitement qui `Get-Job` retourne indique le type de travail.</span><span class="sxs-lookup"><span data-stu-id="2ad31-188">The value of the **PSJobTypeName** property of the job objects that `Get-Job` returns indicates the job type.</span></span>

<span data-ttu-id="2ad31-189">Le tableau suivant répertorie les types de travaux fournis avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ad31-189">The following table lists the job types that come with PowerShell.</span></span>

|    <span data-ttu-id="2ad31-190">Type de travail</span><span class="sxs-lookup"><span data-stu-id="2ad31-190">Job Type</span></span>    |                       <span data-ttu-id="2ad31-191">Description</span><span class="sxs-lookup"><span data-stu-id="2ad31-191">Description</span></span>                        |
| -------------- | -------------------------------------------------------- |
| <span data-ttu-id="2ad31-192">BackgroundJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-192">BackgroundJob</span></span>  | <span data-ttu-id="2ad31-193">A démarré à l’aide de l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-193">Started using the `Start-Job` cmdlet.</span></span>                    |
| <span data-ttu-id="2ad31-194">RemoteJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-194">RemoteJob</span></span>      | <span data-ttu-id="2ad31-195">Démarré à l’aide du paramètre **AsJob** de l'</span><span class="sxs-lookup"><span data-stu-id="2ad31-195">Started using the **AsJob** parameter of the</span></span>             |
|                | <span data-ttu-id="2ad31-196">`Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="2ad31-196">`Invoke-Command` cmdlet.</span></span>                                 |
| <span data-ttu-id="2ad31-197">PSWorkflowJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-197">PSWorkflowJob</span></span>  | <span data-ttu-id="2ad31-198">A démarré à l’aide du paramètre **AsJob** d’un Workflow.</span><span class="sxs-lookup"><span data-stu-id="2ad31-198">Started using the **AsJob** parameter of a workflow.</span></span>     |
| <span data-ttu-id="2ad31-199">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-199">PSScheduledJob</span></span> | <span data-ttu-id="2ad31-200">Instance d’une tâche planifiée démarrée par un déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="2ad31-200">An instance of a scheduled job started by a job trigger.</span></span> |
| <span data-ttu-id="2ad31-201">CIMJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-201">CIMJob</span></span>         | <span data-ttu-id="2ad31-202">Démarré à l’aide du paramètre **AsJob** d’une applet de commande à partir d’un</span><span class="sxs-lookup"><span data-stu-id="2ad31-202">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="2ad31-203">Module CDXML.</span><span class="sxs-lookup"><span data-stu-id="2ad31-203">CDXML module.</span></span>                                            |
| <span data-ttu-id="2ad31-204">WMIJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-204">WMIJob</span></span>         | <span data-ttu-id="2ad31-205">Démarré à l’aide du paramètre **AsJob** d’une applet de commande à partir d’un</span><span class="sxs-lookup"><span data-stu-id="2ad31-205">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="2ad31-206">Module WMI.</span><span class="sxs-lookup"><span data-stu-id="2ad31-206">WMI module.</span></span>                                              |
| <span data-ttu-id="2ad31-207">PSEventJob</span><span class="sxs-lookup"><span data-stu-id="2ad31-207">PSEventJob</span></span>     | <span data-ttu-id="2ad31-208">Créé à l’aide `Register-ObjectEvent` de et en spécifiant un</span><span class="sxs-lookup"><span data-stu-id="2ad31-208">Created using`Register-ObjectEvent` and specifying an</span></span>    |
|                | <span data-ttu-id="2ad31-209">action avec le paramètre d' **action** .</span><span class="sxs-lookup"><span data-stu-id="2ad31-209">action with the **Action** parameter.</span></span>                    |

<span data-ttu-id="2ad31-210">Remarque : avant d’utiliser l’applet de commande `Get-Job` pour obtenir des travaux d’un type particulier, vérifiez que le module qui ajoute le type de travail est importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="2ad31-210">NOTE: Before using the `Get-Job` cmdlet to get jobs of a particular type, verify that the module that adds the job type is imported into the current session.</span></span>
<span data-ttu-id="2ad31-211">Dans le cas contraire, `Get-Job` n’obtient pas les travaux de ce type.</span><span class="sxs-lookup"><span data-stu-id="2ad31-211">Otherwise, `Get-Job` does not get jobs of that type.</span></span>

## <a name="examples"></a><span data-ttu-id="2ad31-212">Exemples</span><span class="sxs-lookup"><span data-stu-id="2ad31-212">Examples</span></span>

<span data-ttu-id="2ad31-213">Les commandes suivantes créent une tâche en arrière-plan locale, une tâche en arrière-plan à distance, une tâche de workflow et une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="2ad31-213">The following commands create a local background job, a remote background job, a workflow job, and a scheduled job.</span></span> <span data-ttu-id="2ad31-214">Elle utilise ensuite l' `Get-Job` applet de commande pour récupérer les tâches.</span><span class="sxs-lookup"><span data-stu-id="2ad31-214">Then, it uses the `Get-Job` cmdlet to get the jobs.</span></span> <span data-ttu-id="2ad31-215">`Get-Job` n’obtient pas la tâche planifiée, mais elle obtient toutes les instances démarrées de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="2ad31-215">`Get-Job` does not get the scheduled job, but it gets any started instances of the scheduled job.</span></span>

<span data-ttu-id="2ad31-216">Démarrez une tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2ad31-216">Start a background job on the local computer.</span></span>

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

<span data-ttu-id="2ad31-217">Démarrez une tâche en arrière-plan qui s’exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2ad31-217">Start a background job that runs on a remote computer.</span></span>

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

<span data-ttu-id="2ad31-218">Créer une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="2ad31-218">Create a scheduled job</span></span>

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

<span data-ttu-id="2ad31-219">Créer un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2ad31-219">Create a workflow.</span></span>

```powershell
PS> workflow Test-Workflow {Get-Process}
```

<span data-ttu-id="2ad31-220">Exécutez le workflow en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="2ad31-220">Run the workflow as a job.</span></span>

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

<span data-ttu-id="2ad31-221">Obtient les tâches.</span><span class="sxs-lookup"><span data-stu-id="2ad31-221">Get the jobs.</span></span> <span data-ttu-id="2ad31-222">La `Get-Job` commande n’obtient pas les tâches planifiées, mais elle obtient les instances de la tâche planifiée qui sont démarrées.</span><span class="sxs-lookup"><span data-stu-id="2ad31-222">The `Get-Job` command does not get scheduled jobs, but it gets instances of the scheduled job that are started.</span></span>

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

<span data-ttu-id="2ad31-223">Pour accéder aux tâches planifiées, utilisez l’applet de commande `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="2ad31-223">To get scheduled jobs, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a><span data-ttu-id="2ad31-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ad31-224">See also</span></span>

- [<span data-ttu-id="2ad31-225">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="2ad31-225">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="2ad31-226">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="2ad31-226">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="2ad31-227">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="2ad31-227">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="2ad31-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="2ad31-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="2ad31-229">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2ad31-229">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="2ad31-230">Start-Job</span><span class="sxs-lookup"><span data-stu-id="2ad31-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="2ad31-231">Get-Job</span><span class="sxs-lookup"><span data-stu-id="2ad31-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="2ad31-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="2ad31-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="2ad31-233">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="2ad31-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="2ad31-234">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="2ad31-234">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="2ad31-235">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="2ad31-235">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="2ad31-236">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="2ad31-236">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="2ad31-237">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="2ad31-237">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
