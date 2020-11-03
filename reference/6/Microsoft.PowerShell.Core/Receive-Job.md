---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 0d22f99341c487d2bd1b64d621cdca99d20e5328
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204489"
---
# Receive-Job

## SYNOPSIS
Obtient les résultats des tâches en arrière-plan PowerShell dans la session active.

## SYNTAX

### Emplacement (par défaut)

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### ComputerName

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### session

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### NameParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### SessionIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## Description

L' `Receive-Job` applet de commande obtient les résultats des travaux en arrière-plan PowerShell, tels que ceux démarrés à l’aide de l' `Start-Job` applet de commande ou du paramètre **AsJob** d’une applet de commande.
Vous pouvez obtenir les résultats de toutes les tâches ou identifier les tâches par leur nom, ID, ID d'instance, nom d'ordinateur, emplacement ou session, ou en envoyant un objet de traitement.

Quand vous démarrez une tâche en arrière-plan PowerShell, le travail démarre, mais les résultats n’apparaissent pas immédiatement. À la place, la commande retourne un objet qui représente la tâche en arrière-plan.
L'objet de traitement contient les informations utiles sur la tâche, mais pas les résultats.
Cette méthode vous permet de continuer à travailler dans la session pendant l’exécution de la tâche.
Pour plus d’informations sur les tâches en arrière-plan dans PowerShell, consultez [about_Jobs](./About/about_Jobs.md).

L' `Receive-Job` applet de commande obtient les résultats qui ont été générés au moment de l’envoi de la `Receive-Job` commande.
Si les résultats ne sont pas encore terminés, vous pouvez exécuter des `Receive-Job` commandes supplémentaires pour obtenir les résultats restants.

Par défaut, les résultats de la tâche sont supprimés du système lorsque vous les recevez, mais vous pouvez utiliser le paramètre **Keep** pour enregistrer les résultats afin de les recevoir à nouveau.
Pour supprimer les résultats du travail, exécutez `Receive-Job` à nouveau la commande sans le paramètre **Keep** , fermez la session ou utilisez l' `Remove-Job` applet de commande pour supprimer la tâche de la session.

À compter de Windows PowerShell 3,0, `Receive-Job` obtient également les résultats des types de tâches personnalisées, tels que les tâches de workflow et les instances de tâches planifiées.
Pour permettre `Receive-Job` à d’obtenir les résultats d’un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter une `Receive-Job` commande, soit à l’aide de l’applet de commande, soit `Import-Module` en utilisant ou en obtenant une applet de commande dans le module.
Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.

## EXEMPLES

### Exemple 1 : obtenir les résultats d’une tâche particulière

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

Ces commandes utilisent le paramètre **Job** de `Receive-Job` pour obtenir les résultats d’une tâche particulière.

La première commande démarre un travail avec `Start-Job` et stocke l’objet de traitement dans la `$job` variable.

La deuxième commande utilise l' `Receive-Job` applet de commande pour obtenir les résultats du travail.
Elle utilise le paramètre **Job** pour spécifier la tâche.

### Exemple 2 : utiliser le paramètre Keep

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

Cet exemple stocke un travail dans la `$job` variable et le dirige vers l’applet de commande `Receive-Job` . Le `-Keep` paramètre est également utilisé pour permettre la récupération de toutes les données de flux agrégées après la première vue.

### Exemple 3 : obtenir les résultats de plusieurs tâches en arrière-plan

Quand vous utilisez le paramètre **AsJob** de `Invoke-Command` pour démarrer un travail, l’objet de traitement est créé sur l’ordinateur local, même si le travail s’exécute sur les ordinateurs distants.
Par conséquent, vous utilisez des commandes locales pour gérer la tâche.

En outre, lorsque vous utilisez **AsJob** , PowerShell retourne un objet de traitement qui contient un travail enfant pour chaque travail démarré. Dans ce cas, l'objet de traitement contient trois tâches enfants, une pour chaque tâche sur chaque ordinateur distant.

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### Exemple 4 : obtenir les résultats des tâches en arrière-plan sur plusieurs ordinateurs distants

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

Cet exemple montre comment obtenir les résultats des tâches en arrière-plan exécutées sur trois ordinateurs distants.
Contrairement à l’exemple précédent, l’utilisation `Invoke-Command` de pour exécuter la `Start-Job` commande a fait démarrer trois tâches indépendantes sur chacun des trois ordinateurs. Par conséquent, la commande a retourné trois objets de travail représentant trois tâches exécutées localement sur trois ordinateurs différents.

> [!NOTE]
> Dans la dernière commande, étant donné que `$j` est une variable locale, le bloc de script utilise le modificateur d’étendue **using** pour identifier la `$j` variable. Pour plus d’informations sur le modificateur d’étendue **using** , consultez [about_Remote_Variables](./About/about_Remote_Variables.md).

### Exemple 5 : accéder aux tâches enfants

