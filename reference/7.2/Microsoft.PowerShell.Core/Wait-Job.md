---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: ffcd0fba9fae9ed49e7f20fa5a971e6e50fc445f
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99596310"
---
# <span data-ttu-id="56a6a-102">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-102">Wait-Job</span></span>

## <span data-ttu-id="56a6a-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="56a6a-103">SYNOPSIS</span></span>
<span data-ttu-id="56a6a-104">Attend que l’un ou l’ensemble des travaux PowerShell en cours d’exécution dans la session soient dans un état d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="56a6a-104">Waits until one or all of the PowerShell jobs running in the session are in a terminating state.</span></span>

## <span data-ttu-id="56a6a-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="56a6a-105">SYNTAX</span></span>

### <span data-ttu-id="56a6a-106">SessionIdParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="56a6a-106">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="56a6a-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a6a-107">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="56a6a-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a6a-108">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="56a6a-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a6a-109">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="56a6a-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a6a-110">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="56a6a-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="56a6a-111">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="56a6a-112">Description</span><span class="sxs-lookup"><span data-stu-id="56a6a-112">DESCRIPTION</span></span>

<span data-ttu-id="56a6a-113">L' `Wait-Job` applet de commande attend qu’une tâche soit dans un état de fin avant de poursuivre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="56a6a-113">The `Wait-Job` cmdlet waits for a job to be in a terminating state before continuing execution.</span></span>
<span data-ttu-id="56a6a-114">Les États de fin sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="56a6a-114">The terminating states are:</span></span>

- <span data-ttu-id="56a6a-115">Completed</span><span class="sxs-lookup"><span data-stu-id="56a6a-115">Completed</span></span>
- <span data-ttu-id="56a6a-116">Échec</span><span class="sxs-lookup"><span data-stu-id="56a6a-116">Failed</span></span>
- <span data-ttu-id="56a6a-117">Arrêté</span><span class="sxs-lookup"><span data-stu-id="56a6a-117">Stopped</span></span>
- <span data-ttu-id="56a6a-118">Interrompu</span><span class="sxs-lookup"><span data-stu-id="56a6a-118">Suspended</span></span>
- <span data-ttu-id="56a6a-119">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="56a6a-119">Disconnected</span></span>

<span data-ttu-id="56a6a-120">Vous pouvez attendre un travail spécifié ou tous les travaux se trouvent dans un état d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="56a6a-120">You can wait until a specified job, or all jobs are in a terminating state.</span></span> <span data-ttu-id="56a6a-121">Vous pouvez également définir un délai d’attente maximal pour le travail à l’aide du paramètre **timeout** , ou utiliser le paramètre **force** pour attendre un travail dans les `Suspended` `Disconnected` États ou.</span><span class="sxs-lookup"><span data-stu-id="56a6a-121">You can also set a maximum wait time for the job using the **Timeout** parameter, or use the **Force** parameter to wait for a job in the `Suspended` or `Disconnected` states.</span></span>

<span data-ttu-id="56a6a-122">Lorsque les commandes du travail sont terminées, `Wait-Job` retourne un objet de traitement et poursuit l’exécution.</span><span class="sxs-lookup"><span data-stu-id="56a6a-122">When the commands in the job are complete, `Wait-Job` returns a job object and continues execution.</span></span>

<span data-ttu-id="56a6a-123">Vous pouvez utiliser l' `Wait-Job` applet de commande pour attendre le démarrage de travaux à l’aide de l' `Start-Job` applet de commande ou du paramètre **AsJob** de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-123">You can use the `Wait-Job` cmdlet to wait for jobs started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="56a6a-124">Pour plus d’informations sur les tâches, consultez [about_Jobs](./about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="56a6a-124">For more information about jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="56a6a-125">À compter de Windows PowerShell 3,0, l’applet de commande `Wait-Job` attend également des types de tâches personnalisés, tels que les tâches de workflow et les instances de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="56a6a-125">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="56a6a-126">Pour permettre `Wait-Job` à d’attendre des tâches d’un type particulier, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter l’applet de commande `Get-Job` , à l’aide de l’applet de commande `Import-Module` ou à l’aide de ou de l’obtention d’une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="56a6a-126">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="56a6a-127">Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="56a6a-127">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="56a6a-128">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="56a6a-128">EXAMPLES</span></span>

