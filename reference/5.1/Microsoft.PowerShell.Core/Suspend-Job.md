---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202649"
---
# Suspend-Job

## SYNOPSIS
Arrête temporairement les tâches de workflow.

## SYNTAX

### SessionIdParameterSet (par défaut)

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet **de commande suspend-Job suspend les** tâches de Workflow.
Suspendre signifie temporairement interrompre ou suspendre une tâche de Workflow.
Cette applet de commande permet aux utilisateurs qui exécutent des workflows de suspendre le workflow.
Il complète l’activité suspend-Workflow https://go.microsoft.com/fwlink/?LinkId=267141 , qui est une commande dans le workflow qui suspend le Workflow.

L'applet de commande **Suspend-Job** fonctionne seulement sur les tâches de workflow.
Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles qui sont démarrées à l’aide de l’applet de commande Start-Job.

Pour identifier une tâche de workflow, recherchez la valeur de PSWorkflowJob dans la propriété **PSJobTypeName** de la tâche.
Pour déterminer si un type particulier de tâche personnalisée prend en charge l'applet de commande **Suspend-Job** , consultez les rubriques d'aide associées à ce type.

Quand vous suspendez une tâche de workflow, la tâche de workflow s'exécute jusqu'au prochain point de contrôle, se met en suspens et retourne immédiatement un objet de tâche de workflow.
Pour attendre la fin de la suspension avant d’obtenir la tâche, utilisez le paramètre *Wait* de l’applet de commande **suspend-Job** ou Wait-Job.
Lorsque la tâche de workflow est interrompue, la valeur de la propriété **State** du travail est suspendue.

Une mise en suspens correcte s'appuie sur les points de contrôle.
L’état actuel de la tâche, les métadonnées et la sortie sont enregistrés dans le point de contrôle afin que la tâche de workflow puisse être reprise sans perte d’État ou de données.
Si la tâche de workflow n’a pas de points de contrôle, elle ne peut pas être suspendue correctement.
Pour ajouter des points de contrôle à un workflow que vous exécutez, utilisez le paramètre commun de workflow *PSPersist* .
Vous pouvez utiliser le paramètre *force* pour suspendre une tâche de workflow immédiatement et suspendre une tâche de workflow qui n’a pas de points de contrôle, mais l’action peut entraîner la perte de l’État et des données.

Avant d’utiliser une applet de commande de tâche sur un type de tâche personnalisé, par exemple une tâche de workflow ( **PSWorkflowJob** ), importez le module qui prend en charge le type de tâche personnalisé, soit à l’aide de l’applet de commande Import-Module, soit à l’aide de ou de l’utilisation d’une applet de commande dans le module.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : suspendre une tâche de workflow par nom

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

Cet exemple montre comment suspendre une tâche de workflow.

### Exemple 2 : suspendre et reprendre une tâche de workflow

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

Cet exemple montre comment suspendre et reprendre une tâche de workflow.

### Exemple 3 : suspendre une tâche de workflow sur un ordinateur distant

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

Cette commande utilise l’applet de commande Invoke-Command pour interrompre une tâche de workflow sur l’ordinateur distant Srv01.
La valeur du paramètre de *filtre* est une table de hachage qui spécifie une valeur CustomId.
Cet élément **CustomID** est une métadonnée de la tâche ( **PSPrivateMetadata** ).

### Exemple 4 : attendre la suspension de la tâche de workflow

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

Cette commande suspend la tâche de workflow VersionCheck.
La commande utilise le paramètre *Wait* pour attendre jusqu'à ce que la tâche de workflow soit suspendue.
Lorsque la tâche de workflow s’exécute jusqu’au point de contrôle suivant et est suspendue, la commande se termine et retourne l’objet de traitement.

### Exemple 5 : forcer l’interruption d’une tâche de workflow

```
PS C:\> Suspend-Job Maintenance -Force
```

Cette commande suspend de force la tâche de workflow Maintenance.
La tâche de maintenance n’a pas de points de contrôle.
Elle ne peut pas être suspendue correctement et peut ne pas reprendre correctement.

