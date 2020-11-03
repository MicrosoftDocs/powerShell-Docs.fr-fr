---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: b69688891df70c396d19911624c58ae7733183d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202618"
---
# <span data-ttu-id="14cf0-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-103">Wait-Job</span></span>

## <span data-ttu-id="14cf0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="14cf0-104">SYNOPSIS</span></span>
<span data-ttu-id="14cf0-105">Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches d’arrière-plan PowerShell en cours d’exécution dans la session soient terminées.</span><span class="sxs-lookup"><span data-stu-id="14cf0-105">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="14cf0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="14cf0-106">SYNTAX</span></span>

### <span data-ttu-id="14cf0-107">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="14cf0-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="14cf0-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="14cf0-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="14cf0-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="14cf0-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="14cf0-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="14cf0-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="14cf0-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="14cf0-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="14cf0-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="14cf0-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="14cf0-113">Description</span><span class="sxs-lookup"><span data-stu-id="14cf0-113">DESCRIPTION</span></span>

<span data-ttu-id="14cf0-114">L’applet de commande **Wait-Job** attend que les tâches en arrière-plan PowerShell se terminent avant d’afficher l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="14cf0-114">The **Wait-Job** cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span>
<span data-ttu-id="14cf0-115">Vous pouvez attendre la fin d'une tâche en arrière-plan donnée ou de toutes les tâches en arrière-plan, et vous pouvez définir un délai d'attente maximal pour la tâche.</span><span class="sxs-lookup"><span data-stu-id="14cf0-115">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="14cf0-116">Quand les commandes figurant dans la tâche sont terminées, **Wait-Job** affiche l'invite de commandes et retourne un objet de traitement pour que vous puissiez la diriger vers une autre commande.</span><span class="sxs-lookup"><span data-stu-id="14cf0-116">When the commands in the job are complete, **Wait-Job** displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="14cf0-117">Vous pouvez utiliser l’applet de commande **Wait-Job** pour attendre des tâches en arrière-plan, telles que celles qui ont été démarrées à l’aide de l’applet de commande Start-Job ou du paramètre *AsJob* de l’applet de commande Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="14cf0-117">You can use **Wait-Job** cmdlet to wait for background jobs, such as those that were started by using the Start-Job cmdlet or the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>
<span data-ttu-id="14cf0-118">Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="14cf0-118">For more information about PowerShell background jobs, see about_Jobs.</span></span>

<span data-ttu-id="14cf0-119">À compter de Windows PowerShell 3,0, l’applet de commande **Wait-Job** attend également des types de tâches personnalisés, tels que les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="14cf0-119">Starting in Windows PowerShell 3.0, the **Wait-Job** cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="14cf0-120">Pour permettre à **Wait-Job** d’attendre des tâches d’un type particulier, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter l’applet de commande Get-Job, à l’aide de l’applet de commande Import-Module ou à l’aide de ou de l’obtention d’une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="14cf0-120">To enable **Wait-Job** to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the Get-Job cmdlet, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="14cf0-121">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="14cf0-121">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="14cf0-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="14cf0-122">EXAMPLES</span></span>

### <span data-ttu-id="14cf0-123">Exemple 1 : attendre tous les travaux</span><span class="sxs-lookup"><span data-stu-id="14cf0-123">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="14cf0-124">Cette commande attend la fin de toutes les tâches en arrière-plan en cours d’exécution dans la session.</span><span class="sxs-lookup"><span data-stu-id="14cf0-124">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="14cf0-125">Exemple 2 : attente des tâches démarrées sur des ordinateurs distants à l’aide de Start-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-125">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="14cf0-126">Cet exemple montre comment utiliser l’applet de commande **Wait-Job** avec des tâches démarrées sur des ordinateurs distants à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-126">This example shows how to use the **Wait-Job** cmdlet with jobs started on remote computers by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="14cf0-127">Les commandes **Start-Job** et **Wait-Job** sont envoyées à l’ordinateur distant à l’aide de l’applet de **commande Invoke-Command** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-127">Both **Start-Job** and **Wait-Job** commands are submitted to the remote computer by using the **Invoke-Command** cmdlet.</span></span>

