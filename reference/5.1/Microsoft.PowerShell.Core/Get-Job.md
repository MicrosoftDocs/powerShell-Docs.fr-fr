---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202302"
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

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
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

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## Description

L'applet de commande **Get-Job** récupère les objets qui représentent les tâches en arrière-plan démarrées dans la session active.
Vous pouvez utiliser l’applet de commande on **-Job** pour récupérer des tâches qui ont été démarrées à l’aide de l’applet de commande Start-Job, ou à l’aide du paramètre *AsJob* d’une applet de commande.

Sans paramètres, une commande **« obtenir-Job »** obtient toutes les tâches de la session active.
Vous pouvez utiliser les paramètres de **Get-Job** pour obtenir des tâches spécifiques.

L'objet de traitement retourné par **Get-Job** contient des informations utiles sur la tâche, mais ne contient pas les résultats de la tâche.
Pour obtenir les résultats, utilisez l’applet de commande Receive-Job.

Une tâche en arrière-plan Windows PowerShell est une commande qui s’exécute en arrière-plan sans interagir avec la session active.
En règle générale, vous utilisez une tâche en arrière-plan pour exécuter une commande complexe qui prend beaucoup de temps.
Pour plus d'informations sur les tâches en arrière-plan, consultez about_Jobs.

À compter de Windows PowerShell 3.0, l'applet de commande **Get-Job** obtient également des types de tâche personnalisés, comme les tâches de workflow et les instances de tâches planifiées.
Pour rechercher le type d'une tâche, utilisez la propriété **PSJobTypeName** de la tâche.

Pour permettre à la **fonction** d’obtention d’un travail d’obtenir un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une commande **obtenir-Job** , soit à l’aide de l’applet de commande Import-Module, soit en utilisant ou en obtenant une applet de commande dans le module.
Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.

## EXEMPLES

### Exemple 1 : récupération de toutes les tâches en arrière-plan démarrées dans la session active

```
PS C:\> Get-Job
```

Cette commande obtient toutes les tâches en arrière-plan démarrées dans la session active.
Elle n'inclut pas les tâches créées dans d'autres sessions, même si elles s'exécutent sur l'ordinateur local.

### Exemple 2 : arrêter un travail à l’aide d’un ID d’instance

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

Ces commandes indiquent comment obtenir l'ID d'instance d'une tâche, puis l'utiliser pour arrêter une tâche.
Contrairement au nom de la tâche, qui n'est pas unique, l'ID d'instance est unique.

### Exemple 3 : obtenir des travaux qui incluent une commande spécifique

```
PS C:\> Get-Job -Command "*get-process*"
```

Cette commande obtient les tâches du système qui incluent une commande Get-Process.
La commande utilise le paramètre *Command* de **Get-Job** pour limiter le nombre de tâches récupérées.
La commande utilise des caractères génériques (*) pour obtenir les tâches qui incluent une commande **« obtenir un processus »** n’importe où dans la chaîne de commande.

### Exemple 4 : obtenir des travaux qui incluent une commande spécifique à l’aide du pipeline

```
PS C:\> "*get-process*" | Get-Job
```

À l’instar de la commande dans l’exemple précédent, cette commande obtient les tâches du système qui incluent une commande **« obtenir-traiter »** .
La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne, entre guillemets, à l’applet de commande **« obtenir-Job »** .
Elle est équivalente à la commande précédente.

### Exemple 5 : obtenir des travaux qui n’ont pas été démarrés

```
PS C:\> Get-Job -State NotStarted
```

Cette commande obtient uniquement les tâches qui ont été créées mais qui n'ont pas encore démarré.
Cela inclut les tâches dont l'exécution est planifiée ultérieurement et celles qui ne sont pas encore planifiées.

### Exemple 6 : obtenir des travaux auxquels aucun nom n’a été attribué

```
PS C:\> Get-Job -Name Job*
```

Cette commande obtient toutes les tâches dont le nom commence par Job.
Étant donné que Job \<number\> est le nom par défaut d’une tâche, cette commande obtient toutes les tâches qui n’ont pas de nom explicitement attribué.

### Exemple 7 : utiliser un objet de traitement pour représenter la tâche dans une commande

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

Cet exemple illustre comment utiliser **Get-Job** pour obtenir une tâche, puis comment utiliser l'objet de traitement pour représenter la tâche dans une commande.

### Exemple 8 : obtenir tous les travaux, y compris les travaux démarrés par une autre méthode

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

Cet exemple montre que l’applet de commande **« obtient-Job »** peut récupérer toutes les tâches qui ont été démarrées dans la session active, même si elles ont été démarrées à l’aide de différentes méthodes.

### Exemple 9 : examiner un travail ayant échoué

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
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

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

Cette commande montre comment utiliser l’objet de traitement retourné par la **fonction-Job** pour déterminer la raison de l’échec d’une tâche.
Elle illustre également comment obtenir les tâches enfant de chaque tâche.

### Exemple 10 : obtenir des résultats filtrés

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

Cet exemple indique comment utiliser le paramètre *Filter* pour obtenir une tâche de workflow.
Le paramètre *Filter* , introduit dans Windows PowerShell 3.0, n'est valide que sur les types de tâche personnalisé, comme les tâches de workflow et les tâches planifiées.

### Exemple 11 : obtenir des informations sur les tâches enfants

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
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

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
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

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

Cet exemple illustre l'utilisation des paramètres *IncludeChildJob* et *ChildJobState* de l'applet de commande **Get-Job** .

## PARAMETERS

### -Après

Obtient les tâches terminées après la date et l'heure spécifiées.
Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date ou une chaîne qui peut être convertie en un objet **DateTime** , tel que `Dec 1, 2012 2:00 AM` ou `11/06` .

Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** .
Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .
Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
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

Ce paramètre fonctionne uniquement sur les types de tâches personnalisés, comme les tâches de workflow et les tâches planifiées, qui ont une propriété **EndTime** .
Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles créées à l’aide de l’applet de commande **Start-Job** .
Pour plus d'informations sur la prise en charge de ce paramètre, consultez la rubrique d'aide relative au type de tâche.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
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
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
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

Lorsque vous utilisez l’applet de commande **Receive-Job** , elle supprime de son stockage propre à la session les résultats renvoyés.
Lorsqu’il a retourné tous les résultats de la tâche dans la session active, il définit la valeur de la propriété **HasMoreData** du travail sur $false) pour indiquer qu’il n’a plus de résultats pour le travail dans la session active.
Utilisez le paramètre *Keep* de **Receive-Job** pour empêcher **Receive-Job** de supprimer des résultats et de modifier la valeur de la propriété **HasMoreData** .
Pour plus d'informations, voir `Get-Help Receive-Job`.

La propriété **HasMoreData** est propre à la session active.
Si les résultats d’un type de tâche personnalisé sont enregistrés en dehors de la session, comme le type de tâche planifiée qui enregistre les résultats du travail sur le disque, vous pouvez utiliser l’applet de commande **Receive-Job** dans une autre session pour obtenir les résultats de la tâche, même si la valeur de **HasMoreData** est $false.
Pour plus d'informations, consultez les rubriques d'aide du type de tâche personnalisé.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
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
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
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
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
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

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)
