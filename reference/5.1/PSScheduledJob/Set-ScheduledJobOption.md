---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202974"
---
# <span data-ttu-id="fd266-103">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fd266-103">Set-ScheduledJobOption</span></span>

## <span data-ttu-id="fd266-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fd266-104">SYNOPSIS</span></span>
<span data-ttu-id="fd266-105">Modifie les options d'une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="fd266-105">Changes the job options of a scheduled job.</span></span>

## <span data-ttu-id="fd266-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fd266-106">SYNTAX</span></span>

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="fd266-107">Description</span><span class="sxs-lookup"><span data-stu-id="fd266-107">DESCRIPTION</span></span>
<span data-ttu-id="fd266-108">L'applet de commande **Set-ScheduledJobOptions** modifie les options de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="fd266-108">The **Set-ScheduledJobOptions** cmdlet changes the job options of scheduled jobs.</span></span>

<span data-ttu-id="fd266-109">Pour modifier les options d’une tâche planifiée, commencez par utiliser l’applet de commande Get-ScheduledJobOption pour obtenir les options de tâche d’une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="fd266-109">To change the options of a scheduled job, begin by using the Get-ScheduledJobOption cmdlet to get the job options of a scheduled job.</span></span>
<span data-ttu-id="fd266-110">Ensuite, dirigez les options vers **Set-ScheduledJobOption** ou enregistrez-les dans une variable et utilisez le paramètre *InputObject* de l'applet de commande **Set-ScheduledJobOption** pour identifier les options.</span><span class="sxs-lookup"><span data-stu-id="fd266-110">Then, pipe the options to **Set-ScheduledJobOption** or save the options in a variable and use the *InputObject* parameter of **Set-ScheduledJobOption** cmdlet to identify the options.</span></span>
<span data-ttu-id="fd266-111">Utilisez les paramètres restants de **Set-ScheduledJobOption** pour modifier les options de tâche.</span><span class="sxs-lookup"><span data-stu-id="fd266-111">Use the remaining parameters of **Set-ScheduledJobOption** to change the job options.</span></span>

<span data-ttu-id="fd266-112">Pour activer une option de tâche, utilisez le paramètre qui définit cette option.</span><span class="sxs-lookup"><span data-stu-id="fd266-112">To turn on a job option, use the parameter that sets that option.</span></span>
<span data-ttu-id="fd266-113">Pour désactiver une option, tapez le nom du paramètre, un signe deux-points ( :) et $False.</span><span class="sxs-lookup"><span data-stu-id="fd266-113">To turn off an option, type the parameter name, a colon (:), and $False.</span></span>
<span data-ttu-id="fd266-114">Par exemple, pour désactiver l’option *RunElevated* , tapez `-RunElevated:$False` .</span><span class="sxs-lookup"><span data-stu-id="fd266-114">For example, to turn off the *RunElevated* option, type `-RunElevated:$False`.</span></span>

<span data-ttu-id="fd266-115">Chaque objet d'options de tâche incluant une propriété JobDefinition qui contient la tâche planifiée, l'association à la tâche planifiée est conservée quand les options de tâche sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="fd266-115">Each job options object includes a JobDefinition property that contains the scheduled job, so the association with the scheduled job is retained when the job options are changed.</span></span>

<span data-ttu-id="fd266-116">Les options de tâche planifiée déterminent le mode d'exécution de la tâche quand elle est démarrée par le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="fd266-116">The scheduled job options determine how the job runs when it is started by Task Scheduler.</span></span>
<span data-ttu-id="fd266-117">Ces options ne s’appliquent pas lorsque vous utilisez l’applet de commande Start-Job pour démarrer une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="fd266-117">These options to not apply when you use the Start-Job cmdlet to start a scheduled job.</span></span>

<span data-ttu-id="fd266-118">**Set-ScheduledJobOption** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd266-118">**Set-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="fd266-119">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="fd266-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="fd266-120">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="fd266-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="fd266-121">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fd266-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="fd266-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fd266-122">EXAMPLES</span></span>

### <span data-ttu-id="fd266-123">Exemple 1 : modifier les options d’un travail</span><span class="sxs-lookup"><span data-stu-id="fd266-123">Example 1: Change job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
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
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

