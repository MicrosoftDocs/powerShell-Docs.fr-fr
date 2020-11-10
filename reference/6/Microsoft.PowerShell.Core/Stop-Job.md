---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 56dc7462e2625768db8b52370d3b7d38c8defafe
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387258"
---
# Stop-Job

## SYNOPSIS
Arrête une tâche en arrière-plan PowerShell.

## SYNTAXE

### SessionIdParameterSet (par défaut)

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Stop-Job` applet de commande arrête les tâches en arrière-plan PowerShell en cours. Vous pouvez utiliser cette applet de commande pour arrêter toutes les tâches ou arrêter les tâches sélectionnées en fonction de leur nom, ID, ID d’instance ou État, ou en passant un objet de traitement à `Stop-Job` .

Vous pouvez utiliser `Stop-Job` pour arrêter des tâches en arrière-plan, telles que celles qui ont été démarrées à l’aide `Start-Job` de l’applet de commande ou du paramètre **AsJob** d’une applet de commande. Lorsque vous arrêtez une tâche en arrière-plan, PowerShell termine toutes les tâches en attente dans la file d’attente de travaux, puis met fin au travail. Aucune nouvelle tâche n'est ajoutée à la file d'attente après que cette commande a été soumise.

Cette applet de commande ne supprime pas les tâches en arrière-plan. Pour supprimer un travail, utilisez l' `Remove-Job` applet de commande.

À compter de Windows PowerShell 3,0, `Stop-Job` arrête également les types de tâches personnalisées, tels que les tâches de workflow et les instances de tâches planifiées. Pour permettre `Stop-Job` à d’arrêter un travail avec un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une `Stop-Job` commande, soit à l’aide de l’applet de commande, soit `Import-Module` en utilisant ou en obtenant une applet de commande dans le module. Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.

## EXEMPLES

### Exemple 1 : arrêter un travail sur un ordinateur distant à l’aide de Invoke-Command

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

Cet exemple montre comment utiliser l' `Stop-Job` applet de commande pour arrêter un travail qui s’exécute sur un ordinateur distant.

Étant donné que la tâche a été démarrée à l’aide `Invoke-Command` de l’applet de commande pour exécuter une `Start-Job` commande à distance, l’objet de traitement est stocké sur l’ordinateur distant. Vous devez utiliser une autre `Invoke-Command` commande pour exécuter une `Stop-Job` commande à distance. Pour plus d'informations sur les tâches distantes en arrière-plan, consultez about_Remote_Jobs.

La première commande crée une session PowerShell ( **PSSession** ) sur l’ordinateur Serveur01, puis stocke l’objet de session dans la `$s` variable. La commande utilise les informations d'identification d'un administrateur de domaine.

La deuxième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande dans la session. La commande qui figure dans la tâche obtient tous les événements du journal d'événements système. L’objet de traitement résultant est stocké dans la `$j` variable.

La troisième commande arrête la tâche. Elle utilise l' `Invoke-Command` applet de commande pour exécuter une `Stop-Job` commande dans la **session PSSession** sur SERVEUR01. Étant donné que les objets de traitement sont stockés dans `$j` , qui est une variable sur l’ordinateur local, la commande utilise le modificateur d’étendue using pour identifier `$j` une variable locale.
Pour plus d’informations sur le modificateur d’étendue using, consultez [about_Remote_Variables](about/about_Remote_Variables.md).

Quand la commande se termine, la tâche est arrêtée et la **session PSSession** dans `$s` peut être utilisée.

### Exemple 2 : arrêter une tâche en arrière-plan

```powershell
Stop-Job -Name "Job1"
```

Cette commande arrête la tâche en arrière-plan Job1.

### Exemple 3 : arrêter plusieurs tâches en arrière-plan

```powershell
Stop-Job -Id 1, 3, 4
```

Cette commande arrête trois tâches.
Elle les identifie par leurs ID.

### Exemple 4 : arrêter toutes les tâches en arrière-plan

```powershell
Get-Job | Stop-Job
```

Cette commande arrête toutes les tâches en arrière-plan dans la session active.

### Exemple 5 : arrêter toutes les tâches en arrière-plan bloquées

```powershell
Stop-Job -State Blocked
```

Cette commande arrête toutes les tâches qui sont bloquées.

### Exemple 6 : arrêter un travail à l’aide d’un ID d’instance

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

Ces commandes montrent comment arrêter une tâche sur la base de son ID d'instance.

La première commande utilise l' `Get-Job` applet de commande pour récupérer les tâches dans la session active. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer les tâches à une `Format-Table` commande, qui affiche une table des propriétés spécifiées de chaque travail. Cette table inclut l'ID d'instance de chaque tâche. Elle utilise une propriété calculée pour afficher l'état de la tâche.

La deuxième commande utilise une `Stop-Job` commande qui a le paramètre **InstanceID** pour arrêter un travail sélectionné.

### Exemple 7 : arrêter un travail sur un ordinateur distant

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

Cet exemple montre comment utiliser l' `Stop-Job` applet de commande pour arrêter un travail qui s’exécute sur un ordinateur distant.

Étant donné que la tâche a été démarrée à l’aide du paramètre **AsJob** de l' `Invoke-Command` applet de commande, l’objet de traitement se trouve sur l’ordinateur local, même si le travail s’exécute sur l’ordinateur distant. Par conséquent, vous pouvez utiliser une `Stop-Job` commande locale pour arrêter le travail.

La première commande utilise l' `Invoke-Command` applet de commande pour démarrer une tâche en arrière-plan sur l’ordinateur SERVEUR01. La commande utilise le paramètre **AsJob** pour exécuter la commande distante en tant que tâche en arrière-plan.

Cette commande retourne un objet de traitement, qui est le même objet de traitement que celui retourné par l’applet de commande `Start-Job` .
La commande enregistre l’objet de traitement dans la `$j` variable.

La deuxième commande utilise un opérateur de pipeline pour envoyer la tâche dans la `$j` variable à `Stop-Job` . La commande utilise le paramètre **PassThru** pour demander `Stop-Job` à de retourner un objet de traitement. L’affichage de l’objet de traitement confirme que l’état du travail est arrêté.

Pour plus d'informations sur les tâches distantes en arrière-plan, consultez about_Remote_Jobs.

## PARAMÈTRES

### -Filter

Spécifie une table de hachage de conditions. Cette applet de commande arrête les travaux qui remplissent toutes les conditions.
Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.

Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées. Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande `Start-Job` . Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -Id

Spécifie les ID des travaux que cette applet de commande arrête. La valeur par défaut est toutes les tâches dans la session active.

L’ID est un entier qui identifie de façon unique le travail dans la session active. Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active. Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules. Pour Rechercher l’ID d’un travail, tapez `Get-Job` .

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Spécifie les ID d’instance des travaux que cette applet de commande arrête. Par défaut, il s'agit de toutes les tâches.

Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur. Pour Rechercher l’ID d’instance d’un travail, utilisez `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Travail

