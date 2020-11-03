---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202994"
---
# <span data-ttu-id="91417-103">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-103">Register-ScheduledJob</span></span>

## <span data-ttu-id="91417-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="91417-104">SYNOPSIS</span></span>
<span data-ttu-id="91417-105">Crée une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-105">Creates a scheduled job.</span></span>

## <span data-ttu-id="91417-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="91417-106">SYNTAX</span></span>

### <span data-ttu-id="91417-107">ScriptBlock (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="91417-107">ScriptBlock (Default)</span></span>

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="91417-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="91417-108">FilePath</span></span>

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="91417-109">Description</span><span class="sxs-lookup"><span data-stu-id="91417-109">DESCRIPTION</span></span>

<span data-ttu-id="91417-110">L' `Register-ScheduledJob` applet de commande crée des tâches planifiées sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="91417-110">The `Register-ScheduledJob` cmdlet creates scheduled jobs on the local computer.</span></span>

<span data-ttu-id="91417-111">Une tâche planifiée est une tâche en arrière-plan Windows PowerShell qui peut être démarrée automatiquement selon une planification ponctuelle ou périodique.</span><span class="sxs-lookup"><span data-stu-id="91417-111">A scheduled job is a Windows PowerShell background job that can be started automatically on a one-time or recurring schedule.</span></span> <span data-ttu-id="91417-112">Les tâches planifiées sont stockées sur le disque et enregistrées dans Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="91417-112">Scheduled jobs are stored on disk and registered in Task Scheduler.</span></span>
<span data-ttu-id="91417-113">Les tâches peuvent être gérées dans Planificateur de tâches ou à l’aide des applets de commande de tâche planifiée dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91417-113">The jobs can be managed in Task Scheduler or by using the Scheduled Job cmdlets in Windows PowerShell.</span></span>

<span data-ttu-id="91417-114">Lorsqu’une tâche planifiée démarre, elle crée une instance de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-114">When a scheduled job starts, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="91417-115">Les instances de tâche planifiée sont identiques aux tâches en arrière-plan Windows PowerShell, sauf que les résultats sont enregistrés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="91417-115">Scheduled job instances are identical to Windows PowerShell background jobs, except that the results are saved on disk.</span></span> <span data-ttu-id="91417-116">Utilisez les applets de commande Job, telles que `Start-Job` , `Get-Job` et `Receive-Job` pour démarrer, afficher et obtenir les résultats des instances de tâche.</span><span class="sxs-lookup"><span data-stu-id="91417-116">Use the Job cmdlets, such as `Start-Job`, `Get-Job`, and `Receive-Job` to start, view, and get the results of the job instances.</span></span>

<span data-ttu-id="91417-117">Utilisez `Register-ScheduledJob` pour créer une nouvelle tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-117">Use `Register-ScheduledJob` to create a new scheduled job.</span></span> <span data-ttu-id="91417-118">Pour spécifier les commandes exécutées par la tâche planifiée, utilisez le paramètre **scriptblock** .</span><span class="sxs-lookup"><span data-stu-id="91417-118">To specify the commands that the scheduled job runs, use the **ScriptBlock** parameter.</span></span> <span data-ttu-id="91417-119">Pour spécifier un script exécuté par la tâche, utilisez le paramètre **filePath** .</span><span class="sxs-lookup"><span data-stu-id="91417-119">To specify a script that the job runs, use the **FilePath** parameter.</span></span>

<span data-ttu-id="91417-120">Windows PowerShell-les tâches planifiées utilisent les mêmes déclencheurs et options de tâche que ceux utilisés par Planificateur de tâches pour les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="91417-120">Windows PowerShell-scheduled jobs use the same job triggers and job options that Task Scheduler uses for scheduled tasks.</span></span>

<span data-ttu-id="91417-121">Le paramètre **Trigger** de `Register-ScheduledJob` ajoute un ou plusieurs déclencheurs de tâche qui démarrent le travail.</span><span class="sxs-lookup"><span data-stu-id="91417-121">The **Trigger** parameter of `Register-ScheduledJob` adds one or more job triggers that start the job.</span></span> <span data-ttu-id="91417-122">Le paramètre de **déclencheur** étant facultatif, vous pouvez ajouter des déclencheurs quand vous créez la tâche planifiée, ajouter des déclencheurs de tâche ultérieurement, ajouter le paramètre **RunNow** pour démarrer la tâche immédiatement, utiliser l' `Start-Job` applet de commande pour démarrer la tâche immédiatement à tout moment, ou enregistrer la tâche planifiée non déclenchée comme modèle pour d’autres travaux.</span><span class="sxs-lookup"><span data-stu-id="91417-122">The **Trigger** parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the **RunNow** parameter to start the job immediately, use the `Start-Job` cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="91417-123">Le paramètre **Options** vous permet de personnaliser les paramètres des options pour la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-123">The **Options** parameter lets you customize the options settings for the scheduled job.</span></span> <span data-ttu-id="91417-124">Le paramètre **options** est facultatif, ce qui vous permet de définir des options de tâche lorsque vous créez la tâche planifiée ou de les modifier à tout moment.</span><span class="sxs-lookup"><span data-stu-id="91417-124">The **Options** parameter is optional, so you can set job options when you create the scheduled job or change them at any time.</span></span> <span data-ttu-id="91417-125">Comme les paramètres d'options de tâche peuvent empêcher l'exécution de la tâche planifiée, passez en revue les options de tâche et définissez-les avec soin.</span><span class="sxs-lookup"><span data-stu-id="91417-125">Because job option settings can prevent the scheduled job from running, review the job options and set them carefully.</span></span>

