---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202998"
---
# <span data-ttu-id="79fa6-103">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-103">New-JobTrigger</span></span>

## <span data-ttu-id="79fa6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="79fa6-104">SYNOPSIS</span></span>
<span data-ttu-id="79fa6-105">Crée un déclencheur pour une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-105">Creates a job trigger for a scheduled job.</span></span>

## <span data-ttu-id="79fa6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79fa6-106">SYNTAX</span></span>

### <span data-ttu-id="79fa6-107">Une fois (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="79fa6-107">Once (Default)</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### <span data-ttu-id="79fa6-108">Quotidien</span><span class="sxs-lookup"><span data-stu-id="79fa6-108">Daily</span></span>

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### <span data-ttu-id="79fa6-109">Hebdomadaire</span><span class="sxs-lookup"><span data-stu-id="79fa6-109">Weekly</span></span>

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### <span data-ttu-id="79fa6-110">AtStartup</span><span class="sxs-lookup"><span data-stu-id="79fa6-110">AtStartup</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### <span data-ttu-id="79fa6-111">AtLogon</span><span class="sxs-lookup"><span data-stu-id="79fa6-111">AtLogon</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## <span data-ttu-id="79fa6-112">Description</span><span class="sxs-lookup"><span data-stu-id="79fa6-112">DESCRIPTION</span></span>
<span data-ttu-id="79fa6-113">L’applet **de commande New-JobTrigger** crée un déclencheur de tâche qui démarre une tâche planifiée selon une planification ponctuelle ou périodique, ou lorsqu’un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="79fa6-113">The **New-JobTrigger** cmdlet creates a job trigger that starts a scheduled job on a one-time or recurring schedule, or when an event occurs.</span></span>

<span data-ttu-id="79fa6-114">Vous pouvez utiliser l'objet **ScheduledJobTrigger** retourné par **New-JobTrigger** pour définir un déclencheur de tâche pour une tâche planifiée nouvelle ou existante.</span><span class="sxs-lookup"><span data-stu-id="79fa6-114">You can use the **ScheduledJobTrigger** object that **New-JobTrigger** returns to set a job trigger for a new or existing scheduled job.</span></span>
<span data-ttu-id="79fa6-115">Vous pouvez également créer un déclencheur de tâche à l’aide de l’applet de commande Get-JobTrigger pour obtenir le déclencheur d’une tâche planifiée existante, ou en utilisant une valeur de table de hachage pour représenter un déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="79fa6-115">You can also create a job trigger by using the Get-JobTrigger cmdlet to get the job trigger of an existing scheduled job, or by using a hash table value to represent a job trigger.</span></span>

<span data-ttu-id="79fa6-116">Lorsque vous créez un déclencheur de tâche, passez en revue les valeurs par défaut des options spécifiées par l’applet de commande New-ScheduledJobOption.</span><span class="sxs-lookup"><span data-stu-id="79fa6-116">When creating a job trigger, review the default values of the options specified by the New-ScheduledJobOption cmdlet.</span></span>
<span data-ttu-id="79fa6-117">Ces options, qui ont les mêmes valeurs valides et par défaut que les options correspondantes dans **Task Scheduler** , affectent la planification et la durée des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="79fa6-117">These options, which have the same valid and default values as the corresponding options in **Task Scheduler** , affect the scheduling and timing of scheduled jobs.</span></span>

<span data-ttu-id="79fa6-118">**New-JobTrigger** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79fa6-118">**New-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="79fa6-119">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="79fa6-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="79fa6-120">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="79fa6-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="79fa6-121">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="79fa6-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="79fa6-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="79fa6-122">EXAMPLES</span></span>

### <span data-ttu-id="79fa6-123">Exemple 1 : planification</span><span class="sxs-lookup"><span data-stu-id="79fa6-123">Example 1: Once Schedule</span></span>

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

