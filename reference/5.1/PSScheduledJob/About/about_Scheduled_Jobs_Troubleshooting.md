---
description: Explique comment résoudre les problèmes liés aux tâches planifiées
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: aac2133cee4abdd7e50e7b433104b9578d74b0a8
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685875"
---
# <a name="about-scheduled-jobs-troubleshooting"></a><span data-ttu-id="0b49c-104">À propos de la résolution des problèmes de tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="0b49c-104">About Scheduled Jobs Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="0b49c-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="0b49c-105">Short description</span></span>

<span data-ttu-id="0b49c-106">Explique comment résoudre les problèmes liés aux tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="0b49c-106">Explains how to resolve problems with scheduled jobs</span></span>

## <a name="long-description"></a><span data-ttu-id="0b49c-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="0b49c-107">Long description</span></span>

<span data-ttu-id="0b49c-108">Ce document décrit certains des problèmes que vous pouvez rencontrer lors de l’utilisation des fonctionnalités de la tâche planifiée de PowerShell et propose des solutions à ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="0b49c-108">This document describes some of the problems that you might experience when using the scheduled job features of PowerShell and it suggests solutions to these problems.</span></span>

<span data-ttu-id="0b49c-109">Avant d’utiliser les tâches planifiées PowerShell, consultez [about_Scheduled_Jobs](about_Scheduled_Jobs.md) et les tâches planifiées associées à propos des rubriques.</span><span class="sxs-lookup"><span data-stu-id="0b49c-109">Before using PowerShell scheduled jobs, see [about_Scheduled_Jobs](about_Scheduled_Jobs.md) and the related scheduled jobs about topics.</span></span>

<span data-ttu-id="0b49c-110">Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="0b49c-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="cant-find-job-results"></a><span data-ttu-id="0b49c-111">Résultats du travail introuvables</span><span class="sxs-lookup"><span data-stu-id="0b49c-111">Can't find job results</span></span>

### <a name="basic-method-for-getting-job-results-in-powershell"></a><span data-ttu-id="0b49c-112">Méthode de base pour obtenir les résultats d’un travail dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b49c-112">Basic method for getting job results in PowerShell</span></span>

<span data-ttu-id="0b49c-113">Lorsqu’une tâche planifiée s’exécute, elle crée une instance de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-113">When a scheduled job runs, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="0b49c-114">Pour afficher, gérer et obtenir les résultats des instances de tâche planifiée, utilisez les applets de commande Job.</span><span class="sxs-lookup"><span data-stu-id="0b49c-114">To view, manage, and get the results of scheduled job instances, use the Job cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="0b49c-115">Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session.</span><span class="sxs-lookup"><span data-stu-id="0b49c-115">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="0b49c-116">Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-116">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="0b49c-117">Pour obtenir la liste de toutes les instances d’une tâche planifiée, utilisez l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-117">To get a list of all instances of a scheduled job, use the `Get-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

<span data-ttu-id="0b49c-118">L' `Get-Job` applet de commande envoie les objets **ProcessJob** vers le dessous du pipeline.</span><span class="sxs-lookup"><span data-stu-id="0b49c-118">The `Get-Job` cmdlet sends **ProcessJob** objects down the pipeline.</span></span> <span data-ttu-id="0b49c-119">L' `Format-Table` applet de commande affiche le **nom**, l' **ID** et les propriétés **PSBeginTime** d’une instance de tâche planifiée dans une table.</span><span class="sxs-lookup"><span data-stu-id="0b49c-119">The `Format-Table` cmdlet displays the **Name**, **ID**, and **PSBeginTime** properties of a scheduled job instance in a table.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

