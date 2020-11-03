---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203001"
---
# Get-ScheduledJobOption

## SYNOPSIS
Obtient les options de tâche des tâches planifiées.

## SYNTAX

### JobDefinition (par défaut)

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-ScheduledJobOption** obtient les options de tâche des tâches planifiées.
Vous pouvez utiliser cette commande pour examiner les options de tâche ou pour les diriger vers d'autres applets de commande.

Les options de tâche ne sont pas enregistrées sur le disque de manière indépendante ; elles font partie d'une tâche planifiée.
Pour obtenir les options d'une tâche planifiée, indiquez la tâche planifiée.

Utilisez les paramètres de l'applet de commande **Get-ScheduledJobOption** pour identifier la tâche planifiée.
Vous pouvez identifier les tâches planifiées par leur nom ou leur numéro d’identification, ou en entrant ou en canalisant des objets **ScheduledJob** , tels que ceux retournés par l’applet de commande Get-ScheduledJob, sur **ScheduledJobOption** .

L’applet de commande **ScheduledJobOption** est une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : options d’extraction de tâche

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
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

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Cette commande obtient les options de tâche des tâches planifiées dont le nom contient BackUp.
Les résultats affichent l'objet d'options de tâche retourné par **Get-ScheduledJobOption** .

### Exemple 2 : récupération de toutes les options de tâche

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

Cette commande obtient les options de toutes les tâches planifiées sur l'ordinateur local.

Elle utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.
Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande **ScheduledJobOption** , qui obtient les options de chaque tâche planifiée.

### Exemple 3 : récupérer les options de la tâche sélectionnée

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

Cet exemple montre comment rechercher l'objet d'options de tâche avec des valeurs particulières.

La première commande obtient les options de travail dans lesquelles la propriété RunElevated a la valeur $True et la propriété RunWithoutNetwork a la valeur $False.
La sortie indique l’objet **JobOptions** qui a été sélectionné.

### Exemple 4 : utiliser des options de tâche pour créer une tâche

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

Cet exemple montre comment utiliser les options de tâche que Get-ScheduledJobOption obtient dans une nouvelle tâche planifiée.

La première commande utilise la commande **ScheduledJobOption** pour accéder aux options de tâches de la tâche planifiée BackupTestLogs.
La commande enregistre les options dans la variable $Opts.

La deuxième commande utilise Register-ScheduledJob applet de commande pour créer une nouvelle tâche planifiée.
La valeur du paramètre *ScheduledJobOption* est l'objet d'options dans la variable $Opts.

### Exemple 5 : obtenir les options d’un travail à partir d’un ordinateur distant

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

Cette commande utilise l’applet de commande Invoke-Command pour accéder aux options de tâche planifiée de la tâche DataDemon sur l’ordinateur Srv01.
La commande enregistre les options dans la variable $O.

## PARAMETERS

### -Id
Spécifie le numéro d'identification d'une tâche planifiée.
**Get-ScheduledJobOption** obtient les options de la tâche planifiée spécifiée.

Pour obtenir les numéros d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.

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

### -InputObject
Spécifie une tâche planifiée.
Entrez une variable qui contient un objet **ScheduledJob** ou tapez une commande ou une expression qui obtient un objet **ScheduledJob** , tel qu’une commande Get-ScheduledJob.
Vous pouvez également acheminer par canal un objet **ScheduledJob** vers **Get-ScheduledJobOption** .

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

### -Name
Spécifie les noms des tâches planifiées.
**Get-ScheduledJobOption** obtient les options de la tâche planifiée spécifiée.
Les caractères génériques sont pris en charge.

Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez diriger une tâche planifiée à partir de Get-ScheduledJob vers **ScheduledJobOption** .

## SORTIES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions

## REMARQUES

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
