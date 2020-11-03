---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202986"
---
# <span data-ttu-id="d34be-103">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-103">Set-JobTrigger</span></span>

## <span data-ttu-id="d34be-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d34be-104">SYNOPSIS</span></span>
<span data-ttu-id="d34be-105">Modifie le déclencheur d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-105">Changes the job trigger of a scheduled job.</span></span>

## <span data-ttu-id="d34be-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d34be-106">SYNTAX</span></span>

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="d34be-107">Description</span><span class="sxs-lookup"><span data-stu-id="d34be-107">DESCRIPTION</span></span>
<span data-ttu-id="d34be-108">L'applet de commande **Set-JobTrigger** modifie les propriétés des déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="d34be-108">The **Set-JobTrigger** cmdlet changes the properties of the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="d34be-109">Vous pouvez l'utiliser pour modifier l'heure ou la fréquence à laquelle les tâches démarrent ou pour passer des planifications basées sur l'heure à des planifications qui sont déclenchées par un démarrage ou une ouverture de session.</span><span class="sxs-lookup"><span data-stu-id="d34be-109">You can use it to change the time or frequency at which the jobs start or to change from a time-based schedules to schedules that are triggered by a logon or startup.</span></span>

<span data-ttu-id="d34be-110">Un déclencheur de tâche définit une planification ou des conditions récurrentes pour le démarrage d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-110">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="d34be-111">Même si les déclencheurs de tâche ne sont pas enregistrés sur disque, vous pouvez modifier les déclencheurs des tâches planifiées, qui sont enregistrées sur disque.</span><span class="sxs-lookup"><span data-stu-id="d34be-111">Although job triggers are not saved to disk, you can change the job triggers of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="d34be-112">Pour modifier un déclencheur de tâche d’une tâche planifiée, commencez par utiliser l’applet de commande Get-JobTrigger pour obtenir le déclencheur d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-112">To change a job trigger of a scheduled job, begin by using the Get-JobTrigger cmdlet to get the job trigger of a scheduled job.</span></span>
<span data-ttu-id="d34be-113">Ensuite, dirigez le déclencheur vers **Set-JobTrigger** ou enregistrez-le dans une variable et utilisez le paramètre *InputObject* de l'applet de commande **Set-JobTrigger** pour identifier le déclencheur.</span><span class="sxs-lookup"><span data-stu-id="d34be-113">Then, pipe the trigger to **Set-JobTrigger** or save the trigger in a variable and use the *InputObject* parameter of **Set-JobTrigger** cmdlet to identify the trigger.</span></span>
<span data-ttu-id="d34be-114">Utilisez les paramètres restants de **Set-JobTrigger** pour modifier le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="d34be-114">Use the remaining parameters of **Set-JobTrigger** to change the job trigger.</span></span>

<span data-ttu-id="d34be-115">Lorsque vous modifiez le type d’un déclencheur de tâche, tel que la modification d’un déclencheur de tâche d’un déclencheur quotidien ou hebdomadaire à un déclencheur *AtLogon* , les propriétés du déclencheur d’origine sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="d34be-115">When you change the type of a job trigger, such as changing a job trigger from a daily or weekly trigger to an *AtLogon* trigger, the original trigger properties are deleted.</span></span>
<span data-ttu-id="d34be-116">Toutefois, si vous modifiez les valeurs du déclencheur, mais pas son type, par exemple en modifiant les jours dans un déclencheur hebdomadaire, seules les propriétés que vous spécifiez sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="d34be-116">However, if you change the values of the trigger, but not its type, such as changing the days in a weekly trigger, only the properties that you specify are changed.</span></span>
<span data-ttu-id="d34be-117">Toutes les autres propriétés du déclencheur de tâche d'origine sont conservées.</span><span class="sxs-lookup"><span data-stu-id="d34be-117">All other properties of the original job trigger are retained.</span></span>

<span data-ttu-id="d34be-118">**Set-JobTrigger** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d34be-118">**Set-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="d34be-119">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="d34be-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="d34be-120">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*`  ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="d34be-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*`  or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="d34be-121">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d34be-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="d34be-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d34be-122">EXAMPLES</span></span>

### <span data-ttu-id="d34be-123">Exemple 1 : modifier les jours dans un déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="d34be-123">Example 1: Change the days in a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

<span data-ttu-id="d34be-124">Cet exemple montre comment modifier les jours dans un déclencheur de tâche hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="d34be-124">This example shows how to change the days in a weekly job trigger.</span></span>

