---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203005"
---
# Get-ScheduledJob

## SYNOPSIS
Obtient les tâches planifiées sur l'ordinateur local.

## SYNTAX

### Dotée DefinitionId (par défaut)

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### DefinitionName

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## Description
L'applet de commande **Get-ScheduledJob** obtient les tâches planifiées sur l'ordinateur local.
La commande **ScheduledJob** obtient uniquement les tâches planifiées qui sont créées par l’utilisateur actuel à l’aide de l’applet de commande Register-ScheduledJob.

Même si les tâches qui sont créées à l'aide de l'applet de commande **Register-ScheduledJob** s'affichent dans le Planificateur de tâches, **Get-ScheduledJob** obtient uniquement les tâches planifiées.
Elle n'obtient pas les tâches planifiées créées dans le Planificateur de tâches.

Sans paramètres, **Get-ScheduledJob** obtient toutes les tâches planifiées sur l'ordinateur.
Vous pouvez utiliser les paramètres de **Get-ScheduledJob** pour obtenir les tâches planifiées par ID ou nom et les examiner ou les diriger vers d'autres applets de commande.

L’applet de commande **ScheduledJob** est une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : récupération de tous les travaux planifiés

```
PS C:\> Get-ScheduledJob
```

Cette commande obtient toutes les tâches planifiées sur l'ordinateur local.

### Exemple 2 : recevoir les tâches planifiées par nom

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

Cette commande obtient toutes les tâches planifiées sur l’ordinateur dont les noms incluent la sauvegarde ou l’archivage.
Ce format de commande vous permet de rechercher des tâches spécifiques.

### Exemple 3 : récupération de tâches planifiées sur des ordinateurs distants

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

Cette commande obtient toutes les tâches planifiées sur les ordinateurs qui sont répertoriés dans le fichier Servers.txt.
La commande utilise l’applet de commande Invoke-Command pour exécuter une commande **obtenir-ScheduleJob** sur chaque ordinateur.

### Exemple 4 : effectuer un canal des tâches planifiées vers d’autres applets de commande

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

Cette commande obtient les déclencheurs des tâches planifiées DailyBackup et WeeklyBackup.
Elle utilise l’applet de commande **ScheduledJob** pour récupérer les tâches planifiées et l’applet de commande Get-JobTrigger pour recevoir les déclencheurs des tâches planifiées.

## PARAMETERS

### -Id
Obtient uniquement les tâches planifiées avec le numéro d'identification (ID) spécifié.
Entrez un ou plusieurs ID de tâches planifiées sur l'ordinateur.
Par défaut, **Get-ScheduledJob** obtient toutes les tâches planifiées sur l'ordinateur.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Obtient uniquement les tâches planifiées avec les noms spécifiés.
Entrez un ou plusieurs noms de tâches planifiées sur l'ordinateur.
Les caractères génériques sont pris en charge.
Par défaut, **Get-ScheduledJob** obtient toutes les tâches planifiées sur l'ordinateur.

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d’entrée vers **ScheduledJob** .

## SORTIES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition

## REMARQUES

* Chaque tâche planifiée est enregistrée dans un sous-répertoire du répertoire $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs sur l'ordinateur local. Le sous-répertoire est nommé pour la tâche planifiée et contient le fichier XML pour cette tâche et les enregistrements de son historique d'exécution. Pour plus d'informations sur les tâches planifiées sur disque, consultez about_Scheduled_Jobs_Advanced.
* Les tâches planifiées que vous créez dans Windows PowerShell apparaissent dans le Planificateur de tâches dans le dossier Library\Microsoft\Windows\PowerShell\ScheduledJobs. Vous pouvez utiliser le Planificateur de tâches pour afficher et modifier la tâche planifiée.
* Vous pouvez utiliser le Planificateur de tâches, l'outil en ligne de commande SchTasks.exe et les applets de commande du Planificateur de tâches pour gérer les tâches planifiées que vous créez avec les applets de commande correspondantes. Toutefois, vous ne pouvez pas utiliser les applets de commande de la tâche planifiée pour gérer les tâches que vous créez dans le Planificateur de tâches.

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
