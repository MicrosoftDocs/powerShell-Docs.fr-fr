---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202993"
---
# Remove-JobTrigger

## SYNOPSIS
Supprimer les déclencheurs de tâche des tâches planifiées.

## SYNTAX

### JobDefinition (par défaut)

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### JobDefinitionId

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## Description
L’applet de commande **Remove-JobTrigger** supprime les déclencheurs de tâche des tâches planifiées.

Un déclencheur de tâche définit une planification ou des conditions récurrentes pour le démarrage d’une tâche planifiée.
Pour gérer les déclencheurs de tâche, utilisez les applets de commande New-JobTrigger, Add-JobTrigger, Set-JobTrigger et Set-ScheduledJob.

Utilisez les paramètres *Name* , *ID* ou *InputObject* de **Remove-JobTrigger** pour identifier les tâches planifiées desquelles les déclencheurs sont supprimés.
Utilisez le paramètre *TriggerID* pour identifier les déclencheurs de tâche à supprimer.
Par défaut, **Remove-JobTrigger** supprime tous les déclencheurs d'une tâche planifiée.

**Remove-JobTrigger** est une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : supprimer tous les déclencheurs de tâche

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

Cette commande supprime tous les déclencheurs des tâches planifiées dont le nom commence par test.

### Exemple 2 : supprimer les déclencheurs de tâche sélectionnés

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

Cette commande supprime uniquement le troisième déclencheur (ID = 3) de la tâche planifiée BackupArchive.

### Exemple 3 : supprimer les déclencheurs de tâche AtStartup de toutes les tâches planifiées

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

Cette fonction supprime tous les déclencheurs de tâche AtStartup de toutes les tâches sur l'ordinateur local.
Pour utiliser la fonction, exécutez-la dans votre session, puis tapez `Delete-AtStartup` .

La fonction Delete-AtStartup contient une seule commande.
La commande utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.
Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande Get-JobTrigger, qui obtient tous les déclencheurs de tâche à partir de chacune des tâches planifiées.
Un opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object, qui sélectionne les déclencheurs de tâche où la valeur de la propriété Frequency du déclencheur de tâche est égale à AtStartup.

Les objets **JobTrigger** ont une propriété **JobDefinition** qui contient la tâche planifiée qu’ils déclenchent.
Le reste de la commande utilise cette précieuse fonctionnalité.

Un opérateur de pipeline envoie les déclencheurs de tâche AtStartup à l’applet de commande ForEach-Object, qui exécute une commande **Remove-JobTrigger** sur chaque déclencheur AtStartup.
La valeur du paramètre *InputObject* de **Remove-JobTrigger** est la tâche planifiée dans la propriété JobDefinition du déclencheur de tâche.
La valeur du paramètre *TriggerID* est l'identificateur dans la propriété ID du déclencheur de tâche.

### Exemple 4 : supprimer un déclencheur d’une tâche planifiée à distance

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

Cette commande supprime le premier déclencheur de tâche de la tâche Inventory sur l'ordinateur Server01.

La commande utilise l’applet de commande **Invoke-Command** pour exécuter l’applet de commande **Remove-JobTrigger** sur l’ordinateur SERVEUR01.
L’applet de commande **Remove-JobTrigger** utilise le paramètre *ID* pour identifier la tâche planifiée Inventory et le paramètre *TriggerID* pour spécifier le premier déclencheur.
Le paramètre *ID* est particulièrement utile quand plusieurs tâches planifiées ont des noms identiques ou similaires.

## PARAMETERS

### -Id
Spécifie les numéros d'identification des tâches planifiées.
**Remove-JobTrigger** supprime les déclencheurs des tâches planifiées spécifiées.

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
Vous pouvez également diriger les objets **ScheduledJob** vers **Remove-JobTrigger** .

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
**Remove-JobTrigger** supprime les déclencheurs des tâches planifiées spécifiées.
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

### -TriggerId
Supprime uniquement les déclencheurs de tâche spécifiés.
Par défaut, **Remove-JobTrigger** supprime tous les déclencheurs des tâches planifiées.
Utilisez ce paramètre quand les tâches planifiées ont plusieurs déclencheurs de tâche.

Entrez les ID d'un ou de plusieurs déclencheurs de tâche d'une tâche planifiée.
Si vous spécifiez plusieurs tâches planifiées, **Remove-JobTrigger** supprime le déclencheur de tâche avec l’ID spécifié de toutes les tâches planifiées.

```yaml
Type: System.Int32[]
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez diriger les tâches planifiées vers l'applet de commande **Remove-JobTrigger** .

## SORTIES

### Aucun
L'applet de commande ne génère pas de résultat.

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