<span data-ttu-id="14cf0-128">Cet exemple utilise **Wait-Job** pour déterminer si une commande Get-Date s’exécutant en tant que tâche en arrière-plan sur trois ordinateurs différents est terminée.</span><span class="sxs-lookup"><span data-stu-id="14cf0-128">This example uses **Wait-Job** to determine whether a Get-Date command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="14cf0-129">La première commande crée une session PowerShell ( **PSSession** ) sur chacun des trois ordinateurs distants et les stocke dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-129">The first command creates a PowerShell session ( **PSSession** ) on each of the three remote computers and stores them in the $s variable.</span></span>

<span data-ttu-id="14cf0-130">La deuxième commande utilise **Invoke-Command** pour exécuter **Start-Job** dans chacune des trois sessions dans $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-130">The second command uses **Invoke-Command** to run **Start-Job** in each of the three sessions in $s.</span></span>
<span data-ttu-id="14cf0-131">Toutes les tâches sont nommées date1.</span><span class="sxs-lookup"><span data-stu-id="14cf0-131">All of the jobs are named Date1.</span></span>

<span data-ttu-id="14cf0-132">La troisième commande utilise **Invoke-Command** pour exécuter **Wait-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-132">The third command uses **Invoke-Command** to run **Wait-Job** .</span></span>
<span data-ttu-id="14cf0-133">Cette commande attend la fin des tâches date1 sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14cf0-133">This command waits for the Date1 jobs on each computer to finish.</span></span>
<span data-ttu-id="14cf0-134">Elle stocke la collection résultante (tableau) des objets de traitement dans la variable $done.</span><span class="sxs-lookup"><span data-stu-id="14cf0-134">It stores the resulting collection (array) of job objects in the $done variable.</span></span>

<span data-ttu-id="14cf0-135">La quatrième commande utilise la propriété **Count** du tableau d’objets de traitement dans la variable $done pour déterminer le nombre de travaux terminés.</span><span class="sxs-lookup"><span data-stu-id="14cf0-135">The fourth command uses the **Count** property of the array of job objects in the $done variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="14cf0-136">Exemple 3 : déterminer à quel moment la première tâche en arrière-plan se termine</span><span class="sxs-lookup"><span data-stu-id="14cf0-136">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="14cf0-137">Cet exemple utilise le paramètre *any* d' **Wait-Job** pour déterminer quand la première des nombreuses tâches en arrière-plan en cours d’exécution dans la session active est terminée.</span><span class="sxs-lookup"><span data-stu-id="14cf0-137">This example uses the *Any* parameter of **Wait-Job** to determine when the first of many background jobs running in the current session are completed.</span></span>
<span data-ttu-id="14cf0-138">Il montre également comment utiliser l’applet de commande **Wait-Job** pour attendre la fin des travaux distants.</span><span class="sxs-lookup"><span data-stu-id="14cf0-138">It also shows how to use the **Wait-Job** cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="14cf0-139">La première commande crée une **session PSSession** sur chacun des ordinateurs listés dans le fichier Machines.txt et stocke les objets **PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-139">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the $s variable.</span></span>
<span data-ttu-id="14cf0-140">La commande utilise l’applet de commande Get-Content pour récupérer le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="14cf0-140">The command uses the Get-Content cmdlet to get the contents of the file.</span></span>
<span data-ttu-id="14cf0-141">La commande d' **extraction de contenu** est placée entre parenthèses pour s’assurer qu’elle s’exécute avant la commande New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="14cf0-141">The **Get-Content** command is enclosed in parentheses to make sure that it runs before the New-PSSession command.</span></span>

<span data-ttu-id="14cf0-142">La deuxième commande stocke une chaîne de commande **obtenir-EventLog** , entre guillemets, dans la variable $c.</span><span class="sxs-lookup"><span data-stu-id="14cf0-142">The second command stores a **Get-EventLog** command string, in quotation marks, in the $c variable.</span></span>