<span data-ttu-id="d34be-125">La première commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de la tâche planifiée DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="d34be-125">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="d34be-126">La sortie indique que le déclencheur démarre la tâche à minuit le mercredi et le samedi.</span><span class="sxs-lookup"><span data-stu-id="d34be-126">The output shows that the trigger starts the job at midnight on Wednesdays and Saturdays.</span></span>

<span data-ttu-id="d34be-127">Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification du déclencheur.</span><span class="sxs-lookup"><span data-stu-id="d34be-127">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="d34be-128">Exemple 2 : modifier le type de déclencheur de tâche</span><span class="sxs-lookup"><span data-stu-id="d34be-128">Example 2: Change the job trigger type</span></span>

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

<span data-ttu-id="d34be-129">Cet exemple montre comment modifier le type de déclencheur de tâche qui démarre une tâche.</span><span class="sxs-lookup"><span data-stu-id="d34be-129">This example shows how to change the type of job trigger that starts a job.</span></span>
<span data-ttu-id="d34be-130">Les commandes de cet exemple remplacent un déclencheur de tâche AtStartup par un déclencheur hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="d34be-130">The commands in this example replace an AtStartup job trigger with a weekly trigger.</span></span>

<span data-ttu-id="d34be-131">La première commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de la tâche planifiée Inventory.</span><span class="sxs-lookup"><span data-stu-id="d34be-131">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the Inventory scheduled job.</span></span>
<span data-ttu-id="d34be-132">La sortie indique que la tâche a deux déclencheurs : un déclencheur quotidien et un déclencheur *AtStartup* .</span><span class="sxs-lookup"><span data-stu-id="d34be-132">The output shows that the job has two triggers a daily trigger and an *AtStartup* trigger.</span></span>

<span data-ttu-id="d34be-133">Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification du déclencheur.</span><span class="sxs-lookup"><span data-stu-id="d34be-133">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="d34be-134">Exemple 3 : modifier l’utilisateur sur un déclencheur de tâche à distance</span><span class="sxs-lookup"><span data-stu-id="d34be-134">Example 3: Change the user on a remote job trigger</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

<span data-ttu-id="d34be-135">Cette commande modifie l’utilisateur dans tous les déclencheurs de tâche *AtLogon* des tâches planifiées sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="d34be-135">This command changes the user in all *AtLogon* job triggers of scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="d34be-136">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="d34be-136">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="d34be-137">La commande distante commence par une commande Get-ScheduledJob qui obtient toutes les tâches planifiées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d34be-137">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="d34be-138">Les tâches planifiées sont dirigées vers l’applet de commande Get-JobTrigger, qui obtient les déclencheurs des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="d34be-138">The scheduled jobs are piped to the Get-JobTrigger cmdlet, which gets the job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="d34be-139">Chaque déclencheur de tâche contenant une propriété JobDefinition qui inclut la tâche planifiée, le déclencheur reste associé à la tâche planifiée, même en cas de modification.</span><span class="sxs-lookup"><span data-stu-id="d34be-139">Each job trigger contains a JobDefinition property that contains the scheduled job, so the trigger remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="d34be-140">Les déclencheurs de tâche sont dirigés vers l’applet de commande Where-Object, qui obtient les déclencheurs de tâche qui ont la propriété User.</span><span class="sxs-lookup"><span data-stu-id="d34be-140">The job triggers are piped to the Where-Object cmdlet, which gets job triggers that have the User property.</span></span>
<span data-ttu-id="d34be-141">Les déclencheurs de tâche sélectionnés sont dirigés vers l'applet de commande **Set-JobTrigger** , qui remplace l'utilisateur par Domain01\Admin02.</span><span class="sxs-lookup"><span data-stu-id="d34be-141">The selected job triggers are piped to the **Set-JobTrigger** cmdlet, which changes the user to Domain01\Admin02.</span></span>