<span data-ttu-id="fd266-124">Cet exemple montre comment modifier les options d'une tâche planifiée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fd266-124">This example shows how to change the options of a scheduled job on the local computer.</span></span>

<span data-ttu-id="fd266-125">La première commande utilise l’applet de commande Get-ScheduledJobOption pour accéder aux options de tâche de la tâche planifiée DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="fd266-125">The first command uses the Get-ScheduledJobOption cmdlet to get the job options of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="fd266-126">La sortie indique que les propriétés WakeToRun et RunElevated sont définies sur $False.</span><span class="sxs-lookup"><span data-stu-id="fd266-126">The output shows that the WakeToRun and RunElevated properties are set to $False.</span></span>

<span data-ttu-id="fd266-127">Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification de l'option.</span><span class="sxs-lookup"><span data-stu-id="fd266-127">This command is not required; it is included only to show the effect of the option change.</span></span>

### <span data-ttu-id="fd266-128">Exemple 2 : modifier une option sur toutes les tâches planifiées distantes</span><span class="sxs-lookup"><span data-stu-id="fd266-128">Example 2: Change an option on all remote scheduled jobs</span></span>

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

<span data-ttu-id="fd266-129">Cette commande remplace la valeur de *IdleTimeout* d’une heure (valeur par défaut) par deux heures sur toutes les tâches planifiées sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="fd266-129">This command changes the value of the *IdleTimeout* from one hour (the default value) to two hours on all scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="fd266-130">La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="fd266-130">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="fd266-131">La commande distante commence par une commande Get-ScheduledJob qui obtient toutes les tâches planifiées sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fd266-131">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="fd266-132">Les tâches planifiées sont dirigées vers l’applet de commande Get-ScheduledJobOption, qui obtient les options de tâche des tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="fd266-132">The scheduled jobs are piped to the Get-ScheduledJobOption cmdlet, which gets the job options of the scheduled jobs.</span></span>
<span data-ttu-id="fd266-133">Chaque objet d'options de tâche contenant une propriété JobDefinition qui inclut la tâche planifiée, l'objet d'options reste associé à la tâche planifiée, même en cas de modification.</span><span class="sxs-lookup"><span data-stu-id="fd266-133">Each job options object contains a JobDefinition property that contains the scheduled job, so the options object remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="fd266-134">Les déclencheurs de tâche sont dirigés vers l’applet de commande **Set-ScheduledJobOption** , qui remplace la valeur de l’option *IdleTimeout* par deux heures (2:00:00).</span><span class="sxs-lookup"><span data-stu-id="fd266-134">The job triggers are piped to the **Set-ScheduledJobOption** cmdlet, which changes the value of the *IdleTimeout* option to two hours (2:00:00).</span></span>

## <span data-ttu-id="fd266-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fd266-135">PARAMETERS</span></span>

### <span data-ttu-id="fd266-136">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="fd266-136">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="fd266-137">Ne pas arrêter la tâche planifiée si l'ordinateur passe en mode d'alimentation par batterie (se déconnecte de l'alimentation secteur) pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="fd266-137">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="fd266-138">Par défaut, les tâches planifiées s'arrêtent quand l'ordinateur se déconnecte de l'alimentation secteur.</span><span class="sxs-lookup"><span data-stu-id="fd266-138">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="fd266-139">Le paramètre *ContinueIfGoingOnBattery* définit la valeur de la propriété StopIfGoingOnBatteries des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="fd266-139">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="fd266-140">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="fd266-140">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="fd266-141">Démarrer la tâche uniquement au moment où elle est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="fd266-141">Start the job only when it is triggered.</span></span>
<span data-ttu-id="fd266-142">Les utilisateurs ne peuvent pas démarrer la tâche manuellement, notamment à l'aide de la fonctionnalité Exécuter du Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="fd266-142">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="fd266-143">Ce paramètre affecte uniquement le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="fd266-143">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="fd266-144">Il n’empêche pas les utilisateurs d’utiliser l’applet de commande Start-Job pour démarrer le travail.</span><span class="sxs-lookup"><span data-stu-id="fd266-144">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="fd266-145">Le paramètre *DoNotAllowDemandStart* définit la valeur de la propriété DoNotAllowDemandStart des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="fd266-145">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="fd266-146">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="fd266-146">-HideInTaskScheduler</span></span>
<span data-ttu-id="fd266-147">Ne pas afficher la tâche dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="fd266-147">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="fd266-148">Cette valeur affecte uniquement l'ordinateur sur lequel s'exécute la tâche.</span><span class="sxs-lookup"><span data-stu-id="fd266-148">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="fd266-149">Par défaut, les tâches planifiées apparaissent dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="fd266-149">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="fd266-150">Même si une tâche est masquée, les utilisateurs peuvent afficher la tâche en sélectionnant l’option Afficher l’affichage des **tâches masquées** dans planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="fd266-150">Even if a task is hidden, users can display the task by selecting the **Show hidden tasks** view option in Task Scheduler.</span></span>