<span data-ttu-id="14cf0-143">La troisième commande utilise Invoke-Command applet de commande pour exécuter **Start-Job** dans chacune des sessions dans $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-143">The third command uses Invoke-Command cmdlet to run **Start-Job** in each of the sessions in $s.</span></span>
<span data-ttu-id="14cf0-144">La commande **Start-Job** démarre une tâche en arrière-plan qui exécute la commande **obtenir-EventLog** dans la variable $c.</span><span class="sxs-lookup"><span data-stu-id="14cf0-144">The **Start-Job** command starts a background job that runs the **Get-EventLog** command in the $c variable.</span></span>

<span data-ttu-id="14cf0-145">La commande utilise le modificateur d'étendue **Using** pour indiquer que la variable $c a été définie sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="14cf0-145">The command uses the **Using** scope modifier to indicate that the $c variable was defined on the local computer.</span></span>
<span data-ttu-id="14cf0-146">Le modificateur d'étendue **Using** a été introduit pour la première fois dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="14cf0-146">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="14cf0-147">Pour plus d’informations sur le modificateur d’étendue **using** , consultez [about_Remote_Variables](about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="14cf0-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="14cf0-148">La quatrième commande utilise **Invoke-Command** pour exécuter une commande **Wait-Job** dans les sessions.</span><span class="sxs-lookup"><span data-stu-id="14cf0-148">The fourth command uses **Invoke-Command** to run a **Wait-Job** command in the sessions.</span></span>
<span data-ttu-id="14cf0-149">Elle utilise le paramètre *any* pour attendre la fin de la première tâche sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="14cf0-149">It uses the *Any* parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="14cf0-150">Exemple 4 : définir un délai d’attente pour des travaux sur des ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="14cf0-150">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="14cf0-151">Cet exemple montre comment utiliser le paramètre *timeout* de **Wait-Job** pour définir un délai d’attente maximal pour les tâches en cours d’exécution sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="14cf0-151">This example shows how to use the *Timeout* parameter of **Wait-Job** to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="14cf0-152">La première commande crée une **session PSSession** sur chacun des trois ordinateurs distants (SERVEUR01, Server02 et Server03), puis stocke les objets **PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-152">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the $s variable.</span></span>

<span data-ttu-id="14cf0-153">La deuxième commande utilise **Invoke-Command** pour exécuter **Start-Job** dans chacun des objets **PSSession** dans $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-153">The second command uses **Invoke-Command** to run **Start-Job** in each of the **PSSession** objects in $s.</span></span>
<span data-ttu-id="14cf0-154">Elle stocke les objets de traitement résultants dans la variable $jobs.</span><span class="sxs-lookup"><span data-stu-id="14cf0-154">It stores the resulting job objects in the $jobs variable.</span></span>

<span data-ttu-id="14cf0-155">La troisième commande utilise **Invoke-Command** pour exécuter **Wait-Job** dans chacune des sessions dans $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-155">The third command uses **Invoke-Command** to run **Wait-Job** in each of the sessions in $s.</span></span>
<span data-ttu-id="14cf0-156">La commande **Wait-Job** détermine si toutes les commandes sont terminées dans un délai de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="14cf0-156">The **Wait-Job** command determines whether all of the commands have completed within 30 seconds.</span></span>
<span data-ttu-id="14cf0-157">Elle utilise le paramètre *timeout* avec la valeur 30 pour établir le délai d’attente maximal, puis stocke les résultats de la commande dans la variable $done.</span><span class="sxs-lookup"><span data-stu-id="14cf0-157">It uses the *Timeout* parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the $done variable.</span></span>