### <span data-ttu-id="d34be-142">Exemple 4 : modifier l’un des nombreux déclencheurs de tâche</span><span class="sxs-lookup"><span data-stu-id="d34be-142">Example 4: Change one of many job triggers</span></span>

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="d34be-143">Les commandes de cet exemple remplacent l'intervalle de répétition du déclencheur de tâche *Once* de la tâche planifiée SecurityCheck « toutes les 60 minutes » par « toutes les 90 minutes ».</span><span class="sxs-lookup"><span data-stu-id="d34be-143">The commands in this example changes the repetition interval of the *Once* job trigger of SecurityCheck scheduled job from every 60 minutes to every 90 minutes.</span></span>
<span data-ttu-id="d34be-144">La tâche planifiée SecurityCheck a trois déclencheurs de tâche, donc les commandes utilisent le paramètre *TriggerId* de l’applet de commande Get-JobTrigger pour identifier le déclencheur de tâche en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="d34be-144">The SecurityCheck scheduled job has three job triggers, so the commands use the *TriggerId* parameter of the Get-JobTrigger cmdlet to identify the job trigger that is being changed.</span></span>

<span data-ttu-id="d34be-145">La première commande utilise l'applet de commande **Get-JobTrigger** pour obtenir tous les déclencheurs de la tâche planifiée SecurityCheck.</span><span class="sxs-lookup"><span data-stu-id="d34be-145">The first command uses the **Get-JobTrigger** cmdlet to get all job triggers of the SecurityCheck scheduled job.</span></span>
<span data-ttu-id="d34be-146">La sortie, qui affiche les ID des déclencheurs de tâche, indique que le déclencheur de tâche *Once* a un ID de 3.</span><span class="sxs-lookup"><span data-stu-id="d34be-146">The output, which displays the IDs of the job triggers, reveals that the *Once* job trigger has an ID of 3.</span></span>

## <span data-ttu-id="d34be-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d34be-147">PARAMETERS</span></span>

### <span data-ttu-id="d34be-148">-À</span><span class="sxs-lookup"><span data-stu-id="d34be-148">-At</span></span>
<span data-ttu-id="d34be-149">Démarre la tâche à la date et à l'heure spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d34be-149">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="d34be-150">Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date, ou une chaîne qui peut être convertie en une heure, telle que « 19 avril, 2012 15:00 », « 12/31/2013 9:00 PM » ou « 3:00 ».</span><span class="sxs-lookup"><span data-stu-id="d34be-150">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a time, such as "April 19, 2012 15:00", "12/31/2013 9:00 PM", or "3am".</span></span>

<span data-ttu-id="d34be-151">Si vous ne spécifiez pas un élément de l’objet **DateTime** , tel que seconds, cet élément du déclencheur de tâche n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="d34be-151">If you don't specify an element of the **DateTime** object, such as seconds, that element of the job trigger is not changed.</span></span>
<span data-ttu-id="d34be-152">Si le déclencheur de tâche d’origine n’inclut pas d’objet **DateTime** et que vous omettez un élément, le déclencheur de tâche est créé avec l’élément correspondant à partir de la date et de l’heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="d34be-152">If the original job trigger didn't include a **DateTime** object and you omit an element, the job trigger is created with the corresponding element from the current date and time.</span></span>

<span data-ttu-id="d34be-153">Quand vous utilisez le paramètre *Once* , affectez au paramètre *At* une date et une heure spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d34be-153">When using the *Once* parameter, set the value of the *At* parameter to a particular date and time.</span></span>
<span data-ttu-id="d34be-154">Comme la date par défaut dans un objet **DateTime** est la date actuelle, la définition d'une heure antérieure à l'heure actuelle sans une date explicite génère un déclencheur de tâche pour une heure dans le passé.</span><span class="sxs-lookup"><span data-stu-id="d34be-154">Because the default date in a **DateTime** object is the current date, setting a time before the current time without an explicit date results in a job trigger for a time in the past.</span></span>

<span data-ttu-id="d34be-155">Les objets **DateTime** , et les chaînes converties en objets **DateTime** , sont automatiquement ajustées pour être compatibles avec les formats de date et d’heure sélectionnés pour l’ordinateur local dans région et langue dans le panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="d34be-155">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d34be-156">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="d34be-156">-AtLogOn</span></span>
<span data-ttu-id="d34be-157">Démarre la tâche planifiée quand les utilisateurs spécifiés se connectent à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d34be-157">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="d34be-158">Pour spécifier un utilisateur, utilisez le paramètre *User* .</span><span class="sxs-lookup"><span data-stu-id="d34be-158">To specify a user, use the *User* parameter.</span></span>

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

### <span data-ttu-id="d34be-159">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="d34be-159">-AtStartup</span></span>
<span data-ttu-id="d34be-160">Démarre la tâche planifiée au démarrage de Windows.</span><span class="sxs-lookup"><span data-stu-id="d34be-160">Starts the scheduled job when Windows starts.</span></span>

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

