---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: e93a46d863fb560c70d9257270af1e6f43d3f248
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391185"
---
# Get-Job

## SYNOPSIS
Obtient les tâches en arrière-plan PowerShell qui s’exécutent dans la session active.

## SYNTAXE

### SessionIdParameterSet (par défaut)

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### NameParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### StateParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

L' `Get-Job` applet de commande obtient les objets qui représentent les tâches en arrière-plan démarrées dans la session active. Vous pouvez utiliser `Get-Job` pour récupérer des tâches qui ont été démarrées à l’aide de l' `Start-Job` applet de commande, ou à l’aide du paramètre **AsJob** d’une applet de commande.

Sans paramètres, une `Get-Job` commande obtient toutes les tâches de la session active. Vous pouvez utiliser les paramètres de `Get-Job` pour accéder à des tâches spécifiques.

L’objet de traitement qui `Get-Job` retourne contient des informations utiles sur le travail, mais il ne contient pas les résultats de la tâche. Pour obtenir les résultats, utilisez l' `Receive-Job` applet de commande.

Une tâche en arrière-plan Windows PowerShell est une commande qui s’exécute en arrière-plan sans interagir avec la session active. En règle générale, vous utilisez une tâche en arrière-plan pour exécuter une commande complexe qui prend beaucoup de temps. Pour plus d'informations sur les tâches en arrière-plan, consultez [about_Jobs](./about/about_Jobs.md).

À compter de Windows PowerShell 3,0, l' `Get-Job` applet de commande obtient également les types de tâches personnalisés, tels que les tâches de workflow et les instances de tâches planifiées. Pour rechercher le type d'une tâche, utilisez la propriété **PSJobTypeName** de la tâche.

Pour permettre `Get-Job` à d’obtenir un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une `Get-Job` commande, soit à l’aide de l’applet de commande, soit `Import-Module` en utilisant ou en obtenant une applet de commande dans le module. Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.

## EXEMPLES

### Exemple 1 : récupération de toutes les tâches en arrière-plan démarrées dans la session active

Cette commande obtient toutes les tâches en arrière-plan démarrées dans la session active. Elle n'inclut pas les tâches créées dans d'autres sessions, même si elles s'exécutent sur l'ordinateur local.

```
PS C:\> Get-Job
```

### Exemple 2 : arrêter un travail à l’aide d’un ID d’instance

Ces commandes indiquent comment obtenir l'ID d'instance d'une tâche, puis l'utiliser pour arrêter une tâche. Contrairement au nom de la tâche, qui n'est pas unique, l'ID d'instance est unique.

La première commande utilise l' `Get-Job` applet de commande pour obtenir un travail. Elle utilise le paramètre **Name** pour identifier le travail. La commande stocke l’objet de traitement qui `Get-Job` retourne dans la `$j` variable. Dans cet exemple, il existe une seule tâche ayant le nom spécifié. La deuxième commande obtient la propriété **InstanceID** de l’objet dans la `$j` variable et la stocke dans la `$ID` variable. La troisième commande affiche la valeur de la `$ID` variable. La quatrième commande utilise l' `Stop-Job` applet de commande pour arrêter la tâche.
Elle utilise le paramètre **InstanceID** pour identifier la tâche et la `$ID` variable afin de représenter l’ID d’instance du travail.

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### Exemple 3 : obtenir des travaux qui incluent une commande spécifique

Cette commande obtient les tâches du système qui incluent une `Get-Process` commande. La commande utilise le paramètre **Command** de `Get-Job` pour limiter les travaux récupérés. La commande utilise des caractères génériques ( `*` ) pour obtenir les tâches qui incluent une `Get-Process` commande n’importe où dans la chaîne de commande.

```
PS C:\> Get-Job -Command "*get-process*"
```

### Exemple 4 : obtenir des travaux qui incluent une commande spécifique à l’aide du pipeline

À l’instar de la commande dans l’exemple précédent, cette commande obtient les tâches du système qui incluent une `Get-Process` commande. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer une chaîne, entre guillemets, à l’applet de commande `Get-Job` . Elle est équivalente à la commande précédente.

```
PS C:\> "*get-process*" | Get-Job
```

### Exemple 5 : obtenir des travaux qui n’ont pas été démarrés

Cette commande obtient uniquement les tâches qui ont été créées mais qui n'ont pas encore démarré. Cela inclut les tâches dont l'exécution est planifiée ultérieurement et celles qui ne sont pas encore planifiées.

```
PS C:\> Get-Job -State NotStarted
```