<span data-ttu-id="79fa6-124">Cette commande utilise l'applet de commande **New-JobTrigger** pour créer un déclencheur de tâche qui démarre une tâche planifiée une seule fois.</span><span class="sxs-lookup"><span data-stu-id="79fa6-124">This command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a scheduled job only one time.</span></span>
<span data-ttu-id="79fa6-125">La valeur du paramètre *At* est une chaîne que Windows PowerShell convertit en un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="79fa6-125">The value of the *At* parameter is a string that Windows PowerShell converts into a **DateTime** object.</span></span>
<span data-ttu-id="79fa6-126">La valeur du paramètre *At* inclut une date explicite, et pas seulement une heure.</span><span class="sxs-lookup"><span data-stu-id="79fa6-126">The *At* parameter value includes an explicit date, not just a time.</span></span>
<span data-ttu-id="79fa6-127">Si la date a été omise, le déclencheur est créé avec la date actuelle et l'heure 3:00, qui est susceptible de représenter une heure dans le passé.</span><span class="sxs-lookup"><span data-stu-id="79fa6-127">If the date were omitted, the trigger would be created with the current date and 3:00 AM time, which is likely to represent a time in the past.</span></span>

### <span data-ttu-id="79fa6-128">Exemple 2 : planification quotidienne</span><span class="sxs-lookup"><span data-stu-id="79fa6-128">Example 2: Daily Schedule</span></span>

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

<span data-ttu-id="79fa6-129">Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée tous les 3 jours à 4:15.</span><span class="sxs-lookup"><span data-stu-id="79fa6-129">This command creates a job trigger that starts a scheduled job every 3 days at 4:15 a.m.</span></span>

<span data-ttu-id="79fa6-130">Étant donné que la valeur du paramètre *At* n'inclut pas de date, la date actuelle est utilisée comme valeur de date dans l'objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="79fa6-130">Because the value of the *At* parameter does not include a date, the current date is used as the date value in the **DateTime** object.</span></span>
<span data-ttu-id="79fa6-131">Si la date et l'heure sont passées, la tâche planifiée est démarrée à l'occurrence suivante, qui a lieu 3 jours plus tard à partir de la valeur du paramètre *At* .</span><span class="sxs-lookup"><span data-stu-id="79fa6-131">If the date and time is in the past, the scheduled job is started at the next occurrence, which is 3 days later from the *At* parameter value.</span></span>

### <span data-ttu-id="79fa6-132">Exemple 3 : planification hebdomadaire</span><span class="sxs-lookup"><span data-stu-id="79fa6-132">Example 3: Weekly Schedule</span></span>

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

<span data-ttu-id="79fa6-133">Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée toutes les 4 semaines les lundi, mercredi et vendredi à 23:00.</span><span class="sxs-lookup"><span data-stu-id="79fa6-133">This command creates a job trigger that starts a scheduled job every 4 weeks on Monday, Wednesday, and Friday at 2300 hours (11:00 PM).</span></span>

<span data-ttu-id="79fa6-134">Vous pouvez également entrer la valeur du paramètre *DaysOfWeek* dans des entiers, par exemple `-DaysOfWeek 1, 5` .</span><span class="sxs-lookup"><span data-stu-id="79fa6-134">You can also enter the *DaysOfWeek* parameter value in integers, such as `-DaysOfWeek 1, 5`.</span></span>

### <span data-ttu-id="79fa6-135">Exemple 4 : planification de l’ouverture de session</span><span class="sxs-lookup"><span data-stu-id="79fa6-135">Example 4: Logon Schedule</span></span>

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

<span data-ttu-id="79fa6-136">Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée chaque fois que l'administrateur de domaine ouvre une session sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="79fa6-136">This command creates a job trigger that starts a scheduled job whenever the domain administrator logs onto the computer.</span></span>

### <span data-ttu-id="79fa6-137">Exemple 5 : utilisation d’un délai aléatoire</span><span class="sxs-lookup"><span data-stu-id="79fa6-137">Example 5: Using a Random Delay</span></span>

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

<span data-ttu-id="79fa6-138">Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée chaque jour à 1:00.</span><span class="sxs-lookup"><span data-stu-id="79fa6-138">This command creates a job trigger that starts a scheduled job every day at 1:00 in the morning.</span></span>
<span data-ttu-id="79fa6-139">La commande utilise le paramètre *RandomDelay* pour définir 20 minutes comme délai maximal.</span><span class="sxs-lookup"><span data-stu-id="79fa6-139">The command uses the *RandomDelay* parameter to set the maximum delay to 20 minutes.</span></span>
<span data-ttu-id="79fa6-140">Par conséquent, la tâche est exécutée chaque jour entre 1:00 et 1:20, avec l'intervalle qui varie de manière pseudo-aléatoire.</span><span class="sxs-lookup"><span data-stu-id="79fa6-140">As a result, the job runs every day between 1:00 AM and 1:20 AM, with the interval varying pseudo-randomly.</span></span>