## PARAMETERS

### -Filter
Spécifie une table de hachage de conditions.
Cette applet de commande suspend les tâches qui répondent à toutes les conditions.
Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force
Suspend immédiatement la tâche de workflow.
Cette action peut entraîner une perte de l’État et des données.

Par défaut, **Suspend-Job** permet à la tâche de workflow de s'exécuter jusqu'au point de contrôle suivant, puis la suspend.
Vous pouvez également utiliser ce paramètre pour suspendre des tâches de workflow qui n'ont pas de points de contrôle.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
Spécifie les ID des travaux que cette applet de commande suspend.

L’ID est un entier qui identifie de façon unique le travail dans la session active.
Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.
Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.
Pour Rechercher l’ID d’un travail, utilisez l’applet de commande Get-Job.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId
Spécifie les ID d’instance des travaux que cette applet de commande suspend.
Par défaut, il s'agit de toutes les tâches.

Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.
Pour rechercher l'ID d'instance d'une tâche, utilisez **Get-Job** .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Travail
Spécifie les tâches de workflow que cette applet de commande arrête.
Entrez une variable qui contient les tâches de workflow ou tapez une commande permettant d'obtenir ces tâches de workflow.
Vous pouvez également diriger des tâches de workflow vers l'applet de commande **Suspend-Job** .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Spécifie les noms conviviaux des travaux que cette applet de commande suspend.
Entrez un ou plusieurs noms de tâches de workflow.
Les caractères génériques sont pris en charge.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -État
Spécifie un état de travail.
Cette applet de commande arrête uniquement les tâches dans l’état spécifié.
Les valeurs valides pour ce paramètre sont :

- NotStarted
- Exécution en cours
- Completed
- Échec
- Arrêté
- Bloqué
- Interrompu
- Déconnecté
- Suspension
- En cours d’arrêt

**Suspend : le travail** suspend uniquement les tâches de workflow dans l’État en **cours d’exécution** .

Pour plus d’informations sur les États de travail, consultez [JobState, énumération](https://msdn.microsoft.com/library/system.management.automation.jobstate) dans MSDN Library.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wait
Indique que cette applet de commande supprime l’invite de commandes jusqu’à ce que la tâche de workflow soit dans l’état suspendu.
Par défaut, **suspend-Job** est retourné immédiatement, même si la tâche de workflow n’est pas encore dans l’État Suspended.

Le paramètre *Wait* équivaut à diriger une commande **suspend-Job** vers l’applet de commande **Wait-Job** .

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

### System. Management. Automation. job
Vous pouvez diriger tous les types de travaux vers cette applet de commande.
Toutefois, si **suspend-Job** obtient une tâche d’un type non pris en charge, elle retourne une erreur d’arrêt.

## SORTIES

### System. Management. Automation. job
Cette applet de commande retourne les tâches qu’elle a suspendues.

## REMARQUES

* Le mécanisme et l'emplacement pour enregistrer une tâche suspendue peuvent varier selon le type de tâche. Par exemple, les tâches de workflow suspendues sont enregistrées par défaut dans un magasin de fichiers plats, mais elles peuvent également être enregistrées dans une base de données.
* Si vous soumettez une tâche de workflow qui n'est pas dans l'état Running, **Suspend-Job** affiche un message d'avertissement. Pour supprimer l’avertissement, utilisez le paramètre commun *WarningAction* avec la valeur SilentlyContinue.

  Si un travail n’est pas d’un type qui prend en charge la suspension, **suspend-Job** retourne une erreur d’arrêt.

* Pour rechercher les tâches de workflow qui sont suspendues, y compris celles qui ont été suspendues par cette applet de commande, utilisez le paramètre *State* de l’applet de commande **obtenir-Job** pour obtenir les tâches de workflow dans l’État Suspended.
* Certains types de tâche ont des options ou des propriétés qui empêchent Windows PowerShell de suspendre la tâche. Si les tentatives d’interruption de la tâche échouent, vérifiez que les options et les propriétés du travail autorisent la suspension.

## LIENS CONNEXES

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
