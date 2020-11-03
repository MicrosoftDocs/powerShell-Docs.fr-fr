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
# Get-JobTrigger

## SYNOPSIS
Obtient les déclencheurs des tâches planifiées.

## SYNTAX

### JobDefinition (par défaut)

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## Description
L'applet de commande **Get-JobTrigger** obtient les déclencheurs des tâches planifiées.
Vous pouvez utiliser cette commande pour examiner les déclencheurs de tâche ou pour les diriger vers d'autres applets de commande.

Un déclencheur de tâche définit une planification ou des conditions récurrentes pour le démarrage d’une tâche planifiée.
Les déclencheurs de tâche ne sont pas enregistrés sur le disque de manière indépendante ; ils font partie d'une tâche planifiée.
Pour obtenir un déclencheur de tâche, spécifiez la tâche planifiée que le déclencheur démarre.

Utilisez les paramètres de l'applet de commande **Get-JobTrigger** pour identifier les tâches planifiées.
Vous pouvez identifier les tâches planifiées par leur nom ou numéro d’identification, ou en entrant ou en canalisant des objets **ScheduledJob** , tels que ceux retournés par l’applet de commande Get-ScheduledJob, à la commande **JobTrigger** .

L’applet de commande **JobTrigger** est une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : obtenir un déclencheur de tâche par nom de tâche planifiée

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

La commande utilise le paramètre *Name* de la commande **JobTrigger** pour recevoir les déclencheurs de la tâche planifiée BackupJob.

### Exemple 2 : obtenir un déclencheur de tâche par ID

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

L’exemple utilise le paramètre *ID* de la fonction **JobTrigger** pour obtenir les déclencheurs d’une tâche planifiée.

### Exemple 3 : obtenir des déclencheurs de tâche en canalisant un travail

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

Cette commande obtient les déclencheurs de toutes les tâches dont le nom contient la sauvegarde ou l’archive.

### Exemple 4 : obtenir le déclencheur d’un travail sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

Cette commande obtient l'un des deux déclencheurs d'une tâche planifiée sur un ordinateur distant.

La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur SERVEUR01.
Elle utilise l’applet de commande Get-ScheduledJob pour récupérer la tâche planifiée Backup, qu’elle dirige vers l’applet de commande **JobTrigger** .
Elle utilise le paramètre *TriggerID* pour récupérer uniquement le second déclencheur.

### Exemple 5 : récupération de tous les déclencheurs de tâche

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

Cette commande obtient tous les déclencheurs de toutes les tâches planifiées sur l'ordinateur local.

La commande utilise la Get-ScheduledJob pour obtenir les tâches planifiées sur l’ordinateur local et les dirige vers la commande **JobTrigger** , qui obtient le déclencheur de chaque tâche planifiée (le cas échéant).

Pour ajouter le nom de la tâche planifiée à l’affichage du déclencheur de tâche, la commande utilise la fonctionnalité de propriété calculée de l’applet de commande Format-Table.
Outre les propriétés de déclencheur de tâche qui sont affichées par défaut, la commande crée une nouvelle propriété ScheduledJob qui affiche le nom de la tâche planifiée.

### Exemple 6 : obtenir la propriété de déclencheur de tâche d’une tâche planifiée

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

Les déclencheurs d'une tâche planifiée sont stockés dans la propriété JobTriggers de la tâche.
Cet exemple montre des alternatives à l’utilisation de l’applet de commande **JobTrigger** pour récupérer les déclencheurs de tâche.
Les résultats sont identiques à l'utilisation de l'applet de commande **Get-JobTrigger** et les techniques peuvent être utilisées indifféremment.

### Exemple 7 : comparer les déclencheurs de tâche

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

Cet exemple montre comment comparer les déclencheurs de deux tâches planifiées.

## PARAMETERS

### -Id
Spécifie le numéro d'identification d'une tâche planifiée.
**Get-JobTrigger** obtient le déclencheur de la tâche planifiée spécifiée.

Pour obtenir le numéro d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.

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
Entrez une variable qui contient des objets  **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.
Vous pouvez également diriger les objets **ScheduledJob** vers la **JobTrigger** .

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
Spécifie le nom d'une tâche planifiée.
**Get-JobTrigger** obtient le déclencheur de la tâche planifiée spécifiée.
Les caractères génériques sont pris en charge.

Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.

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

### -TriggerId
Obtient les déclencheurs de tâche spécifiés.
Entrez les ID d'un ou de plusieurs déclencheurs de tâche d'une tâche planifiée.
Utilisez ce paramètre quand la tâche planifiée qui est spécifiée par les paramètres *Name* , *ID* ou *InputObject* possède plusieurs déclencheurs de tâche.

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

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez diriger une tâche planifiée à partir de Get-ScheduledJob vers **JobTrigger** .

## SORTIES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger

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