### Exemple 6 : obtenir des travaux auxquels aucun nom n’a été attribué

Cette commande obtient toutes les tâches dont le nom commence par Job. Étant donné que `job<number>` est le nom par défaut d’une tâche, cette commande obtient toutes les tâches qui n’ont pas de nom explicitement attribué.

```
PS C:\> Get-Job -Name Job*
```

### Exemple 7 : utiliser un objet de traitement pour représenter la tâche dans une commande

Cet exemple montre comment utiliser `Get-Job` pour obtenir un objet de traitement, puis il montre comment utiliser l’objet de traitement pour représenter la tâche dans une commande.

La première commande utilise l' `Start-Job` applet de commande pour démarrer une tâche en arrière-plan qui exécute une `Get-Process` commande sur l’ordinateur local. La commande utilise le paramètre **Name** de `Start-Job` pour affecter un nom convivial à la tâche. La deuxième commande utilise `Get-Job` pour récupérer la tâche. Elle utilise le paramètre **Name** de `Get-Job` pour identifier le travail. La commande enregistre l’objet de traitement résultant dans la `$j` variable. La troisième commande affiche la valeur de l’objet de traitement dans la `$j` variable. La valeur de la propriété **State** indique que la tâche est terminée. La valeur de la propriété **HasMoreData** indique que des résultats de la tâche sont disponibles, mais qu'ils n'ont pas encore été récupérés. La quatrième commande utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail. Elle utilise l’objet de traitement dans la `$j` variable pour représenter la tâche. Vous pouvez également utiliser un opérateur de pipeline pour envoyer un objet de traitement à `Receive-Job` .

```
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob
PS C:\> $j = Get-Job -Name MyJob
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```


### Exemple 8 : obtenir tous les travaux, y compris les travaux démarrés par une autre méthode

Cet exemple montre que l' `Get-Job` applet de commande peut récupérer toutes les tâches qui ont été démarrées dans la session active, même si elles ont été démarrées à l’aide de différentes méthodes.

La première commande utilise l' `Start-Job` applet de commande pour démarrer un travail sur l’ordinateur local. La deuxième commande utilise le paramètre **AsJob** de l' `Invoke-Command` applet de commande pour démarrer un travail sur l’ordinateur S1. Bien que les commandes de la tâche s'exécutent sur l'ordinateur distant, l'objet de traitement est créé sur l'ordinateur local, vous utilisez donc les commandes locales pour gérer la tâche. La troisième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande sur l’ordinateur S2. À l’aide de cette méthode, l’objet de traitement est créé sur l’ordinateur distant. vous utilisez donc des commandes à distance pour gérer le travail. La quatrième commande utilise `Get-Job` pour récupérer les travaux stockés sur l’ordinateur local. La propriété **PSJobTypeName** des travaux, introduite dans Windows PowerShell 3,0, montre que la tâche locale démarrée à l’aide de l’applet de commande `Start-Job` est une tâche en arrière-plan et que la tâche démarrée dans une session à distance à l’aide de l' `Invoke-Command` applet de commande est une tâche à distance. La cinquième commande utilise `Invoke-Command` pour exécuter une `Get-Job` commande sur l’ordinateur S2. L’exemple de sortie montre les résultats de la `Get-Job` commande. Sur l'ordinateur S2, la tâche semble être une tâche locale. Le nom de l’ordinateur est localhost et le type de travail est une tâche en arrière-plan. Pour plus d’informations sur la façon d’exécuter des tâches en arrière-plan sur des ordinateurs distants, consultez [about_Remote_Jobs](./about/about_Remote_Jobs.md).