<span data-ttu-id="14cf0-158">Dans ce cas, après 30 secondes, seule la commande sur l'ordinateur Server02 s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="14cf0-158">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span>
<span data-ttu-id="14cf0-159">**Wait-Job** met fin à l’attente, affiche l’invite de commandes et retourne l’objet qui représente le travail terminé.</span><span class="sxs-lookup"><span data-stu-id="14cf0-159">**Wait-Job** ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="14cf0-160">La variable $done contient un objet de traitement qui représente la tâche qui s'exécutait sur Server02.</span><span class="sxs-lookup"><span data-stu-id="14cf0-160">The $done variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="14cf0-161">Exemple 5 : attendre la fin de l’exécution de l’une des tâches suivantes</span><span class="sxs-lookup"><span data-stu-id="14cf0-161">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="14cf0-162">Cette commande identifie trois tâches par leur ID et attend la fin de l’une d’entre elles.</span><span class="sxs-lookup"><span data-stu-id="14cf0-162">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="14cf0-163">L’invite de commandes s’affiche lorsque la première tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="14cf0-163">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="14cf0-164">Exemple 6 : attendre un point, puis autoriser la tâche à continuer en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="14cf0-164">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="14cf0-165">Cette commande attend 120 secondes (deux minutes) que la tâche Dailyjob se se termine.</span><span class="sxs-lookup"><span data-stu-id="14cf0-165">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span>
<span data-ttu-id="14cf0-166">Si la tâche ne se termine pas dans les deux minutes qui suivent, l’invite de commandes réapparaît et la tâche continue de s’exécuter en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="14cf0-166">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="14cf0-167">Exemple 7 : attendre un travail par nom</span><span class="sxs-lookup"><span data-stu-id="14cf0-167">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="14cf0-168">Cette commande utilise le nom du travail pour identifier le travail à attendre.</span><span class="sxs-lookup"><span data-stu-id="14cf0-168">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="14cf0-169">Exemple 8 : attente des travaux sur l’ordinateur local démarrés avec Start-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-169">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="14cf0-170">Cet exemple montre comment utiliser l’applet de commande **Wait-Job** avec des tâches démarrées sur l’ordinateur local à l’aide de **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-170">This example shows how to use the **Wait-Job** cmdlet with jobs started on the local computer by using **Start-Job** .</span></span>

<span data-ttu-id="14cf0-171">Ces commandes démarrent une tâche qui obtient les fichiers de script PowerShell qui ont été ajoutés ou mis à jour au cours de la semaine dernière.</span><span class="sxs-lookup"><span data-stu-id="14cf0-171">These commands start a job that gets the PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="14cf0-172">La première commande utilise **Start-Job** pour démarrer une tâche en arrière-plan sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="14cf0-172">The first command uses **Start-Job** to start a background job on the local computer.</span></span>
<span data-ttu-id="14cf0-173">La tâche exécute une commande Get-ChildItem qui obtient tous les fichiers ayant une extension de nom de fichier. ps1 qui ont été ajoutés ou mis à jour au cours de la semaine dernière.</span><span class="sxs-lookup"><span data-stu-id="14cf0-173">The job runs a Get-ChildItem command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="14cf0-174">La troisième commande utilise **Wait-Job** pour attendre la fin du travail.</span><span class="sxs-lookup"><span data-stu-id="14cf0-174">The third command uses **Wait-Job** to wait until the job is completed.</span></span>
<span data-ttu-id="14cf0-175">Une fois la tâche terminée, la commande affiche l’objet de traitement, qui contient des informations sur le travail.</span><span class="sxs-lookup"><span data-stu-id="14cf0-175">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="14cf0-176">Exemple 9 : attente des tâches démarrées sur des ordinateurs distants à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="14cf0-176">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="14cf0-177">Cet exemple montre comment utiliser **Wait-Job** avec les travaux démarrés sur des ordinateurs distants à l’aide du paramètre *AsJob* de **Invoke-Command** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-177">This example shows how to use **Wait-Job** with jobs started on remote computers by using the *AsJob* parameter of **Invoke-Command** .</span></span>
<span data-ttu-id="14cf0-178">Lorsque vous utilisez *AsJob* , le travail est créé sur l’ordinateur local et les résultats sont automatiquement retournés à l’ordinateur local, même si le travail s’exécute sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="14cf0-178">When using *AsJob* , the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="14cf0-179">Cet exemple utilise **Wait-Job** pour déterminer si une commande d’exécution de **processus** en cours d’exécution dans les sessions sur trois ordinateurs distants est terminée.</span><span class="sxs-lookup"><span data-stu-id="14cf0-179">This example uses **Wait-Job** to determine whether a **Get-Process** command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="14cf0-180">La première commande crée des objets **PSSession** sur trois ordinateurs et les stocke dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-180">The first command creates **PSSession** objects on three computers and stores them in the $s variable.</span></span>