<span data-ttu-id="79fa6-141">Vous pouvez utiliser un délai aléatoire pour l'échantillonnage, l'équilibrage de charge et d'autres tâches d'administration.</span><span class="sxs-lookup"><span data-stu-id="79fa6-141">You can use a random delay for sampling, load balancing, and other administrative tasks.</span></span>
<span data-ttu-id="79fa6-142">Lors de la définition de la valeur de délai, examinez les valeurs effectives et par défaut de l’applet de commande New-ScheduledJobOption et coordonnez le délai avec les paramètres d’option.</span><span class="sxs-lookup"><span data-stu-id="79fa6-142">When setting the delay value, review the effective and default values of the New-ScheduledJobOption cmdlet and coordinate the delay with the option settings.</span></span>

### <span data-ttu-id="79fa6-143">Exemple 6 : créer un déclencheur de tâche pour une nouvelle tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="79fa6-143">Example 6: Create a Job Trigger for a New Scheduled Job</span></span>

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

<span data-ttu-id="79fa6-144">Ces commandes utilisent un déclencheur de tâche pour créer une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-144">These commands use a job trigger to create a new scheduled job.</span></span>

### <span data-ttu-id="79fa6-145">Exemple 7 : ajouter un déclencheur de tâche à une tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="79fa6-145">Example 7: Add a Job Trigger to a Scheduled Job</span></span>

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

<span data-ttu-id="79fa6-146">Cet exemple montre comment ajouter un déclencheur de tâche à une tâche planifiée existante.</span><span class="sxs-lookup"><span data-stu-id="79fa6-146">This example shows how to add a job trigger to an existing scheduled job.</span></span>
<span data-ttu-id="79fa6-147">Vous pouvez ajouter plusieurs déclencheurs de tâche à n'importe quelle tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-147">You can add multiple job triggers to any scheduled job.</span></span>

<span data-ttu-id="79fa6-148">La commande utilise l’applet de commande Add-JobTrigger pour ajouter le déclencheur de tâche à la tâche planifiée SynchronizeApps.</span><span class="sxs-lookup"><span data-stu-id="79fa6-148">The command uses the Add-JobTrigger cmdlet to add the job trigger to the SynchronizeApps scheduled job.</span></span>
<span data-ttu-id="79fa6-149">La valeur du paramètre *Trigger* est une commande **New-JobTrigger** qui exécute la tâche chaque jour à 3:10.</span><span class="sxs-lookup"><span data-stu-id="79fa6-149">The value of the *Trigger* parameter is a **New-JobTrigger** command that runs the job every day at 3:10 AM.</span></span>

<span data-ttu-id="79fa6-150">Quand l'exécution de la commande est terminée, SynchronizeApps est une tâche planifiée qui s'exécute aux heures spécifiées par le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="79fa6-150">When the command completes, SynchronizeApps is a scheduled job that runs at the times specified by the job trigger.</span></span>

### <span data-ttu-id="79fa6-151">Exemple 8 : créer un déclencheur de tâche répétée</span><span class="sxs-lookup"><span data-stu-id="79fa6-151">Example 8: Create a repeating job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

<span data-ttu-id="79fa6-152">Cette commande crée un déclencheur de tâche qui exécute une tâche toutes les 60 minutes pendant 48 heures à compter du 12 septembre 2013 à 1:00.</span><span class="sxs-lookup"><span data-stu-id="79fa6-152">This command creates a job trigger that runs a job every 60 minutes for 48 hours beginning on September 12, 2013 at 1:00 AM.</span></span>

### <span data-ttu-id="79fa6-153">Exemple 9 : arrêter un déclencheur de tâche répétée</span><span class="sxs-lookup"><span data-stu-id="79fa6-153">Example 9: Stop a repeating job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