### <span data-ttu-id="56a6a-129">Exemple 1 : attendre tous les travaux</span><span class="sxs-lookup"><span data-stu-id="56a6a-129">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="56a6a-130">Cette commande attend la fin de toutes les tâches en cours d’exécution dans la session.</span><span class="sxs-lookup"><span data-stu-id="56a6a-130">This command waits for all of the jobs running in the session to finish.</span></span>

### <span data-ttu-id="56a6a-131">Exemple 2 : attente des tâches démarrées sur des ordinateurs distants à l’aide de Start-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-131">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="56a6a-132">Cet exemple montre comment utiliser l' `Wait-Job` applet de commande avec les travaux démarrés sur des ordinateurs distants à l’aide de l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-132">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="56a6a-133">Les `Start-Job` `Wait-Job` commandes et sont envoyées à l’ordinateur distant à l’aide de l’applet de commande `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-133">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="56a6a-134">Cet exemple utilise `Wait-Job` pour déterminer si une `Get-Date` commande s’exécutant en tant que tâche sur trois ordinateurs différents est terminée.</span><span class="sxs-lookup"><span data-stu-id="56a6a-134">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a job on three different computers is finished.</span></span>

<span data-ttu-id="56a6a-135">La première commande crée une session Windows PowerShell (**PSSession**) sur chacun des trois ordinateurs distants et les stocke dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-135">The first command creates a Windows PowerShell session (**PSSession**) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="56a6a-136">La deuxième commande utilise `Invoke-Command` pour s’exécuter `Start-Job` dans chacune des trois sessions dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-136">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="56a6a-137">Toutes les tâches sont nommées date1.</span><span class="sxs-lookup"><span data-stu-id="56a6a-137">All of the jobs are named Date1.</span></span>

<span data-ttu-id="56a6a-138">La troisième commande utilise `Invoke-Command` pour exécuter `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-138">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="56a6a-139">Cette commande attend la fin des `Date1` travaux sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56a6a-139">This command waits for the `Date1` jobs on each computer to finish.</span></span> <span data-ttu-id="56a6a-140">Elle stocke la collection résultante (**tableau**) d’objets de **traitement** dans la `$done` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-140">It stores the resulting collection (**array**) of **job** objects in the `$done` variable.</span></span>

<span data-ttu-id="56a6a-141">La quatrième commande utilise la propriété **Count** du tableau d’objets de traitement dans la `$done` variable pour déterminer le nombre de travaux terminés.</span><span class="sxs-lookup"><span data-stu-id="56a6a-141">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="56a6a-142">Exemple 3 : déterminer à quel moment la première tâche se termine</span><span class="sxs-lookup"><span data-stu-id="56a6a-142">Example 3: Determine when the first job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="56a6a-143">Cet exemple utilise le paramètre **any** de `Wait-Job` pour déterminer quand le premier des nombreuses tâches en cours d’exécution dans la session active se termine.</span><span class="sxs-lookup"><span data-stu-id="56a6a-143">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many jobs running in the current session are in a terminating state.</span></span> <span data-ttu-id="56a6a-144">Il montre également comment utiliser l' `Wait-Job` applet de commande pour attendre la fin des travaux distants.</span><span class="sxs-lookup"><span data-stu-id="56a6a-144">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="56a6a-145">La première commande crée une **session PSSession** sur chacun des ordinateurs figurant dans le fichier Machines.txt et stocke les objets **PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-145">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="56a6a-146">La commande utilise l' `Get-Content` applet de commande pour récupérer le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="56a6a-146">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="56a6a-147">La `Get-Content` commande est placée entre parenthèses pour vérifier qu’elle s’exécute avant la `New-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="56a6a-147">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="56a6a-148">La deuxième commande stocke une `Get-EventLog` chaîne de commande, entre guillemets, dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-148">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="56a6a-149">La troisième commande utilise l’applet de commande `Invoke-Command` pour s’exécuter `Start-Job` dans chacune des sessions dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-149">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="56a6a-150">La `Start-Job` commande démarre un travail qui exécute la `Get-EventLog` commande dans la `$c` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-150">The `Start-Job` command starts a job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="56a6a-151">La commande utilise le modificateur d’étendue **using** pour indiquer que la `$c` variable a été définie sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56a6a-151">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="56a6a-152">Le modificateur d'étendue **Using** a été introduit pour la première fois dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="56a6a-152">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="56a6a-153">Pour plus d’informations sur le modificateur d’étendue **using** , consultez [about_Remote_Variables](./about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="56a6a-153">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="56a6a-154">La quatrième commande utilise `Invoke-Command` pour exécuter une `Wait-Job` commande dans les sessions.</span><span class="sxs-lookup"><span data-stu-id="56a6a-154">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="56a6a-155">Elle utilise le paramètre **any** pour attendre la fin de la première tâche sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="56a6a-155">It uses the **Any** parameter to wait until the first job on the remote computers is terminating state.</span></span>