<span data-ttu-id="0b49c-120">Pour obtenir les résultats d’une instance d’une tâche planifiée, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-120">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="0b49c-121">La commande suivante obtient les résultats de l’instance la plus récente de ProcessJob (ID = 50).</span><span class="sxs-lookup"><span data-stu-id="0b49c-121">The following command gets the results of the newest instance of the ProcessJob (ID = 50).</span></span>

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a><span data-ttu-id="0b49c-122">Méthode de base pour rechercher des résultats de travail sur disque</span><span class="sxs-lookup"><span data-stu-id="0b49c-122">Basic method for finding job results on disk</span></span>

<span data-ttu-id="0b49c-123">Pour gérer les tâches planifiées, utilisez les applets de commande Job, telles que `Get-Job` et `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-123">To manage scheduled jobs, use the job cmdlets, such as `Get-Job` and `Receive-Job`.</span></span>

<span data-ttu-id="0b49c-124">Si `Get-Job` n’obtient pas l’instance de tâche ou `Receive-Job` n’obtient pas les résultats du travail, vous pouvez rechercher la tâche sur le disque dans les fichiers de l’historique d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0b49c-124">If `Get-Job` does not get the job instance or `Receive-Job` does not get the job results, you can search the execution history files for the job on disk.</span></span>
<span data-ttu-id="0b49c-125">L’historique d’exécution contient un enregistrement de toutes les instances de tâche déclenchées.</span><span class="sxs-lookup"><span data-stu-id="0b49c-125">The execution history contains a record of all triggered job instances.</span></span>

<span data-ttu-id="0b49c-126">Vérifiez qu’il existe un répertoire nommé timestamp dans le répertoire pour une tâche planifiée dans le chemin d’accès suivant :</span><span class="sxs-lookup"><span data-stu-id="0b49c-126">Verify that there is a timestamp-named directory in the directory for a scheduled job in the following path:</span></span>

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="0b49c-127">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0b49c-127">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="0b49c-128">Par exemple, l' `Get-ChildItem` applet de commande obtient l’historique d’exécution sur le disque de la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0b49c-128">For example, the `Get-ChildItem` cmdlet gets the on-disk execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

<span data-ttu-id="0b49c-129">Chaque répertoire nommé timestamp représente une instance de tâche.</span><span class="sxs-lookup"><span data-stu-id="0b49c-129">Each timestamp-named directory represents a job instance.</span></span> <span data-ttu-id="0b49c-130">Les résultats de chaque instance de tâche sont enregistrés dans un fichier **Results.xml** dans le répertoire nommé timestamp.</span><span class="sxs-lookup"><span data-stu-id="0b49c-130">The results of each job instance are saved in a **Results.xml** file in the timestamp-named directory.</span></span>

<span data-ttu-id="0b49c-131">Par exemple, la commande suivante obtient les fichiers de **Results.xml** pour chaque instance enregistrée de la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0b49c-131">For example, the following command gets the **Results.xml** files for every saved instance of the **ProcessJob** scheduled job.</span></span> <span data-ttu-id="0b49c-132">Si le fichier **Results.xml** est manquant, PowerShell ne peut pas retourner ou afficher les résultats du travail.</span><span class="sxs-lookup"><span data-stu-id="0b49c-132">If the **Results.xml** file is missing, PowerShell cannot return or display the job results.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

<span data-ttu-id="0b49c-133">L’applet de commande Job peut ne pas être en mesure d’obtenir des instances de tâche planifiée ou leurs résultats, car le module **PSScheduledJob** n’est pas importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="0b49c-133">The job cmdlet might not be able to get scheduled job instances or their results because the **PSScheduledJob** module is not imported into the session.</span></span>

> [!NOTE]
> <span data-ttu-id="0b49c-134">Avant d’utiliser une applet de commande Job sur des instances de tâche planifiée, vérifiez que le module **PSScheduledJob** est inclus dans la session.</span><span class="sxs-lookup"><span data-stu-id="0b49c-134">Before using a job cmdlet on scheduled job instances, verify that the **PSScheduledJob** module is included in the session.</span></span> <span data-ttu-id="0b49c-135">Sans le module **PSScheduledJob** , les applets de commande Job ne peuvent pas obtenir les instances de tâche planifiée ou leurs résultats.</span><span class="sxs-lookup"><span data-stu-id="0b49c-135">Without the **PSScheduledJob** module, the job cmdlets cannot get scheduled job instances or their results.</span></span>

<span data-ttu-id="0b49c-136">Pour importer le module **PSScheduledJob** :</span><span class="sxs-lookup"><span data-stu-id="0b49c-136">To import the **PSScheduledJob** module:</span></span>

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a><span data-ttu-id="0b49c-137">Receive-Job applet de commande a peut-être déjà retourné les résultats</span><span class="sxs-lookup"><span data-stu-id="0b49c-137">Receive-Job cmdlet might already have returned the results</span></span>

<span data-ttu-id="0b49c-138">Si `Receive-Job` ne retourne pas de résultats d’instance de travail, cela peut être dû au fait qu’une `Receive-Job` commande a été exécutée pour cette instance de tâche dans la session active sans le paramètre **Keep** .</span><span class="sxs-lookup"><span data-stu-id="0b49c-138">If `Receive-Job` does not return job instance results, it might be because a `Receive-Job` command has been run for that job instance in the current session without the **Keep** parameter.</span></span>

<span data-ttu-id="0b49c-139">Lorsque vous utilisez `Receive-Job` sans le paramètre **Keep** , `Receive-Job` retourne les résultats de la tâche et définit la propriété **HasMoreData** de l’instance de tâche sur **false**.</span><span class="sxs-lookup"><span data-stu-id="0b49c-139">When you use `Receive-Job` without the **Keep** parameter, `Receive-Job` returns the job results and sets the job instance's **HasMoreData** property to **False**.</span></span> <span data-ttu-id="0b49c-140">La valeur **false** signifie que `Receive-Job` a retourné les résultats de la tâche et que l’instance n’a plus de résultats à retourner.</span><span class="sxs-lookup"><span data-stu-id="0b49c-140">The **False** value means that `Receive-Job` returned the job's results and the instance has no more results to return.</span></span> <span data-ttu-id="0b49c-141">Ce paramètre est approprié pour les travaux en arrière-plan standard, mais pas pour les instances de tâches planifiées, qui sont enregistrées sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0b49c-141">This setting is appropriate for standard background jobs, but not for instances of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="0b49c-142">Pour réafficher les résultats de l’instance de tâche, démarrez une nouvelle session PowerShell en tapant `PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-142">To get the job instance results again, start a new PowerShell session by typing `PowerShell`.</span></span> <span data-ttu-id="0b49c-143">Importez le module **PSScheduledJob** , puis réessayez d' `Receive-Job` exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="0b49c-143">Import the **PSScheduledJob** module, and try the `Receive-Job` command again.</span></span>

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a><span data-ttu-id="0b49c-144">Utilisation du paramètre Keep pour obtenir des résultats plus d’une fois dans une session</span><span class="sxs-lookup"><span data-stu-id="0b49c-144">Using Keep parameter to get results more than one time in a session</span></span>

