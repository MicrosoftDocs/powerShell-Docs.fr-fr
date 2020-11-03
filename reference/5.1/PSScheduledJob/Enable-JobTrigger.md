---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203009"
---
# Enable-JobTrigger

## SYNOPSIS
Active les déclencheurs des tâches planifiées.

## SYNTAX

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Enable-JobTrigger** réactive les déclencheurs des tâches planifiées, telles que celles qui ont été désactivées à l’aide de l’applet de commande Disable-JobTrigger.
Les déclencheurs de tâche activés et réactivés peuvent démarrer des tâches planifiées immédiatement ; il est inutile de redémarrer Windows ou Windows PowerShell.

Pour utiliser cette applet de commande, utilisez l’applet de commande Get-JobTrigger pour récupérer les déclencheurs de tâche.
Ensuite, dirigez les déclencheurs de tâche vers **Enable-JobTrigger** ou utilisez son paramètre *InputObject* .

Pour activer un déclencheur de tâche, l’applet de commande **Enable-JobTrigger** affecte la valeur $true à la propriété Enabled du déclencheur de tâche.

**Enable-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : activer un déclencheur de tâche

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

Cette commande active le premier déclencheur (ID=1) de la tâche planifiée Backup-Archives sur l'ordinateur local.

La commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de tâche.
Un opérateur pipeline envoie le déclencheur de tâche à l'applet de commande **Enable-JobTrigger** , qui l'active.

### Exemple 2 : activer tous les déclencheurs de tâche

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

La commande utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.
Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande Get-JobTrigger, qui obtient tous les déclencheurs de tâche des tâches planifiées.
Un autre opérateur pipeline envoie les déclencheurs de tâche à l'applet de commande **Enable-JobTrigger** , qui les active.

### Exemple 3 : activer le déclencheur d’une tâche planifiée sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

Cette commande réactive les déclencheurs de tâche AtLogon sur la tâche planifiée DeployPackage sur l'ordinateur distant Server01.

La commande utilise l’applet de commande Invoke-Command pour exécuter les commandes sur l’ordinateur SERVEUR01.
La commande distante utilise l’applet de commande Get-JobTrigger pour recevoir les déclencheurs de la tâche planifiée DeployPackage.
Un opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object qui retourne uniquement les déclencheurs de tâche AtLogon.
Un opérateur de pipeline envoie les déclencheurs de tâche AtLogon à l’applet de commande **Enable-JobTrigger** , qui les active.

### Exemple 4 : afficher les déclencheurs de tâche désactivée

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

Cette commande affiche tous les déclencheurs de tâche désactivés de toutes les tâches planifiées dans une table.
Vous pouvez utiliser une commande similaire à celle-ci pour découvrir les déclencheurs de tâche qui doivent peut-être être activés.

La commande utilise l’applet de commande Get-ScheduledJob pour récupérer les tâches planifiées sur l’ordinateur local.
Un opérateur de pipeline (|) envoie les tâches planifiées à l’applet de commande Get-JobTrigger, qui obtient tous les déclencheurs de tâche des tâches planifiées.
Un autre opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object, qui retourne uniquement les déclencheurs de tâche qui sont désactivés, autrement dit, où la valeur de la propriété Enabled du déclencheur de tâche n’est pas ( !) true.

Un autre opérateur de pipeline envoie les déclencheurs de tâche désactivée à l’applet de commande Format-Table, qui affiche les propriétés sélectionnées des déclencheurs de tâche dans une table.
Les propriétés incluent une nouvelle propriété JobName qui affiche le nom de la tâche planifiée dans la propriété JobDefinition du déclencheur.

## PARAMETERS

### -InputObject
Spécifie le déclencheur de tâche à activer.
Entrez une variable qui contient des objets **ScheduledJobTrigger** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.
Vous pouvez également diriger un objet **ScheduledJobTrigger** vers **Enable-JobTrigger** .

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

### -PassThru
Retourne un objet représentant l’élément que vous utilisez.
Par défaut, cette applet de commande ne génère aucun résultat.

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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger
Vous pouvez diriger les déclencheurs de tâche vers **Enable-JobTrigger** .

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* **Enable-JobTrigger** ne génère pas d’erreurs ou d’avertissements si vous activez un déclencheur de tâche qui est déjà activé.

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