<span data-ttu-id="14cf0-181">La deuxième commande utilise **Invoke-Command** pour exécuter **le processus d’extraction** dans chacune des trois sessions dans $s.</span><span class="sxs-lookup"><span data-stu-id="14cf0-181">The second command uses **Invoke-Command** to run **Get-Process** in each of the three sessions in $s.</span></span>
<span data-ttu-id="14cf0-182">La commande utilise le paramètre *AsJob* pour exécuter la commande de façon asynchrone en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="14cf0-182">The command uses the *AsJob* parameter to run the command asynchronously as a background job.</span></span>
<span data-ttu-id="14cf0-183">La commande retourne un objet de traitement, tout comme les tâches démarrées à l’aide de **Start-Job** , et l’objet de traitement est stocké dans la variable $j.</span><span class="sxs-lookup"><span data-stu-id="14cf0-183">The command returns a job object, just like the jobs started by using **Start-Job** , and the job object is stored in the $j variable.</span></span>

<span data-ttu-id="14cf0-184">La troisième commande utilise un opérateur de pipeline (|) pour envoyer l’objet de traitement dans $j à l’applet de commande **Wait-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-184">The third command uses a pipeline operator (|) to send the job object in $j to the **Wait-Job** cmdlet.</span></span>
<span data-ttu-id="14cf0-185">Dans ce cas, une commande **Invoke-Command** n’est pas requise, car le travail se trouve sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="14cf0-185">An **Invoke-Command** command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="14cf0-186">Exemple 10 : attendre un travail qui a un ID</span><span class="sxs-lookup"><span data-stu-id="14cf0-186">Example 10: Wait for a job that has an ID</span></span>

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

<span data-ttu-id="14cf0-187">Cette commande attend la tâche dotée d'un ID de valeur 1.</span><span class="sxs-lookup"><span data-stu-id="14cf0-187">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="14cf0-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="14cf0-188">PARAMETERS</span></span>

### <span data-ttu-id="14cf0-189">-Any</span><span class="sxs-lookup"><span data-stu-id="14cf0-189">-Any</span></span>

<span data-ttu-id="14cf0-190">Indique que cette applet de commande affiche l’invite de commandes et retourne l’objet de traitement, quand une tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="14cf0-190">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span>
<span data-ttu-id="14cf0-191">Par défaut, **Wait-Job** attend que toutes les tâches spécifiées soient terminées avant d’afficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="14cf0-191">By default, **Wait-Job** waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="14cf0-192">-Filter</span><span class="sxs-lookup"><span data-stu-id="14cf0-192">-Filter</span></span>

<span data-ttu-id="14cf0-193">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="14cf0-193">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="14cf0-194">Cette applet de commande attend des tâches qui répondent à toutes les conditions de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="14cf0-194">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="14cf0-195">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="14cf0-195">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="14cf0-196">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="14cf0-196">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="14cf0-197">Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-197">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="14cf0-198">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="14cf0-198">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="14cf0-199">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="14cf0-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="14cf0-200">-Force</span><span class="sxs-lookup"><span data-stu-id="14cf0-200">-Force</span></span>

<span data-ttu-id="14cf0-201">Indique que cette applet de commande continue à attendre des tâches dans l’État Suspended ou Disconnected.</span><span class="sxs-lookup"><span data-stu-id="14cf0-201">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span>
<span data-ttu-id="14cf0-202">Par défaut, **Wait-Job** retourne, ou met fin à l’attente, lorsque les tâches sont dans l’un des États suivants :</span><span class="sxs-lookup"><span data-stu-id="14cf0-202">By default, **Wait-Job** returns, or ends  the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="14cf0-203">Completed</span><span class="sxs-lookup"><span data-stu-id="14cf0-203">Completed</span></span>
- <span data-ttu-id="14cf0-204">Échec</span><span class="sxs-lookup"><span data-stu-id="14cf0-204">Failed</span></span>
- <span data-ttu-id="14cf0-205">Arrêté</span><span class="sxs-lookup"><span data-stu-id="14cf0-205">Stopped</span></span>
- <span data-ttu-id="14cf0-206">Interrompu</span><span class="sxs-lookup"><span data-stu-id="14cf0-206">Suspended</span></span>
- <span data-ttu-id="14cf0-207">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="14cf0-207">Disconnected</span></span>

