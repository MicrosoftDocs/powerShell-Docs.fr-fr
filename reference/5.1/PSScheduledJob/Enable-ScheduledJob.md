---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203010"
---
# Enable-ScheduledJob

## SYNOPSIS
Active une tâche planifiée.

## SYNTAX

### Définition (par défaut)

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Dotée DefinitionId

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Enable-ScheduledJob** réactive les tâches planifiées qui sont désactivées, telles que celles qui sont désactivées à l’aide de l’applet de commande Disable-ScheduledJob.
Les tâches activées s'exécutent automatiquement quand elles sont déclenchées.

Pour activer une tâche planifiée, l’applet de commande **Enable-ScheduledJob** définit la propriété Enabled de la tâche planifiée sur $true.

**Enabled-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : activer une tâche planifiée

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

Cette commande active la tâche planifiée avec l'ID 2 sur l'ordinateur local.
La sortie illustre l'effet de la commande.

### Exemple 2 : activer toutes les tâches planifiées

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

Cette commande active toutes les tâches planifiées sur l'ordinateur local.
Elle utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées et l’applet de commande **Enable-ScheduledJob** pour les activer.

**Enable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous activez une tâche planifiée qui est déjà activée, ce qui vous permet d’activer toutes les tâches planifiées sans conditions.

### Exemple 3 : activer les tâches planifiées sélectionnées

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

Cette commande active les tâches planifiées qui ne nécessitent pas de connexion réseau.

La commande utilise l’applet de commande Get-ScheduledJob pour récupérer toutes les tâches planifiées sur l’ordinateur.
Un opérateur de pipeline envoie les tâches planifiées à l’applet de commande Get-ScheduledJobOption, qui obtient les options de chaque tâche planifiée.
Chaque objet d'options de tâche possède une propriété JobDefinition qui contient la tâche planifiée associée.
La propriété JobDefinition est utilisée pour terminer la commande.

La commande utilise un opérateur de pipeline (|) pour envoyer les options de tâche à l’applet de commande Where-Object, qui sélectionne les objets d’options de tâche planifiés dans lesquels la propriété **RunWithoutNetwork** a la valeur True ($true).
Un autre opérateur de pipeline envoie les objets d’options de tâche planifiés sélectionnés à l’applet de commande ForEach-Object qui exécute une commande **Enable-ScheduledJob** sur la tâche planifiée dans la valeur de la propriété JobDefinition de chaque objet d’options de tâche.

### Exemple 4 : activer les tâches planifiées sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

Cette commande active les tâches planifiées dont le nom contient « test » sur deux ordinateurs distants, Srv01 et Srv10.

La commande utilise l’applet de commande Invoke-Command pour exécuter une commande **Enable-ScheduledJob** sur les ordinateurs Srv01 et Srv10.
La commande utilise le paramètre *Name* de **Enable-ScheduledJob** pour activer la tâche planifiée Inventory sur chaque ordinateur.

## PARAMETERS

### -Id
Active la tâche planifiée avec le numéro d'identification (ID) spécifié.
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
Spécifie la tâche planifiée à activer.
Entrez une variable qui contient des objets **ScheduledJobDefinition** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobDefinition** , par exemple une commande Get-ScheduledJob.
Vous pouvez également diriger un objet **ScheduledJobDefinition** vers **Enable-ScheduledJob** .

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
Active les tâches planifiées avec les noms spécifiés.
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
Vous pouvez diriger une tâche planifiée vers **Enable-ScheduledJob** .

## SORTIES

### Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Si vous utilisez le paramètre **Passthru** , **Enable-ScheduledJob** retourne la tâche planifiée qui a été activée.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* **Enable-ScheduledJob** ne génère pas d’avertissements ni d’erreurs si vous l’utilisez pour activer une tâche planifiée qui est déjà activée.

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