<span data-ttu-id="0b49c-145">Pour obtenir le résultat d’une instance de tâche plus d’une fois dans une session, utilisez le paramètre **Keep** de l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-145">To get the result of a job instance more than one time in a session, use the **Keep** parameter of the `Receive-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a><span data-ttu-id="0b49c-146">La tâche planifiée est peut-être endommagée</span><span class="sxs-lookup"><span data-stu-id="0b49c-146">The scheduled job might be corrupted</span></span>

<span data-ttu-id="0b49c-147">Si une tâche planifiée est endommagée, PowerShell supprime la tâche planifiée endommagée et ses résultats.</span><span class="sxs-lookup"><span data-stu-id="0b49c-147">If a scheduled job becomes corrupted, PowerShell deletes the corrupted scheduled job and its results.</span></span> <span data-ttu-id="0b49c-148">Vous ne pouvez pas récupérer les résultats d’une tâche planifiée endommagée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-148">You cannot recover the results of a corrupted scheduled job.</span></span>

<span data-ttu-id="0b49c-149">Pour déterminer si une tâche planifiée existe toujours, utilisez l’applet de commande `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-149">To determine if a scheduled job still exists, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a><span data-ttu-id="0b49c-150">Le nombre de résultats a peut-être dépassé le ExecutionHistoryLength</span><span class="sxs-lookup"><span data-stu-id="0b49c-150">The number of results might have exceeded the ExecutionHistoryLength</span></span>

<span data-ttu-id="0b49c-151">La propriété **ExecutionHistoryLength** d’une tâche planifiée détermine le nombre d’instances de travail, ainsi que leurs résultats, qui sont enregistrés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0b49c-151">The **ExecutionHistoryLength** property of a scheduled job determines how many job instances, and their results, are saved to disk.</span></span> <span data-ttu-id="0b49c-152">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="0b49c-152">The default value is 32.</span></span>
<span data-ttu-id="0b49c-153">Lorsque le nombre d’instances d’une tâche planifiée dépasse cette valeur, PowerShell supprime l’instance de tâche la plus ancienne pour faire de la place pour chaque nouvelle instance de tâche.</span><span class="sxs-lookup"><span data-stu-id="0b49c-153">When the number of instances of a scheduled job exceeds this value, PowerShell deletes the oldest job instance to make room for each new job instance.</span></span>

<span data-ttu-id="0b49c-154">Pour obtenir la valeur de la propriété **ExecutionHistoryLength** d’une tâche planifiée, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="0b49c-154">To get the value of the **ExecutionHistoryLength** property of a scheduled job, use the following command format:</span></span>

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

<span data-ttu-id="0b49c-155">Par exemple, la commande suivante obtient la valeur de la propriété **ExecutionHistoryLength** de la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0b49c-155">For example, the following command gets the value of the **ExecutionHistoryLength** property of the **ProcessJob** scheduled job.</span></span>

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

<span data-ttu-id="0b49c-156">Pour définir ou modifier la valeur de la propriété **ExecutionHistoryLength** , utilisez le paramètre **MaxResultCount** des applets de commande `Register-ScheduledJob` et `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-156">To set or change the value of the **ExecutionHistoryLength** property, use the **MaxResultCount** parameter of the `Register-ScheduledJob` and `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="0b49c-157">La commande suivante augmente la valeur de la propriété **ExecutionHistoryLength** à 50.</span><span class="sxs-lookup"><span data-stu-id="0b49c-157">The following command increases the value of the **ExecutionHistoryLength** property to 50.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a><span data-ttu-id="0b49c-158">Les résultats de l’instance de tâche ont peut-être été supprimés</span><span class="sxs-lookup"><span data-stu-id="0b49c-158">The job instance results might have been deleted</span></span>