<span data-ttu-id="14cf0-208">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="14cf0-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="14cf0-209">-Id</span><span class="sxs-lookup"><span data-stu-id="14cf0-209">-Id</span></span>

<span data-ttu-id="14cf0-210">Spécifie un tableau d’ID des travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="14cf0-210">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="14cf0-211">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="14cf0-211">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="14cf0-212">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="14cf0-212">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="14cf0-213">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="14cf0-213">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="14cf0-214">Pour Rechercher l’ID d’un travail, tapez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="14cf0-214">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="14cf0-215">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="14cf0-215">-InstanceId</span></span>

<span data-ttu-id="14cf0-216">Spécifie un tableau d’ID d’instance des travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="14cf0-216">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span>
<span data-ttu-id="14cf0-217">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="14cf0-217">The default is all jobs.</span></span>

<span data-ttu-id="14cf0-218">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14cf0-218">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="14cf0-219">Pour rechercher l'ID d'instance d'une tâche, utilisez **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-219">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="14cf0-220">-Travail</span><span class="sxs-lookup"><span data-stu-id="14cf0-220">-Job</span></span>

<span data-ttu-id="14cf0-221">Spécifie les travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="14cf0-221">Specifies the jobs for which this cmdlet waits.</span></span>
<span data-ttu-id="14cf0-222">Entrez une variable qui contient les objets de traitement ou une commande permettant d'obtenir ces objets de traitement.</span><span class="sxs-lookup"><span data-stu-id="14cf0-222">Enter a variable that contains the job objects or a command that gets the job objects.</span></span>
<span data-ttu-id="14cf0-223">Vous pouvez également utiliser un opérateur de pipeline pour envoyer des objets de traitement à l’applet de commande **Wait-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-223">You can also use a pipeline operator to send job objects to the **Wait-Job** cmdlet.</span></span>
<span data-ttu-id="14cf0-224">Par défaut, **Wait-Job** attend toutes les tâches créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="14cf0-224">By default, **Wait-Job** waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="14cf0-225">-Name</span><span class="sxs-lookup"><span data-stu-id="14cf0-225">-Name</span></span>

<span data-ttu-id="14cf0-226">Spécifie les noms conviviaux des travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="14cf0-226">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14cf0-227">-État</span><span class="sxs-lookup"><span data-stu-id="14cf0-227">-State</span></span>

<span data-ttu-id="14cf0-228">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="14cf0-228">Specifies a job state.</span></span>
<span data-ttu-id="14cf0-229">Cette applet de commande attend uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="14cf0-229">This cmdlet waits only for jobs in the specified state.</span></span>
<span data-ttu-id="14cf0-230">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="14cf0-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="14cf0-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="14cf0-231">NotStarted</span></span>
- <span data-ttu-id="14cf0-232">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="14cf0-232">Running</span></span>
- <span data-ttu-id="14cf0-233">Completed</span><span class="sxs-lookup"><span data-stu-id="14cf0-233">Completed</span></span>
- <span data-ttu-id="14cf0-234">Échec</span><span class="sxs-lookup"><span data-stu-id="14cf0-234">Failed</span></span>
- <span data-ttu-id="14cf0-235">Arrêté</span><span class="sxs-lookup"><span data-stu-id="14cf0-235">Stopped</span></span>
- <span data-ttu-id="14cf0-236">Bloqué</span><span class="sxs-lookup"><span data-stu-id="14cf0-236">Blocked</span></span>
- <span data-ttu-id="14cf0-237">Interrompu</span><span class="sxs-lookup"><span data-stu-id="14cf0-237">Suspended</span></span>
- <span data-ttu-id="14cf0-238">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="14cf0-238">Disconnected</span></span>
- <span data-ttu-id="14cf0-239">Suspension</span><span class="sxs-lookup"><span data-stu-id="14cf0-239">Suspending</span></span>
- <span data-ttu-id="14cf0-240">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="14cf0-240">Stopping</span></span>

