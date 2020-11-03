---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 76644dbf15d2bdabd7a365f4bd5910a50502e17d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201942"
---
# Get-Job

## SYNOPSIS
Obtient les tâches en arrière-plan PowerShell qui s’exécutent dans la session active.

## SYNTAX

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

## Description

L'applet de commande **Get-Job** récupère les objets qui représentent les tâches en arrière-plan démarrées dans la session active. Vous pouvez utiliser l’applet de commande on **-Job** pour récupérer des tâches qui ont été démarrées à l’aide de l’applet de commande Start-Job, ou à l’aide du paramètre *AsJob* d’une applet de commande.

Sans paramètres, une commande **« obtenir-Job »** obtient toutes les tâches de la session active.
Vous pouvez utiliser les paramètres de **Get-Job** pour obtenir des tâches spécifiques.

L'objet de traitement retourné par **Get-Job** contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche. Pour obtenir les résultats, utilisez l’applet de commande Receive-Job.

Une tâche en arrière-plan PowerShell est une commande qui s’exécute en arrière-plan sans interagir avec la session active. En règle générale, vous utilisez une tâche en arrière-plan pour exécuter une commande complexe qui prend beaucoup de temps. Pour plus d’informations sur les tâches en arrière-plan dans PowerShell, consultez about_Jobs.

À compter de Windows PowerShell 3.0, l'applet de commande **Get-Job** obtient également des types de tâche personnalisés, comme les tâches de workflow et les instances de tâches planifiées. Pour rechercher le type d'une tâche, utilisez la propriété **PSJobTypeName** de la tâche.

Pour permettre à la **fonction** d’obtention d’un travail d’obtenir un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une commande **obtenir-Job** , soit à l’aide de l’applet de commande Import-Module, soit en utilisant ou en obtenant une applet de commande dans le module. Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.

## EXEMPLES

### Exemple 1 : récupération de toutes les tâches en arrière-plan démarrées dans la session active

```powershell
Get-Job
```

Cette commande obtient toutes les tâches en arrière-plan démarrées dans la session active.
Elle n'inclut pas les tâches créées dans d'autres sessions, même si elles s'exécutent sur l'ordinateur local.

### Exemple 2 : arrêter un travail à l’aide d’un ID d’instance

Ces commandes indiquent comment obtenir l'ID d'instance d'une tâche, puis l'utiliser pour arrêter une tâche.
Contrairement au nom de la tâche, qui n'est pas unique, l'ID d'instance est unique.

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

La première commande utilise l'applet de commande **Get-Job** pour obtenir une tâche. Elle utilise le paramètre *Name* pour identifier le travail. La commande stocke l'objet de traitement retourné par **Get-Job** dans la variable $j. Dans cet exemple, il existe une seule tâche ayant le nom spécifié.

La deuxième commande obtient la propriété **InstanceId** de l'objet dans la variable $j et le stocke dans la variable $ID.

La troisième commande affiche la valeur de la variable $ID.

La quatrième commande utilise Stop-Job applet de commande pour arrêter la tâche. Elle utilise le paramètre *InstanceId* pour identifier la tâche et la variable $ID afin de représenter l'ID d'instance de la tâche.

### Exemple 3 : obtenir des travaux qui incluent une commande spécifique

```powershell
Get-Job -Command "*get-process*"
```

Cette commande obtient les tâches du système qui incluent une commande Get-Process. La commande utilise le paramètre *Command* de **Get-Job** pour limiter le nombre de tâches récupérées. La commande utilise des caractères génériques (*) pour obtenir les tâches qui incluent une commande **« obtenir un processus »** n’importe où dans la chaîne de commande.

### Exemple 4 : obtenir des travaux qui incluent une commande spécifique à l’aide du pipeline

```powershell
"*get-process*" | Get-Job
```

À l’instar de la commande dans l’exemple précédent, cette commande obtient les tâches du système qui incluent une commande **« obtenir-traiter »** . La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne, entre guillemets, à l’applet de commande **« obtenir-Job »** . Elle est équivalente à la commande précédente.

### Exemple 5 : obtenir des travaux qui n’ont pas été démarrés

```powershell
Get-Job -State NotStarted
```

