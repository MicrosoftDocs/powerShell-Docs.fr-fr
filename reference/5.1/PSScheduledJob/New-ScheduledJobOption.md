---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202997"
---
# <span data-ttu-id="035e2-103">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="035e2-103">New-ScheduledJobOption</span></span>

## <span data-ttu-id="035e2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="035e2-104">SYNOPSIS</span></span>
<span data-ttu-id="035e2-105">Crée un objet qui contient des options avancées pour une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="035e2-105">Creates an object that contains advanced options for a scheduled job.</span></span>

## <span data-ttu-id="035e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="035e2-106">SYNTAX</span></span>

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="035e2-107">Description</span><span class="sxs-lookup"><span data-stu-id="035e2-107">DESCRIPTION</span></span>
<span data-ttu-id="035e2-108">L'applet de commande **New-ScheduledJobOption** crée un objet qui contient des options avancées pour une tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="035e2-108">The **New-ScheduledJobOption** cmdlet creates an object that contains advanced options for a scheduled job.</span></span>

<span data-ttu-id="035e2-109">Vous pouvez utiliser l'objet **ScheduledJobOptions** retourné par **New-ScheduledJobOption** pour définir des options de tâche pour une tâche planifiée nouvelle ou existante.</span><span class="sxs-lookup"><span data-stu-id="035e2-109">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set job options for a new or existing scheduled job.</span></span>
<span data-ttu-id="035e2-110">Vous pouvez également définir des options de tâche à l’aide de l’applet de commande Get-ScheduledJobOption pour obtenir les options de tâche d’une tâche planifiée existante ou à l’aide d’une valeur de table de hachage pour représenter les options du travail.</span><span class="sxs-lookup"><span data-stu-id="035e2-110">Alternatively, you can set job options by using the Get-ScheduledJobOption cmdlet to get the job options of an existing scheduled job or by using a hash table value to represent the job options.</span></span>

<span data-ttu-id="035e2-111">Sans paramètres, **New-ScheduledJobOption** génère un objet qui contient les valeurs par défaut pour toutes les options.</span><span class="sxs-lookup"><span data-stu-id="035e2-111">Without parameters, **New-ScheduledJobOption** generates an object that contains the default values for all of the options.</span></span>
<span data-ttu-id="035e2-112">Étant donné que toutes les propriétés à l'exception de la propriété JobDefinition peuvent être modifiées, vous pouvez utiliser l'objet résultant comme modèle et créer des objets d'options standard pour votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="035e2-112">Because all of the properties except for the JobDefinition property can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="035e2-113">Lors de la création de tâches planifiées et de la définition des options de tâches planifiées, examinez les valeurs par défaut de toutes les options de tâches planifiées.</span><span class="sxs-lookup"><span data-stu-id="035e2-113">When creating scheduled jobs and setting scheduled job options, review the default values of all scheduled job options.</span></span>
<span data-ttu-id="035e2-114">Les tâches planifiées sont exécutées uniquement quand toutes les conditions définies pour leur exécution sont satisfaites.</span><span class="sxs-lookup"><span data-stu-id="035e2-114">Scheduled jobs run only when all conditions set for their execution are satisfied.</span></span>

<span data-ttu-id="035e2-115">**New-ScheduledJobOption** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="035e2-115">**New-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="035e2-116">Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="035e2-116">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="035e2-117">Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="035e2-117">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="035e2-118">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="035e2-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="035e2-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="035e2-119">EXAMPLES</span></span>

### <span data-ttu-id="035e2-120">Exemple 1 : créer un objet d’option de tâche planifiée avec des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="035e2-120">Example 1: Create a scheduled job option object with default values</span></span>