<span data-ttu-id="fd266-151">Le paramètre *HideInTaskScheduler* définit la valeur de la propriété ShowInTaskScheduler des tâches planifiées sur $false.</span><span class="sxs-lookup"><span data-stu-id="fd266-151">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="fd266-152">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="fd266-152">-IdleDuration</span></span>
<span data-ttu-id="fd266-153">Spécifie la durée pendant laquelle l'ordinateur doit être inactif avant que la tâche commence.</span><span class="sxs-lookup"><span data-stu-id="fd266-153">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="fd266-154">La valeur par défaut est 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="fd266-154">The default value is 10 minutes.</span></span>
<span data-ttu-id="fd266-155">Si l'ordinateur n'est pas inactif pendant la durée spécifiée avant l'expiration de la valeur *IdleTimeout* , la tâche planifiée ne s'exécute pas avant la prochaine planification, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fd266-155">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="fd266-156">Entrez un objet TimeSpan, tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="fd266-156">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="fd266-157">Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="fd266-157">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="fd266-158">Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="fd266-158">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="fd266-159">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="fd266-159">-IdleTimeout</span></span>
<span data-ttu-id="fd266-160">Spécifie la durée pendant laquelle l'ordinateur doit être inactif avant que la tâche commence.</span><span class="sxs-lookup"><span data-stu-id="fd266-160">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="fd266-161">La valeur par défaut est 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="fd266-161">The default value is 10 minutes.</span></span>
<span data-ttu-id="fd266-162">Si l'ordinateur n'est pas inactif pendant la durée spécifiée avant l'expiration de la valeur **IdleTimeout** , la tâche planifiée ne s'exécute pas avant la prochaine planification, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fd266-162">If the computer is not idle for the specified duration before the value of **IdleTimeout** expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="fd266-163">Entrez un objet TimeSpan, tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="fd266-163">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="fd266-164">Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="fd266-164">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="fd266-165">Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="fd266-165">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="fd266-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fd266-166">-InputObject</span></span>
<span data-ttu-id="fd266-167">Spécifie les options de tâche.</span><span class="sxs-lookup"><span data-stu-id="fd266-167">Specifies the job options.</span></span>
<span data-ttu-id="fd266-168">Entrez une variable qui contient des objets **ScheduledJobOptions** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobOptions** , par exemple une commande Get-ScheduledJobOption.</span><span class="sxs-lookup"><span data-stu-id="fd266-168">Enter a variable that contains **ScheduledJobOptions** objects or type a command or expression that gets **ScheduledJobOptions** objects, such as a Get-ScheduledJobOption command.</span></span>
<span data-ttu-id="fd266-169">Vous pouvez également diriger un objet **ScheduledJobOptions** vers **Set-ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="fd266-169">You can also pipe a **ScheduledJobOptions** object to **Set-ScheduledJobOption** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fd266-170">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="fd266-170">-MultipleInstancePolicy</span></span>
<span data-ttu-id="fd266-171">Détermine comment le système répond à une demande de démarrage d'une instance d'une tâche planifiée alors qu'une autre instance de la tâche est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="fd266-171">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="fd266-172">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="fd266-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fd266-173">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="fd266-173">IgnoreNew.</span></span>
<span data-ttu-id="fd266-174">La nouvelle instance de la tâche est ignorée.</span><span class="sxs-lookup"><span data-stu-id="fd266-174">The new job instance is ignored.</span></span>
<span data-ttu-id="fd266-175">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd266-175">This is the default value.</span></span>
- <span data-ttu-id="fd266-176">Parallel.</span><span class="sxs-lookup"><span data-stu-id="fd266-176">Parallel.</span></span>
<span data-ttu-id="fd266-177">La nouvelle instance de la tâche démarre immédiatement.</span><span class="sxs-lookup"><span data-stu-id="fd266-177">The new job instance starts immediately.</span></span>
- <span data-ttu-id="fd266-178">File d'attente.</span><span class="sxs-lookup"><span data-stu-id="fd266-178">Queue.</span></span>
<span data-ttu-id="fd266-179">La nouvelle instance de la tâche démarre dès que l'instance actuelle se termine.</span><span class="sxs-lookup"><span data-stu-id="fd266-179">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="fd266-180">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="fd266-180">StopExisting.</span></span>
<span data-ttu-id="fd266-181">L'instance actuelle de la tâche s'arrête et la nouvelle instance démarre.</span><span class="sxs-lookup"><span data-stu-id="fd266-181">The current instance of the job stop and the new instance starts.</span></span>

