---
description: Fournit des détails sur les tâches en arrière-plan sur les ordinateurs locaux et distants.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: cd6c633e9f409054b0ee89021de961c36d84ac3b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208574"
---
# <a name="about-job-details"></a>À propos des détails de la tâche

## <a name="short-description"></a>Description courte
Fournit des détails sur les tâches en arrière-plan sur les ordinateurs locaux et distants.

## <a name="detailed-description"></a>Description détaillée

Cette rubrique explique le concept de tâche en arrière-plan et fournit des informations techniques sur le fonctionnement des tâches en arrière-plan dans PowerShell.

Cette rubrique est un complément des rubriques [about_Jobs](about_Jobs.md), [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)et [about_Remote_Jobs](about_Remote_Jobs.md) .

### <a name="about-background-jobs"></a>À propos des tâches en arrière-plan

Une tâche en arrière-plan exécute une commande ou une expression de manière asynchrone. Il peut exécuter une applet de commande, une fonction, un script ou toute autre tâche basée sur une commande. Il est conçu pour exécuter des commandes qui prennent un certain temps, mais vous pouvez l’utiliser pour exécuter n’importe quelle commande en arrière-plan.

Lorsqu’une commande synchrone s’exécute, l’invite de commandes PowerShell est supprimée jusqu’à ce que la commande soit terminée. Toutefois, un travail en arrière-plan ne supprime pas l’invite PowerShell. Une commande permettant de démarrer une tâche en arrière-plan retourne un objet de traitement.
L’invite s’affiche immédiatement pour vous permettre de travailler sur d’autres tâches pendant l’exécution de la tâche en arrière-plan.

Toutefois, lorsque vous démarrez une tâche en arrière-plan, vous ne recevez pas les résultats immédiatement, même si le travail s’exécute très rapidement. L’objet de traitement retourné contient des informations utiles sur la tâche, mais elle ne contient pas les résultats de la tâche. Vous devez exécuter une commande distincte pour obtenir les résultats de la tâche. Vous pouvez également exécuter des commandes pour arrêter la tâche, attendre la fin de la tâche et supprimer la tâche.

Pour effectuer la synchronisation d’un travail en arrière-plan indépendamment d’autres commandes, chaque travail en arrière-plan s’exécute dans sa propre session PowerShell. Toutefois, il peut s’agir d’une connexion temporaire qui est créée uniquement pour exécuter le travail et qui est ensuite détruite, ou il peut s’agir d’une **session PSSession** permanente que vous pouvez utiliser pour exécuter plusieurs tâches ou commandes associées.

### <a name="using-the-job-cmdlets"></a>Utilisation des applets de commande Job

Utilisez une `Start-Job` commande pour démarrer une tâche en arrière-plan sur un ordinateur local.
`Start-Job` retourne un objet de traitement. Vous pouvez également récupérer des objets représentant les tâches qui ont été démarrées sur l’ordinateur local à l’aide de l’applet de commande `Get-Job` .

Pour obtenir les résultats du travail, utilisez une `Receive-Job` commande. Si la tâche n’est pas terminée, `Receive-Job` retourne des résultats partiels. Vous pouvez également utiliser l' `Wait-Job` applet de commande pour supprimer l’invite de commandes jusqu’à ce qu’une ou toutes les tâches démarrées dans la session soient terminées.

Pour arrêter une tâche en arrière-plan, utilisez l’applet de commande `Stop-Job` . Pour supprimer un travail, utilisez l' `Remove-Job` applet de commande.

Pour plus d’informations sur le fonctionnement des applets de commande, consultez la rubrique d’aide pour chaque applet de commande et consultez [about_Jobs](about_Jobs.md).

### <a name="starting-background-jobs-on-remote-computers"></a>Démarrage des tâches en arrière-plan sur des ordinateurs distants

Vous pouvez créer et gérer des tâches en arrière-plan sur un ordinateur local ou distant. Pour exécuter une tâche en arrière-plan à distance, utilisez le paramètre **AsJob** d’une applet de commande telle que `Invoke-Command` , ou utilisez l' `Invoke-Command` applet de commande pour exécuter une `Start-Job` commande à distance. Vous pouvez également démarrer une tâche en arrière-plan dans une session interactive.

