---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202973"
---
# Unregister-ScheduledJob

## SYNOPSIS
Supprime les tâches planifiées de l'ordinateur local.

## SYNTAX

### Définition (par défaut)

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Dotée DefinitionId

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L'applet de commande **Unregister-ScheduledJob** supprime les tâches planifiées de l'ordinateur local.

Lorsqu’il supprime ou annule l’inscription d’une tâche planifiée, **Unregister-ScheduledJob** supprime le répertoire de la tâche planifiée (dans le répertoire $home \appdata\local\microsoft\windows\powershell\scheduledjobs), qui contient le fichier XML qui définit la tâche planifiée, l’historique d’exécution du travail et tous les résultats de la tâche.
Cette action supprime également la tâche du Planificateur de tâches.

**Unregister-ScheduledJob** supprime uniquement les tâches planifiées qui sont créées à l’aide de l’applet de commande Register-ScheduledJob.
Elle ne supprime pas les tâches planifiées qui sont créées dans le Planificateur de tâches.

Vous pouvez utiliser les paramètres de **Unregister-ScheduledJob** pour supprimer les tâches planifiées par ID ou par nom, ou les tâches planifiées de canal de Get-ScheduledJob à **Unregister-ScheduledJob** .

**Unregister-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : supprimer une tâche planifiée

```
PS C:\> Unregister-ScheduledJob TestJob
```

Cette commande supprime la tâche planifiée TestJob sur l'ordinateur local.

### Exemple 2 : supprimer tous les travaux planifiés

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

Cet exemple montre deux commandes différentes qui suppriment toutes les tâches planifiées sur l’ordinateur local.

La première commande utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur local.
Un opérateur pipeline (|) envoie les tâches planifiées vers **Unregister-ScheduleJob** , qui les supprime.

La deuxième commande utilise le paramètre *Name* de **Unregister-ScheduledJob** avec la valeur toutes les (*) pour supprimer toutes les tâches planifiées.

Les deux commandes utilisent le paramètre *Force* , qui supprime une tâche planifiée, même si une instance de la tâche est en cours d'exécution.

### Exemple 3 : supprimer une tâche planifiée sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

Cette commande supprime les tâches planifiées dont le nom commence par test sur l’ordinateur distant SERVEUR01.
La commande utilise l’applet de commande Invoke-Command pour exécuter la commande **Unregister-ScheduledJob** sur l’ordinateur Server02.

## PARAMETERS

### -Force
Supprime la tâche planifiée même si une instance de la tâche est en cours d'exécution.
Par défaut, **Unregister-ScheduledJob** n'interrompt pas les tâches en cours d'exécution.

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

### -Id
Supprime les tâches planifiées avec les numéros d'identification (ID) spécifiés.
Entrez les ID des tâches planifiées sur l'ordinateur.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie une tâche planifiée.
Entrez une variable qui contient des objets **ScheduledJob** ou tapez une commande ou une expression qui obtient des objets **ScheduledJob** , par exemple une commande Get-ScheduledJob.
Vous pouvez également diriger les objets **ScheduledJob** vers **Unregister-JobTrigger** .

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Supprime les tâches planifiées avec les noms spécifiés.
Entrez le nom d'une ou de plusieurs tâches planifiées sur l'ordinateur.
Les caractères génériques sont pris en charge.

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

### -Confirm
Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez diriger les tâches planifiées vers Unregister-ScheduledJob

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

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