<span data-ttu-id="0b49c-159">Le paramètre **ClearExecutionHistory** de l' `Set-ScheduledJob` applet de commande supprime l’historique d’exécution d’un travail.</span><span class="sxs-lookup"><span data-stu-id="0b49c-159">The **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet deletes the execution history of a job.</span></span> <span data-ttu-id="0b49c-160">Vous pouvez utiliser cette fonctionnalité pour libérer de l’espace disque ou supprimer des résultats qui ne sont pas nécessaires, ou déjà utilisés, analysés ou enregistrés à un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="0b49c-160">You can use this feature to free up disk space or delete results that are not needed, or already used, analyzed or saved in a different location.</span></span>

<span data-ttu-id="0b49c-161">Pour supprimer l’historique d’exécution d’une tâche planifiée, utilisez le paramètre **ClearExecutionHistory** de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-161">To delete the execution history of a scheduled job, use the **ClearExecutionHistory** parameter of the scheduled job.</span></span>

<span data-ttu-id="0b49c-162">La commande suivante supprime l’historique d’exécution de la tâche planifiée **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0b49c-162">The following command deletes the execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="0b49c-163">En outre, l’applet de commande supprime les résultats de la `Remove-Job` tâche.</span><span class="sxs-lookup"><span data-stu-id="0b49c-163">Also, the `Remove-Job` cmdlet deletes job results.</span></span> <span data-ttu-id="0b49c-164">Lorsque vous utilisez `Remove-Job` pour supprimer une tâche planifiée, elle supprime toutes les instances du travail sur le disque, y compris l’historique d’exécution et tous les résultats de la tâche.</span><span class="sxs-lookup"><span data-stu-id="0b49c-164">When you use `Remove-Job` to delete a scheduled job, it deletes all instances of the job on disk, including the execution history and all job results.</span></span>

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a><span data-ttu-id="0b49c-165">Les travaux démarrés à l’aide de l’applet de commande Start-Job ne sont pas enregistrés sur le disque</span><span class="sxs-lookup"><span data-stu-id="0b49c-165">Jobs started by using the Start-Job cmdlet are not saved to disk</span></span>