<span data-ttu-id="fd266-182">Pour exécuter la tâche, toutes les conditions de la planification des tâches doivent être remplies.</span><span class="sxs-lookup"><span data-stu-id="fd266-182">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="fd266-183">Par exemple, si les conditions définies par les paramètres *RequireNetwork* , *IdleDuration* et *IdleTimeout* ne sont pas satisfaites, l’instance de tâche n’est pas démarrée, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd266-183">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd266-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fd266-184">-PassThru</span></span>
<span data-ttu-id="fd266-185">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fd266-185">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="fd266-186">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="fd266-186">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fd266-187">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="fd266-187">-RequireNetwork</span></span>
<span data-ttu-id="fd266-188">Exécute la tâche planifiée uniquement quand des connexions réseau sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd266-188">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="fd266-189">Si vous spécifiez ce paramètre et que le réseau n'est pas disponible à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fd266-189">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="fd266-190">Le paramètre *RequireNetwork* définit la valeur de la propriété RunWithoutNetwork des tâches planifiées sur $false.</span><span class="sxs-lookup"><span data-stu-id="fd266-190">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="fd266-191">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="fd266-191">-RestartOnIdleResume</span></span>
<span data-ttu-id="fd266-192">Redémarre une tâche planifiée quand l'ordinateur devient inactif.</span><span class="sxs-lookup"><span data-stu-id="fd266-192">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="fd266-193">Ce paramètre fonctionne avec le paramètre *StopIfGoingOffIdle* , qui interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (quitte l'état d'inactivité).</span><span class="sxs-lookup"><span data-stu-id="fd266-193">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="fd266-194">Le paramètre *RestartOnIdleResume* définit la valeur de la propriété RestartOnIdleResume des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="fd266-194">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="fd266-195">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="fd266-195">-RunElevated</span></span>
<span data-ttu-id="fd266-196">Exécute la tâche planifiée avec les autorisations d'un membre du groupe Administrateurs sur l'ordinateur sur lequel s'exécute la tâche.</span><span class="sxs-lookup"><span data-stu-id="fd266-196">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="fd266-197">Pour permettre l’exécution d’une tâche planifiée avec des autorisations d’administrateur, utilisez le paramètre *Credential* de Register-ScheduledJob pour fournir des informations d’identification explicites pour le travail.</span><span class="sxs-lookup"><span data-stu-id="fd266-197">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="fd266-198">Le paramètre **RunElevated** définit la valeur de la propriété **RunElevated** des tâches planifiées sur true.</span><span class="sxs-lookup"><span data-stu-id="fd266-198">The **RunElevated** parameter sets the value of the **RunElevated** property of scheduled jobs to True.</span></span>

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

### <span data-ttu-id="fd266-199">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="fd266-199">-StartIfIdle</span></span>
<span data-ttu-id="fd266-200">Démarre la tâche planifiée si l'ordinateur a été inactif pendant la durée spécifiée par le paramètre **IdleDuration** avant que l'heure spécifiée par le paramètre *IdleTimeout* n'expire.</span><span class="sxs-lookup"><span data-stu-id="fd266-200">Starts the scheduled job if the computer has been idle for the time specified by the **IdleDuration** parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="fd266-201">Par défaut, les paramètres *IdleDuration* et *IdleTimeout* sont ignorés et la tâche démarre à l'heure de début planifiée, même si l'ordinateur est occupé.</span><span class="sxs-lookup"><span data-stu-id="fd266-201">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="fd266-202">Si vous spécifiez ce paramètre et que l'ordinateur est occupé (non inactif) à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fd266-202">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="fd266-203">Le paramètre *StartIfIdle* définit la valeur de la propriété **StartIfNotIdle** des tâches planifiées sur false.</span><span class="sxs-lookup"><span data-stu-id="fd266-203">The *StartIfIdle* parameter sets the value of the **StartIfNotIdle** property of scheduled jobs to False.</span></span>

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