Pour plus d’informations sur les travaux en arrière-plan distants, consultez [about_Remote_Jobs](about_Remote_Jobs.md).

### <a name="child-jobs"></a>Travaux enfants

Chaque travail en arrière-plan est constitué d’un travail parent et d’un ou plusieurs travaux enfants. Dans les tâches démarrées à l’aide `Start-Job` de ou du paramètre **AsJob** de `Invoke-Command` , le travail parent est un dirigeant. Elle n’exécute aucune commande et ne retourne aucun résultat. Les commandes sont exécutées en fait par les tâches enfants. Les travaux démarrés à l’aide d’autres applets de commande peuvent fonctionner différemment.

Les tâches enfants sont stockées dans la propriété **ChildJobs** de l’objet de tâche parent. La propriété **ChildJobs** peut contenir un ou plusieurs objets de tâche enfants.
Les objets de travail enfants ont un **nom** , un **ID** et un **InstanceID** qui diffèrent du travail parent, ce qui vous permet de gérer les travaux parent et enfant individuellement ou en tant qu’unité.

Pour obtenir les tâches parent et enfant d’un travail, utilisez le paramètre **IncludeChildJobs** de l' `Get-Job` applet de commande. Le paramètre **IncludeChildJob** a été introduit dans Windows PowerShell 3,0.

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Pour obtenir le travail parent et uniquement les tâches enfants avec une valeur d' **État** particulière, utilisez le paramètre **ChildJobState** de l’applet de commande `Get-Job` . Le paramètre **ChildJobState** a été introduit dans Windows PowerShell 3,0.

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Pour obtenir les tâches enfants d’un travail sur toutes les versions de PowerShell, utilisez la propriété **ChildJob** de la tâche parente.

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Vous pouvez également utiliser une `Get-Job` commande sur le travail enfant, comme indiqué dans la commande suivante :

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

La configuration du travail enfant dépend de la commande que vous utilisez pour démarrer le travail.

- Lorsque vous utilisez `Start-Job` pour démarrer un travail sur un ordinateur local, le travail se compose d’un travail parent exécutif et d’un travail enfant qui exécute la commande.

- Quand vous utilisez le paramètre **AsJob** de `Invoke-Command` pour démarrer un travail sur un ou plusieurs ordinateurs, le travail se compose d’un travail parent et d’un travail enfant pour chaque travail exécuté sur chaque ordinateur.

- Lorsque vous utilisez `Invoke-Command` pour exécuter une `Start-Job` commande sur un ou plusieurs ordinateurs distants, le résultat est le même qu’une commande locale exécutée sur chaque ordinateur distant. La commande retourne un objet de traitement pour chaque ordinateur. L’objet de traitement est constitué d’un travail parent et d’un travail enfant qui exécute la commande.

La tâche parente représente toutes les tâches enfants. Lorsque vous gérez un travail parent, vous gérez également les tâches enfants associées. Par exemple, si vous arrêtez un travail parent, toutes les tâches enfants sont arrêtées. Si vous récupérez les résultats d’une tâche parente, vous pouvez obtenir les résultats de toutes les tâches enfants.

Toutefois, vous pouvez également gérer les tâches enfants individuellement. Cela est très utile lorsque vous souhaitez examiner un problème lié à un travail ou obtenir les résultats d’un seul nombre de travaux enfants démarrés à l’aide du paramètre **AsJob** de `Invoke-Command` .

La commande suivante utilise le paramètre **AsJob** de `Invoke-Command` pour démarrer des tâches en arrière-plan sur l’ordinateur local et sur deux ordinateurs distants. La commande enregistre la tâche dans la `$j` variable.

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

Lorsque vous affichez les propriétés Name et **ChildJob** de la tâche dans `$j` , elle indique que la commande a retourné un objet de traitement avec trois tâches enfants, une pour chaque ordinateur.

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

Lorsque vous affichez le travail parent, il indique que le travail a échoué.

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

Toutefois, lorsque vous exécutez une `Get-Job` commande qui obtient les tâches enfants, la sortie indique qu’une seule tâche enfant a échoué.

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

Pour obtenir les résultats de toutes les tâches enfants, utilisez l' `Receive-Job` applet de commande pour obtenir les résultats de la tâche parente. Toutefois, vous pouvez également obtenir les résultats d’un travail enfant particulier, comme indiqué dans la commande suivante.

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

