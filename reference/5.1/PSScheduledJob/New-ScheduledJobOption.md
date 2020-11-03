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
# New-ScheduledJobOption

## SYNOPSIS
Crée un objet qui contient des options avancées pour une tâche planifiée.

## SYNTAX

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## Description
L'applet de commande **New-ScheduledJobOption** crée un objet qui contient des options avancées pour une tâche planifiée.

Vous pouvez utiliser l'objet **ScheduledJobOptions** retourné par **New-ScheduledJobOption** pour définir des options de tâche pour une tâche planifiée nouvelle ou existante.
Vous pouvez également définir des options de tâche à l’aide de l’applet de commande Get-ScheduledJobOption pour obtenir les options de tâche d’une tâche planifiée existante ou à l’aide d’une valeur de table de hachage pour représenter les options du travail.

Sans paramètres, **New-ScheduledJobOption** génère un objet qui contient les valeurs par défaut pour toutes les options.
Étant donné que toutes les propriétés à l'exception de la propriété JobDefinition peuvent être modifiées, vous pouvez utiliser l'objet résultant comme modèle et créer des objets d'options standard pour votre entreprise.

Lors de la création de tâches planifiées et de la définition des options de tâches planifiées, examinez les valeurs par défaut de toutes les options de tâches planifiées.
Les tâches planifiées sont exécutées uniquement quand toutes les conditions définies pour leur exécution sont satisfaites.

**New-ScheduledJobOption** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : créer un objet d’option de tâche planifiée avec des valeurs par défaut

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

Cette commande crée un objet d'options de tâche planifiée qui inclut toutes les valeurs par défaut.

### Exemple 2 : créer un objet d’option de tâche planifiée avec des valeurs personnalisées

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

La commande suivante crée un objet de tâche planifiée qui nécessite le réseau et exécute la tâche planifiée, même si l'ordinateur n'est pas connecté à l'alimentation secteur.

La sortie indique que le paramètre *RequireNetwork* a modifié la valeur de la propriété RunWithoutNetwork en $false et que le paramètre *StartIfOnBattery* a modifié la valeur de la propriété StartIfOnBatteries en $true.

### Exemple 3 : définir les options d’une nouvelle tâche planifiée

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

Cet exemple montre comment utiliser l'objet **ScheduledJobOptions** retourné par **New-ScheduledJobOption** pour définir les options pour une nouvelle tâche planifiée.

### Exemple 4 : trier les propriétés d’un objet d’option de tâche planifiée

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

Cet exemple montre comment trier les propriétés d'un objet **ScheduledJobOptions** par ordre alphabétique pour faciliter la lecture.

La première commande utilise l'applet de commande **New-ScheduledJobOption** pour créer un objet **ScheduledJobOptions** .
La commande utilise le paramètre *WakeToRun* et enregistre l'objet résultant dans la variable $Options.

Pour récupérer les propriétés de $Options sous la forme d’objets, la deuxième commande utilise la propriété **PSObject** de tous les objets Windows PowerShell et de sa propriété Properties.
La commande dirige ensuite les objets de propriété vers l’applet de commande Sort-Object, qui trie les propriétés par ordre alphabétique par nom, puis vers l’applet de commande Format-Table, qui affiche les noms et les valeurs des propriétés dans une table.

Ce format facilite grandement la recherche de la propriété WakeToRun de l’objet **ScheduledJobOptions** dans $options et pour vérifier que sa valeur a été modifiée de $False à $true.

## PARAMETERS