### <span data-ttu-id="56a6a-156">Exemple 4 : définir un délai d’attente pour des travaux sur des ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="56a6a-156">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

<span data-ttu-id="56a6a-157">Cet exemple montre comment utiliser le paramètre **timeout** de `Wait-Job` pour définir un délai d’attente maximal pour les tâches en cours d’exécution sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="56a6a-157">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="56a6a-158">La première commande crée une **session PSSession** sur chacun des trois ordinateurs distants (SERVEUR01, Server02 et Server03), puis stocke les objets **PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-158">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="56a6a-159">La deuxième commande utilise `Invoke-Command` pour s’exécuter `Start-Job` dans chacun des objets **PSSession** dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-159">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="56a6a-160">Elle stocke les objets de traitement résultants dans la `$jobs` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-160">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="56a6a-161">La troisième commande utilise `Invoke-Command` pour s’exécuter `Wait-Job` dans chacune des sessions dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-161">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="56a6a-162">La `Wait-Job` commande détermine si toutes les commandes sont terminées dans un délai de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="56a6a-162">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="56a6a-163">Elle utilise le paramètre **timeout** avec la valeur 30 pour établir le délai d’attente maximal, puis stocke les résultats de la commande dans la `$done` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-163">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="56a6a-164">Dans ce cas, après 30 secondes, seule la commande sur l'ordinateur Server02 s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="56a6a-164">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="56a6a-165">`Wait-Job` met fin à l’attente, retourne l’objet qui représente la tâche qui a été exécutée et affiche l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="56a6a-165">`Wait-Job` ends the wait, returns the object that represents the job that was completed, and displays the command prompt.</span></span>

<span data-ttu-id="56a6a-166">La `$done` variable contient un objet de traitement qui représente la tâche qui s’est exécutée sur Server02.</span><span class="sxs-lookup"><span data-stu-id="56a6a-166">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="56a6a-167">Exemple 5 : attendre la fin de l’exécution de l’une des tâches suivantes</span><span class="sxs-lookup"><span data-stu-id="56a6a-167">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="56a6a-168">Cette commande identifie trois tâches par leur ID et attend jusqu’à ce que l’un d’eux se trouve dans un état d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="56a6a-168">This command identifies three jobs by their IDs and waits until any one of them are in a terminating state.</span></span> <span data-ttu-id="56a6a-169">L’exécution se poursuit lorsque la première tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="56a6a-169">Execution continues when the first job finishes.</span></span>