<span data-ttu-id="79fa6-154">Cette commande arrête de force la tâche SecurityCheck, dont l'exécution est déclenchée toutes les 60 minutes jusqu'à l'expiration de son déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="79fa6-154">This command forcibly stops the SecurityCheck job, which is triggered to run every 60 minutes until its job trigger expires.</span></span>

<span data-ttu-id="79fa6-155">Pour empêcher la répétition du travail, la commande utilise la Get-JobTrigger pour recevoir le déclencheur de la tâche SecurityCheck et l’applet de commande Set-JobTrigger pour modifier l’intervalle de répétition et la durée de répétition du déclencheur de tâche sur zéro (0).</span><span class="sxs-lookup"><span data-stu-id="79fa6-155">To prevent the job from repeating, the command uses the Get-JobTrigger to get the job trigger of the SecurityCheck job and the Set-JobTrigger cmdlet to change the repetition interval and repetition duration of the job trigger to zero (0).</span></span>

### <span data-ttu-id="79fa6-156">Exemple 10 : créer un déclencheur de travail horaire</span><span class="sxs-lookup"><span data-stu-id="79fa6-156">Example 10: Create an hourly job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

<span data-ttu-id="79fa6-157">La commande suivante crée un déclencheur de tâche qui exécute une tâche planifiée toutes les 12 heures pendant une durée indéterminée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-157">The following command creates a job trigger that runs a scheduled job once every 12 hours for an indefinite period of time.</span></span>
<span data-ttu-id="79fa6-158">La planification commence demain (21/9/2012) à minuit (0:00).</span><span class="sxs-lookup"><span data-stu-id="79fa6-158">The schedule begins tomorrow (9/21/2012) at midnight (0:00 AM).</span></span>

## <span data-ttu-id="79fa6-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79fa6-159">PARAMETERS</span></span>

### <span data-ttu-id="79fa6-160">-À</span><span class="sxs-lookup"><span data-stu-id="79fa6-160">-At</span></span>
<span data-ttu-id="79fa6-161">Démarre la tâche à la date et à l'heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="79fa6-161">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="79fa6-162">Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date, ou une chaîne pouvant être convertie en date et heure, telle que « April 19, 2012 15:00 », « 12/31 » ou « 3:00 ».</span><span class="sxs-lookup"><span data-stu-id="79fa6-162">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a date and time, such as "April 19, 2012 15:00", "12/31", or "3am".</span></span>
<span data-ttu-id="79fa6-163">Si vous ne spécifiez pas un élément de la date, par exemple l'année, la date dans le déclencheur a l'élément correspondant de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="79fa6-163">If you don't specify an element of the date, such as the year, the date in the trigger has the corresponding element from the current date.</span></span>

<span data-ttu-id="79fa6-164">Quand vous utilisez le paramètre *Once* , affectez au paramètre *At* une date et une heure futures.</span><span class="sxs-lookup"><span data-stu-id="79fa6-164">When using the *Once* parameter, set the value of the *At* parameter to a future date and time.</span></span>
<span data-ttu-id="79fa6-165">Comme la date par défaut dans un objet **DateTime** est la date actuelle, la définition d'une heure antérieure à l'heure actuelle sans une date explicite crée un déclencheur de tâche pour une heure dans le passé.</span><span class="sxs-lookup"><span data-stu-id="79fa6-165">Because the default date in a **DateTime** object is the current date, if you specify a time before the current time without an explicit date, the job trigger is created for a time in the past.</span></span>