<span data-ttu-id="14cf0-241">Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="14cf0-241">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="14cf0-242">-Timeout</span><span class="sxs-lookup"><span data-stu-id="14cf0-242">-Timeout</span></span>

<span data-ttu-id="14cf0-243">Spécifie la durée d’attente maximale, en secondes, pour chaque travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="14cf0-243">Specifies the maximum wait time for each background job, in seconds.</span></span>
<span data-ttu-id="14cf0-244">La valeur par défaut,-1, indique que l’applet de commande attend que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="14cf0-244">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span>
<span data-ttu-id="14cf0-245">Le minutage démarre lorsque vous envoyez la commande **Wait-Job** , et non la commande **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="14cf0-245">The timing starts when you submit the **Wait-Job** command, not the **Start-Job** command.</span></span>

<span data-ttu-id="14cf0-246">Si ce délai est dépassé, l'attente se termine et l'invite de commandes réapparaît, même si la tâche est encore en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="14cf0-246">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span>
<span data-ttu-id="14cf0-247">La commande n’affiche aucun message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="14cf0-247">The command does not display any error message.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14cf0-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14cf0-248">CommonParameters</span></span>

<span data-ttu-id="14cf0-249">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14cf0-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14cf0-250">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14cf0-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14cf0-251">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="14cf0-251">INPUTS</span></span>

### <span data-ttu-id="14cf0-252">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="14cf0-252">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="14cf0-253">Vous pouvez diriger un objet de traitement vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14cf0-253">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="14cf0-254">SORTIES</span><span class="sxs-lookup"><span data-stu-id="14cf0-254">OUTPUTS</span></span>

### <span data-ttu-id="14cf0-255">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="14cf0-255">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="14cf0-256">Cette applet de commande retourne les objets de traitement qui représentent les tâches terminées.</span><span class="sxs-lookup"><span data-stu-id="14cf0-256">This cmdlet returns job objects that represent the completed jobs.</span></span>
<span data-ttu-id="14cf0-257">Si l’attente se termine parce que la valeur du paramètre *timeout* est dépassée, **Wait-Job** ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="14cf0-257">If the wait ends because the value of the *Timeout* parameter is exceeded, **Wait-Job** does not return any objects.</span></span>

## <span data-ttu-id="14cf0-258">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="14cf0-258">NOTES</span></span>

* <span data-ttu-id="14cf0-259">Par défaut, **Wait-Job** retourne, ou met fin à l’attente, lorsque les tâches sont dans l’un des États suivants :</span><span class="sxs-lookup"><span data-stu-id="14cf0-259">By default, **Wait-Job** returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="14cf0-260">Completed</span><span class="sxs-lookup"><span data-stu-id="14cf0-260">Completed</span></span>
- <span data-ttu-id="14cf0-261">Échec</span><span class="sxs-lookup"><span data-stu-id="14cf0-261">Failed</span></span>
- <span data-ttu-id="14cf0-262">Arrêté</span><span class="sxs-lookup"><span data-stu-id="14cf0-262">Stopped</span></span>
- <span data-ttu-id="14cf0-263">Interrompu</span><span class="sxs-lookup"><span data-stu-id="14cf0-263">Suspended</span></span>
- <span data-ttu-id="14cf0-264">Déconnecté de l' **attente directe-travail** pour continuer à attendre les tâches interrompues et déconnectées, utilisez le paramètre *force* .</span><span class="sxs-lookup"><span data-stu-id="14cf0-264">Disconnected To direct **Wait-Job** to continue to wait for Suspended and Disconnected jobs, use the *Force* parameter.</span></span>

## <span data-ttu-id="14cf0-265">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="14cf0-265">RELATED LINKS</span></span>

[<span data-ttu-id="14cf0-266">Get-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-266">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="14cf0-267">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="14cf0-267">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="14cf0-268">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-268">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="14cf0-269">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-269">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="14cf0-270">Start-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-270">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="14cf0-271">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="14cf0-271">Stop-Job</span></span>](Stop-Job.md)