### <span data-ttu-id="d34be-161">-Tous les jours</span><span class="sxs-lookup"><span data-stu-id="d34be-161">-Daily</span></span>
<span data-ttu-id="d34be-162">Spécifie une planification de tâche quotidienne périodique.</span><span class="sxs-lookup"><span data-stu-id="d34be-162">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="d34be-163">Utilisez les autres paramètres du jeu de paramètres *Daily* pour spécifier les détails de la planification.</span><span class="sxs-lookup"><span data-stu-id="d34be-163">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="d34be-164">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="d34be-164">-DaysInterval</span></span>
<span data-ttu-id="d34be-165">Spécifie le nombre de jours entre les occurrences d'une planification quotidienne.</span><span class="sxs-lookup"><span data-stu-id="d34be-165">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="d34be-166">Par exemple, une valeur de 3 démarre la tâche planifiée les jours 1, 4, 7 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d34be-166">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="d34be-167">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="d34be-167">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d34be-168">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="d34be-168">-DaysOfWeek</span></span>
<span data-ttu-id="d34be-169">Spécifie les jours de la semaine qu'une tâche planifiée hebdomadaire s'exécute.</span><span class="sxs-lookup"><span data-stu-id="d34be-169">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="d34be-170">Entrez les noms des jours, tels que lundi, jeudi, entiers 0-6, où 0 représente dimanche, ou un astérisque ( \* ) pour représenter tous les jours.</span><span class="sxs-lookup"><span data-stu-id="d34be-170">Enter day names, such as Monday, Thursday, integers 0-6, where 0 represents Sunday, or an asterisk (\*) to represent every day.</span></span>
<span data-ttu-id="d34be-171">Ce paramètre est obligatoire dans le jeu de paramètres Weekly.</span><span class="sxs-lookup"><span data-stu-id="d34be-171">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="d34be-172">Les noms de jours sont convertis dans leurs valeurs entières dans le déclencheur de tâche.</span><span class="sxs-lookup"><span data-stu-id="d34be-172">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="d34be-173">Lorsque vous placez les noms de jours entre guillemets droits dans une commande, faites-le séparément, par exemple "Lundi", "Mardi".</span><span class="sxs-lookup"><span data-stu-id="d34be-173">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="d34be-174">Si vous incluez plusieurs noms de jours dans une seule paire de guillemets droits, les valeurs entières correspondantes sont additionnées.</span><span class="sxs-lookup"><span data-stu-id="d34be-174">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="d34be-175">Par exemple, "Lundi, Mardi" (1, 2) donne la valeur "Mercredi" (3).</span><span class="sxs-lookup"><span data-stu-id="d34be-175">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d34be-176">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d34be-176">-InputObject</span></span>
<span data-ttu-id="d34be-177">Spécifie les déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="d34be-177">Specifies the job triggers.</span></span>
<span data-ttu-id="d34be-178">Entrez une variable qui contient des objets **ScheduledJobTrigger** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.</span><span class="sxs-lookup"><span data-stu-id="d34be-178">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="d34be-179">Vous pouvez également diriger un objet **ScheduledJobTrigger** vers **Set-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="d34be-179">You can also pipe a **ScheduledJobTrigger** object to **Set-JobTrigger** .</span></span>

<span data-ttu-id="d34be-180">Si vous spécifiez plusieurs déclencheurs de tâche, **Set-JobTrigger** apporte les mêmes modifications à tous les déclencheurs de tâche.</span><span class="sxs-lookup"><span data-stu-id="d34be-180">If you specify multiple job triggers, **Set-JobTrigger** makes the same changes to all job triggers.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d34be-181">-Une fois</span><span class="sxs-lookup"><span data-stu-id="d34be-181">-Once</span></span>
<span data-ttu-id="d34be-182">Spécifie une planification non périodique (unique).</span><span class="sxs-lookup"><span data-stu-id="d34be-182">Specifies a non-recurring (one time) schedule.</span></span>

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

