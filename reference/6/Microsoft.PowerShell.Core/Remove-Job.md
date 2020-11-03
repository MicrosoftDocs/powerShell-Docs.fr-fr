---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 6a79c546bf1677fc3d5cf27afc9fa0a53e60fdc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204877"
---
# Remove-Job

## SYNOPSIS
Supprime une tâche en arrière-plan PowerShell.

## SYNTAX

### SessionIdParameterSet (par défaut)

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandParameterSet

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-Job` applet de commande supprime les tâches en arrière-plan PowerShell qui ont été démarrées par l’applet de commande `Start-Job` ou par des applets de commande telles que `Invoke-Command` qui prennent en charge le paramètre **AsJob** .

Vous pouvez utiliser `Remove-Job` pour supprimer tous les travaux ou supprimer les travaux sélectionnés. Les travaux sont identifiés par leur **nom** , **ID** , **ID d’instance** , **commande** ou **État** . Ou un objet de traitement peut être envoyé dans le pipeline à `Remove-Job` . Sans paramètres ou valeurs de paramètre, n' `Remove-Job` a aucun effet.

Depuis PowerShell 3,0, `Remove-Job` peut supprimer des types de tâches personnalisées, tels que les tâches planifiées et les tâches de Workflow. Par exemple, `Remove-Job` supprime la tâche planifiée, toutes les instances de la tâche planifiée sur le disque et les résultats de toutes les instances de tâche déclenchées.

Si vous tentez de supprimer un travail en cours d’exécution, `Remove-Job` échoue. Utilisez l' `Stop-Job` applet de commande pour arrêter un travail en cours d’exécution. `Remove-Job`Vous pouvez utiliser avec le paramètre **force** pour supprimer un travail en cours d’exécution.

Les travaux restent dans le cache global des tâches jusqu’à ce que vous supprimiez la tâche en arrière-plan ou que vous fermiez la session PowerShell.

## EXEMPLES

### Exemple 1 : supprimer un travail à l’aide de son nom

Cet exemple utilise une variable et le pipeline pour supprimer un travail par son nom.

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

`Get-Job` utilise le paramètre **Name** pour spécifier le travail, **BatchJob** . L’objet de traitement est stocké dans la `$batch` variable. L’objet dans `$batch` est envoyé dans le pipeline à `Remove-Job` .

Une alternative consiste à utiliser le paramètre de **tâche** , tel que `Remove-Job -Job $batch` .

### Exemple 2 : supprimer tous les travaux d’une session

Dans cet exemple, toutes les tâches de la session PowerShell active sont supprimées.

```powershell
Get-job | Remove-Job
```

`Get-Job` Obtient toutes les tâches dans la session PowerShell en cours. Les objets de travail sont envoyés dans le pipeline à `Remove-Job` .

### Exemple 3 : supprimer des tâches NotStarted

Cet exemple supprime tous les travaux de la session PowerShell active qui n’ont pas démarré.

```powershell
Remove-Job -State NotStarted
```

`Remove-Job` utilise le paramètre **State** pour spécifier l’état du travail.

### Exemple 4 : supprimer des travaux à l’aide d’un nom convivial

Cet exemple supprime toutes les tâches de la session active avec des noms conviviaux qui se terminent par * Batch * *, y compris les travaux en cours d’exécution.

```powershell
Remove-Job -Name *batch -Force
```

`Remove-Job` utilise le paramètre **Name** pour spécifier un modèle de nom de tâche. Le modèle comprend le `*` caractère générique astérisque () pour rechercher tous les noms de travail qui se terminent par **batch** . Le paramètre **force** supprime les travaux qui exécutent.

### Exemple 5 : supprimer un travail qui a été créé par Invoke-Command

Cet exemple supprime une tâche qui a été démarrée sur un ordinateur distant à l’aide `Invoke-Command` de avec le paramètre **AsJob** .

Étant donné que l’exemple utilise le paramètre **AsJob** , l’objet de traitement est créé sur l’ordinateur local.
Toutefois, le travail s’exécute sur un ordinateur distant. Par conséquent, vous utilisez des commandes locales pour gérer la tâche.

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

`Invoke-Command` exécute un travail sur l’ordinateur **SERVEUR01** . Le paramètre **AsJob** exécute le **scriptblock** en tant que tâche en arrière-plan. L’objet de traitement est stocké dans la `$job` variable. L' `$job` objet variable est envoyé dans le pipeline à `Remove-Job` .

### Exemple 6 : supprimer un travail qui a été créé par Invoke-Command et Start-Job

Cet exemple montre comment supprimer un travail sur un ordinateur distant qui a été démarré à l’aide `Invoke-Command` de pour exécuter `Start-Job` . L’objet de traitement est créé sur l’ordinateur distant et les commandes à distance sont utilisées pour gérer le travail. Une connexion permanente est nécessaire lors de l’exécution d’une commande à distance `Start-Job` .

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

`New-PSSession` crée une **session PSSession** , une connexion permanente, à l’ordinateur **SERVEUR01** . La connexion est enregistrée dans la `$S` variable.

`Invoke-Command` établit une connexion à la session enregistrée dans `$S` . Le **scriptblock** utilise `Start-Job` pour démarrer un travail distant. La tâche exécute une `Get-Process` commande et utilise le paramètre **Name** pour spécifier un nom de travail convivial, **MyJob** .

`Invoke-Command` utilise la `$S` session et s’exécute `Remove-Job` . Le paramètre **Name** spécifie que la tâche nommée **MyJob** est supprimée.

### Exemple 7 : supprimer un travail à l’aide de son InstanceId

Cet exemple supprime un travail en fonction de son **InstanceID** .

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` démarre une tâche en arrière-plan et l’objet de traitement est enregistré dans la `$job` variable.