<span data-ttu-id="79fa6-166">Les objets **DateTime** , et les chaînes converties en objets **DateTime** , sont automatiquement ajustées pour être compatibles avec les formats de date et d’heure sélectionnés pour l’ordinateur local dans région et langue dans le panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="79fa6-166">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-167">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="79fa6-167">-AtLogOn</span></span>
<span data-ttu-id="79fa6-168">Démarre la tâche planifiée quand les utilisateurs spécifiés se connectent à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="79fa6-168">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="79fa6-169">Pour spécifier un utilisateur, utilisez le paramètre *User* .</span><span class="sxs-lookup"><span data-stu-id="79fa6-169">To specify a user, use the *User* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-170">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="79fa6-170">-AtStartup</span></span>
<span data-ttu-id="79fa6-171">Démarre la tâche planifiée au démarrage de Windows.</span><span class="sxs-lookup"><span data-stu-id="79fa6-171">Starts the scheduled job when Windows starts.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-172">-Tous les jours</span><span class="sxs-lookup"><span data-stu-id="79fa6-172">-Daily</span></span>
<span data-ttu-id="79fa6-173">Spécifie une planification de tâche quotidienne périodique.</span><span class="sxs-lookup"><span data-stu-id="79fa6-173">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="79fa6-174">Utilisez les autres paramètres du jeu de paramètres *Daily* pour spécifier les détails de la planification.</span><span class="sxs-lookup"><span data-stu-id="79fa6-174">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-175">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="79fa6-175">-DaysInterval</span></span>
<span data-ttu-id="79fa6-176">Spécifie le nombre de jours entre les occurrences d'une planification quotidienne.</span><span class="sxs-lookup"><span data-stu-id="79fa6-176">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="79fa6-177">Par exemple, une valeur de 3 démarre la tâche planifiée les jours 1, 4, 7 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="79fa6-177">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="79fa6-178">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="79fa6-178">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-179">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="79fa6-179">-DaysOfWeek</span></span>
<span data-ttu-id="79fa6-180">Spécifie les jours de la semaine qu'une tâche planifiée hebdomadaire s'exécute.</span><span class="sxs-lookup"><span data-stu-id="79fa6-180">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="79fa6-181">Entrez les noms des jours, par exemple « Lundi », ou des entiers de 0 à 6, où 0 représente Dimanche.</span><span class="sxs-lookup"><span data-stu-id="79fa6-181">Enter day names, such as "Monday" or integers 0-6, where 0 represents Sunday.</span></span>
<span data-ttu-id="79fa6-182">Ce paramètre est obligatoire dans le jeu de paramètres Weekly.</span><span class="sxs-lookup"><span data-stu-id="79fa6-182">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="79fa6-183">Les noms de jours sont convertis dans leurs valeurs entières dans le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="79fa6-183">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="79fa6-184">Lorsque vous placez les noms de jours entre guillemets droits dans une commande, faites-le séparément, par exemple "Lundi", "Mardi".</span><span class="sxs-lookup"><span data-stu-id="79fa6-184">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="79fa6-185">Si vous incluez plusieurs noms de jours dans une seule paire de guillemets droits, les valeurs entières correspondantes sont additionnées.</span><span class="sxs-lookup"><span data-stu-id="79fa6-185">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="79fa6-186">Par exemple, "Lundi, Mardi" (1, 2) donne la valeur "Mercredi" (3).</span><span class="sxs-lookup"><span data-stu-id="79fa6-186">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-187">-Une fois</span><span class="sxs-lookup"><span data-stu-id="79fa6-187">-Once</span></span>
<span data-ttu-id="79fa6-188">Spécifie une planification non périodique (unique) ou récurrente personnalisée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-188">Specifies a non-recurring (one time) or custom repeating schedule.</span></span>
<span data-ttu-id="79fa6-189">Pour créer une planification récurrente, utilisez le paramètre *Once* avec les paramètres *RepetitionDuration* et *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="79fa6-189">To create a repeating schedule, use the *Once* parameter with the *RepetitionDuration* and *RepetitionInterval* parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-190">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="79fa6-190">-RandomDelay</span></span>
<span data-ttu-id="79fa6-191">Active un délai aléatoire qui commence à l'heure de début planifiée et définit la valeur maximale du délai.</span><span class="sxs-lookup"><span data-stu-id="79fa6-191">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="79fa6-192">La longueur du délai est définie de manière pseudo-aléatoire pour chaque démarrage et elle varie entre aucun délai et la durée spécifiée par la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="79fa6-192">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="79fa6-193">La valeur par défaut, zéro (00:00:00), désactive le délai aléatoire.</span><span class="sxs-lookup"><span data-stu-id="79fa6-193">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="79fa6-194">Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> format, qui est automatiquement convertie en objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="79fa6-194">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a **TimeSpan** object.</span></span>

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