Cette commande obtient uniquement les tâches qui ont été créées mais qui n'ont pas encore démarré.
Cela inclut les tâches dont l'exécution est planifiée ultérieurement et celles qui ne sont pas encore planifiées.

### Exemple 6 : obtenir des travaux auxquels aucun nom n’a été attribué

```powershell
Get-Job -Name Job*
```

Cette commande obtient toutes les tâches dont le nom commence par Job.
Étant donné que Job \<number\> est le nom par défaut d’une tâche, cette commande obtient toutes les tâches qui n’ont pas de nom explicitement attribué.

### Exemple 7 : utiliser un objet de traitement pour représenter la tâche dans une commande

Cet exemple illustre comment utiliser **Get-Job** pour obtenir une tâche, puis comment utiliser l'objet de traitement pour représenter la tâche dans une commande.

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

La première commande utilise l’applet de commande **Start-Job** pour démarrer une tâche en arrière-plan qui exécute une commande **« obtenir-traiter »** sur l’ordinateur local. La commande utilise le paramètre *Name* de **Start-Job** pour attribuer un nom convivial à la tâche.

La deuxième commande utilise Get-Job pour obtenir la tâche. Elle utilise le paramètre *Name* de **Get-Job** pour identifier la tâche. Elle enregistre l'objet de traitement résultant dans la variable $j.

La troisième commande affiche la valeur de l'objet de traitement dans la variable $j. La valeur de la propriété **State** indique que la tâche est terminée. La valeur de la propriété **HasMoreData** indique que des résultats de la tâche sont disponibles, mais qu'ils n'ont pas encore été récupérés.

La quatrième commande utilise l’applet de commande **Receive-Job** pour obtenir les résultats de la tâche. Elle utilise l'objet de traitement de la variable $j pour représenter la tâche. Vous pouvez également utiliser un opérateur de pipeline pour envoyer un objet de tâche au **travail de réception** .

### Exemple 8 : obtenir tous les travaux, y compris les travaux démarrés par une autre méthode

Cet exemple montre que l’applet de commande **« obtient-Job »** peut récupérer toutes les tâches qui ont été démarrées dans la session active, même si elles ont été démarrées à l’aide de différentes méthodes.

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

La première commande utilise l’applet de commande **Start-Job** pour démarrer une tâche sur l’ordinateur local.

La deuxième commande utilise le paramètre *AsJob* de l’applet de **commande Invoke-Command** pour démarrer une tâche sur l’ordinateur S1. Bien que les commandes de la tâche s'exécutent sur l'ordinateur distant, l'objet de traitement est créé sur l'ordinateur local, vous utilisez donc les commandes locales pour gérer la tâche.

La troisième commande utilise l'applet de commande **Invoke-Command** pour exécuter une commande **Start-Job** sur l'ordinateur S2. À l’aide de cette méthode, l’objet de traitement est créé sur l’ordinateur distant. vous utilisez donc des commandes à distance pour gérer le travail.

La quatrième commande utilise **Get-Job** pour obtenir les tâches stockées sur l'ordinateur local. La propriété **PSJobTypeName** des travaux, introduite dans Windows PowerShell 3,0, indique que la tâche locale démarrée à l’aide de l’applet de commande **Start-Job** est une tâche en arrière-plan et que la tâche démarrée dans une session à distance à l’aide de l’applet de **commande Invoke-Command** est une tâche à distance.

La cinquième commande utilise **Invoke-Command** pour exécuter une commande **obtenir-Job** sur l’ordinateur S2. L’exemple de sortie montre les résultats de la commande Get-Job. Sur l'ordinateur S2, la tâche semble être une tâche locale. Le nom de l’ordinateur est localhost et le type de travail est une tâche en arrière-plan.

Pour plus d’informations sur la façon d’exécuter des tâches en arrière-plan sur des ordinateurs distants, consultez about_Remote_Jobs.

### Exemple 9 : examiner un travail ayant échoué

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
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
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

Cette commande montre comment utiliser l’objet de traitement retourné par la **fonction-Job** pour déterminer la raison de l’échec d’une tâche.
Elle illustre également comment obtenir les tâches enfant de chaque tâche.

La première commande utilise l’applet de commande **Start-Job** pour démarrer une tâche sur l’ordinateur local. L'objet tâche retourné par **Start-Job** indique que la tâche a échoué. La valeur de la propriété **State** est failed.

