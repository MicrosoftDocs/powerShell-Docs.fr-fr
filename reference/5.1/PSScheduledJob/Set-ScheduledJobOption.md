---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202974"
---
# Set-ScheduledJobOption

## SYNOPSIS
Modifie les options d'une tâche planifiée.

## SYNTAX

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## Description
L'applet de commande **Set-ScheduledJobOptions** modifie les options de tâche des tâches planifiées.

Pour modifier les options d’une tâche planifiée, commencez par utiliser l’applet de commande Get-ScheduledJobOption pour obtenir les options de tâche d’une tâche planifiée.
Ensuite, dirigez les options vers **Set-ScheduledJobOption** ou enregistrez-les dans une variable et utilisez le paramètre *InputObject* de l'applet de commande **Set-ScheduledJobOption** pour identifier les options.
Utilisez les paramètres restants de **Set-ScheduledJobOption** pour modifier les options de tâche.

Pour activer une option de tâche, utilisez le paramètre qui définit cette option.
Pour désactiver une option, tapez le nom du paramètre, un signe deux-points ( :) et $False.
Par exemple, pour désactiver l’option *RunElevated* , tapez `-RunElevated:$False` .

Chaque objet d'options de tâche incluant une propriété JobDefinition qui contient la tâche planifiée, l'association à la tâche planifiée est conservée quand les options de tâche sont modifiées.

Les options de tâche planifiée déterminent le mode d'exécution de la tâche quand elle est démarrée par le Planificateur de tâches.
Ces options ne s’appliquent pas lorsque vous utilisez l’applet de commande Start-Job pour démarrer une tâche planifiée.

**Set-ScheduledJobOption** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : modifier les options d’un travail

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

Cet exemple montre comment modifier les options d'une tâche planifiée sur l'ordinateur local.

La première commande utilise l’applet de commande Get-ScheduledJobOption pour accéder aux options de tâche de la tâche planifiée DeployPackage.
La sortie indique que les propriétés WakeToRun et RunElevated sont définies sur $False.

Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification de l'option.

### Exemple 2 : modifier une option sur toutes les tâches planifiées distantes

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

Cette commande remplace la valeur de *IdleTimeout* d’une heure (valeur par défaut) par deux heures sur toutes les tâches planifiées sur l’ordinateur SERVEUR01.

La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur SERVEUR01.

La commande distante commence par une commande Get-ScheduledJob qui obtient toutes les tâches planifiées sur l’ordinateur.
Les tâches planifiées sont dirigées vers l’applet de commande Get-ScheduledJobOption, qui obtient les options de tâche des tâches planifiées.
Chaque objet d'options de tâche contenant une propriété JobDefinition qui inclut la tâche planifiée, l'objet d'options reste associé à la tâche planifiée, même en cas de modification.

Les déclencheurs de tâche sont dirigés vers l’applet de commande **Set-ScheduledJobOption** , qui remplace la valeur de l’option *IdleTimeout* par deux heures (2:00:00).

## PARAMETERS