### <span data-ttu-id="79fa6-195">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="79fa6-195">-RepeatIndefinitely</span></span>
<span data-ttu-id="79fa6-196">Ce paramètre, disponible à partir de Windows PowerShell 4.0, élimine le besoin de spécifier une valeur **TimeSpan.MaxValue** pour le paramètre *RepetitionDuration* pour exécuter une tâche planifiée à plusieurs reprises, pendant une durée indéterminée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-196">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-197">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="79fa6-197">-RepetitionDuration</span></span>
<span data-ttu-id="79fa6-198">Répète la tâche jusqu'à ce que le délai spécifié expire.</span><span class="sxs-lookup"><span data-stu-id="79fa6-198">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="79fa6-199">La fréquence de répétition est déterminée par la valeur du paramètre *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="79fa6-199">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="79fa6-200">Par exemple, si la valeur de **RepetitionInterval** est égale à 5 minutes et la valeur de **RepetitionDuration** à 2 heures, la tâche se déclenche toutes les cinq minutes pendant deux heures.</span><span class="sxs-lookup"><span data-stu-id="79fa6-200">For example, if the value of **RepetitionInterval** is 5 minutes and the value of **RepetitionDuration** is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="79fa6-201">Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».</span><span class="sxs-lookup"><span data-stu-id="79fa6-201">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="79fa6-202">Pour exécuter une tâche indéfiniment, ajoutez plutôt le paramètre *RepeatIndefinitely* .</span><span class="sxs-lookup"><span data-stu-id="79fa6-202">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="79fa6-203">Pour arrêter un travail avant l’expiration de la durée de répétition du déclencheur de tâche, utilisez l’applet de commande Set-JobTrigger pour définir la valeur *RepetitionDuration* sur zéro (0).</span><span class="sxs-lookup"><span data-stu-id="79fa6-203">To stop a job before the job trigger repetition duration expires, use the Set-JobTrigger cmdlet to set the *RepetitionDuration* value to zero (0).</span></span>

<span data-ttu-id="79fa6-204">Ce paramètre est valide uniquement quand les paramètres *Once* , *At* et *RepetitionInterval* sont utilisés dans la commande.</span><span class="sxs-lookup"><span data-stu-id="79fa6-204">This parameter is valid only when the *Once* , *At* and *RepetitionInterval* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-205">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="79fa6-205">-RepetitionInterval</span></span>
<span data-ttu-id="79fa6-206">Répète la tâche à l'intervalle de temps spécifié.</span><span class="sxs-lookup"><span data-stu-id="79fa6-206">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="79fa6-207">Par exemple, si la valeur de ce paramètre est de 2 heures, la tâche est déclenchée toutes les deux heures.</span><span class="sxs-lookup"><span data-stu-id="79fa6-207">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="79fa6-208">La valeur par défaut, 0, ne répète pas la tâche.</span><span class="sxs-lookup"><span data-stu-id="79fa6-208">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="79fa6-209">Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».</span><span class="sxs-lookup"><span data-stu-id="79fa6-209">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="79fa6-210">Ce paramètre est valide uniquement quand les paramètres *Once* , *At* et *RepetitionDuration* sont utilisés dans la commande.</span><span class="sxs-lookup"><span data-stu-id="79fa6-210">This parameter is valid only when the *Once* , *At* , and *RepetitionDuration* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-211">-User</span><span class="sxs-lookup"><span data-stu-id="79fa6-211">-User</span></span>
<span data-ttu-id="79fa6-212">Spécifie les utilisateurs qui déclenchent un démarrage *AtLogon* d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-212">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="79fa6-213">Entrez le nom d’un utilisateur au \<UserName\> format ou, \<Domain\Username\> ou entrez un astérisque ( \* ) pour représenter tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="79fa6-213">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="79fa6-214">La valeur par défaut est tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="79fa6-214">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-215">-Hebdomadaire</span><span class="sxs-lookup"><span data-stu-id="79fa6-215">-Weekly</span></span>
<span data-ttu-id="79fa6-216">Spécifie une planification de tâche hebdomadaire périodique.</span><span class="sxs-lookup"><span data-stu-id="79fa6-216">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="79fa6-217">Utilisez les autres paramètres du jeu de paramètres Weekly pour spécifier les détails de la planification.</span><span class="sxs-lookup"><span data-stu-id="79fa6-217">Use the other parameters in the Weekly parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-218">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="79fa6-218">-WeeksInterval</span></span>
<span data-ttu-id="79fa6-219">Spécifie le nombre de semaines entre les occurrences d'une planification de tâche hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="79fa6-219">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="79fa6-220">Par exemple, une valeur de 3 démarre la tâche planifiée les semaines 1, 4, 7 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="79fa6-220">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="79fa6-221">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="79fa6-221">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Weekly
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fa6-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79fa6-222">CommonParameters</span></span>
<span data-ttu-id="79fa6-223">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="79fa6-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79fa6-224">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="79fa6-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79fa6-225">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="79fa6-225">INPUTS</span></span>