### <span data-ttu-id="56a6a-170">Exemple 6 : attendre un point, puis autoriser la tâche à continuer en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="56a6a-170">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="56a6a-171">Cette commande attend 120 secondes (deux minutes) que la tâche Dailyjob se se termine.</span><span class="sxs-lookup"><span data-stu-id="56a6a-171">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="56a6a-172">Si la tâche ne se termine pas dans les deux minutes suivantes, l’exécution continue et la tâche continue de s’exécuter en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="56a6a-172">If the job does not finish in the next two minutes, execution continues, and the job continues to run in the background.</span></span>

### <span data-ttu-id="56a6a-173">Exemple 7 : attendre un travail par nom</span><span class="sxs-lookup"><span data-stu-id="56a6a-173">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="56a6a-174">Cette commande utilise le nom du travail pour identifier le travail à attendre.</span><span class="sxs-lookup"><span data-stu-id="56a6a-174">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="56a6a-175">Exemple 8 : attente des travaux sur l’ordinateur local démarrés avec Start-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-175">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="56a6a-176">Cet exemple montre comment utiliser l' `Wait-Job` applet de commande avec les travaux démarrés sur l’ordinateur local à l’aide de `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-176">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="56a6a-177">Ces commandes démarrent une tâche qui obtient les fichiers de script Windows PowerShell qui ont été ajoutés ou mis à jour au cours de la semaine précédente.</span><span class="sxs-lookup"><span data-stu-id="56a6a-177">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="56a6a-178">La première commande utilise `Start-Job` pour démarrer un travail sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56a6a-178">The first command uses `Start-Job` to start a job on the local computer.</span></span> <span data-ttu-id="56a6a-179">La tâche exécute une `Get-ChildItem` commande qui obtient tous les fichiers qui ont une extension de nom de fichier. ps1 qui ont été ajoutés ou mis à jour au cours de la semaine dernière.</span><span class="sxs-lookup"><span data-stu-id="56a6a-179">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="56a6a-180">La troisième commande utilise `Wait-Job` pour attendre que la tâche se termine par un état d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="56a6a-180">The third command uses `Wait-Job` to wait until the job is in a terminating state.</span></span> <span data-ttu-id="56a6a-181">Une fois la tâche terminée, la commande affiche l’objet de traitement, qui contient des informations sur le travail.</span><span class="sxs-lookup"><span data-stu-id="56a6a-181">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="56a6a-182">Exemple 9 : attente des tâches démarrées sur des ordinateurs distants à l’aide de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="56a6a-182">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="56a6a-183">Cet exemple montre comment utiliser `Wait-Job` avec les travaux démarrés sur des ordinateurs distants à l’aide du paramètre **AsJob** de `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-183">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="56a6a-184">Lorsque vous utilisez **AsJob**, le travail est créé sur l’ordinateur local et les résultats sont automatiquement retournés à l’ordinateur local, même si le travail s’exécute sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="56a6a-184">When using **AsJob**, the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="56a6a-185">Cet exemple utilise `Wait-Job` pour déterminer si une `Get-Process` commande exécutée dans les sessions sur trois ordinateurs distants est dans un état d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="56a6a-185">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is in a terminating state.</span></span>

<span data-ttu-id="56a6a-186">La première commande crée des objets **PSSession** sur trois ordinateurs et les stocke dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-186">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="56a6a-187">La deuxième commande utilise `Invoke-Command` pour s’exécuter `Get-Process` dans chacune des trois sessions dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-187">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="56a6a-188">La commande utilise le paramètre **AsJob** pour exécuter la commande de façon asynchrone en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="56a6a-188">The command uses the **AsJob** parameter to run the command asynchronously as a job.</span></span> <span data-ttu-id="56a6a-189">La commande retourne un objet de traitement, tout comme les tâches démarrées à l’aide de `Start-Job` , et l’objet de traitement est stocké dans la `$j` variable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-189">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="56a6a-190">La troisième commande utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet de traitement dans `$j` l’applet de commande `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-190">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="56a6a-191">`Invoke-Command`Dans ce cas, une commande n’est pas requise, car le travail se trouve sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56a6a-191">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="56a6a-192">Exemple 10 : attendre un travail qui a un ID</span><span class="sxs-lookup"><span data-stu-id="56a6a-192">Example 10: Wait for a job that has an ID</span></span>

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

