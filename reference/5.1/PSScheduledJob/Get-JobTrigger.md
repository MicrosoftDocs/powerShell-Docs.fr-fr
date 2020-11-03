---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203006"
---
# <span data-ttu-id="c5c5c-103">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-103">Get-JobTrigger</span></span>

## <span data-ttu-id="c5c5c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c5c5c-104">SYNOPSIS</span></span>
<span data-ttu-id="c5c5c-105">Obtient les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-105">Gets the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="c5c5c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c5c5c-106">SYNTAX</span></span>

### <span data-ttu-id="c5c5c-107">JobDefinition (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c5c5c-107">JobDefinition (Default)</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="c5c5c-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c5c5c-108">JobDefinitionId</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="c5c5c-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="c5c5c-109">JobDefinitionName</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="c5c5c-110">Description</span><span class="sxs-lookup"><span data-stu-id="c5c5c-110">DESCRIPTION</span></span>
<span data-ttu-id="c5c5c-111">L'applet de commande **Get-JobTrigger** obtient les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-111">The **Get-JobTrigger** cmdlet gets the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="c5c5c-112">Vous pouvez utiliser cette commande pour examiner les déclencheurs de tâche ou pour les diriger vers d'autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-112">You can use this command to examine the job triggers or to pipe the job triggers to other cmdlets.</span></span>

<span data-ttu-id="c5c5c-113">Un déclencheur de tâche définit une planification ou des conditions récurrentes pour le démarrage d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-113">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="c5c5c-114">Les déclencheurs de tâche ne sont pas enregistrés sur le disque de manière indépendante ; ils font partie d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-114">Job triggers are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="c5c5c-115">Pour obtenir un déclencheur de tâche, spécifiez la tâche planifiée que le déclencheur démarre.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-115">To get a job trigger, specify the scheduled job that the trigger starts.</span></span>

<span data-ttu-id="c5c5c-116">Utilisez les paramètres de l'applet de commande **Get-JobTrigger** pour identifier les tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-116">Use the parameters of the **Get-JobTrigger** cmdlet to identify the scheduled jobs.</span></span>
<span data-ttu-id="c5c5c-117">Vous pouvez identifier les tâches planifiées par leur nom ou numéro d’identification, ou en entrant ou en canalisant des objets **ScheduledJob** , tels que ceux retournés par l’applet de commande Get-ScheduledJob, à la commande **JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="c5c5c-117">You can identify the scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-JobTrigger** .</span></span>

<span data-ttu-id="c5c5c-118">L’applet de commande **JobTrigger** est une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-118">**Get-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="c5c5c-119">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="c5c5c-120">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="c5c5c-121">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c5c5c-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c5c5c-122">EXAMPLES</span></span>

### <span data-ttu-id="c5c5c-123">Exemple 1 : obtenir un déclencheur de tâche par nom de tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="c5c5c-123">Example 1: Get a job trigger by scheduled job name</span></span>

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

<span data-ttu-id="c5c5c-124">La commande utilise le paramètre *Name* de la commande **JobTrigger** pour recevoir les déclencheurs de la tâche planifiée BackupJob.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-124">The command uses the *Name* parameter of **Get-JobTrigger** to get the job triggers of the BackupJob scheduled job.</span></span>

### <span data-ttu-id="c5c5c-125">Exemple 2 : obtenir un déclencheur de tâche par ID</span><span class="sxs-lookup"><span data-stu-id="c5c5c-125">Example 2: Get a job trigger by ID</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

<span data-ttu-id="c5c5c-126">L’exemple utilise le paramètre *ID* de la fonction **JobTrigger** pour obtenir les déclencheurs d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-126">The example uses the *ID* parameter of **Get-JobTrigger** to get the job triggers of a scheduled job.</span></span>

### <span data-ttu-id="c5c5c-127">Exemple 3 : obtenir des déclencheurs de tâche en canalisant un travail</span><span class="sxs-lookup"><span data-stu-id="c5c5c-127">Example 3: Get job triggers by piping a job</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