### <span data-ttu-id="79fa6-226">Aucun</span><span class="sxs-lookup"><span data-stu-id="79fa6-226">None</span></span>
<span data-ttu-id="79fa6-227">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="79fa6-227">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="79fa6-228">SORTIES</span><span class="sxs-lookup"><span data-stu-id="79fa6-228">OUTPUTS</span></span>

### <span data-ttu-id="79fa6-229">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-229">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="79fa6-230">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="79fa6-230">NOTES</span></span>

* <span data-ttu-id="79fa6-231">Les déclencheurs de tâche ne sont pas enregistrés sur disque.</span><span class="sxs-lookup"><span data-stu-id="79fa6-231">Job triggers are not saved to disk.</span></span> <span data-ttu-id="79fa6-232">Toutefois, les tâches planifiées sont enregistrées sur le disque, et vous pouvez utiliser la Get-JobTrigger pour recevoir le déclencheur d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="79fa6-232">However, scheduled jobs are saved to disk, and you can use the Get-JobTrigger to get the job trigger of any scheduled job.</span></span>
* <span data-ttu-id="79fa6-233">**New-JobTrigger** ne vous empêche pas de créer un déclencheur de tâche qui n’exécutera pas de tâche planifiée, comme un déclencheur à usage unique pour une date dans le passé.</span><span class="sxs-lookup"><span data-stu-id="79fa6-233">**New-JobTrigger** does not prevent you from creating a job trigger that will not run a scheduled job, such as one-time trigger for a date in the past.</span></span>
* <span data-ttu-id="79fa6-234">L’applet de commande Register-ScheduledJob accepte un objet ScheduledJobTrigger, tel que celui retourné par les applets de commande **New-JobTrigger** ou Get-JobTrigger, ou une table de hachage avec des valeurs de déclencheur.</span><span class="sxs-lookup"><span data-stu-id="79fa6-234">The Register-ScheduledJob cmdlet accepts a ScheduledJobTrigger object, such as one returned by the **New-JobTrigger** or Get-JobTrigger cmdlets, or a hash table with trigger values.</span></span>

  <span data-ttu-id="79fa6-235">Pour envoyer une table de hachage, utilisez les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="79fa6-235">To submit a hash table, use the following keys.</span></span>

  <span data-ttu-id="79fa6-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (ou toute chaîne d’heure valide); `DaysOfWeek="Monday", "Wednesday"` (ou toute combinaison de noms de jours); `Interval=2` (ou n’importe quel intervalle de fréquence valide); `RandomDelay="30minutes"` (ou toute chaîne TimeSpan valide); `User="Domain1\User01` (ou tout utilisateur valide ; utilisé uniquement avec la valeur de fréquence *AtLogon* )}</span><span class="sxs-lookup"><span data-stu-id="79fa6-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01` (or any valid user; used only with the *AtLogon* frequency value) }</span></span>

## <span data-ttu-id="79fa6-237">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="79fa6-237">RELATED LINKS</span></span>

[<span data-ttu-id="79fa6-238">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-238">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="79fa6-239">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-239">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="79fa6-240">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="79fa6-240">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="79fa6-241">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-241">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="79fa6-242">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="79fa6-242">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="79fa6-243">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-243">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="79fa6-244">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="79fa6-244">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="79fa6-245">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="79fa6-245">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="79fa6-246">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-246">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="79fa6-247">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="79fa6-247">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="79fa6-248">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="79fa6-248">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="79fa6-249">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-249">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="79fa6-250">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="79fa6-250">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="79fa6-251">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="79fa6-251">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="79fa6-252">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="79fa6-252">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="79fa6-253">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="79fa6-253">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