### -ContinueIfGoingOnBattery
Ne pas arrêter la tâche planifiée si l'ordinateur passe en mode d'alimentation par batterie (se déconnecte de l'alimentation secteur) pendant l'exécution de la tâche.
Par défaut, les tâches planifiées s'arrêtent quand l'ordinateur se déconnecte de l'alimentation secteur.

Le paramètre *ContinueIfGoingOnBattery* définit la valeur de la propriété StopIfGoingOnBatteries des tâches planifiées sur $true.

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

### -DoNotAllowDemandStart
Démarrer la tâche uniquement au moment où elle est déclenchée.
Les utilisateurs ne peuvent pas démarrer la tâche manuellement, notamment à l'aide de la fonctionnalité Exécuter du Planificateur de tâches.

Ce paramètre affecte uniquement le Planificateur de tâches.
Il n’empêche pas les utilisateurs d’utiliser l’applet de commande Start-Job pour démarrer le travail.

Le paramètre *DoNotAllowDemandStart* définit la valeur de la propriété DoNotAllowDemandStart des tâches planifiées sur $true.

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

### -HideInTaskScheduler
Ne pas afficher la tâche dans le Planificateur de tâches.
Cette valeur affecte uniquement l'ordinateur sur lequel s'exécute la tâche.
Par défaut, les tâches planifiées apparaissent dans le Planificateur de tâches.

Même si une tâche est masquée, les utilisateurs peuvent afficher la tâche en sélectionnant l’option Afficher l’affichage des tâches masquées dans Planificateur de tâches.

Le paramètre *HideInTaskScheduler* définit la valeur de la propriété ShowInTaskScheduler des tâches planifiées sur $false.

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

### -IdleDuration
Spécifie la durée pendant laquelle l'ordinateur doit être inactif avant que la tâche commence.
La valeur par défaut est 10 minutes.
Si l'ordinateur n'est pas inactif pendant la durée spécifiée avant l'expiration de la valeur *IdleTimeout* , la tâche planifiée ne s'exécute pas avant la prochaine planification, le cas échéant.

Entrez un objet **TimeSpan** , tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .

Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .
Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .

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

### -IdleTimeout
Spécifie la durée pendant laquelle la tâche planifiée attend que l'ordinateur soit inactif.
Si ce délai d'attente expire avant que l'ordinateur ne reste inactif pendant le délai spécifié par le paramètre *IdleDuration* , la tâche ne s'exécute pas jusqu'à la prochaine heure planifiée, le cas échéant.
La valeur par défaut est une heure.

Entrez un objet **TimeSpan** , tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .

Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .
Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .

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

### -MultipleInstancePolicy
Détermine comment le système répond à une demande de démarrage d'une instance d'une tâche planifiée alors qu'une autre instance de la tâche est en cours d'exécution.
La valeur par défaut est IgnoreNew.
Les valeurs valides pour ce paramètre sont :

- IgnoreNew.
La nouvelle instance de la tâche est ignorée.
- Parallel.
La nouvelle instance de la tâche démarre immédiatement.
- File d'attente.
La nouvelle instance de la tâche démarre dès que l'instance actuelle se termine.
- StopExisting.
L’instance actuelle du travail s’arrête et la nouvelle instance démarre.

Pour exécuter la tâche, toutes les conditions de la planification des tâches doivent être remplies.
Par exemple, si les conditions définies par les paramètres *RequireNetwork* , *IdleDuration* et *IdleTimeout* ne sont pas satisfaites, l’instance de tâche n’est pas démarrée, quelle que soit la valeur de ce paramètre.

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

### -RequireNetwork
Exécute la tâche planifiée uniquement quand des connexions réseau sont disponibles.

Si vous spécifiez ce paramètre et que le réseau n'est pas disponible à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.

Le paramètre *RequireNetwork* définit la valeur de la propriété RunWithoutNetwork des tâches planifiées sur $false.

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

### -RestartOnIdleResume
Redémarre une tâche planifiée quand l'ordinateur devient inactif.
Ce paramètre fonctionne avec le paramètre *StopIfGoingOffIdle* , qui interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (quitte l'état d'inactivité).

Le paramètre *RestartOnIdleResume* définit la valeur de la propriété RestartOnIdleResume des tâches planifiées sur $true.

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

### -RunElevated
Exécute la tâche planifiée avec les autorisations d'un membre du groupe Administrateurs sur l'ordinateur sur lequel s'exécute la tâche.

Pour permettre l’exécution d’une tâche planifiée avec des autorisations d’administrateur, utilisez le paramètre *Credential* de Register-ScheduledJob pour fournir des informations d’identification explicites pour le travail.

Le paramètre *RunElevated* définit la valeur de la propriété RunElevated des tâches planifiées sur $true.

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

### -StartIfIdle
Démarre la tâche planifiée si l'ordinateur a été inactif pendant la durée spécifiée par le paramètre *IdleDuration* avant que l'heure spécifiée par le paramètre *IdleTimeout* n'expire.

Par défaut, les paramètres *IdleDuration* et *IdleTimeout* sont ignorés et la tâche démarre à l'heure de début planifiée, même si l'ordinateur est occupé.

Si vous spécifiez ce paramètre et que l'ordinateur est occupé (non inactif) à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.

Le paramètre *StartIfIdle* définit la valeur de la propriété StartIfNotIdle des tâches planifiées sur $false.

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

### -StartIfOnBattery
Démarre la tâche planifiée, même si l'ordinateur fonctionne sur batterie à l'heure de début planifiée.
La valeur par défaut est $False.

Le paramètre *StartIfOnBattery* définit la valeur de la propriété StartIfOnBatteries des tâches planifiées sur $true.

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

### -StopIfGoingOffIdle
Interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (non inactif) alors que la tâche est en cours d'exécution.

Par défaut, une tâche planifiée qui est suspendue quand l'ordinateur devient actif reprend quand il redevient inactif.
Pour modifier ce comportement par défaut, utilisez le paramètre *RestartOnIdleResume* .

Le paramètre *StopIfGoingOffIdle* définit la valeur de la propriété StopIfGoingOffIdle des tâches planifiées sur $true.

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

### -WakeToRun
Sort l'ordinateur de son état de veille prolongée ou de veille à l'heure de début planifiée afin qu'il puisse exécuter la tâche.
Par défaut, si l'ordinateur est dans un état de veille prolongée ou de veille à l'heure de début planifiée, la tâche ne s'exécute pas.

Le paramètre *WakeToRun* définit la valeur de la propriété WakeToRun des tâches planifiées sur $true.

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

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions

## REMARQUES

* Vous pouvez utiliser l’objet **ScheduledJobOptions** créé par **New-ScheduledJobOption** en tant que valeur du paramètre *ScheduledJobOption* de l’applet de commande Register-ScheduledJob. Toutefois, le paramètre *ScheduledJobOption* peut également prendre une valeur de table de hachage qui spécifie les propriétés de l’objet **ScheduledJobOptions** et leurs valeurs, telles que :

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## LIENS CONNEXES

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