La fonctionnalité tâches enfants des tâches en arrière-plan PowerShell vous donne davantage de contrôle sur les tâches que vous exécutez.

### <a name="job-types"></a>Types de travaux

PowerShell prend en charge différents types de tâches pour différentes tâches. À compter de Windows PowerShell 3,0, les développeurs peuvent écrire des « adaptateurs de source de tâche » qui ajoutent de nouveaux types de travaux à PowerShell et incluent les adaptateurs de source de travail dans les modules.
Lorsque vous importez le module, vous pouvez utiliser le nouveau type de travail dans votre session.

Par exemple, le module PSScheduledJob ajoute des tâches planifiées et le module PSWorkflow ajoute des tâches de Workflow.

Les types de tâches personnalisées peuvent différer considérablement des tâches en arrière-plan PowerShell standard. Par exemple, les tâches planifiées sont enregistrées sur le disque. ils n’existent pas uniquement dans une session particulière. Les tâches de workflow peuvent être suspendues et reprises.

Les applets de commande que vous utilisez pour gérer les tâches personnalisées dépendent du type de travail. Pour certains, vous utilisez les applets de commande de tâche standard, telles que `Get-Job` et `Start-Job` . D’autres sont fournies avec des applets de commande spécialisées qui gèrent uniquement un type particulier de tâche. Pour plus d’informations sur les types de tâches personnalisés, consultez les rubriques d’aide sur le type de travail.

Pour rechercher le type de tâche d’un travail, utilisez l’applet de commande `Get-Job` . `Get-Job` Retourne différents objets de travail pour différents types de travaux. La valeur de la propriété **PSJobTypeName** des objets de traitement qui `Get-Job` retourne indique le type de travail.

Le tableau suivant répertorie les types de travaux fournis avec PowerShell.

|    Type de travail    |                       Description                        |
| -------------- | -------------------------------------------------------- |
| BackgroundJob  | A démarré à l’aide de l’applet de commande `Start-Job` .                    |
| RemoteJob      | Démarré à l’aide du paramètre **AsJob** de l'             |
|                | `Invoke-Command`.                                 |
| PSWorkflowJob  | A démarré à l’aide du paramètre **AsJob** d’un Workflow.     |
| PSScheduledJob | Instance d’une tâche planifiée démarrée par un déclencheur de tâche. |
| CIMJob         | Démarré à l’aide du paramètre **AsJob** d’une applet de commande à partir d’un |
|                | Module CDXML.                                            |
| WMIJob         | Démarré à l’aide du paramètre **AsJob** d’une applet de commande à partir d’un |
|                | Module WMI.                                              |
| PSEventJob     | Créé à l’aide `Register-ObjectEvent` de et en spécifiant un    |
|                | action avec le paramètre d' **action** .                    |

Remarque : avant d’utiliser l’applet de commande `Get-Job` pour obtenir des travaux d’un type particulier, vérifiez que le module qui ajoute le type de travail est importé dans la session active.
Dans le cas contraire, `Get-Job` n’obtient pas les travaux de ce type.

## <a name="examples"></a>Exemples

Les commandes suivantes créent une tâche en arrière-plan locale, une tâche en arrière-plan à distance, une tâche de workflow et une tâche planifiée. Elle utilise ensuite l' `Get-Job` applet de commande pour récupérer les tâches. `Get-Job` n’obtient pas la tâche planifiée, mais elle obtient toutes les instances démarrées de la tâche planifiée.

Démarrez une tâche en arrière-plan sur l’ordinateur local.

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

Démarrez une tâche en arrière-plan qui s’exécute sur un ordinateur distant.

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

Créer une tâche planifiée

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

Créer un flux de travail.

```powershell
PS> workflow Test-Workflow {Get-Process}
```

Exécutez le workflow en tant que tâche.

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

Obtient les tâches. La `Get-Job` commande n’obtient pas les tâches planifiées, mais elle obtient les instances de la tâche planifiée qui sont démarrées.

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

Pour accéder aux tâches planifiées, utilisez l’applet de commande `Get-ScheduledJob` .

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a>Voir aussi

- [about_Jobs](about_Jobs.md)
- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)
- [about_Remote](about_Remote.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