Le `-Keep` paramètre conserve l’état des flux agrégés d’un travail afin qu’il puisse être affiché à nouveau. Sans ce paramètre, toutes les données de flux agrégées sont effacées lors de la réception du travail. Pour plus d’informations, consultez [about_Job_Details](About/about_Job_Details.md#child-jobs)

> [!NOTE]
> Les flux agrégés incluent les flux de toutes les tâches enfants. Vous pouvez toujours atteindre les flux de données individuels via l’objet de tâche et les objets de travail enfants.

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## PARAMETERS

### -AutoRemoveJob

Indique que cette applet de commande supprime le travail après avoir retourné les résultats de la tâche.
Si le travail a plus de résultats, le travail est toujours supprimé, mais `Receive-Job` affiche un message.

Ce paramètre fonctionne uniquement sur les types de tâches personnalisées.
Il est conçu pour les instances de types de tâches qui enregistrent la tâche ou le type en dehors de la session, telles que les instances de tâches planifiées.

Ce paramètre ne peut pas être utilisé sans le paramètre **Wait** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -ComputerName

Spécifie un tableau de noms d’ordinateurs.

Ce paramètre procède à une sélection parmi les résultats des tâches stockés sur l'ordinateur local.
Il n’obtient pas de données pour les travaux exécutés sur des ordinateurs distants.
Pour obtenir des résultats de travail stockés sur des ordinateurs distants, utilisez l' `Invoke-Command` applet de commande pour exécuter une `Receive-Job` commande à distance.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Force

Indique que cette applet de commande continue à attendre si les tâches sont dans l’état **Suspended** ou **Disconnected** . Par défaut, le paramètre **Wait** de `Receive-Job` retourne ou met fin à l’attente, lorsque les tâches sont dans l’un des États suivants :

- Completed
- Échec
- Arrêté
- Interrompu
- Déconnecté.

Le paramètre **Force** n'est valide que lorsque le paramètre **Wait** est également utilisé dans la commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -Id

Spécifie un tableau d'ID.
Cette applet de commande obtient les résultats des tâches avec les ID spécifiés.

L’ID est un entier qui identifie de façon unique le travail dans la session active.
Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active. Vous pouvez taper un ou plusieurs ID séparés par des virgules.
Pour Rechercher l’ID d’un travail, utilisez `Get-Job` .

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

Spécifie un tableau d’ID d’instance.
Cette applet de commande obtient les résultats des tâches avec les ID d’instance spécifiés.

Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur.
Pour Rechercher l’ID d’instance d’un travail, utilisez l’applet de commande `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Travail

Spécifie la tâche pour laquelle les résultats sont récupérés.

Entrez une variable qui contient la tâche ou une commande qui obtient la tâche.
Vous pouvez également diriger un objet de traitement vers `Receive-Job` .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Conserver

Indique que cette applet de commande enregistre les données de flux agrégées dans le système, même après que vous les avez reçues. Par défaut, les données de flux agrégées sont effacées après leur affichage avec `Receive-Job` .

La fermeture de la session ou la suppression de la tâche avec l’applet de commande `Remove-Job` supprime également les données de flux agrégées.

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

### -Location

Spécifie un tableau d’emplacements.
Cette applet de commande obtient uniquement les résultats des tâches aux emplacements spécifiés.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms conviviaux.
Cette applet de commande obtient les résultats des tâches qui ont les noms spécifiés.
Les caractères génériques sont pris en charge.

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

### -Norécurrent

Indique que cette applet de commande obtient les résultats uniquement à partir du travail spécifié.
Par défaut, `Receive-Job` obtient également les résultats de toutes les tâches enfants du travail spécifié.

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

### -Session

Spécifie un tableau de sessions.
Cette applet de commande obtient les résultats des tâches qui ont été exécutées dans la session PowerShell spécifiée ( **PSSession** ).
Entrez une variable qui contient la **session PSSession** ou une commande qui obtient la **session PSSession** , telle qu’une `Get-PSSession` commande.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wait

Indique que cette applet de commande supprime l’invite de commandes jusqu’à ce que tous les résultats de la tâche soient reçus.
Par défaut, `Receive-Job` retourne immédiatement les résultats disponibles.

Par défaut, le paramètre **Wait** attend jusqu'à ce que la tâche soit dans l'un des états suivants :

- Completed
- Échec
- Arrêté
- Interrompu
- Déconnecté.

Pour indiquer au paramètre **Wait** de continuer à attendre si l’état du travail est Suspended ou Disconnected, utilisez le paramètre **force** avec le paramètre **Wait** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -WriteEvents

Indique que cette applet de commande signale les modifications de l’état du travail pendant qu’elle attend la fin du travail.

Ce paramètre est valide uniquement quand le paramètre **Wait** est utilisé dans la commande et que le paramètre **Keep** est omis.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -WriteJobInResults

Indique que cette applet de commande retourne l’objet de traitement suivi des résultats.

Ce paramètre est valide uniquement quand le paramètre **Wait** est utilisé dans la commande et que le paramètre **Keep** est omis.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).

## ENTRÉES

### System. Management. Automation. job

Vous pouvez diriger les objets de travail vers cette applet de commande.

## SORTIES

### PSObject

Cette applet de commande retourne les résultats des commandes dans le travail.

## REMARQUES

## LIENS CONNEXES

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)