### <span data-ttu-id="d34be-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d34be-183">-PassThru</span></span>
<span data-ttu-id="d34be-184">Retourne les déclencheurs de tâche modifiés.</span><span class="sxs-lookup"><span data-stu-id="d34be-184">Returns the job triggers that changed.</span></span>
<span data-ttu-id="d34be-185">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="d34be-185">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d34be-186">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="d34be-186">-RandomDelay</span></span>
<span data-ttu-id="d34be-187">Active un délai aléatoire qui commence à l'heure de début planifiée et définit la valeur maximale du délai.</span><span class="sxs-lookup"><span data-stu-id="d34be-187">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="d34be-188">La longueur du délai est définie de manière pseudo-aléatoire pour chaque démarrage et elle varie entre aucun délai et la durée spécifiée par la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d34be-188">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="d34be-189">La valeur par défaut, zéro (00:00:00), désactive le délai aléatoire.</span><span class="sxs-lookup"><span data-stu-id="d34be-189">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="d34be-190">Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> format, qui est automatiquement convertie en objet TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="d34be-190">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a timespan object.</span></span>

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

### <span data-ttu-id="d34be-191">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="d34be-191">-RepeatIndefinitely</span></span>
<span data-ttu-id="d34be-192">Ce paramètre, disponible à partir de Windows PowerShell 4.0, élimine le besoin de spécifier une valeur **TimeSpan.MaxValue** pour le paramètre *RepetitionDuration* pour exécuter une tâche planifiée à plusieurs reprises, pendant une durée indéterminée.</span><span class="sxs-lookup"><span data-stu-id="d34be-192">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

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

### <span data-ttu-id="d34be-193">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="d34be-193">-RepetitionDuration</span></span>
<span data-ttu-id="d34be-194">Répète la tâche jusqu'à ce que le délai spécifié expire.</span><span class="sxs-lookup"><span data-stu-id="d34be-194">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="d34be-195">La fréquence de répétition est déterminée par la valeur du paramètre *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="d34be-195">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="d34be-196">Par exemple, si la valeur de **RepetitionInterval** est égale à 5 minutes et la valeur de *RepetitionDuration* à 2 heures, la tâche se déclenche toutes les cinq minutes pendant deux heures.</span><span class="sxs-lookup"><span data-stu-id="d34be-196">For example, if the value of **RepetitionInterval** is 5 minutes and the value of *RepetitionDuration* is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="d34be-197">Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».</span><span class="sxs-lookup"><span data-stu-id="d34be-197">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="d34be-198">Pour exécuter une tâche indéfiniment, ajoutez plutôt le paramètre *RepeatIndefinitely* .</span><span class="sxs-lookup"><span data-stu-id="d34be-198">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="d34be-199">Pour arrêter une tâche avant l'expiration de la durée de répétition de déclencheur de tâche, affectez à **RepetitionDuration** la valeur zéro (0).</span><span class="sxs-lookup"><span data-stu-id="d34be-199">To stop a job before the job trigger repetition duration expires, set the **RepetitionDuration** value to zero (0).</span></span>

<span data-ttu-id="d34be-200">Pour modifier la durée de répétition ou l'intervalle de répétition d'un déclencheur de tâche *Once* , la commande doit inclure les paramètres **RepetitionInterval** et **RepetitionDuration** .</span><span class="sxs-lookup"><span data-stu-id="d34be-200">To change the repetition duration or repetition interval of a *Once* job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="d34be-201">Pour modifier la durée de répétition ou les intervalles de répétition d'autres types de déclencheur de tâche, la commande doit inclure les paramètres *Once* , *At* , *RepetitionInterval* et *RepetitionDuration* .</span><span class="sxs-lookup"><span data-stu-id="d34be-201">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the *Once* , *At* , *RepetitionInterval* and *RepetitionDuration* parameters.</span></span>

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

### <span data-ttu-id="d34be-202">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="d34be-202">-RepetitionInterval</span></span>
<span data-ttu-id="d34be-203">Répète la tâche à l'intervalle de temps spécifié.</span><span class="sxs-lookup"><span data-stu-id="d34be-203">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="d34be-204">Par exemple, si la valeur de ce paramètre est de 2 heures, la tâche est déclenchée toutes les deux heures.</span><span class="sxs-lookup"><span data-stu-id="d34be-204">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="d34be-205">La valeur par défaut, 0, ne répète pas la tâche.</span><span class="sxs-lookup"><span data-stu-id="d34be-205">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="d34be-206">Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».</span><span class="sxs-lookup"><span data-stu-id="d34be-206">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="d34be-207">Pour modifier la durée de répétition ou l'intervalle de répétition d'un déclencheur de tâche **Once** , la commande doit inclure les paramètres **RepetitionInterval** et **RepetitionDuration** .</span><span class="sxs-lookup"><span data-stu-id="d34be-207">To change the repetition duration or repetition interval of a **Once** job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="d34be-208">Pour modifier la durée de répétition ou les intervalles de répétition d'autres types de déclencheur de tâche, la commande doit inclure les paramètres **Once** , **At** , **RepetitionInterval** et **RepetitionDuration** .</span><span class="sxs-lookup"><span data-stu-id="d34be-208">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the **Once** , **At** , **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>

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