<span data-ttu-id="0b49c-166">Lorsque vous utilisez `Start-Job` pour démarrer une tâche planifiée, au lieu d’utiliser un déclencheur de tâche, `Start-Job` démarre une tâche en arrière-plan standard.</span><span class="sxs-lookup"><span data-stu-id="0b49c-166">When you use `Start-Job` to start a scheduled job, instead of using a job trigger, `Start-Job` starts a standard background job.</span></span> <span data-ttu-id="0b49c-167">La tâche en arrière-plan et ses résultats ne sont pas stockés dans l’historique d’exécution du travail sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0b49c-167">The background job and its results are not stored in the execution history of the job on disk.</span></span>

<span data-ttu-id="0b49c-168">Vous pouvez utiliser l' `Get-Job` applet de commande pour obtenir le travail et l' `Receive-Job` applet de commande pour obtenir les résultats de la tâche, mais les résultats sont disponibles uniquement jusqu’à ce que vous les receviez, à moins que vous n’utilisiez le paramètre Keep de l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-168">You can use the `Get-Job` cmdlet to get the job and the `Receive-Job` cmdlet to get the job results, but the results are available only until you receive them, unless you use the Keep parameter of the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="0b49c-169">En outre, les travaux en arrière-plan et leurs résultats sont spécifiques à la session ; ils existent uniquement dans la session dans laquelle ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="0b49c-169">Also, background jobs and their results are session-specific; they exist only in the session in which they are created.</span></span> <span data-ttu-id="0b49c-170">Si vous supprimez le travail avec `Remove-Job` , fermez la session ou fermez PowerShell, l’instance de tâche et ses résultats sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="0b49c-170">If you delete the job with `Remove-Job`, close the session or close PowerShell, the job instance and its results are deleted.</span></span>

## <a name="scheduled-job-doesnt-run"></a><span data-ttu-id="0b49c-171">La tâche planifiée ne s’exécute pas</span><span class="sxs-lookup"><span data-stu-id="0b49c-171">Scheduled job doesn't run</span></span>

<span data-ttu-id="0b49c-172">Les tâches planifiées ne s’exécutent pas automatiquement si le travail est déclenché ou si la tâche planifiée est désactivée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-172">Scheduled jobs don't run automatically if the job triggers or the scheduled job are disabled.</span></span>

<span data-ttu-id="0b49c-173">Utilisez l' `Get-ScheduledJob` applet de commande pour récupérer la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-173">Use the `Get-ScheduledJob` cmdlet to get the scheduled job.</span></span> <span data-ttu-id="0b49c-174">Vérifiez que la valeur de la propriété **Enabled** de la tâche planifiée est **true**.</span><span class="sxs-lookup"><span data-stu-id="0b49c-174">Verify that the value of the **Enabled** property of the scheduled job is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