<span data-ttu-id="91417-126">`Register-ScheduledJob` est l’une des collections d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91417-126">`Register-ScheduledJob` is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="91417-127">Pour plus d’informations sur les tâches planifiées, consultez la rubrique à propos des articles dans le module **PSScheduledJob** .</span><span class="sxs-lookup"><span data-stu-id="91417-127">For more information about Scheduled Jobs, see the About articles in the **PSScheduledJob** module.</span></span>
<span data-ttu-id="91417-128">Importez le module **PSScheduledJob** , puis tapez : `Get-Help about_Scheduled*` ou consultez [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="91417-128">Import the **PSScheduledJob** module and then type: `Get-Help about_Scheduled*` or see [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span></span>

<span data-ttu-id="91417-129">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="91417-129">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="91417-130">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="91417-130">EXAMPLES</span></span>

### <span data-ttu-id="91417-131">Exemple 1 : créer une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="91417-131">Example 1: Create a scheduled job</span></span>

<span data-ttu-id="91417-132">Cet exemple crée une tâche planifiée sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="91417-132">This example creates a scheduled job on the local computer.</span></span>

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

<span data-ttu-id="91417-133">`Register-ScheduledJob` utilise le paramètre **Name** pour créer la tâche planifiée **Archive-scripts** .</span><span class="sxs-lookup"><span data-stu-id="91417-133">`Register-ScheduledJob` uses the **Name** parameter to create the **Archive-Scripts** scheduled job.</span></span>
<span data-ttu-id="91417-134">Le paramètre **scriptblock** s’exécute `Get-ChildItem` et recherche les `$home` fichiers de manière récursive dans le répertoire `.ps1` .</span><span class="sxs-lookup"><span data-stu-id="91417-134">The **ScriptBlock** parameter runs `Get-ChildItem` that searches the `$home` directory recursively for `.ps1` files.</span></span> <span data-ttu-id="91417-135">L' `Copy-Item` applet de commande copie les fichiers dans un répertoire spécifié par le paramètre **destination** .</span><span class="sxs-lookup"><span data-stu-id="91417-135">The `Copy-Item` cmdlet copies the files to a directory specified by the **Destination** parameter.</span></span>

<span data-ttu-id="91417-136">Étant donné que la tâche planifiée ne contient pas de déclencheur, elle n’est pas démarrée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="91417-136">Because the scheduled job doesn't contain a trigger, it's not started automatically.</span></span> <span data-ttu-id="91417-137">Vous pouvez ajouter des déclencheurs de tâche avec `Add-JobTrigger` , utiliser l' `Start-Job` applet de commande pour démarrer le travail à la demande ou utiliser la tâche planifiée comme modèle pour d’autres tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="91417-137">You can add job triggers with `Add-JobTrigger`, use the `Start-Job` cmdlet to start the job on demand, or use the scheduled job as a template for other scheduled jobs.</span></span>

### <span data-ttu-id="91417-138">Exemple 2 : créer une tâche planifiée avec des déclencheurs et des options personnalisées</span><span class="sxs-lookup"><span data-stu-id="91417-138">Example 2: Create a scheduled job with triggers and custom options</span></span>

<span data-ttu-id="91417-139">Cet exemple montre comment créer une tâche planifiée qui a un déclencheur de tâche et des options de tâche personnalisées.</span><span class="sxs-lookup"><span data-stu-id="91417-139">This example shows how to create a scheduled job that has a job trigger and custom job options.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

<span data-ttu-id="91417-140">La `$O` variable stocke l’objet d’option de travail créé par l’applet de commande `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="91417-140">The `$O` variable stores the job option object that the `New-ScheduledJobOption` cmdlet created.</span></span> <span data-ttu-id="91417-141">Les options démarrent la tâche planifiée même si l’ordinateur n’est pas inactif, sort de veille l’ordinateur pour exécuter le travail, si nécessaire, et autorise l’exécution de plusieurs instances du travail dans une série.</span><span class="sxs-lookup"><span data-stu-id="91417-141">The options start the scheduled job even if the computer isn't idle, wakes the computer to run the job, if necessary, and allows multiple instances of the job to run in a series.</span></span>

<span data-ttu-id="91417-142">La `$T` variable stocke le résultat de l' `New-JobTrigger` applet de commande pour créer un déclencheur de tâche qui démarre un travail tous les autres lundis à 9:00 pm.</span><span class="sxs-lookup"><span data-stu-id="91417-142">The `$T` variable stores the result from the `New-JobTrigger` cmdlet to create job trigger that starts a job every other Monday at 9:00 PM.</span></span>

<span data-ttu-id="91417-143">La `$path` variable stocke le chemin d’accès au `UpdateVersion.ps1` fichier de script.</span><span class="sxs-lookup"><span data-stu-id="91417-143">The `$path` variable stores the path to the `UpdateVersion.ps1` script file.</span></span>

<span data-ttu-id="91417-144">`Register-ScheduledJob` utilise le paramètre **Name** pour créer la tâche planifiée **UpdateVersion** .</span><span class="sxs-lookup"><span data-stu-id="91417-144">`Register-ScheduledJob` uses the **Name** paramter to create the **UpdateVersion** scheduled job.</span></span>
<span data-ttu-id="91417-145">Le paramètre **filePath** utilise `$path` pour spécifier le script exécuté par le travail.</span><span class="sxs-lookup"><span data-stu-id="91417-145">The **FilePath** parameter uses `$path` to specify the script that the job runs.</span></span> <span data-ttu-id="91417-146">Le paramètre **ScheduledJobOption** utilise les options de travail stockées dans `$O` .</span><span class="sxs-lookup"><span data-stu-id="91417-146">The **ScheduledJobOption** parameter uses the job options stored in `$O`.</span></span> <span data-ttu-id="91417-147">Le paramètre **Trigger** utilise les déclencheurs de tâche stockés dans `$T` .</span><span class="sxs-lookup"><span data-stu-id="91417-147">The **Trigger** parameter uses the job triggers stored in `$T`.</span></span>

### <span data-ttu-id="91417-148">Exemple 3 : utiliser des tables de hachage pour spécifier un déclencheur et des options de tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="91417-148">Example 3: Use hash tables to specify a trigger and scheduled job options</span></span>

<span data-ttu-id="91417-149">Cet exemple a le même effet que la commande dans l’exemple 2.</span><span class="sxs-lookup"><span data-stu-id="91417-149">This example has the same effect as the command in Example 2.</span></span> <span data-ttu-id="91417-150">Il crée une tâche planifiée à l’aide de tables de hachage pour spécifier les valeurs des paramètres **déclencheur** et **ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="91417-150">It creates a scheduled job, using hash tables to specify the values of the **Trigger** and **ScheduledJobOption** parameters.</span></span> <span data-ttu-id="91417-151">Les `$O` `$T` variables et définies dans l’exemple 2 sont remplacées par des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="91417-151">The `$O` and `$T`variables defined in Example 2 are replaced with hash tables.</span></span>

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### <span data-ttu-id="91417-152">Exemple 4 : créer des tâches planifiées sur des ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="91417-152">Example 4: Create scheduled jobs on remote computers</span></span>

<span data-ttu-id="91417-153">Dans cet exemple, la tâche planifiée **EnergyData** est créée sur plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="91417-153">In this example, the **EnergyData** scheduled job is created on multiple remote computers.</span></span> <span data-ttu-id="91417-154">La tâche planifiée exécute un script qui recueille les données brutes et les enregistre dans un journal d’exécution sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="91417-154">The scheduled job runs a script that gathers raw data and saves it in a running log on the remote computer.</span></span>

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

<span data-ttu-id="91417-155">La `$Cred` variable stocke les informations d’identification dans un objet **PSCredential** pour un utilisateur disposant des autorisations nécessaires pour créer des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="91417-155">The `$Cred` variable stores credentials in a **PSCredential** object for a user with permissions to create scheduled jobs.</span></span> <span data-ttu-id="91417-156">La `$O` variable stocke les options de travail créées avec `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="91417-156">The `$O` variable stores the job options created with `New-ScheduledJobOption`.</span></span> <span data-ttu-id="91417-157">La `$T` variable stocke les déclencheurs de tâche créés avec `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="91417-157">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="91417-158">L' `Invoke-Command` applet de commande utilise le paramètre **ComputerName** pour obtenir une liste de noms de serveurs à partir du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="91417-158">The `Invoke-Command` cmdlet uses the **ComputerName** parameter to get a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="91417-159">Le paramètre **Credential** obtient l’objet Credential stocké dans `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="91417-159">The **Credential** parameter gets the credential object stored in `$Cred`.</span></span>
<span data-ttu-id="91417-160">Le paramètre **scriptblock** exécute une `Register-ScheduledJob` commande sur les ordinateurs du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="91417-160">The **ScriptBlock** parameter runs a `Register-ScheduledJob` command on the computers in the `Servers.txt` file.</span></span>

<span data-ttu-id="91417-161">Les paramètres de `Register-ScheduledJob` sont définis par `$params` .</span><span class="sxs-lookup"><span data-stu-id="91417-161">The parameters for `Register-ScheduledJob` are defined by `$params`.</span></span> <span data-ttu-id="91417-162">Les paramètres **Name** spécifient que le travail est nommé **« EnergyData »** sur chaque ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="91417-162">The **Name** parameters specifies the job is named **Get-EnergyData** on each remote computer.</span></span> <span data-ttu-id="91417-163">**FilePath** fournit l’emplacement du `EnergyData.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="91417-163">**FilePath** provides the location of the `EnergyData.ps1` script.</span></span> <span data-ttu-id="91417-164">Le script se trouve sur un serveur de fichiers qui est disponible pour tous les ordinateurs participants. La tâche s’exécute selon la planification spécifiée par les déclencheurs de tâche dans `$T` et les options de tâche dans `$O` .</span><span class="sxs-lookup"><span data-stu-id="91417-164">The script is located on a file server that is available to all participating computers.The job runs on the schedule specified by the job triggers in `$T` and the job options in `$O`.</span></span>

<span data-ttu-id="91417-165">La `Register-ScheduledJob @params` commande crée la tâche planifiée avec les paramètres du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="91417-165">The `Register-ScheduledJob @params` command creates the scheduled job with the parameters from the script block.</span></span>

### <span data-ttu-id="91417-166">Exemple 5 : créer une tâche planifiée qui exécute un script sur des ordinateurs distants</span><span class="sxs-lookup"><span data-stu-id="91417-166">Example 5: Create a scheduled job that runs a script on remote computers</span></span>

<span data-ttu-id="91417-167">Cet exemple crée la tâche planifiée **CollectEnergyData** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="91417-167">This example creates the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="91417-168">La tâche s’exécute sur plusieurs ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="91417-168">The job runs on multiple remote computers.</span></span>

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

<span data-ttu-id="91417-169">La `$Admin` variable stocke les informations d’identification d’un utilisateur disposant des autorisations nécessaires pour exécuter les commandes dans un objet **PSCredential** .</span><span class="sxs-lookup"><span data-stu-id="91417-169">The `$Admin` variable stores credentials for a user with permissions to run the commands in a **PSCredential** object.</span></span> <span data-ttu-id="91417-170">La `$T` variable stocke les déclencheurs de tâche créés avec `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="91417-170">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="91417-171">L' `Register-ScheduledJob` applet de commande utilise le paramètre **Name** pour créer la tâche planifiée **CollectEnergyData** sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="91417-171">The `Register-ScheduledJob` cmdlet uses the **Name** parameter to create the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="91417-172">Le paramètre **Trigger** spécifie les déclencheurs de tâche dans `$T` et le paramètre **MaxResultCount** augmente le nombre de résultats enregistrés à 99.</span><span class="sxs-lookup"><span data-stu-id="91417-172">The **Trigger** parameter specifies the job triggers in `$T` and the **MaxResultCount** parameter increases the number of saved results to 99.</span></span>

<span data-ttu-id="91417-173">Le paramètre **scriptblock** définit les `Invoke-Command` paramètres avec `$params` .</span><span class="sxs-lookup"><span data-stu-id="91417-173">The **ScriptBlock** parameter defines the `Invoke-Command` parameters with `$params`.</span></span> <span data-ttu-id="91417-174">Le paramètre **AsJob** crée l’objet de tâche en arrière-plan sur l’ordinateur local, même si le `Energydata.ps1` script s’exécute sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="91417-174">The **AsJob** parameter creates the background job object on the local computer, even though the `Energydata.ps1` script runs on the remote computers.</span></span> <span data-ttu-id="91417-175">Le paramètre **ComputerName** obtient une liste de noms de serveurs à partir du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="91417-175">The **ComputerName** parameter gets a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="91417-176">Le paramètre **Credential** spécifie un compte d’utilisateur qui a l’autorisation d’exécuter des scripts sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="91417-176">The **Credential** parameter specifies a user account that has permission to run scripts on the remote computers.</span></span> <span data-ttu-id="91417-177">Et, le paramètre **Authentication** spécifie la valeur **CredSSP** pour autoriser les informations d’identification déléguées.</span><span class="sxs-lookup"><span data-stu-id="91417-177">And, the **Authentication** parameter specifies a value of **CredSSP** to allow delegated credentials.</span></span>

<span data-ttu-id="91417-178">Le `Invoke-Command @params` exécute la commande avec les paramètres du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="91417-178">The `Invoke-Command @params` runs the command with the parameters from the script block.</span></span>

## <span data-ttu-id="91417-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="91417-179">PARAMETERS</span></span>

### <span data-ttu-id="91417-180">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="91417-180">-ArgumentList</span></span>

<span data-ttu-id="91417-181">Spécifie des valeurs pour les paramètres du script spécifié par le paramètre **FilePath** ou pour la commande spécifiée par le paramètre **ScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="91417-181">Specifies values for the parameters of the script that is specified by the **FilePath** parameter or for the command that is specified by the **ScriptBlock** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-182">-Authentification</span><span class="sxs-lookup"><span data-stu-id="91417-182">-Authentication</span></span>

<span data-ttu-id="91417-183">Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="91417-183">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="91417-184">La valeur par défaut est Default.</span><span class="sxs-lookup"><span data-stu-id="91417-184">The default value is Default.</span></span>

<span data-ttu-id="91417-185">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="91417-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="91417-186">Default</span><span class="sxs-lookup"><span data-stu-id="91417-186">Default</span></span>
- <span data-ttu-id="91417-187">Basic</span><span class="sxs-lookup"><span data-stu-id="91417-187">Basic</span></span>
- <span data-ttu-id="91417-188">CredSSP</span><span class="sxs-lookup"><span data-stu-id="91417-188">Credssp</span></span>
- <span data-ttu-id="91417-189">Digest</span><span class="sxs-lookup"><span data-stu-id="91417-189">Digest</span></span>
- <span data-ttu-id="91417-190">Kerberos</span><span class="sxs-lookup"><span data-stu-id="91417-190">Kerberos</span></span>
- <span data-ttu-id="91417-191">Negotiate</span><span class="sxs-lookup"><span data-stu-id="91417-191">Negotiate</span></span>
- <span data-ttu-id="91417-192">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="91417-192">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="91417-193">Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="91417-193">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="91417-194">L'authentification CredSSP (Credential Security Service Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="91417-194">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="91417-195">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="91417-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="91417-196">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="91417-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="91417-197">-Confirm</span></span>

<span data-ttu-id="91417-198">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="91417-198">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-199">-Credential</span><span class="sxs-lookup"><span data-stu-id="91417-199">-Credential</span></span>

<span data-ttu-id="91417-200">Spécifie un compte d'utilisateur qui a l'autorisation d'exécuter la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-200">Specifies a user account that has permission to run the scheduled job.</span></span> <span data-ttu-id="91417-201">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="91417-201">The default is the current user.</span></span>

<span data-ttu-id="91417-202">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="91417-202">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="91417-203">Si vous entrez uniquement un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="91417-203">If you enter only a user name, you're prompted for a password.</span></span>

<span data-ttu-id="91417-204">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="91417-204">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="91417-205">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="91417-205">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-206">-FilePath</span><span class="sxs-lookup"><span data-stu-id="91417-206">-FilePath</span></span>

<span data-ttu-id="91417-207">Spécifie un script exécuté par la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-207">Specifies a script that the scheduled job runs.</span></span> <span data-ttu-id="91417-208">Entrez le chemin d’accès à un `.ps1` fichier sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="91417-208">Enter the path to a `.ps1` file on the local computer.</span></span> <span data-ttu-id="91417-209">Pour spécifier les valeurs par défaut des paramètres de script, utilisez le paramètre **ArgumentList** .</span><span class="sxs-lookup"><span data-stu-id="91417-209">To specify default values for the script parameters, use the **ArgumentList** parameter.</span></span>
<span data-ttu-id="91417-210">Chaque `Register-ScheduledJob` commande doit utiliser les paramètres **scriptblock** ou **filePath** .</span><span class="sxs-lookup"><span data-stu-id="91417-210">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-211">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="91417-211">-InitializationScript</span></span>

<span data-ttu-id="91417-212">Spécifie le chemin d’accès complet à un script Windows PowerShell ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="91417-212">Specifies the fully qualified path to a Windows PowerShell script (`.ps1`).</span></span> <span data-ttu-id="91417-213">Le script d'initialisation s'exécute dans la session créée pour la tâche en arrière-plan avant les commandes spécifiées par le paramètre **ScriptBlock** ou le script spécifié par le paramètre **FilePath** .</span><span class="sxs-lookup"><span data-stu-id="91417-213">The initialization script runs in the session that is created for the background job before the commands that are specified by the **ScriptBlock** parameter or the script that is specified by the **FilePath** parameter.</span></span> <span data-ttu-id="91417-214">Vous pouvez utiliser le script d'initialisation pour configurer la session, par exemple, pour ajouter des fichiers, des fonctions ou des alias, pour créer des répertoires ou pour vérifier des conditions préalables.</span><span class="sxs-lookup"><span data-stu-id="91417-214">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="91417-215">Pour spécifier un script qui exécute les commandes de tâche principales, utilisez le paramètre **FilePath** .</span><span class="sxs-lookup"><span data-stu-id="91417-215">To specify a script that runs the primary job commands, use the **FilePath** parameter.</span></span>

<span data-ttu-id="91417-216">Si le script d’initialisation génère une erreur, même une erreur sans fin d’exécution, l’instance actuelle de la tâche planifiée ne s’exécute pas et son état est **failed** .</span><span class="sxs-lookup"><span data-stu-id="91417-216">If the initialization script generates an error, even a non-terminating error, the current instance of the scheduled job doesn't run and its status is **Failed** .</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-217">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="91417-217">-MaxResultCount</span></span>

<span data-ttu-id="91417-218">Spécifie le nombre d'entrées de résultat de tâche qui sont conservées pour la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-218">Specifies how many job result entries are maintained for the scheduled job.</span></span> <span data-ttu-id="91417-219">La valeur par défaut est 32.</span><span class="sxs-lookup"><span data-stu-id="91417-219">The default value is 32.</span></span>

<span data-ttu-id="91417-220">Windows PowerShell enregistre l'historique d'exécution et les résultats de chaque instance déclenchée de la tâche planifiée sur le disque.</span><span class="sxs-lookup"><span data-stu-id="91417-220">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span> <span data-ttu-id="91417-221">La valeur de ce paramètre détermine le nombre de résultats d'instance de tâche qui sont enregistrés pour cette tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-221">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span> <span data-ttu-id="91417-222">Quand le nombre de résultats d'instance de tâche dépasse cette valeur, Windows PowerShell supprime les résultats de l'instance de tâche la plus ancienne pour libérer de l'espace pour les résultats de la dernière instance de tâche.</span><span class="sxs-lookup"><span data-stu-id="91417-222">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="91417-223">L’historique d’exécution des travaux et les résultats des travaux sont enregistrés dans le `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span><span class="sxs-lookup"><span data-stu-id="91417-223">The job execution history and job results are saved in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span></span>
<span data-ttu-id="91417-224">répertoires sur l’ordinateur sur lequel le travail est créé.</span><span class="sxs-lookup"><span data-stu-id="91417-224">directories on the computer on which the job is created.</span></span> <span data-ttu-id="91417-225">Pour afficher l’historique d’exécution, utilisez l’applet de commande `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="91417-225">To see the execution history, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="91417-226">Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="91417-226">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="91417-227">Le paramètre **MaxResultCount** définit la valeur de la propriété ExecutionHistoryLength de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-227">The **MaxResultCount** parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="91417-228">Pour supprimer l’historique d’exécution actuel et les résultats des tâches, utilisez le paramètre **ClearExecutionHistory** de l’applet de commande `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="91417-228">To delete the current execution history and job results, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-229">-Name</span><span class="sxs-lookup"><span data-stu-id="91417-229">-Name</span></span>

<span data-ttu-id="91417-230">Spécifie un nom pour la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-230">Specifies a name for the scheduled job.</span></span> <span data-ttu-id="91417-231">Le nom est également utilisé pour toutes les instances démarrées de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-231">The name is also used for all started instances of the scheduled job.</span></span> <span data-ttu-id="91417-232">Le nom doit être unique sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="91417-232">The name must be unique on the computer.</span></span> <span data-ttu-id="91417-233">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="91417-233">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-234">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="91417-234">-RunAs32</span></span>

<span data-ttu-id="91417-235">Exécute la tâche planifiée dans un processus 32 bits.</span><span class="sxs-lookup"><span data-stu-id="91417-235">Runs the scheduled job in a 32-bit process.</span></span>

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

### <span data-ttu-id="91417-236">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="91417-236">-RunEvery</span></span>

<span data-ttu-id="91417-237">Utilisé pour spécifier la fréquence d’exécution du travail.</span><span class="sxs-lookup"><span data-stu-id="91417-237">Used to specify how often to run the job.</span></span> <span data-ttu-id="91417-238">Par exemple, utilisez cette option pour exécuter un travail toutes les 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="91417-238">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-239">-RunNow</span><span class="sxs-lookup"><span data-stu-id="91417-239">-RunNow</span></span>

<span data-ttu-id="91417-240">Démarre une tâche immédiatement, dès que l' `Register-ScheduledJob` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="91417-240">Starts a job immediately, as soon as the `Register-ScheduledJob` cmdlet is run.</span></span> <span data-ttu-id="91417-241">Ce paramètre élimine le besoin de déclencher des Planificateur de tâches pour exécuter un script Windows PowerShell immédiatement après l’inscription et n’oblige pas les utilisateurs à créer un déclencheur qui spécifie une date et une heure de début.</span><span class="sxs-lookup"><span data-stu-id="91417-241">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and doesn't require users to create a trigger that specifies a starting date and time.</span></span>

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

### <span data-ttu-id="91417-242">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="91417-242">-ScheduledJobOption</span></span>

<span data-ttu-id="91417-243">Définit les options de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-243">Sets options for the scheduled job.</span></span> <span data-ttu-id="91417-244">Entrez un objet **ScheduledJobOptions** , tel que celui que vous créez à l’aide de l’applet de commande `New-ScheduledJobOption` , ou une valeur de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="91417-244">Enter a **ScheduledJobOptions** object, such as one that you create by using the `New-ScheduledJobOption` cmdlet, or a hash table value.</span></span>

<span data-ttu-id="91417-245">Vous pouvez définir les options d’une tâche planifiée lors de l’inscription du travail de planification ou utiliser les `Set-ScheduledJobOption` `Set-ScheduledJob` applets de commande ou pour modifier les options.</span><span class="sxs-lookup"><span data-stu-id="91417-245">You can set options for a scheduled job when you register the schedule job or use the `Set-ScheduledJobOption` or `Set-ScheduledJob` cmdlets to change the options.</span></span>

<span data-ttu-id="91417-246">La plupart des options et leurs valeurs par défaut déterminent si et quand une tâche planifiée s'exécute.</span><span class="sxs-lookup"><span data-stu-id="91417-246">Many of the options and their default values determine whether and when a scheduled job runs.</span></span> <span data-ttu-id="91417-247">Veillez à consulter ces options avant de planifier une tâche.</span><span class="sxs-lookup"><span data-stu-id="91417-247">Be sure to review these options before scheduling a job.</span></span> <span data-ttu-id="91417-248">Pour obtenir une description des options de tâche planifiée, y compris les valeurs par défaut, consultez `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="91417-248">For a description of the scheduled job options, including the default values, see `New-ScheduledJobOption`.</span></span>

<span data-ttu-id="91417-249">Pour envoyer une table de hachage, utilisez les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="91417-249">To submit a hash table, use the following keys.</span></span> <span data-ttu-id="91417-250">Dans la table de hachage suivante, les clés sont affichées avec leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="91417-250">In the following hash table, the keys are shown with their default values.</span></span>

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-251">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="91417-251">-ScriptBlock</span></span>

<span data-ttu-id="91417-252">Spécifie les commandes exécutées par la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-252">Specifies the commands that the scheduled job runs.</span></span> <span data-ttu-id="91417-253">Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="91417-253">Enclose the commands in curly braces (`{}`) to create a script block.</span></span> <span data-ttu-id="91417-254">Pour spécifier les valeurs par défaut des paramètres de commande, utilisez le paramètre **ArgumentList** .</span><span class="sxs-lookup"><span data-stu-id="91417-254">To specify default values for command parameters, use the **ArgumentList** parameter.</span></span>

<span data-ttu-id="91417-255">Chaque `Register-ScheduledJob` commande doit utiliser les paramètres **scriptblock** ou **filePath** .</span><span class="sxs-lookup"><span data-stu-id="91417-255">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-256">-Déclencheur</span><span class="sxs-lookup"><span data-stu-id="91417-256">-Trigger</span></span>

<span data-ttu-id="91417-257">Spécifie les déclencheurs de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-257">Specifies the triggers for the scheduled job.</span></span> <span data-ttu-id="91417-258">Entrez un ou plusieurs objets **ScheduledJobTrigger** , tels que les objets `New-JobTrigger` renvoyés par l’applet de commande, ou une table de hachage de clés et de valeurs de déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="91417-258">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the `New-JobTrigger` cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="91417-259">Un déclencheur de tâche démarre le travail de planification.</span><span class="sxs-lookup"><span data-stu-id="91417-259">A job trigger starts the schedule job.</span></span> <span data-ttu-id="91417-260">Le déclencheur peut spécifier une planification ponctuelle ou périodique, ou un événement, tel que le moment où un utilisateur ouvre une session ou où Windows démarre.</span><span class="sxs-lookup"><span data-stu-id="91417-260">The trigger can specify a one-time or recurring scheduled or an event, such as when a user logs on or Windows starts.</span></span>

<span data-ttu-id="91417-261">Le paramètre **Trigger** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="91417-261">The **Trigger** parameter is optional.</span></span> <span data-ttu-id="91417-262">Vous pouvez ajouter un déclencheur quand vous créez la tâche planifiée, utiliser les `Add-JobTrigger` `Set-JobTrigger` `Set-ScheduledJob` applets de commande, ou pour ajouter ou modifier des déclencheurs de tâche ultérieurement, ou utiliser l' `Start-Job` applet de commande pour démarrer immédiatement la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-262">You can add a trigger when you create the scheduled job, use the `Add-JobTrigger`, `Set-JobTrigger`, or `Set-ScheduledJob` cmdlets to add or change job triggers later, or use the `Start-Job` cmdlet to start the scheduled job immediately.</span></span> <span data-ttu-id="91417-263">Vous pouvez également créer et gérer une tâche planifiée sans un déclencheur qui est utilisée comme modèle.</span><span class="sxs-lookup"><span data-stu-id="91417-263">You can also create and maintain a scheduled job without a trigger that is used as a template.</span></span>

<span data-ttu-id="91417-264">Pour envoyer une table de hachage, utilisez les clés suivantes :</span><span class="sxs-lookup"><span data-stu-id="91417-264">To submit a hash table, use the following keys:</span></span>

- <span data-ttu-id="91417-265">**Fréquence** : quotidienne, hebdomadaire, AtStartup, AtLogon</span><span class="sxs-lookup"><span data-stu-id="91417-265">**Frequency** : Daily, Weekly, AtStartup, AtLogon</span></span>
- <span data-ttu-id="91417-266">**À** : toute chaîne d’heure valide</span><span class="sxs-lookup"><span data-stu-id="91417-266">**At** : Any valid time string</span></span>
- <span data-ttu-id="91417-267">**DaysOfWeek** -toute combinaison de noms de jours</span><span class="sxs-lookup"><span data-stu-id="91417-267">**DaysOfWeek** - Any combination of day names</span></span>
- <span data-ttu-id="91417-268">**Interval** -tout intervalle de fréquence valide</span><span class="sxs-lookup"><span data-stu-id="91417-268">**Interval** - Any valid frequency interval</span></span>
- <span data-ttu-id="91417-269">**RandomDelay** : toute chaîne TimeSpan valide</span><span class="sxs-lookup"><span data-stu-id="91417-269">**RandomDelay** : Any valid timespan string</span></span>
- <span data-ttu-id="91417-270">**Utilisateur** : tout utilisateur valide.</span><span class="sxs-lookup"><span data-stu-id="91417-270">**User** : Any valid user.</span></span> <span data-ttu-id="91417-271">Utilisé uniquement avec la valeur de fréquence AtLogon</span><span class="sxs-lookup"><span data-stu-id="91417-271">Used only with the AtLogon frequency value</span></span>

<span data-ttu-id="91417-272">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="91417-272">For example:</span></span>

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="91417-273">-WhatIf</span></span>

<span data-ttu-id="91417-274">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="91417-274">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="91417-275">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="91417-275">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91417-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="91417-276">CommonParameters</span></span>

<span data-ttu-id="91417-277">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="91417-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="91417-278">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="91417-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="91417-279">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="91417-279">INPUTS</span></span>

### <span data-ttu-id="91417-280">Aucun</span><span class="sxs-lookup"><span data-stu-id="91417-280">None</span></span>

<span data-ttu-id="91417-281">Vous ne pouvez pas envoyer d’entrée dans le pipeline vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="91417-281">You can't send input down the pipeline to this cmdlet.</span></span>

## <span data-ttu-id="91417-282">SORTIES</span><span class="sxs-lookup"><span data-stu-id="91417-282">OUTPUTS</span></span>

### <span data-ttu-id="91417-283">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="91417-283">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="91417-284">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="91417-284">NOTES</span></span>

<span data-ttu-id="91417-285">Chaque tâche planifiée est enregistrée dans un sous-répertoire du `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="91417-285">Each scheduled job is saved in a subdirectory of the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span>
<span data-ttu-id="91417-286">Le sous-répertoire est nommé pour la tâche planifiée et contient un fichier XML pour la tâche planifiée et les enregistrements de son historique d’exécution.</span><span class="sxs-lookup"><span data-stu-id="91417-286">The subdirectory is named for the scheduled job and contains an XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="91417-287">Pour plus d’informations sur les tâches planifiées sur le disque, consultez [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span><span class="sxs-lookup"><span data-stu-id="91417-287">For more information about scheduled jobs on disk, see [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span></span>

<span data-ttu-id="91417-288">Les tâches planifiées que vous créez dans Windows PowerShell s’affichent dans Planificateur de tâches dans le `Library\Microsoft\Windows\PowerShell\ScheduledJobs` dossier planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="91417-288">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler `Library\Microsoft\Windows\PowerShell\ScheduledJobs` folder.</span></span> <span data-ttu-id="91417-289">Vous pouvez utiliser le Planificateur de tâches pour afficher et modifier la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="91417-289">You can use Task Scheduler to view and edit the scheduled job.</span></span>

<span data-ttu-id="91417-290">Vous pouvez utiliser Planificateur de tâches, l’outil en ligne de commande **schtasks.exe** et les applets de commande planificateur de tâches pour gérer les tâches planifiées que vous créez avec les applets de commande Job Schedule.</span><span class="sxs-lookup"><span data-stu-id="91417-290">You can use Task Scheduler, the **schtasks.exe** command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="91417-291">Toutefois, vous ne pouvez pas utiliser les applets de commande Job scheduled pour gérer les tâches que vous créez dans Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="91417-291">However, you can't use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

<span data-ttu-id="91417-292">En cas d'échec d'une commande de la tâche planifiée, Windows PowerShell retourne un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="91417-292">If a scheduled job command fails, Windows PowerShell returns an error message.</span></span> <span data-ttu-id="91417-293">Toutefois, si le travail échoue quand Planificateur de tâches tente de l’exécuter, l’erreur n’est pas disponible pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91417-293">However, if the job fails when Task Scheduler tries to run it, the error isn't available to Windows PowerShell.</span></span>

<span data-ttu-id="91417-294">Si une tâche planifiée ne s’exécute pas, utilisez les méthodes suivantes pour rechercher la raison :</span><span class="sxs-lookup"><span data-stu-id="91417-294">If a scheduled job doesn't run, use the following methods to find the reason:</span></span>

- <span data-ttu-id="91417-295">Vérifiez que le déclencheur de tâche est correctement défini.</span><span class="sxs-lookup"><span data-stu-id="91417-295">Verify that the job trigger is set properly.</span></span>
  - <span data-ttu-id="91417-296">Vérifiez que les conditions définies dans les options de tâche sont satisfaites.</span><span class="sxs-lookup"><span data-stu-id="91417-296">Verify that the conditions set in the job options are satisfied.</span></span>
- <span data-ttu-id="91417-297">Vérifiez que le compte d’utilisateur sous lequel la tâche s’exécute est autorisé à exécuter les commandes ou les scripts du travail.</span><span class="sxs-lookup"><span data-stu-id="91417-297">Verify that the user account under which the job runs has permission to run the commands or scripts in the job.</span></span>
- <span data-ttu-id="91417-298">Recherchez les erreurs dans l’historique des Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="91417-298">Check the Task Scheduler history for errors.</span></span>
- <span data-ttu-id="91417-299">Recherchez les erreurs dans le journal des événements Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="91417-299">Check the Task Scheduler event log for errors.</span></span>

<span data-ttu-id="91417-300">Pour plus d’informations, consultez [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="91417-300">For more information, see [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span></span>

## <span data-ttu-id="91417-301">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="91417-301">RELATED LINKS</span></span>

[<span data-ttu-id="91417-302">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-302">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="91417-303">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-303">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="91417-304">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-304">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="91417-305">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-305">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="91417-306">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-306">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="91417-307">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-307">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="91417-308">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-308">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="91417-309">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="91417-309">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="91417-310">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-310">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="91417-311">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="91417-311">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="91417-312">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-312">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="91417-313">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-313">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="91417-314">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="91417-314">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="91417-315">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-315">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="91417-316">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="91417-316">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="91417-317">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91417-317">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