### -ContinueIfGoingOnBattery
Ne pas arrêter la tâche planifiée si l'ordinateur passe en mode d'alimentation par batterie (se déconnecte de l'alimentation secteur) pendant l'exécution de la tâche.
Par défaut, les tâches planifiées s'arrêtent quand l'ordinateur se déconnecte de l'alimentation secteur.

Le paramètre *ContinueIfGoingOnBattery* définit la valeur de la propriété StopIfGoingOnBatteries des tâches planifiées sur $true.

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

### -DoNotAllowDemandStart
Démarrer la tâche uniquement au moment où elle est déclenchée.
Les utilisateurs ne peuvent pas démarrer la tâche manuellement, notamment à l'aide de la fonctionnalité Exécuter du Planificateur de tâches.

Ce paramètre affecte uniquement le Planificateur de tâches.
Il n’empêche pas les utilisateurs d’utiliser l’applet de commande Start-Job pour démarrer le travail.

Le paramètre *DoNotAllowDemandStart* définit la valeur de la propriété DoNotAllowDemandStart des tâches planifiées sur $true.

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

### -HideInTaskScheduler
Ne pas afficher la tâche dans le Planificateur de tâches.
Cette valeur affecte uniquement l'ordinateur sur lequel s'exécute la tâche.
Par défaut, les tâches planifiées apparaissent dans le Planificateur de tâches.

Même si une tâche est masquée, les utilisateurs peuvent afficher la tâche en sélectionnant l’option Afficher l’affichage des **tâches masquées** dans planificateur de tâches.

Le paramètre *HideInTaskScheduler* définit la valeur de la propriété ShowInTaskScheduler des tâches planifiées sur $false.

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

### -IdleDuration
Spécifie la durée pendant laquelle l'ordinateur doit être inactif avant que la tâche commence.
La valeur par défaut est 10 minutes.
Si l'ordinateur n'est pas inactif pendant la durée spécifiée avant l'expiration de la valeur *IdleTimeout* , la tâche planifiée ne s'exécute pas avant la prochaine planification, le cas échéant.

Entrez un objet TimeSpan, tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .

Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .
Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout
Spécifie la durée pendant laquelle l'ordinateur doit être inactif avant que la tâche commence.
La valeur par défaut est 10 minutes.
Si l'ordinateur n'est pas inactif pendant la durée spécifiée avant l'expiration de la valeur **IdleTimeout** , la tâche planifiée ne s'exécute pas avant la prochaine planification, le cas échéant.

Entrez un objet TimeSpan, tel que celui généré par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> qui est automatiquement convertie en objet **TimeSpan** .

Pour activer cette valeur, utilisez le paramètre *StartIfIdle* .
Par défaut, la propriété StartIfNotIdle des tâches planifiées a la valeur $True et Windows PowerShell ignore les valeurs *IdleDuration* et *IdleTimeout* .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie les options de tâche.
Entrez une variable qui contient des objets **ScheduledJobOptions** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobOptions** , par exemple une commande Get-ScheduledJobOption.
Vous pouvez également diriger un objet **ScheduledJobOptions** vers **Set-ScheduledJobOption** .

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MultipleInstancePolicy
Détermine comment le système répond à une demande de démarrage d'une instance d'une tâche planifiée alors qu'une autre instance de la tâche est en cours d'exécution.
Les valeurs valides pour ce paramètre sont :

- IgnoreNew.
La nouvelle instance de la tâche est ignorée.
Il s’agit de la valeur par défaut.
- Parallel.
La nouvelle instance de la tâche démarre immédiatement.
- File d'attente.
La nouvelle instance de la tâche démarre dès que l'instance actuelle se termine.
- StopExisting.
L'instance actuelle de la tâche s'arrête et la nouvelle instance démarre.

Pour exécuter la tâche, toutes les conditions de la planification des tâches doivent être remplies.
Par exemple, si les conditions définies par les paramètres *RequireNetwork* , *IdleDuration* et *IdleTimeout* ne sont pas satisfaites, l’instance de tâche n’est pas démarrée, quelle que soit la valeur de ce paramètre.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
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

### -RequireNetwork
Exécute la tâche planifiée uniquement quand des connexions réseau sont disponibles.

Si vous spécifiez ce paramètre et que le réseau n'est pas disponible à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.

Le paramètre *RequireNetwork* définit la valeur de la propriété RunWithoutNetwork des tâches planifiées sur $false.

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

### -RestartOnIdleResume
Redémarre une tâche planifiée quand l'ordinateur devient inactif.
Ce paramètre fonctionne avec le paramètre *StopIfGoingOffIdle* , qui interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (quitte l'état d'inactivité).

Le paramètre *RestartOnIdleResume* définit la valeur de la propriété RestartOnIdleResume des tâches planifiées sur $true.

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

### -RunElevated
Exécute la tâche planifiée avec les autorisations d'un membre du groupe Administrateurs sur l'ordinateur sur lequel s'exécute la tâche.

Pour permettre l’exécution d’une tâche planifiée avec des autorisations d’administrateur, utilisez le paramètre *Credential* de Register-ScheduledJob pour fournir des informations d’identification explicites pour le travail.

Le paramètre **RunElevated** définit la valeur de la propriété **RunElevated** des tâches planifiées sur true.

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

### -StartIfIdle
Démarre la tâche planifiée si l'ordinateur a été inactif pendant la durée spécifiée par le paramètre **IdleDuration** avant que l'heure spécifiée par le paramètre *IdleTimeout* n'expire.

Par défaut, les paramètres *IdleDuration* et *IdleTimeout* sont ignorés et la tâche démarre à l'heure de début planifiée, même si l'ordinateur est occupé.

Si vous spécifiez ce paramètre et que l'ordinateur est occupé (non inactif) à l'heure de début planifiée, la tâche ne s'exécute pas avant la prochaine heure de début planifiée, le cas échéant.

Le paramètre *StartIfIdle* définit la valeur de la propriété **StartIfNotIdle** des tâches planifiées sur false.

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

### -StartIfOnBattery
Démarre la tâche planifiée, même si l'ordinateur fonctionne sur batterie à l'heure de début planifiée.
La valeur par défaut est False.

Le paramètre *StartIfOnBattery* définit la valeur de la propriété **StartIfOnBatteries** des tâches planifiées sur $true.

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

### -StopIfGoingOffIdle
Interrompt une tâche planifiée en cours d'exécution si l'ordinateur devient actif (non inactif) alors que la tâche est en cours d'exécution.

Par défaut, une tâche planifiée qui est suspendue quand l'ordinateur devient actif reprend quand il redevient inactif.
Pour modifier ce comportement par défaut, utilisez le paramètre *RestartOnIdleResume* .

Le paramètre *StopIfGoingOffIdle* définit la valeur de la propriété StopIfGoingOffIdle des tâches planifiées sur $true.

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

### -WakeToRun
Sort l'ordinateur de son état de veille prolongée ou de veille à l'heure de début planifiée afin qu'il puisse exécuter la tâche.
Par défaut, si l'ordinateur est dans un état de veille prolongée ou de veille à l'heure de début planifiée, la tâche ne s'exécute pas.

Le paramètre *WakeToRun* définit la valeur de la propriété WakeToRun des tâches planifiées sur $true.

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

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions
Vous pouvez acheminer par canal un objet d'options de tâche planifiée vers **Set-ScheduledJobOption** .

## SORTIES

### Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions
Quand vous utilisez le paramètre *Passthru* , **Set-ScheduledJobOption** retourne les options de tâche modifiées.
Sinon, cette applet de commande ne génère aucune sortie.

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