<span data-ttu-id="0b49c-175">Utilisez l' `Get-JobTrigger` applet de commande pour récupérer les déclencheurs de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-175">Use the `Get-JobTrigger` cmdlet to get the job triggers of the scheduled job.</span></span>
<span data-ttu-id="0b49c-176">Vérifiez que la valeur de la propriété **Enabled** du déclencheur de tâche est **true**.</span><span class="sxs-lookup"><span data-stu-id="0b49c-176">Verify that the value of the **Enabled** property of the job trigger is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a><span data-ttu-id="0b49c-177">Les tâches planifiées ne s’exécutent pas automatiquement si les déclencheurs de tâche ne sont pas valides</span><span class="sxs-lookup"><span data-stu-id="0b49c-177">Scheduled jobs don't run automatically if job triggers are invalid</span></span>

<span data-ttu-id="0b49c-178">Par exemple, un déclencheur de tâche peut spécifier une date passée ou une date qui ne se produit pas, par exemple, le 5e lundi du mois.</span><span class="sxs-lookup"><span data-stu-id="0b49c-178">For example, a job trigger might specify a date in the past or a date that does not occur, such as the 5th Monday of the month.</span></span>

<span data-ttu-id="0b49c-179">Les tâches planifiées ne s’exécutent pas automatiquement si les conditions du déclencheur de tâche ou des options de tâche ne sont pas satisfaites.</span><span class="sxs-lookup"><span data-stu-id="0b49c-179">Scheduled jobs do not run automatically if the conditions of the job trigger or the job options are not satisfied.</span></span>

<span data-ttu-id="0b49c-180">Par exemple, une tâche planifiée qui s’exécute uniquement lorsqu’un utilisateur particulier ouvre une session sur l’ordinateur ne s’exécutera pas si cet utilisateur ne se connecte pas ou ne se connecte qu’à distance.</span><span class="sxs-lookup"><span data-stu-id="0b49c-180">For example, a scheduled job that runs only when a particular user logs on to the computer will not run if that user does not log on or only connects remotely.</span></span>

<span data-ttu-id="0b49c-181">Examinez les options de la tâche planifiée et assurez-vous qu’elles sont satisfaites.</span><span class="sxs-lookup"><span data-stu-id="0b49c-181">Examine the options of the scheduled job and make sure that they are satisfied.</span></span>
<span data-ttu-id="0b49c-182">Par exemple, une tâche planifiée qui requiert que l’ordinateur soit inactif ou nécessite une connexion réseau, ou qui a un long **IdleDuration** ou un bref **IdleTimeout** peut ne jamais s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="0b49c-182">For example, a scheduled job that requires that the computer be idle or requires a network connection, or has a long **IdleDuration** or a brief **IdleTimeout** might never run.</span></span>

<span data-ttu-id="0b49c-183">Utilisez l' `Get-ScheduledJobOption` applet de commande pour examiner les options de tâche et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="0b49c-183">Use the `Get-ScheduledJobOption` cmdlet to examine the job options and their values.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="0b49c-184">Pour obtenir une description des options de tâche planifiée, consultez [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span><span class="sxs-lookup"><span data-stu-id="0b49c-184">For descriptions of the scheduled job options, see [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

### <a name="the-scheduled-job-instance-might-have-failed"></a><span data-ttu-id="0b49c-185">L’instance de tâche planifiée a peut-être échoué</span><span class="sxs-lookup"><span data-stu-id="0b49c-185">The scheduled job instance might have failed</span></span>

<span data-ttu-id="0b49c-186">Si une commande de tâche planifiée échoue, PowerShell la signale immédiatement en générant un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0b49c-186">If a scheduled job command fails, PowerShell reports it immediately by generating an error message.</span></span> <span data-ttu-id="0b49c-187">Toutefois, si le travail échoue quand Planificateur de tâches tente de l’exécuter, l’erreur n’est pas disponible pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b49c-187">However, if the job fails when Task Scheduler tries to run it, the error is not available to PowerShell.</span></span>