<span data-ttu-id="c5c5c-128">Cette commande obtient les déclencheurs de toutes les tâches dont le nom contient la sauvegarde ou l’archive.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-128">This command gets the job triggers of all jobs that have Backup or Archive in their names.</span></span>

### <span data-ttu-id="c5c5c-129">Exemple 4 : obtenir le déclencheur d’un travail sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="c5c5c-129">Example 4: Get the job trigger of a job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

<span data-ttu-id="c5c5c-130">Cette commande obtient l'un des deux déclencheurs d'une tâche planifiée sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-130">This command gets one of the two job triggers of a scheduled job on a remote computer.</span></span>

<span data-ttu-id="c5c5c-131">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-131">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>
<span data-ttu-id="c5c5c-132">Elle utilise l’applet de commande Get-ScheduledJob pour récupérer la tâche planifiée Backup, qu’elle dirige vers l’applet de commande **JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="c5c5c-132">It uses the Get-ScheduledJob cmdlet to get the Backup scheduled job, which it pipes to the **Get-JobTrigger** cmdlet.</span></span>
<span data-ttu-id="c5c5c-133">Elle utilise le paramètre *TriggerID* pour récupérer uniquement le second déclencheur.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-133">It uses the *TriggerID* parameter to get only the second trigger.</span></span>

### <span data-ttu-id="c5c5c-134">Exemple 5 : récupération de tous les déclencheurs de tâche</span><span class="sxs-lookup"><span data-stu-id="c5c5c-134">Example 5: Get all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

<span data-ttu-id="c5c5c-135">Cette commande obtient tous les déclencheurs de toutes les tâches planifiées sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-135">This command gets all job triggers of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="c5c5c-136">La commande utilise la Get-ScheduledJob pour obtenir les tâches planifiées sur l’ordinateur local et les dirige vers la commande **JobTrigger** , qui obtient le déclencheur de chaque tâche planifiée (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="c5c5c-136">The command uses the Get-ScheduledJob to get the scheduled jobs on the local computer and pipes them to **Get-JobTrigger** , which gets the job trigger of each scheduled job (if any).</span></span>

<span data-ttu-id="c5c5c-137">Pour ajouter le nom de la tâche planifiée à l’affichage du déclencheur de tâche, la commande utilise la fonctionnalité de propriété calculée de l’applet de commande Format-Table.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-137">To add the name of the scheduled job to the job trigger display, the command uses the calculated property feature of the Format-Table cmdlet.</span></span>
<span data-ttu-id="c5c5c-138">Outre les propriétés de déclencheur de tâche qui sont affichées par défaut, la commande crée une nouvelle propriété ScheduledJob qui affiche le nom de la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-138">In addition to the job trigger properties that are displayed by default, the command creates a new ScheduledJob property that displays the name of the scheduled job.</span></span>

### <span data-ttu-id="c5c5c-139">Exemple 6 : obtenir la propriété de déclencheur de tâche d’une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="c5c5c-139">Example 6: Get the job trigger property of a scheduled job</span></span>

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

<span data-ttu-id="c5c5c-140">Les déclencheurs d'une tâche planifiée sont stockés dans la propriété JobTriggers de la tâche.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-140">The job triggers of a scheduled job are stored in the JobTriggers property of the job.</span></span>
<span data-ttu-id="c5c5c-141">Cet exemple montre des alternatives à l’utilisation de l’applet de commande **JobTrigger** pour récupérer les déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-141">This example shows alternatives to using the **Get-JobTrigger** cmdlet to get job triggers.</span></span>
<span data-ttu-id="c5c5c-142">Les résultats sont identiques à l'utilisation de l'applet de commande **Get-JobTrigger** et les techniques peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-142">The results are identical to using the **Get-JobTrigger** cmdlet and the techniques can be used interchangeably.</span></span>

### <span data-ttu-id="c5c5c-143">Exemple 7 : comparer les déclencheurs de tâche</span><span class="sxs-lookup"><span data-stu-id="c5c5c-143">Example 7: Compare job triggers</span></span>

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

