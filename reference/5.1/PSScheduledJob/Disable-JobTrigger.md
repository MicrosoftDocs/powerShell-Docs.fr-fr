---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203033"
---
# Disable-JobTrigger

## SYNOPSIS
Désactive les déclencheurs des tâches planifiées.

## SYNTAX

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L'applet de commande **Disable-JobTrigger** désactive temporairement les déclencheurs des tâches planifiées.
La désactivation conserve toutes les propriétés de déclencheur de tâche, mais l'empêche de démarrer la tâche planifiée.

Pour utiliser cette applet de commande, utilisez l’applet de commande Get-JobTrigger pour récupérer les déclencheurs de tâche.
Ensuite, dirigez les déclencheurs de tâche vers **Disable-JobTrigger** ou utilisez son paramètre *InputObject* .

Pour désactiver un déclencheur de tâche, l’applet de commande **Disable-JobTrigger** affecte la valeur $false à la propriété Enabled du déclencheur de tâche.
Pour réactiver le déclencheur de tâche, utilisez l’applet de commande Enable-JobTrigger, qui définit la propriété **Enabled** du déclencheur sur $true.
La désactivation d’un déclencheur de tâche ne désactive pas la tâche planifiée, comme c’est le cas par l’applet de commande Disable-ScheduledJob, mais si vous désactivez tous les déclencheurs de tâche, l’effet est identique à la désactivation de la tâche planifiée.

Si vous désactivez une tâche planifiée ou désactivez tous les déclencheurs d’une tâche planifiée, vous pouvez toujours démarrer la tâche à l’aide de l’applet de commande Start-Job ou utiliser la tâche planifiée désactivée comme modèle.

**Disable-ScheduledJob** est une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : désactiver un déclencheur de tâche

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

Cette commande désactive le premier déclencheur (ID=1) de la tâche planifiée Backup-Archives sur l'ordinateur local.

La commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de tâche.
Un opérateur pipeline envoie le déclencheur de tâche à l'applet de commande **Disable-JobTrigger** , qui le désactive.

### Exemple 2 : désactiver tous les déclencheurs de tâche

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

Ces commandes désactivent tous les déclencheurs de tâche sur deux tâches planifiées et affichent les résultats.

### Exemple 3 : désactiver le déclencheur de tâche d’une tâche planifiée sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

Cette commande désactive les déclencheurs de tâche quotidienne sur la tâche planifiée DeployPackage sur l'ordinateur distant Server01.

La commande utilise l’applet de commande Invoke-Command pour exécuter les commandes sur l’ordinateur SERVEUR01.
La commande distante utilise l’applet de commande Get-JobTrigger pour recevoir les déclencheurs de la tâche planifiée DeployPackage.
Un opérateur de pipeline envoie les déclencheurs de tâche à l’applet de commande Where-Object, qui retourne uniquement les déclencheurs de tâche quotidiens.
Un opérateur de pipeline envoie les déclencheurs de tâche quotidienne à l’applet de commande **Disable-JobTrigger** , qui les désactive.

## PARAMETERS

### -InputObject
Spécifie le déclencheur de tâche à désactiver.
Entrez une variable qui contient des objets  **ScheduledJobTrigger** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.
Vous pouvez également diriger un objet **ScheduledJobTrigger** vers **Disable-JobTrigger** .

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
Vous pouvez diriger les déclencheurs de tâche vers **Disable-JobTrigger** .

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* **Disable-JobTrigger** ne génère pas d’erreurs ou d’avertissements si vous désactivez un déclencheur de tâche qui est déjà désactivé.

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