### <span data-ttu-id="d34be-209">-User</span><span class="sxs-lookup"><span data-stu-id="d34be-209">-User</span></span>
<span data-ttu-id="d34be-210">Spécifie les utilisateurs qui déclenchent un démarrage *AtLogon* d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-210">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="d34be-211">Entrez le nom d’un utilisateur au \<UserName\> format ou, \<Domain\Username\> ou entrez un astérisque ( \* ) pour représenter tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d34be-211">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="d34be-212">La valeur par défaut est tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d34be-212">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d34be-213">-Hebdomadaire</span><span class="sxs-lookup"><span data-stu-id="d34be-213">-Weekly</span></span>
<span data-ttu-id="d34be-214">Spécifie une planification de tâche hebdomadaire périodique.</span><span class="sxs-lookup"><span data-stu-id="d34be-214">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="d34be-215">Utilisez les autres paramètres du jeu de paramètres *Weekly* pour spécifier les détails de la planification.</span><span class="sxs-lookup"><span data-stu-id="d34be-215">Use the other parameters in the *Weekly* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="d34be-216">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="d34be-216">-WeeksInterval</span></span>
<span data-ttu-id="d34be-217">Spécifie le nombre de semaines entre les occurrences d'une planification de tâche hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="d34be-217">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="d34be-218">Par exemple, une valeur de 3 démarre la tâche planifiée les semaines 1, 4, 7 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d34be-218">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="d34be-219">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="d34be-219">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d34be-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d34be-220">CommonParameters</span></span>
<span data-ttu-id="d34be-221">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d34be-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d34be-222">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d34be-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d34be-223">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d34be-223">INPUTS</span></span>

### <span data-ttu-id="d34be-224">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-224">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="d34be-225">Vous pouvez diriger plusieurs déclencheurs de tâche vers **Set-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="d34be-225">You can pipe multiple job triggers to **Set-JobTrigger** .</span></span>

## <span data-ttu-id="d34be-226">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d34be-226">OUTPUTS</span></span>

### <span data-ttu-id="d34be-227">Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-227">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="d34be-228">Quand vous utilisez le paramètre *Passthru* , **Set-JobTrigger** retourne les déclencheurs de tâche modifiés.</span><span class="sxs-lookup"><span data-stu-id="d34be-228">When you use the *Passthru* parameter, **Set-JobTrigger** returns the job triggers that were changed.</span></span>
<span data-ttu-id="d34be-229">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d34be-229">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d34be-230">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d34be-230">NOTES</span></span>

* <span data-ttu-id="d34be-231">Les déclencheurs de tâche ont une propriété JobDefintion qui les associe à la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-231">Job triggers have a JobDefintion property that associates them with the scheduled job.</span></span> <span data-ttu-id="d34be-232">Quand vous modifiez le déclencheur d'une tâche planifiée, la tâche est modifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-232">When you change the job trigger of a scheduled job, the job is changed.</span></span> <span data-ttu-id="d34be-233">Vous n’avez pas besoin d’utiliser une commande Set-ScheduledJob pour appliquer le déclencheur modifié à la tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="d34be-233">You do not need to use a Set-ScheduledJob command to apply the changed trigger to the scheduled job.</span></span>

## <span data-ttu-id="d34be-234">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d34be-234">RELATED LINKS</span></span>

[<span data-ttu-id="d34be-235">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-235">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="d34be-236">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-236">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="d34be-237">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d34be-237">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="d34be-238">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-238">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="d34be-239">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d34be-239">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="d34be-240">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-240">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="d34be-241">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d34be-241">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="d34be-242">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="d34be-242">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="d34be-243">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-243">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="d34be-244">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="d34be-244">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="d34be-245">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d34be-245">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="d34be-246">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-246">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="d34be-247">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="d34be-247">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="d34be-248">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d34be-248">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="d34be-249">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="d34be-249">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="d34be-250">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="d34be-250">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