### <span data-ttu-id="fd266-204">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="fd266-204">-StartIfOnBattery</span></span>
<span data-ttu-id="fd266-205">Démarre la tâche planifiée, même si l'ordinateur fonctionne sur batterie à l'heure de début planifiée.</span><span class="sxs-lookup"><span data-stu-id="fd266-205">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="fd266-206">La valeur par défaut est False.</span><span class="sxs-lookup"><span data-stu-id="fd266-206">The default value is False.</span></span>

<span data-ttu-id="fd266-207">Le paramètre *StartIfOnBattery* définit la valeur de la propriété **StartIfOnBatteries** des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="fd266-207">The *StartIfOnBattery* parameter sets the value of the **StartIfOnBatteries** property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="fd266-208">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="fd266-208">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="fd266-209">Interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (non inactif) alors que la tâche est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="fd266-209">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="fd266-210">Par défaut, une tâche planifiée qui est suspendue quand l'ordinateur devient actif reprend quand il redevient inactif.</span><span class="sxs-lookup"><span data-stu-id="fd266-210">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="fd266-211">Pour modifier ce comportement par défaut, utilisez le paramètre *RestartOnIdleResume* .</span><span class="sxs-lookup"><span data-stu-id="fd266-211">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="fd266-212">Le paramètre *StopIfGoingOffIdle* définit la valeur de la propriété StopIfGoingOffIdle des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="fd266-212">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="fd266-213">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="fd266-213">-WakeToRun</span></span>
<span data-ttu-id="fd266-214">Sort l'ordinateur de son état de veille prolongée ou de veille à l'heure de début planifiée afin qu'il puisse exécuter la tâche.</span><span class="sxs-lookup"><span data-stu-id="fd266-214">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="fd266-215">Par défaut, si l'ordinateur est dans un état de veille prolongée ou de veille à l'heure de début planifiée, la tâche ne s'exécute pas.</span><span class="sxs-lookup"><span data-stu-id="fd266-215">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="fd266-216">Le paramètre *WakeToRun* définit la valeur de la propriété WakeToRun des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="fd266-216">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="fd266-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd266-217">CommonParameters</span></span>
<span data-ttu-id="fd266-218">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fd266-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fd266-219">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fd266-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fd266-220">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fd266-220">INPUTS</span></span>

### <span data-ttu-id="fd266-221">Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="fd266-221">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="fd266-222">Vous pouvez acheminer par canal un objet d'options de tâche planifiée vers **Set-ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="fd266-222">You can pipe a scheduled job options object to **Set-ScheduledJobOption** .</span></span>

## <span data-ttu-id="fd266-223">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fd266-223">OUTPUTS</span></span>

### <span data-ttu-id="fd266-224">Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="fd266-224">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="fd266-225">Quand vous utilisez le paramètre *Passthru* , **Set-ScheduledJobOption** retourne les options de tâche modifiées.</span><span class="sxs-lookup"><span data-stu-id="fd266-225">When you use the *Passthru* parameter, **Set-ScheduledJobOption** returns the job options that were changed.</span></span>
<span data-ttu-id="fd266-226">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="fd266-226">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fd266-227">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fd266-227">NOTES</span></span>

## <span data-ttu-id="fd266-228">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fd266-228">RELATED LINKS</span></span>

[<span data-ttu-id="fd266-229">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-229">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="fd266-230">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-230">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="fd266-231">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fd266-231">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="fd266-232">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-232">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="fd266-233">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fd266-233">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="fd266-234">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-234">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="fd266-235">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fd266-235">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="fd266-236">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fd266-236">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="fd266-237">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-237">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="fd266-238">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fd266-238">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="fd266-239">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fd266-239">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="fd266-240">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-240">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="fd266-241">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="fd266-241">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="fd266-242">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fd266-242">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="fd266-243">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="fd266-243">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="fd266-244">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="fd266-244">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