L’objet dans `$job` est envoyé dans le pipeline à `Format-List` . Le paramètre **Property** utilise un astérisque ( `*` ) pour spécifier que toutes les propriétés de l’objet sont affichées dans une liste.

`Remove-Job` utilise le paramètre **InstanceID** pour spécifier la tâche à supprimer.

## PARAMETERS

### -Command

Supprime les tâches qui incluent les mots spécifiés dans la commande. Vous pouvez entrer un tableau de valeurs séparées par des virgules.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer avant l' `Remove-Job` exécution de.

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

### -Filter

Supprime les tâches qui répondent à toutes les conditions établies dans la table de hachage associée. Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.

Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées. Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de `Start-Job` .

Ce paramètre est introduit dans PowerShell 3.0.

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

Supprime un travail même si l’état de la tâche est **en cours d’exécution** . Si le paramètre **force** n’est pas spécifié, `Remove-Job` ne supprime pas les travaux en cours d’exécution.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, NameParameterSet, InstanceIdParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Supprime les tâches en arrière-plan avec l' **ID** spécifié. Vous pouvez entrer un tableau de valeurs séparées par des virgules. L' **ID** du travail est un entier unique qui identifie un travail au sein de la session active.

Pour Rechercher l' **ID** d’un travail, utilisez `Get-Job` sans paramètres.

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

Supprime les travaux avec l' **InstanceID** spécifié. Vous pouvez entrer un tableau de valeurs séparées par des virgules. Un **InstanceID** est un GUID unique qui identifie un travail.

Pour Rechercher l' **InstanceID** d’un travail, utilisez `Get-Job` .

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

Spécifie les tâches à supprimer. Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches. Vous pouvez entrer un tableau de valeurs séparées par des virgules.

Vous pouvez envoyer des objets de travail vers le dessous du pipeline `Remove-Job` .

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

Supprime uniquement les tâches avec le nom convivial spécifié. Les caractères génériques sont autorisés. Vous pouvez entrer un tableau de valeurs séparées par des virgules.

Il n’est pas garanti que les noms conviviaux des travaux soient uniques, même au sein d’une session PowerShell. Utilisez les paramètres **WhatIf** et **Confirm** lorsque vous supprimez des fichiers par nom.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -État

Supprime uniquement les tâches avec l’état spécifié. Pour supprimer des travaux avec un état **en cours d’exécution** , utilisez le paramètre **force** .

Valeurs acceptées :

- AtBreakpoint
- Bloqué
- Effectué
- Déconnecté
- Échec
- NotStarted
- Exécution en cours
- Arrêté
- En cours d’arrêt
- Interrompu
- Suspension

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe si `Remove-Job` s’exécute. L’applet de commande n’est pas exécutée.

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

Vous pouvez envoyer un objet de traitement vers le dessous du pipeline `Remove-Job` .

## SORTIES

### Aucun

`Remove-Job` ne génère aucune sortie.

## REMARQUES

Un travail PowerShell crée un nouveau processus. Une fois le travail terminé, le processus se termine. Lorsque `Remove-Job` est exécuté, l’état du travail est supprimé.

Si un travail s’arrête avant la fin et que son processus n’a pas quitté, le processus est arrêté de force.

## LIENS CONNEXES

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)