<span data-ttu-id="56a6a-193">Cette commande attend la tâche dotée d'un ID de valeur 1.</span><span class="sxs-lookup"><span data-stu-id="56a6a-193">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="56a6a-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56a6a-194">PARAMETERS</span></span>

### <span data-ttu-id="56a6a-195">-Any</span><span class="sxs-lookup"><span data-stu-id="56a6a-195">-Any</span></span>

<span data-ttu-id="56a6a-196">Indique que cette applet de commande retourne l’objet de traitement et poursuit l’exécution lorsqu’une tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="56a6a-196">Indicates that this cmdlet returns the job object and continues execution when any job finishes.</span></span> <span data-ttu-id="56a6a-197">Par défaut, `Wait-Job` attend que toutes les tâches spécifiées soient terminées avant d’afficher l’invite.</span><span class="sxs-lookup"><span data-stu-id="56a6a-197">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="56a6a-198">-Filter</span><span class="sxs-lookup"><span data-stu-id="56a6a-198">-Filter</span></span>

<span data-ttu-id="56a6a-199">Spécifie une table de hachage de conditions.</span><span class="sxs-lookup"><span data-stu-id="56a6a-199">Specifies a hash table of conditions.</span></span> <span data-ttu-id="56a6a-200">Cette applet de commande attend des tâches qui répondent à toutes les conditions de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="56a6a-200">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="56a6a-201">Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.</span><span class="sxs-lookup"><span data-stu-id="56a6a-201">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="56a6a-202">Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="56a6a-202">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="56a6a-203">Il ne fonctionne pas sur les travaux standard, tels que ceux créés à l’aide de l’applet de commande `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-203">It does not work on standard jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="56a6a-204">Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.</span><span class="sxs-lookup"><span data-stu-id="56a6a-204">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="56a6a-205">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="56a6a-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="56a6a-206">-Force</span><span class="sxs-lookup"><span data-stu-id="56a6a-206">-Force</span></span>

<span data-ttu-id="56a6a-207">Indique que cette applet de commande continue à attendre des tâches dans l’État Suspended ou Disconnected.</span><span class="sxs-lookup"><span data-stu-id="56a6a-207">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="56a6a-208">Par défaut, `Wait-Job` retourne, ou termine l’attente, lorsque les tâches sont dans l’un des États suivants :</span><span class="sxs-lookup"><span data-stu-id="56a6a-208">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="56a6a-209">Completed</span><span class="sxs-lookup"><span data-stu-id="56a6a-209">Completed</span></span>
- <span data-ttu-id="56a6a-210">Échec</span><span class="sxs-lookup"><span data-stu-id="56a6a-210">Failed</span></span>
- <span data-ttu-id="56a6a-211">Arrêté</span><span class="sxs-lookup"><span data-stu-id="56a6a-211">Stopped</span></span>
- <span data-ttu-id="56a6a-212">Interrompu</span><span class="sxs-lookup"><span data-stu-id="56a6a-212">Suspended</span></span>
- <span data-ttu-id="56a6a-213">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="56a6a-213">Disconnected</span></span>

<span data-ttu-id="56a6a-214">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="56a6a-214">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="56a6a-215">-Id</span><span class="sxs-lookup"><span data-stu-id="56a6a-215">-Id</span></span>

<span data-ttu-id="56a6a-216">Spécifie un tableau d’ID des travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="56a6a-216">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="56a6a-217">L’ID est un entier qui identifie de façon unique le travail dans la session active.</span><span class="sxs-lookup"><span data-stu-id="56a6a-217">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="56a6a-218">Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.</span><span class="sxs-lookup"><span data-stu-id="56a6a-218">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="56a6a-219">Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.</span><span class="sxs-lookup"><span data-stu-id="56a6a-219">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="56a6a-220">Pour Rechercher l’ID d’un travail, tapez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-220">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="56a6a-221">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="56a6a-221">-InstanceId</span></span>

<span data-ttu-id="56a6a-222">Spécifie un tableau d’ID d’instance des travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="56a6a-222">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="56a6a-223">Par défaut, il s'agit de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="56a6a-223">The default is all jobs.</span></span>

<span data-ttu-id="56a6a-224">Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56a6a-224">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="56a6a-225">Pour Rechercher l’ID d’instance d’un travail, utilisez `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-225">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="56a6a-226">-Travail</span><span class="sxs-lookup"><span data-stu-id="56a6a-226">-Job</span></span>