La deuxième commande utilise l'applet de commande **Get-Job** pour obtenir la tâche. La commande utilise la méthode du point pour obtenir la valeur de la propriété **JobStateInfo** de l'objet. Elle utilise un opérateur de pipeline pour envoyer l’objet dans la propriété **JobStateInfo** à l’applet de commande Format-List, qui met en forme toutes les propriétés de l’objet (*) dans une liste. Le résultat de la commande **format-list** indique que la valeur de la propriété **reason** de la tâche est vide.

La troisième commande étudie davantage. Elle utilise une commande **« obtenir-Job »** pour obtenir la tâche, puis utilise un opérateur de pipeline pour envoyer l’intégralité de l’objet de traitement à l’applet de commande **format-list** , qui affiche toutes les propriétés du travail dans une liste. L’affichage de toutes les propriétés de l’objet de traitement indique que le travail contient un travail enfant nommé Job2.

La quatrième commande utilise **Get-Job** pour obtenir l'objet de traitement qui représente la tâche enfant Job2. Il s'agit de la tâche dans laquelle a été exécutée la commande. Elle utilise la méthode point pour avoir la propriété **reason** de la propriété **JobStateInfo** . Le résultat indique que la tâche a échoué en raison d’une erreur d’accès refusé. Dans ce cas, l’utilisateur a oublié d’utiliser l’option Exécuter en tant qu’administrateur lors du démarrage de PowerShell. comme les travaux en arrière-plan utilisent les fonctionnalités de communication à distance de PowerShell, l’ordinateur doit être configuré pour que l’accès distant exécute un travail, même lorsque le travail s’exécute sur l’ordinateur local.

### Exemple 10 : obtenir des résultats filtrés

Cet exemple indique comment utiliser le paramètre *Filter* pour obtenir une tâche de workflow.
Le paramètre *Filter* , introduit dans Windows PowerShell 3.0, n'est valide que sur les types de tâche personnalisé, comme les tâches de workflow et les tâches planifiées.

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

La première commande utilise le mot clé **Workflow** pour créer le flux de travail WFProcess.

La deuxième commande utilise le paramètre *AsJob* du flux de travail WFProcess pour exécuter le workflow en tant que tâche en arrière-plan. Elle utilise le paramètre *JobName* du workflow pour spécifier un nom pour la tâche et le paramètre *PSPrivateMetadata* du workflow pour spécifier un ID personnalisé.

La troisième commande utilise le paramètre *Filter* de **Get-Job** pour obtenir la tâche par son ID personnalisé spécifié dans le paramètre *PSPrivateMetadata* .

### Exemple 11 : obtenir des informations sur les tâches enfants

Cet exemple illustre l'utilisation des paramètres *IncludeChildJob* et *ChildJobState* de l'applet de commande **Get-Job** .

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
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
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

La première commande obtient les tâches de la session active. La sortie inclut une tâche en arrière-plan, une tâche à distance et plusieurs instances d'une tâche planifiée. La tâche à distance, Job4, semble avoir échoué.

La deuxième commande utilise le paramètre *IncludeChildJob* de **Get-Job** . La sortie ajoute les tâches enfants de tous les travaux qui ont des tâches enfants. Dans ce cas, la sortie révisée indique que seule la tâche enfant JOB5 de Job4 a échoué.

La troisième commande utilise le paramètre *ChildJobState* avec la valeur failed. la sortie comprend tous les travaux parents et uniquement les tâches enfants ayant échoué.

La quatrième commande utilise la propriété **JobStateInfo** des travaux et sa propriété **reason** pour découvrir la raison de l’échec de JOB5.

## PARAMETERS

### -Après

Obtient les tâches terminées après la date et l'heure spécifiées. Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date ou une chaîne qui peut être convertie en un objet **DateTime** , tel que `Dec 1, 2012 2:00 AM` ou `11/06` .

Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** . Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** . Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

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

Obtient les tâches terminées avant la date et l'heure spécifiées.
Entrez un objet **DateTime** .

Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** . Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** . Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

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

Obtient uniquement les tâches enfant dans l'état spécifié.
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

