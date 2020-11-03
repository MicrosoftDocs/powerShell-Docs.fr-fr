---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203025"
---
# Disable-ScheduledJob

## SYNOPSIS
Désactive une tâche planifiée.

## SYNTAX

### Définition (par défaut)

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Dotée DefinitionId

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L'applet de commande **Disable-ScheduledJob** désactive temporairement les tâches planifiées.
La désactivation conserve toutes les propriétés des tâches et ne désactive pas les déclencheurs de tâche, mais elle empêche les tâches planifiées de démarrer automatiquement lors du déclenchement.
Vous pouvez démarrer une tâche planifiée désactivée à l’aide de l’applet de commande Start-Job ou utiliser une tâche planifiée désactivée comme modèle.

Pour désactiver une tâche planifiée, l'applet de commande **Disable-ScheduledJob** affecte à la propriété **Enabled** de la tâche planifiée la valeur False ($false).
Pour réactiver la tâche planifiée, utilisez l’applet de commande Enable-ScheduledJob.

**Disable-ScheduledJob** est une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : désactiver une tâche planifiée

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

Cette commande désactive la tâche planifiée avec l'ID 2 sur l'ordinateur local.
La sortie illustre l'effet de la commande.

### Exemple 2 : désactiver toutes les tâches planifiées

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

Cette commande désactive toutes les tâches planifiées sur l'ordinateur local.
Elle utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées et l’applet de commande **Disable-ScheduledJob** pour les désactiver.

Vous pouvez réactiver la tâche planifiée à l’aide de l’applet de commande Enable-ScheduledJob et exécuter une tâche planifiée désactivée à l’aide de l’applet de commande Start-Job.

**Disable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous désactivez une tâche planifiée qui est déjà désactivée, de sorte que vous pouvez désactiver toutes les tâches planifiées sans conditions.

### Exemple 3 : désactiver les tâches planifiées sélectionnées

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

Cette commande désactive une tâche planifiée sans informations d'identification.
Les tâches sans informations d'identification s'exécutent avec l'autorisation de l'utilisateur qui les a créées.

La commande utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur.
Un opérateur de pipeline envoie les tâches planifiées à l’applet de commande Where-Object, qui sélectionne les tâches planifiées qui n’ont pas d’informations d’identification.
La commande utilise l'opérateur not (!) et fait référence à la propriété Credential de la tâche planifiée.
Un autre opérateur pipeline envoie les tâches planifiées sélectionnées à l'applet de commande **Disable-ScheduledJob** , qui les désactive.

### Exemple 4 : désactiver les tâches planifiées sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

Cette commande désactive la tâche planifiée TestJob sur deux ordinateurs distants, Srv01 et Srv10.

La commande utilise l’applet de commande Invoke-Command pour exécuter une commande **Disable-ScheduledJob** sur les ordinateurs Srv01 et Srv10.
La commande utilise le paramètre *Name* de **Disable-ScheduledJob** pour sélectionner la tâche planifiée TestJob sur chaque ordinateur.

### Exemple 5 : désactiver une tâche planifiée par son ID global

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

Cet exemple montre comment désactiver une tâche planifiée à l'aide de son identificateur global.
La valeur de la propriété GlobalID d'une tâche planifiée est un identificateur unique (GUID).
Utilisez la valeur GlobalID quand la précision est requise, par exemple quand vous désactivez des tâches planifiées sur plusieurs ordinateurs.

## PARAMETERS

### -Id
Désactive la tâche planifiée avec le numéro d'identification (ID) spécifié.
Entrez l'ID d'une tâche planifiée.

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie la tâche planifiée à désactiver.
Entrez une variable qui contient des objets  **ScheduledJobDefinition** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobDefinition** , par exemple une commande Get-ScheduledJob.
Vous pouvez également diriger un objet **ScheduledJobDefinition** vers **Disable-ScheduledJob** .

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Désactive les tâches planifiées avec les noms spécifiés.
Entrez le nom d'une tâche planifiée.
Les caractères génériques sont pris en charge.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez acheminer par canal une tâche planifiée vers **Disable-ScheduledJob** .

## SORTIES

### Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Si vous utilisez le paramètre **Passthru** , **Disable-ScheduledJob** retourne la tâche planifiée qui a été désactivée.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* **Disable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous l’utilisez pour désactiver une tâche planifiée qui est déjà désactivée.

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