<span data-ttu-id="56a6a-227">Spécifie les travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="56a6a-227">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="56a6a-228">Entrez une variable qui contient les objets de traitement ou une commande permettant d'obtenir ces objets de traitement.</span><span class="sxs-lookup"><span data-stu-id="56a6a-228">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="56a6a-229">Vous pouvez également utiliser un opérateur de pipeline pour envoyer des objets de traitement à l’applet de commande `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="56a6a-229">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="56a6a-230">Par défaut, `Wait-Job` attend tous les travaux créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="56a6a-230">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="56a6a-231">-Name</span><span class="sxs-lookup"><span data-stu-id="56a6a-231">-Name</span></span>

<span data-ttu-id="56a6a-232">Spécifie les noms conviviaux des travaux que cette applet de commande attend.</span><span class="sxs-lookup"><span data-stu-id="56a6a-232">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

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

### <span data-ttu-id="56a6a-233">-État</span><span class="sxs-lookup"><span data-stu-id="56a6a-233">-State</span></span>

<span data-ttu-id="56a6a-234">Spécifie un état de travail.</span><span class="sxs-lookup"><span data-stu-id="56a6a-234">Specifies a job state.</span></span> <span data-ttu-id="56a6a-235">Cette applet de commande attend uniquement les tâches dans l’état spécifié.</span><span class="sxs-lookup"><span data-stu-id="56a6a-235">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="56a6a-236">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="56a6a-236">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="56a6a-237">NotStarted</span><span class="sxs-lookup"><span data-stu-id="56a6a-237">NotStarted</span></span>
- <span data-ttu-id="56a6a-238">Exécution en cours</span><span class="sxs-lookup"><span data-stu-id="56a6a-238">Running</span></span>
- <span data-ttu-id="56a6a-239">Completed</span><span class="sxs-lookup"><span data-stu-id="56a6a-239">Completed</span></span>
- <span data-ttu-id="56a6a-240">Échec</span><span class="sxs-lookup"><span data-stu-id="56a6a-240">Failed</span></span>
- <span data-ttu-id="56a6a-241">Arrêté</span><span class="sxs-lookup"><span data-stu-id="56a6a-241">Stopped</span></span>
- <span data-ttu-id="56a6a-242">Bloqué</span><span class="sxs-lookup"><span data-stu-id="56a6a-242">Blocked</span></span>
- <span data-ttu-id="56a6a-243">Interrompu</span><span class="sxs-lookup"><span data-stu-id="56a6a-243">Suspended</span></span>
- <span data-ttu-id="56a6a-244">Déconnecté</span><span class="sxs-lookup"><span data-stu-id="56a6a-244">Disconnected</span></span>
- <span data-ttu-id="56a6a-245">Suspension</span><span class="sxs-lookup"><span data-stu-id="56a6a-245">Suspending</span></span>
- <span data-ttu-id="56a6a-246">En cours d’arrêt</span><span class="sxs-lookup"><span data-stu-id="56a6a-246">Stopping</span></span>