Spécifie les travaux que cette applet de commande arrête. Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches. Vous pouvez également utiliser un opérateur de pipeline pour envoyer des travaux à l’applet de commande `Stop-Job` . Par défaut, `Stop-Job` supprime tous les travaux qui ont été démarrés dans la session active.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms conviviaux des travaux que cette applet de commande arrête. Entrez les noms de tâches dans une liste séparée par des virgules ou utilisez des caractères génériques (*) pour entrer un modèle de nom de tâche. Par défaut, `Stop-Job` arrête tous les travaux créés dans la session active.

Étant donné que le nom convivial n’est pas forcément unique, utilisez les paramètres **WhatIf** et **Confirm** lors de l’arrêt des tâches par nom.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -État

Spécifie un état de travail. Cette applet de commande arrête uniquement les tâches dans l’état spécifié. Les valeurs valides pour ce paramètre sont :

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

Pour plus d’informations sur les États de travail, consultez [énumération JobState](/dotnet/api/system.management.automation.jobstate).

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
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

### System. Management. Automation. RemotingJob

Vous pouvez diriger un objet de traitement vers cette applet de commande.

## SORTIES

### Aucun, System. Management. Automation. PSRemotingJob

Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Wait-Job](Wait-Job.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Remote_Variables](About/about_Remote_Variables.md)

[about_Jobs](About/about_Jobs.md)

[about_Scopes](About/about_scopes.md)