<span data-ttu-id="0b49c-188">Utilisez les méthodes suivantes pour détecter et corriger les échecs de tâche :</span><span class="sxs-lookup"><span data-stu-id="0b49c-188">Use the following methods to detect and correct job failures:</span></span>

<span data-ttu-id="0b49c-189">Recherchez les erreurs dans le journal des événements Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="0b49c-189">Check the Task Scheduler event log for errors.</span></span> <span data-ttu-id="0b49c-190">Pour vérifier le journal, utilisez observateur d’événements ou une commande PowerShell telle que la suivante :</span><span class="sxs-lookup"><span data-stu-id="0b49c-190">To check the log, use Event Viewer or a PowerShell command such as the following:</span></span>

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

<span data-ttu-id="0b49c-191">Vérifiez l’enregistrement du travail dans Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="0b49c-191">Check the job record in Task Scheduler.</span></span> <span data-ttu-id="0b49c-192">Les tâches planifiées PowerShell sont stockées dans le dossier planifié de tâches suivant :</span><span class="sxs-lookup"><span data-stu-id="0b49c-192">PowerShell scheduled jobs are stored in the following Task Scheduled folder:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a><span data-ttu-id="0b49c-193">La tâche planifiée peut ne pas s’exécuter en raison d’une autorisation insuffisante</span><span class="sxs-lookup"><span data-stu-id="0b49c-193">The scheduled job might not run because of insufficient permission</span></span>

<span data-ttu-id="0b49c-194">Les tâches planifiées s’exécutent avec les autorisations de l’utilisateur qui a créé le travail ou les autorisations de l’utilisateur spécifié par le paramètre **Credential** dans la `Register-ScheduledJob` `Set-ScheduledJob` commande ou.</span><span class="sxs-lookup"><span data-stu-id="0b49c-194">Scheduled jobs run with the permissions of the user who created the job or the permissions of the user who is specified by the **Credential** parameter in the `Register-ScheduledJob` or `Set-ScheduledJob` command.</span></span>

<span data-ttu-id="0b49c-195">Si cet utilisateur n’est pas autorisé à exécuter les commandes ou les scripts, le travail échoue.</span><span class="sxs-lookup"><span data-stu-id="0b49c-195">If that user does not have permission to run the commands or scripts, the job fails.</span></span>

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a><span data-ttu-id="0b49c-196">Impossible d’effectuer une tâche planifiée ou une tâche planifiée endommagée</span><span class="sxs-lookup"><span data-stu-id="0b49c-196">Can't get scheduled job or scheduled job is corrupted</span></span>

<span data-ttu-id="0b49c-197">Dans de rares occasions, les tâches planifiées peuvent être endommagées ou contenir des contradictions internes qui ne peuvent pas être résolues.</span><span class="sxs-lookup"><span data-stu-id="0b49c-197">On rare occasions, scheduled jobs can become corrupted or contain internal contradictions that cannot be resolved.</span></span> <span data-ttu-id="0b49c-198">En général, cela se produit lorsque les fichiers XML de la tâche planifiée sont modifiés manuellement, ce qui génère un code XML non valide.</span><span class="sxs-lookup"><span data-stu-id="0b49c-198">Typically, this happens when the XML files for the scheduled job are manually edited, resulting in invalid XML.</span></span>

<span data-ttu-id="0b49c-199">Lorsqu’une tâche planifiée est endommagée, PowerShell tente de supprimer la tâche planifiée, son historique d’exécution et ses résultats sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0b49c-199">When a scheduled job is corrupted, PowerShell attempts to delete the scheduled job, its execution history, and its results from disk.</span></span>

