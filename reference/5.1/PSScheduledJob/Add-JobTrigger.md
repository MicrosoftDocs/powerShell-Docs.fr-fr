---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203034"
---
# Add-JobTrigger

## SYNOPSIS
Ajoute des déclencheurs aux tâches planifiées.

## SYNTAX

### JobDefinition (par défaut)

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### JobDefinitionId

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## Description
L'applet de commande **Add-JobTrigger** ajoute des déclencheurs aux tâches planifiées.
Vous pouvez l'utiliser pour ajouter plusieurs déclencheurs à plusieurs tâches planifiées.

Un déclencheur de tâche démarre une tâche planifiée selon une planification ponctuelle ou périodique, ou quand un événement se produit.

Utilisez le paramètre *Trigger* de **Add-JobTrigger** pour identifier les déclencheurs de tâche à ajouter.
Utilisez les paramètres *Name* , *ID* ou *InputObject* de **Add-JobTrigger** pour identifier la tâche planifiée à laquelle les déclencheurs sont ajoutés.

Pour créer des déclencheurs de tâche pour la valeur du paramètre *Trigger* , utilisez l’applet de commande New-JobTrigger ou utilisez une table de hachage pour spécifier le déclencheur de tâche.

**Add-JobTrigger** fait partie d’une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : ajouter un déclencheur de tâche à une tâche planifiée

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

Ces commandes ajoutent le déclencheur Daily à la tâche planifiée TestJob.

La première commande utilise l’applet de commande New-JobTrigger pour créer un déclencheur de tâche qui démarre une tâche planifiée tous les jours à 3:00 h 00.
La commande enregistre le déclencheur de tâche dans la variable $Daily.

La deuxième commande utilise l'applet de commande **Add-JobTrigger** pour ajouter le déclencheur de tâche de la variable $Startup à la tâche planifiée TestJob.

### Exemple 2 : ajout d’un déclencheur de tâche à plusieurs tâches planifiées

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

Cette commande ajoute un déclencheur de tâche AtStartup à toutes les tâches planifiées sur l'ordinateur local.
Il utilise la Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur.
Elle utilise un opérateur pipeline (|) pour envoyer les tâches à l'applet de commande **Add-JobTrigger** , qui ajoute le déclencheur à chacune des tâches planifiées.
La valeur du paramètre *Trigger* est une commande New-JobTrigger qui crée le déclencheur de tâche AtStartup.

### Exemple 3 : copier un déclencheur de tâche

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

Ces commandes copient le déclencheur de tâche de la tâche planifiée BackupArchives et l'ajoutent aux tâches planifiées TestBackup et BackupLogs.

La première commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de la tâche planifiée BackupArchives.
La commande enregistre le déclencheur dans la variable $t.

La deuxième commande utilise l'applet de commande **Add-JobTrigger** pour ajouter le déclencheur de tâche dans $t aux tâches planifiées TestBackup et BackupLogs.

## PARAMETERS

### -Id
Spécifie les numéros d'identification des tâches planifiées.
**Add-JobTrigger** ajoute les déclencheurs aux tâches planifiées spécifiées.

Pour obtenir le numéro d’identification des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie les tâches planifiées.
Entrez une variable qui contient des objets **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.
Vous pouvez également diriger les objets **ScheduledJob** vers **Add-JobTrigger** .

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
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
**Add-JobTrigger** ajoute les déclencheurs aux tâches planifiées spécifiées.
Les caractères génériques sont pris en charge.

Pour obtenir les noms des tâches planifiées sur l’ordinateur local ou sur un ordinateur distant, utilisez l’applet de commande Get-ScheduledJob.

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Déclencheur
Spécifie les déclencheurs de tâche à ajouter.
Entrez une table de hachage qui spécifie les déclencheurs de tâche ou une variable qui contient des objets **ScheduledJobTrigger** , ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.
Vous pouvez également diriger les objets **ScheduledJobTrigger** vers **Add-JobTrigger** .

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger, Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez diriger des déclencheurs de tâche ou des tâches planifiées vers **Add-JobTrigger** .

## SORTIES

### Aucun
Cette applet de commande ne retourne aucune sortie.

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