```
PS C:\> New-ScheduledJobOption
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
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="035e2-121">Cette commande crée un objet d'options de tâche planifiée qui inclut toutes les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="035e2-121">This command creates a scheduled job option object that has all of the default values.</span></span>

### <span data-ttu-id="035e2-122">Exemple 2 : créer un objet d’option de tâche planifiée avec des valeurs personnalisées</span><span class="sxs-lookup"><span data-stu-id="035e2-122">Example 2: Create a scheduled job option object with custom values</span></span>

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
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
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="035e2-123">La commande suivante crée un objet de tâche planifiée qui nécessite le réseau et exécute la tâche planifiée, même si l'ordinateur n'est pas connecté à l'alimentation secteur.</span><span class="sxs-lookup"><span data-stu-id="035e2-123">The following command creates a scheduled job object that requires the network and runs the scheduled job even if the computer is not connected to AC power.</span></span>

<span data-ttu-id="035e2-124">La sortie indique que le paramètre *RequireNetwork* a modifié la valeur de la propriété RunWithoutNetwork en $false et que le paramètre *StartIfOnBattery* a modifié la valeur de la propriété StartIfOnBatteries en $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-124">The output shows that the *RequireNetwork* parameter changed the value of the RunWithoutNetwork property to $False and the *StartIfOnBattery* parameter changed the value of the StartIfOnBatteries property to $True.</span></span>

### <span data-ttu-id="035e2-125">Exemple 3 : définir les options d’une nouvelle tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="035e2-125">Example 3: Set options for a new scheduled job</span></span>

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="035e2-126">Cet exemple montre comment utiliser l'objet **ScheduledJobOptions** retourné par **New-ScheduledJobOption** pour définir les options pour une nouvelle tâche planifiée.</span><span class="sxs-lookup"><span data-stu-id="035e2-126">This example shows how to use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set the options for a new scheduled job.</span></span>

### <span data-ttu-id="035e2-127">Exemple 4 : trier les propriétés d’un objet d’option de tâche planifiée</span><span class="sxs-lookup"><span data-stu-id="035e2-127">Example 4: Sort the properties of a scheduled job option object</span></span>

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

<span data-ttu-id="035e2-128">Cet exemple montre comment trier les propriétés d'un objet **ScheduledJobOptions** par ordre alphabétique pour faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="035e2-128">This example shows how to sort the properties of a **ScheduledJobOptions** object in alphabetical order for easy reading.</span></span>

<span data-ttu-id="035e2-129">La première commande utilise l'applet de commande **New-ScheduledJobOption** pour créer un objet **ScheduledJobOptions** .</span><span class="sxs-lookup"><span data-stu-id="035e2-129">The first command uses the **New-ScheduledJobOption** cmdlet to create a **ScheduledJobOptions** object.</span></span>
<span data-ttu-id="035e2-130">La commande utilise le paramètre *WakeToRun* et enregistre l'objet résultant dans la variable $Options.</span><span class="sxs-lookup"><span data-stu-id="035e2-130">The command uses the *WakeToRun* parameter and saves the resulting object in the $Options variable.</span></span>

<span data-ttu-id="035e2-131">Pour récupérer les propriétés de $Options sous la forme d’objets, la deuxième commande utilise la propriété **PSObject** de tous les objets Windows PowerShell et de sa propriété Properties.</span><span class="sxs-lookup"><span data-stu-id="035e2-131">To get the properties of $Options as objects, the second command uses the **PSObject** property of all Windows PowerShell objects and its Properties property.</span></span>
<span data-ttu-id="035e2-132">La commande dirige ensuite les objets de propriété vers l’applet de commande Sort-Object, qui trie les propriétés par ordre alphabétique par nom, puis vers l’applet de commande Format-Table, qui affiche les noms et les valeurs des propriétés dans une table.</span><span class="sxs-lookup"><span data-stu-id="035e2-132">The command then pipes the property objects to the Sort-Object cmdlet, which sorts the properties in alphabetical order by name, and then to the Format-Table cmdlet, which displays the names and values of the properties in a table.</span></span>

<span data-ttu-id="035e2-133">Ce format facilite grandement la recherche de la propriété WakeToRun de l’objet **ScheduledJobOptions** dans $options et pour vérifier que sa valeur a été modifiée de $False à $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-133">This format makes it much easier to find the WakeToRun property of the **ScheduledJobOptions** object in $Options and to verify that its value was changed from $False to $True.</span></span>

## <span data-ttu-id="035e2-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="035e2-134">PARAMETERS</span></span>

### <span data-ttu-id="035e2-135">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="035e2-135">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="035e2-136">Ne pas arrêter la tâche planifiée si l'ordinateur passe en mode d'alimentation par batterie (se déconnecte de l'alimentation secteur) pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="035e2-136">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="035e2-137">Par défaut, les tâches planifiées s'arrêtent quand l'ordinateur se déconnecte de l'alimentation secteur.</span><span class="sxs-lookup"><span data-stu-id="035e2-137">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="035e2-138">Le paramètre *ContinueIfGoingOnBattery* définit la valeur de la propriété StopIfGoingOnBatteries des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-138">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-139">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="035e2-139">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="035e2-140">Démarrer la tâche uniquement au moment où elle est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="035e2-140">Start the job only when it is triggered.</span></span>
<span data-ttu-id="035e2-141">Les utilisateurs ne peuvent pas démarrer la tâche manuellement, notamment à l'aide de la fonctionnalité Exécuter du Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="035e2-141">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="035e2-142">Ce paramètre affecte uniquement le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="035e2-142">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="035e2-143">Il n’empêche pas les utilisateurs d’utiliser l’applet de commande Start-Job pour démarrer le travail.</span><span class="sxs-lookup"><span data-stu-id="035e2-143">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="035e2-144">Le paramètre *DoNotAllowDemandStart* définit la valeur de la propriété DoNotAllowDemandStart des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-144">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-145">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="035e2-145">-HideInTaskScheduler</span></span>
<span data-ttu-id="035e2-146">Ne pas afficher la tâche dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="035e2-146">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="035e2-147">Cette valeur affecte uniquement l'ordinateur sur lequel s'exécute la tâche.</span><span class="sxs-lookup"><span data-stu-id="035e2-147">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="035e2-148">Par défaut, les tâches planifiées apparaissent dans le Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="035e2-148">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="035e2-149">Même si une tâche est masquée, les utilisateurs peuvent afficher la tâche en sélectionnant l’option Afficher l’affichage des tâches masquées dans Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="035e2-149">Even if a task is hidden, users can display the task by selecting the Show hidden tasks view option in Task Scheduler.</span></span>

<span data-ttu-id="035e2-150">Le paramètre *HideInTaskScheduler* définit la valeur de la propriété ShowInTaskScheduler des tâches planifiées sur $false.</span><span class="sxs-lookup"><span data-stu-id="035e2-150">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="035e2-151">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="035e2-151">-IdleDuration</span></span>
<span data-ttu-id="035e2-152">Spécifie la durée pendant laquelle l'ordinateur doit être inactif avant que la tâche commence.</span><span class="sxs-lookup"><span data-stu-id="035e2-152">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="035e2-153">La valeur par défaut est 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="035e2-153">The default value is 10 minutes.</span></span>
<span data-ttu-id="035e2-154">Si l'ordinateur n'est pas inactif pendant la durée spécifiée avant l'expiration de la valeur *IdleTimeout* , la tâche planifiée ne s'exécute pas avant la prochaine planification, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="035e2-154">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="035e2-155">Entrez un objet **TimeSpan** , tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="035e2-155">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format  that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="035e2-156">Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="035e2-156">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="035e2-157">Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="035e2-157">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="035e2-158">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="035e2-158">-IdleTimeout</span></span>
<span data-ttu-id="035e2-159">Spécifie la durée pendant laquelle la tâche planifiée attend que l'ordinateur soit inactif.</span><span class="sxs-lookup"><span data-stu-id="035e2-159">Specifies how long the scheduled job waits for the computer to be idle.</span></span>
<span data-ttu-id="035e2-160">Si ce délai d'attente expire avant que l'ordinateur ne reste inactif pendant le délai spécifié par le paramètre *IdleDuration* , la tâche ne s'exécute pas jusqu'à la prochaine heure planifiée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="035e2-160">If this timeout expires before the computer remains idle for the time period that is specified by the *IdleDuration* parameter, the job does not run until the next scheduled time, if any.</span></span>
<span data-ttu-id="035e2-161">La valeur par défaut est une heure.</span><span class="sxs-lookup"><span data-stu-id="035e2-161">The default value is one hour.</span></span>

<span data-ttu-id="035e2-162">Entrez un objet **TimeSpan** , tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .</span><span class="sxs-lookup"><span data-stu-id="035e2-162">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="035e2-163">Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .</span><span class="sxs-lookup"><span data-stu-id="035e2-163">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="035e2-164">Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="035e2-164">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="035e2-165">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="035e2-165">-MultipleInstancePolicy</span></span>
<span data-ttu-id="035e2-166">Détermine comment le système répond à une demande de démarrage d'une instance d'une tâche planifiée alors qu'une autre instance de la tâche est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="035e2-166">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="035e2-167">La valeur par défaut est IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="035e2-167">The default value is IgnoreNew.</span></span>
<span data-ttu-id="035e2-168">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="035e2-168">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="035e2-169">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="035e2-169">IgnoreNew.</span></span>
<span data-ttu-id="035e2-170">La nouvelle instance de la tâche est ignorée.</span><span class="sxs-lookup"><span data-stu-id="035e2-170">The new job instance is ignored.</span></span>
- <span data-ttu-id="035e2-171">Parallel.</span><span class="sxs-lookup"><span data-stu-id="035e2-171">Parallel.</span></span>
<span data-ttu-id="035e2-172">La nouvelle instance de la tâche démarre immédiatement.</span><span class="sxs-lookup"><span data-stu-id="035e2-172">The new job instance starts immediately.</span></span>
- <span data-ttu-id="035e2-173">File d'attente.</span><span class="sxs-lookup"><span data-stu-id="035e2-173">Queue.</span></span>
<span data-ttu-id="035e2-174">La nouvelle instance de la tâche démarre dès que l'instance actuelle se termine.</span><span class="sxs-lookup"><span data-stu-id="035e2-174">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="035e2-175">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="035e2-175">StopExisting.</span></span>
<span data-ttu-id="035e2-176">L’instance actuelle du travail s’arrête et la nouvelle instance démarre.</span><span class="sxs-lookup"><span data-stu-id="035e2-176">The current instance of the job stops and the new instance starts.</span></span>

<span data-ttu-id="035e2-177">Pour exécuter la tâche, toutes les conditions de la planification des tâches doivent être remplies.</span><span class="sxs-lookup"><span data-stu-id="035e2-177">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="035e2-178">Par exemple, si les conditions définies par les paramètres *RequireNetwork* , *IdleDuration* et *IdleTimeout* ne sont pas satisfaites, l’instance de tâche n’est pas démarrée, quelle que soit la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="035e2-178">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

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

### <span data-ttu-id="035e2-179">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="035e2-179">-RequireNetwork</span></span>
<span data-ttu-id="035e2-180">Exécute la tâche planifiée uniquement quand des connexions réseau sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="035e2-180">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="035e2-181">Si vous spécifiez ce paramètre et que le réseau n'est pas disponible à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="035e2-181">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="035e2-182">Le paramètre *RequireNetwork* définit la valeur de la propriété RunWithoutNetwork des tâches planifiées sur $false.</span><span class="sxs-lookup"><span data-stu-id="035e2-182">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="035e2-183">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="035e2-183">-RestartOnIdleResume</span></span>
<span data-ttu-id="035e2-184">Redémarre une tâche planifiée quand l'ordinateur devient inactif.</span><span class="sxs-lookup"><span data-stu-id="035e2-184">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="035e2-185">Ce paramètre fonctionne avec le paramètre *StopIfGoingOffIdle* , qui interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (quitte l'état d'inactivité).</span><span class="sxs-lookup"><span data-stu-id="035e2-185">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="035e2-186">Le paramètre *RestartOnIdleResume* définit la valeur de la propriété RestartOnIdleResume des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-186">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-187">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="035e2-187">-RunElevated</span></span>
<span data-ttu-id="035e2-188">Exécute la tâche planifiée avec les autorisations d'un membre du groupe Administrateurs sur l'ordinateur sur lequel s'exécute la tâche.</span><span class="sxs-lookup"><span data-stu-id="035e2-188">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="035e2-189">Pour permettre l’exécution d’une tâche planifiée avec des autorisations d’administrateur, utilisez le paramètre *Credential* de Register-ScheduledJob pour fournir des informations d’identification explicites pour le travail.</span><span class="sxs-lookup"><span data-stu-id="035e2-189">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="035e2-190">Le paramètre *RunElevated* définit la valeur de la propriété RunElevated des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-190">The *RunElevated* parameter sets the value of the RunElevated property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-191">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="035e2-191">-StartIfIdle</span></span>
<span data-ttu-id="035e2-192">Démarre la tâche planifiée si l'ordinateur a été inactif pendant la durée spécifiée par le paramètre *IdleDuration* avant que l'heure spécifiée par le paramètre *IdleTimeout* n'expire.</span><span class="sxs-lookup"><span data-stu-id="035e2-192">Starts the scheduled job if the computer has been idle for the time specified by the *IdleDuration* parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="035e2-193">Par défaut, les paramètres *IdleDuration* et *IdleTimeout* sont ignorés et la tâche démarre à l'heure de début planifiée, même si l'ordinateur est occupé.</span><span class="sxs-lookup"><span data-stu-id="035e2-193">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="035e2-194">Si vous spécifiez ce paramètre et que l'ordinateur est occupé (non inactif) à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="035e2-194">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="035e2-195">Le paramètre *StartIfIdle* définit la valeur de la propriété StartIfNotIdle des tâches planifiées sur $false.</span><span class="sxs-lookup"><span data-stu-id="035e2-195">The *StartIfIdle* parameter sets the value of the StartIfNotIdle property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="035e2-196">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="035e2-196">-StartIfOnBattery</span></span>
<span data-ttu-id="035e2-197">Démarre la tâche planifiée, même si l'ordinateur fonctionne sur batterie à l'heure de début planifiée.</span><span class="sxs-lookup"><span data-stu-id="035e2-197">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="035e2-198">La valeur par défaut est $False.</span><span class="sxs-lookup"><span data-stu-id="035e2-198">The default value is $False.</span></span>

<span data-ttu-id="035e2-199">Le paramètre *StartIfOnBattery* définit la valeur de la propriété StartIfOnBatteries des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-199">The *StartIfOnBattery* parameter sets the value of the StartIfOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-200">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="035e2-200">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="035e2-201">Interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (non inactif) alors que la tâche est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="035e2-201">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="035e2-202">Par défaut, une tâche planifiée qui est suspendue quand l'ordinateur devient actif reprend quand il redevient inactif.</span><span class="sxs-lookup"><span data-stu-id="035e2-202">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="035e2-203">Pour modifier ce comportement par défaut, utilisez le paramètre *RestartOnIdleResume* .</span><span class="sxs-lookup"><span data-stu-id="035e2-203">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="035e2-204">Le paramètre *StopIfGoingOffIdle* définit la valeur de la propriété StopIfGoingOffIdle des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-204">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-205">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="035e2-205">-WakeToRun</span></span>
<span data-ttu-id="035e2-206">Sort l'ordinateur de son état de veille prolongée ou de veille à l'heure de début planifiée afin qu'il puisse exécuter la tâche.</span><span class="sxs-lookup"><span data-stu-id="035e2-206">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="035e2-207">Par défaut, si l'ordinateur est dans un état de veille prolongée ou de veille à l'heure de début planifiée, la tâche ne s'exécute pas.</span><span class="sxs-lookup"><span data-stu-id="035e2-207">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="035e2-208">Le paramètre *WakeToRun* définit la valeur de la propriété WakeToRun des tâches planifiées sur $true.</span><span class="sxs-lookup"><span data-stu-id="035e2-208">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="035e2-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="035e2-209">CommonParameters</span></span>
<span data-ttu-id="035e2-210">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="035e2-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="035e2-211">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="035e2-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="035e2-212">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="035e2-212">INPUTS</span></span>

### <span data-ttu-id="035e2-213">Aucun</span><span class="sxs-lookup"><span data-stu-id="035e2-213">None</span></span>
<span data-ttu-id="035e2-214">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="035e2-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="035e2-215">SORTIES</span><span class="sxs-lookup"><span data-stu-id="035e2-215">OUTPUTS</span></span>

### <span data-ttu-id="035e2-216">Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="035e2-216">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="035e2-217">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="035e2-217">NOTES</span></span>

* <span data-ttu-id="035e2-218">Vous pouvez utiliser l’objet **ScheduledJobOptions** créé par **New-ScheduledJobOption** en tant que valeur du paramètre *ScheduledJobOption* de l’applet de commande Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="035e2-218">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** creates as the value of the *ScheduledJobOption* parameter of the Register-ScheduledJob cmdlet.</span></span> <span data-ttu-id="035e2-219">Toutefois, le paramètre *ScheduledJobOption* peut également prendre une valeur de table de hachage qui spécifie les propriétés de l’objet **ScheduledJobOptions** et leurs valeurs, telles que :</span><span class="sxs-lookup"><span data-stu-id="035e2-219">However, the *ScheduledJobOption* parameter can also take a hash table value that specifies the properties of the **ScheduledJobOptions** object and their values, such as:</span></span>

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## <span data-ttu-id="035e2-220">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="035e2-220">RELATED LINKS</span></span>

[<span data-ttu-id="035e2-221">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-221">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="035e2-222">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-222">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="035e2-223">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="035e2-223">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="035e2-224">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-224">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="035e2-225">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="035e2-225">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="035e2-226">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-226">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="035e2-227">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="035e2-227">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="035e2-228">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="035e2-228">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="035e2-229">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-229">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="035e2-230">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="035e2-230">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="035e2-231">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="035e2-231">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="035e2-232">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-232">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="035e2-233">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="035e2-233">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="035e2-234">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="035e2-234">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="035e2-235">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="035e2-235">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="035e2-236">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="035e2-236">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