<span data-ttu-id="56a6a-247">Pour plus d’informations sur les États de travail, consultez [énumération JobState](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="56a6a-247">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="56a6a-248">-Timeout</span><span class="sxs-lookup"><span data-stu-id="56a6a-248">-Timeout</span></span>

<span data-ttu-id="56a6a-249">Spécifie la durée d’attente maximale, en secondes, pour chaque travail.</span><span class="sxs-lookup"><span data-stu-id="56a6a-249">Specifies the maximum wait time for each job, in seconds.</span></span> <span data-ttu-id="56a6a-250">La valeur par défaut,-1, indique que l’applet de commande attend que la tâche se termine.</span><span class="sxs-lookup"><span data-stu-id="56a6a-250">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="56a6a-251">Le minutage démarre lorsque vous envoyez la `Wait-Job` commande, et non la `Start-Job` commande.</span><span class="sxs-lookup"><span data-stu-id="56a6a-251">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="56a6a-252">Si ce délai est dépassé, l’attente se termine et l’exécution se poursuit, même si le travail est toujours en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="56a6a-252">If this time is exceeded, the wait ends and execution continues, even if the job is still running.</span></span>
<span data-ttu-id="56a6a-253">La commande n’affiche aucun message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="56a6a-253">The command does not display any error message.</span></span>

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

### <span data-ttu-id="56a6a-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56a6a-254">CommonParameters</span></span>

<span data-ttu-id="56a6a-255">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56a6a-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56a6a-256">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="56a6a-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56a6a-257">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="56a6a-257">INPUTS</span></span>

### <span data-ttu-id="56a6a-258">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="56a6a-258">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="56a6a-259">Vous pouvez diriger un objet de traitement vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="56a6a-259">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="56a6a-260">SORTIES</span><span class="sxs-lookup"><span data-stu-id="56a6a-260">OUTPUTS</span></span>

### <span data-ttu-id="56a6a-261">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="56a6a-261">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="56a6a-262">Cette applet de commande retourne les objets de travail qui représentent les travaux dans un état d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="56a6a-262">This cmdlet returns job objects that represent the jobs in a terminating state.</span></span> <span data-ttu-id="56a6a-263">Si l’attente se termine parce que la valeur du paramètre **timeout** est dépassée, `Wait-Job` ne retourne aucun objet.</span><span class="sxs-lookup"><span data-stu-id="56a6a-263">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="56a6a-264">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="56a6a-264">NOTES</span></span>

<span data-ttu-id="56a6a-265">Par défaut, `Wait-Job` retourne, ou termine l’attente, lorsque les tâches sont dans l’un des États suivants :</span><span class="sxs-lookup"><span data-stu-id="56a6a-265">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="56a6a-266">Completed</span><span class="sxs-lookup"><span data-stu-id="56a6a-266">Completed</span></span>
- <span data-ttu-id="56a6a-267">Échec</span><span class="sxs-lookup"><span data-stu-id="56a6a-267">Failed</span></span>
- <span data-ttu-id="56a6a-268">Arrêté</span><span class="sxs-lookup"><span data-stu-id="56a6a-268">Stopped</span></span>
- <span data-ttu-id="56a6a-269">Interrompu</span><span class="sxs-lookup"><span data-stu-id="56a6a-269">Suspended</span></span>
- <span data-ttu-id="56a6a-270">Déconnecté pour `Wait-Job` que direct continue à attendre les tâches interrompues et déconnectées, utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="56a6a-270">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="56a6a-271">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="56a6a-271">RELATED LINKS</span></span>

[<span data-ttu-id="56a6a-272">Get-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-272">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="56a6a-273">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="56a6a-273">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="56a6a-274">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-274">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="56a6a-275">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-275">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="56a6a-276">Start-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-276">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="56a6a-277">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="56a6a-277">Stop-Job</span></span>](Stop-Job.md)