<span data-ttu-id="0b49c-200">S’il ne peut pas supprimer la tâche planifiée, vous obtiendrez un message d’erreur de travail endommagé chaque fois que vous exécutez l’applet de commande `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-200">If it cannot remove the scheduled job, you will get a corrupted job error message each time you run the `Get-ScheduledJob` cmdlet.</span></span>

<span data-ttu-id="0b49c-201">Pour supprimer une tâche planifiée endommagée, utilisez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0b49c-201">To remove a corrupted scheduled job, use either one of the following methods:</span></span>

<span data-ttu-id="0b49c-202">Supprimez le `<ScheduledJobName>` Répertoire de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-202">Delete the `<ScheduledJobName>` directory for the scheduled job.</span></span> <span data-ttu-id="0b49c-203">Ne supprimez pas le répertoire **ScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="0b49c-203">Don't delete the **ScheduledJob** directory.</span></span>

<span data-ttu-id="0b49c-204">Emplacement du répertoire :</span><span class="sxs-lookup"><span data-stu-id="0b49c-204">The directory's location:</span></span>

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

<span data-ttu-id="0b49c-205">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0b49c-205">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

<span data-ttu-id="0b49c-206">Utilisez Planificateur de tâches pour supprimer la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="0b49c-206">Use Task Scheduler to delete the scheduled job.</span></span> <span data-ttu-id="0b49c-207">Les tâches planifiées PowerShell s’affichent dans le chemin d’accès Planificateur de tâches suivant :</span><span class="sxs-lookup"><span data-stu-id="0b49c-207">PowerShell scheduled tasks appear in the following Task Scheduler path:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a><span data-ttu-id="0b49c-208">Les applets de commande Job ne peuvent pas trouver régulièrement des tâches planifiées</span><span class="sxs-lookup"><span data-stu-id="0b49c-208">Job cmdlets can't consistently find scheduled jobs</span></span>

<span data-ttu-id="0b49c-209">Lorsque le module **PSScheduledJob** n’est pas dans la session active, les applets de commande Job ne peuvent pas obtenir de tâches planifiées, les démarrer ou obtenir leurs résultats.</span><span class="sxs-lookup"><span data-stu-id="0b49c-209">When the **PSScheduledJob** module isn't in the current session, the job cmdlets cannot get scheduled jobs, start them, or get their results.</span></span>

<span data-ttu-id="0b49c-210">Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou exécutez ou récupérez une applet de commande dans le module, telle que l’applet de commande `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0b49c-210">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or run or get any cmdlet in the module, such as the `Get-ScheduledJob` cmdlet.</span></span>
<span data-ttu-id="0b49c-211">À compter de PowerShell 3,0, les modules sont importés automatiquement lorsque vous récupérez ou utilisez une applet de commande dans le module.</span><span class="sxs-lookup"><span data-stu-id="0b49c-211">Beginning in PowerShell 3.0, modules are imported automatically when you get or use any cmdlet in the module.</span></span>

<span data-ttu-id="0b49c-212">Lorsque le module **PSScheduledJob** n’est pas dans la session active, la séquence de commandes suivante est possible.</span><span class="sxs-lookup"><span data-stu-id="0b49c-212">When the **PSScheduledJob** module isn't in the current session, the following command sequence is possible.</span></span>

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

<span data-ttu-id="0b49c-213">Ce comportement se produit parce que la `Get-ScheduledJob` commande importe automatiquement le module **PSScheduledJob** , puis exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="0b49c-213">This behavior occurs because the `Get-ScheduledJob` command automatically imports the **PSScheduledJob** module, and then runs the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b49c-214">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b49c-214">See also</span></span>

[<span data-ttu-id="0b49c-215">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="0b49c-215">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="0b49c-216">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="0b49c-216">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="0b49c-217">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="0b49c-217">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

<span data-ttu-id="0b49c-218">Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)</span><span class="sxs-lookup"><span data-stu-id="0b49c-218">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="0b49c-219">Planificateur de tâches</span><span class="sxs-lookup"><span data-stu-id="0b49c-219">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