```
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

### Exemple 9 : examiner un travail ayant échoué

Cette commande montre comment utiliser l’objet de traitement qui `Get-Job` retourne pour déterminer la raison de l’échec d’un travail.
Elle illustre également comment obtenir les tâches enfant de chaque tâche.

La première commande utilise l' `Start-Job` applet de commande pour démarrer un travail sur l’ordinateur local. L’objet de traitement qui `Start-Job` retourne indique que le travail a échoué. La valeur de la propriété **State** est failed.

La deuxième commande utilise l' `Get-Job` applet de commande pour récupérer le travail. La commande utilise la méthode du point pour obtenir la valeur de la propriété **JobStateInfo** de l'objet. Elle utilise un opérateur de pipeline pour envoyer l’objet dans la propriété **JobStateInfo** à l’applet de commande `Format-List` , qui met en forme toutes les propriétés de l’objet ( `*` ) dans une liste. Le résultat de la `Format-List` commande indique que la valeur de la propriété **reason** de la tâche est vide.

La troisième commande étudie davantage. Elle utilise une `Get-Job` commande pour obtenir la tâche, puis utilise un opérateur de pipeline pour envoyer l’intégralité de l’objet de traitement à l’applet de commande `Format-List` , qui affiche toutes les propriétés du travail dans une liste. L’affichage de toutes les propriétés de l’objet de traitement indique que le travail contient un travail enfant nommé Job2.

La quatrième commande utilise `Get-Job` pour récupérer l’objet de traitement qui représente la tâche enfant Job2. Il s'agit de la tâche dans laquelle a été exécutée la commande. Elle utilise la méthode point pour avoir la propriété **reason** de la propriété **JobStateInfo** . Le résultat indique que la tâche a échoué en raison d’une erreur d’accès refusé. Dans ce cas, l’utilisateur a oublié d’utiliser l’option Exécuter en tant qu’administrateur lors du démarrage de Windows PowerShell. étant donné que les travaux en arrière-plan utilisent les fonctionnalités de communication à distance de Windows PowerShell, l’ordinateur doit être configuré pour que l’accès distant exécute un travail, même lorsque le travail s’exécute sur l’ordinateur local. Pour plus d’informations sur la configuration requise pour la communication à distance dans Windows PowerShell, consultez [about_Remote_Requirements](./about/about_Remote_Requirements.md). Pour des conseils sur la résolution des problèmes, consultez [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).

```
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the
following error message: Access is denied.
```

### Exemple 10 : obtenir des résultats filtrés

Cet exemple indique comment utiliser le paramètre **Filter** pour obtenir une tâche de workflow. Le paramètre **Filter** , introduit dans Windows PowerShell 3.0, n'est valide que sur les types de tâche personnalisé, comme les tâches de workflow et les tâches planifiées.

La première commande utilise le mot clé **Workflow** pour créer le flux de travail WFProcess. La deuxième commande utilise le paramètre **AsJob** du flux de travail WFProcess pour exécuter le workflow en tant que tâche en arrière-plan. Elle utilise le paramètre **JobName** du workflow pour spécifier un nom pour la tâche et le paramètre **PSPrivateMetadata** du workflow pour spécifier un ID personnalisé. La troisième commande utilise le paramètre **Filter** de `Get-Job` pour récupérer le travail par l’ID personnalisé qui a été spécifié dans le paramètre **PSPrivateMetadata** .

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### Exemple 11 : obtenir des informations sur les tâches enfants

Cet exemple montre l’effet de l’utilisation des paramètres **IncludeChildJob** et **ChildJobState** de l’applet de commande `Get-Job` .

La première commande obtient les tâches de la session active. La sortie inclut une tâche en arrière-plan, une tâche à distance et plusieurs instances d'une tâche planifiée. La tâche à distance, Job4, semble avoir échoué.
La deuxième commande utilise le paramètre **IncludeChildJob** de `Get-Job` . La sortie ajoute les tâches enfants de tous les travaux qui ont des tâches enfants. Dans ce cas, la sortie révisée indique que seule la tâche enfant JOB5 de Job4 a échoué. La troisième commande utilise le paramètre **ChildJobState** avec la valeur failed. la sortie comprend tous les travaux parents et uniquement les tâches enfants ayant échoué. La cinquième commande utilise la propriété **JobStateInfo** des travaux et sa propriété **reason** pour découvrir la raison de l’échec de JOB5.

```
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
```

Pour plus d’informations, consultez la rubrique d’aide [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) .

## PARAMÈTRES

### -Après

Obtient les tâches terminées après la date et l'heure spécifiées. Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande, `Get-Date` ou une chaîne qui peut être convertie en un objet **DateTime** , tel que `Dec 1, 2012 2:00 AM` ou `11/06` .

Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime**. Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande `Start-Job` . Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Avant

Obtient les tâches terminées avant la date et l'heure spécifiées. Entrez un objet **DateTime** .

Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime**. Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande `Start-Job` . Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

Obtient uniquement les tâches enfant dans l'état spécifié. Les valeurs valides pour ce paramètre sont :

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

Par défaut, `Get-Job` n’obtient pas les tâches enfants. En utilisant le paramètre **IncludeChildJob** , `Get-Job` obtient toutes les tâches enfants. Si vous utilisez le paramètre **ChildJobState** , le paramètre **IncludeChildJob** n'a aucun effet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

Spécifie un tableau de commandes sous forme de chaînes. Cette applet de commande obtient les tâches qui incluent les commandes spécifiées. Par défaut, il s'agit de toutes les tâches. Vous pouvez utiliser des caractères génériques pour spécifier un modèle de commande.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Filter

Spécifie une table de hachage de conditions. Cette applet de commande obtient les tâches qui répondent à toutes les conditions.
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

### -HasMoreData

Indique si cette applet de commande obtient uniquement les tâches qui ont la valeur de propriété **HasMoreData** spécifiée.
La propriété **HasMoreData** indique si tous les résultats de la tâche ont été reçus dans la session active. Pour obtenir des travaux qui ont plus de résultats, affectez la valeur à `$True` . Pour obtenir des travaux qui n’ont pas plus de résultats, affectez la valeur à `$False` .

Pour obtenir les résultats d’un travail, utilisez l' `Receive-Job` applet de commande.

Lorsque vous utilisez l' `Receive-Job` applet de commande, elle supprime de son stockage propre à la session les résultats qu’elle a retournés. Lorsqu’il a retourné tous les résultats de la tâche dans la session active, il définit la valeur de la propriété **HasMoreData** du travail sur `$False` ) pour indiquer qu’il n’a plus de résultats pour le travail dans la session active. Utilisez le paramètre **Keep** de `Receive-Job` pour empêcher `Receive-Job` de supprimer des résultats et de modifier la valeur de la propriété **HasMoreData** .
Pour plus d'informations, voir `Get-Help Receive-Job`.

La propriété **HasMoreData** est propre à la session active. Si les résultats d’un type de tâche personnalisé sont enregistrés en dehors de la session, par exemple le type de tâche planifiée, qui enregistre les résultats du travail sur le disque, vous pouvez utiliser l' `Receive-Job` applet de commande dans une autre session pour obtenir les résultats de la tâche, même si la valeur de **HasMoreData** est `$False` . Pour plus d'informations, consultez les rubriques d'aide du type de tâche personnalisé.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie un tableau d’ID des travaux que cette applet de commande obtient.

L’ID est un entier qui identifie de façon unique le travail dans la session active. Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active. Vous pouvez taper un ou plusieurs ID séparés par des virgules. Pour Rechercher l’ID d’un travail, tapez `Get-Job` sans paramètres.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeChildJob

Indique que cette applet de commande retourne des travaux enfants, en plus des travaux parents.

Ce paramètre est particulièrement utile pour examiner les tâches de workflow, pour lesquelles `Get-Job` retourne un travail parent de conteneur et les échecs de travail, car la raison de l’échec est enregistrée dans une propriété du travail enfant.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Spécifie un tableau d’ID d’instance des travaux que cette applet de commande obtient. Par défaut, il s'agit de toutes les tâches.

Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur. Pour Rechercher l’ID d’instance d’un travail, utilisez `Get-Job` .

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

### -Name

Spécifie un tableau de noms conviviaux d’instance des travaux que cette applet de commande obtient. Entrez un nom de tâche ou utilisez des caractères génériques pour entrer un modèle de nom de tâche. Par défaut, `Get-Job` obtient toutes les tâches de la session active.

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

### -Plus récent

Spécifie un nombre de travaux à obtenir. Cette applet de commande obtient les tâches qui ont été terminées en dernier.

Le paramètre **Newest** ne trie pas ni ne retourne les tâches les plus récentes selon l'heure de fin. Pour trier la sortie, utilisez l' `Sort-Object` applet de commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -État

Spécifie un état de travail. Cette applet de commande obtient uniquement les tâches dans l’état spécifié. Les valeurs valides pour ce paramètre sont :

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

Par défaut, `Get-Job` obtient toutes les tâches de la session active.

Pour plus d’informations sur les États de travail, consultez [énumération JobState](/dotnet/api/system.management.automation.jobstate).

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. RemotingJob

Cette applet de commande retourne des objets qui représentent les tâches dans la session.

## REMARQUES

La propriété **PSJobTypeName** des tâches indique le type de la tâche. La valeur de propriété est déterminée par l'auteur du type de tâche. La liste suivante affiche les types de tâches courants.

- **BackgroundJob**. Tâche locale démarrée à l’aide de `Start-Job` .
- **RemoteJob**. Travail démarré dans une **session PSSession** à l’aide du paramètre **AsJob** de l’applet de commande `Invoke-Command` .
- **PSWorkflowJob**. tâche démarrée à l'aide du paramètre **AsJob** commun des workflows.

## LIENS CONNEXES

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)