<span data-ttu-id="c5c5c-144">Cet exemple montre comment comparer les déclencheurs de deux tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-144">This example shows how to compare the job triggers of two scheduled jobs.</span></span>

## <span data-ttu-id="c5c5c-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c5c5c-145">PARAMETERS</span></span>

### <span data-ttu-id="c5c5c-146">-Id</span><span class="sxs-lookup"><span data-stu-id="c5c5c-146">-Id</span></span>
<span data-ttu-id="c5c5c-147">Spécifie le numéro d'identification d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-147">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="c5c5c-148">**Get-JobTrigger** obtient le déclencheur de la tâche planifiée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-148">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>

<span data-ttu-id="c5c5c-149">Pour obtenir le numéro d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-149">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c5c5c-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c5c5c-150">-InputObject</span></span>
<span data-ttu-id="c5c5c-151">Spécifie une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-151">Specifies a scheduled job.</span></span>
<span data-ttu-id="c5c5c-152">Entrez une variable qui contient des objets  **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-152">Enter a variable that contains  **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="c5c5c-153">Vous pouvez également diriger les objets **ScheduledJob** vers la **JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="c5c5c-153">You can also pipe **ScheduledJob** objects to **Get-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c5c5c-154">-Name</span><span class="sxs-lookup"><span data-stu-id="c5c5c-154">-Name</span></span>
<span data-ttu-id="c5c5c-155">Spécifie le nom d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-155">Specifies the name of a scheduled job.</span></span>
<span data-ttu-id="c5c5c-156">**Get-JobTrigger** obtient le déclencheur de la tâche planifiée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-156">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>
<span data-ttu-id="c5c5c-157">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-157">Wildcards are supported.</span></span>

<span data-ttu-id="c5c5c-158">Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-158">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c5c5c-159">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="c5c5c-159">-TriggerId</span></span>
<span data-ttu-id="c5c5c-160">Obtient les déclencheurs de tâche spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-160">Gets the specified job triggers.</span></span>
<span data-ttu-id="c5c5c-161">Entrez les ID d'un ou de plusieurs déclencheurs de tâche d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="c5c5c-162">Utilisez ce paramètre quand la tâche planifiée qui est spécifiée par les paramètres *Name* , *ID* ou *InputObject* possède plusieurs déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-162">Use this parameter when the scheduled job that is specified by the *Name* , *ID* , or *InputObject* parameters has multiple job triggers.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c5c5c-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c5c5c-163">CommonParameters</span></span>
<span data-ttu-id="c5c5c-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c5c5c-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c5c5c-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c5c5c-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c5c5c-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c5c5c-166">INPUTS</span></span>

### <span data-ttu-id="c5c5c-167">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="c5c5c-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="c5c5c-168">Vous pouvez diriger une tâche planifiée à partir de Get-ScheduledJob vers **JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="c5c5c-168">You can pipe a scheduled job from Get-ScheduledJob to **Get-JobTrigger** .</span></span>

## <span data-ttu-id="c5c5c-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c5c5c-169">OUTPUTS</span></span>

### <span data-ttu-id="c5c5c-170">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-170">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="c5c5c-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c5c5c-171">NOTES</span></span>

## <span data-ttu-id="c5c5c-172">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c5c5c-172">RELATED LINKS</span></span>

[<span data-ttu-id="c5c5c-173">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-173">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="c5c5c-174">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-174">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="c5c5c-175">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c5c5c-175">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="c5c5c-176">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-176">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="c5c5c-177">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c5c5c-177">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="c5c5c-178">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-178">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="c5c5c-179">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c5c5c-179">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="c5c5c-180">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c5c5c-180">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="c5c5c-181">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-181">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="c5c5c-182">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c5c5c-182">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="c5c5c-183">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c5c5c-183">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="c5c5c-184">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-184">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="c5c5c-185">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c5c5c-185">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="c5c5c-186">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c5c5c-186">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="c5c5c-187">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c5c5c-187">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="c5c5c-188">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c5c5c-188">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