Par défaut, **Get-Job** n'obtient pas les tâches enfant.
En utilisant le paramètre *IncludeChildJob* , la **fonction « obtenir-Job »** obtient toutes les tâches enfants.
Si vous utilisez le paramètre *ChildJobState* , le paramètre *IncludeChildJob* n'a aucun effet.

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

Spécifie un tableau de commandes sous forme de chaînes.
Cette applet de commande obtient les tâches qui incluent les commandes spécifiées.
Par défaut, il s'agit de toutes les tâches.
Vous pouvez utiliser des caractères génériques pour spécifier un modèle de commande.

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

Spécifie une table de hachage de conditions.
Cette applet de commande obtient les tâches qui répondent à toutes les conditions.
Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.

Ce paramètre fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de workflow et les tâches planifiées.
Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .
Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

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
La propriété **HasMoreData** indique si tous les résultats de la tâche ont été reçus dans la session active.
Pour obtenir des travaux qui ont plus de résultats, spécifiez la valeur $True.
Pour obtenir des travaux qui n’ont pas plus de résultats, spécifiez une valeur de $False.

Pour obtenir les résultats d’un travail, utilisez l’applet de commande Receive-Job.

Lorsque vous utilisez l’applet de commande **Receive-Job** , elle supprime de son stockage propre à la session les résultats renvoyés. Lorsqu’il a retourné tous les résultats de la tâche dans la session active, il définit la valeur de la propriété **HasMoreData** du travail sur $false) pour indiquer qu’il n’a plus de résultats pour le travail dans la session active. Utilisez le paramètre *Keep* de **Receive-Job** pour empêcher **Receive-Job** de supprimer des résultats et de modifier la valeur de la propriété **HasMoreData** . Pour plus d'informations, voir `Get-Help Receive-Job`.

La propriété **HasMoreData** est propre à la session active. Si les résultats d’un type de tâche personnalisé sont enregistrés en dehors de la session, comme le type de tâche planifiée qui enregistre les résultats du travail sur le disque, vous pouvez utiliser l’applet de commande **Receive-Job** dans une autre session pour obtenir les résultats de la tâche, même si la valeur de **HasMoreData** est $false. Pour plus d'informations, consultez les rubriques d'aide du type de tâche personnalisé.

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

L’ID est un entier qui identifie de façon unique le travail dans la session active.
Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.
Vous pouvez taper un ou plusieurs ID séparés par des virgules.
Pour Rechercher l’ID d’un travail, tapez `Get-Job` sans paramètres.

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

Ce paramètre est particulièrement utile pour examiner les tâches de workflow, pour lesquelles l’opération d' **extraction** de travail retourne un travail parent de conteneur et les échecs de travaux, car la raison de l’échec est enregistrée dans une propriété du travail enfant.

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

Spécifie un tableau d’ID d’instance des travaux que cette applet de commande obtient.
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

### -Name

Spécifie un tableau de noms conviviaux d’instance des travaux que cette applet de commande obtient.
Entrez un nom de tâche ou utilisez des caractères génériques pour entrer un modèle de nom de tâche.
Par défaut, **Get-Job** obtient toutes les tâches de la session active.

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

Spécifie un nombre de travaux à obtenir.
Cette applet de commande obtient les tâches qui ont été terminées en dernier.

Le paramètre *Newest* ne trie pas ni ne retourne les tâches les plus récentes selon l'heure de fin.
Pour trier la sortie, utilisez l’applet de commande Sort-Object.

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

Spécifie un état de travail.
Cette applet de commande obtient uniquement les tâches dans l’état spécifié.
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

Par défaut, **Get-Job** obtient toutes les tâches de la session active.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. RemotingJob

Cette applet de commande retourne des objets qui représentent les tâches dans la session.

## REMARQUES

* La propriété **PSJobTypeName** des tâches indique le type de la tâche. La valeur de propriété est déterminée par l'auteur du type de tâche. La liste suivante affiche les types de tâches courants.

  - **BackgroundJob** .
Tâche locale démarrée à l’aide de **Start-Job** .

  - **RemoteJob** .
La tâche a démarré dans une **session PSSession** à l’aide du paramètre *AsJob* de l’applet de commande Invoke-Command.

  - **PSWorkflowJob** .
tâche démarrée à l'aide du paramètre *AsJob* commun des workflows.

## LIENS CONNEXES

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)
