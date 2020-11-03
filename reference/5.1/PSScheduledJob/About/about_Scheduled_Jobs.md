---
description: Décrit les tâches planifiées et explique comment utiliser et gérer les tâches planifiées dans PowerShell et dans Planificateur de tâches.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207257"
---
# <a name="about-scheduled-jobs"></a>À propos des tâches planifiées

## <a name="short-description"></a>Description courte

Décrit les tâches planifiées et explique comment utiliser et gérer les tâches planifiées dans PowerShell et dans Planificateur de tâches.

## <a name="long-description"></a>Description longue

Les tâches planifiées PowerShell sont un hybride utile des tâches en arrière-plan PowerShell et des tâches de Planificateur de tâches.

Comme les tâches en arrière-plan PowerShell, les tâches planifiées s’exécutent de façon asynchrone en arrière-plan. Les instances de tâches planifiées qui ont été exécutées peuvent être gérées à l’aide des applets de commande Job, telles que `Start-Job` ,, `Get-Job` `Stop-Job` et `Receive-Job` .

À l’instar des tâches de Planificateur de tâches, les tâches planifiées sont enregistrées sur le disque. Vous pouvez afficher et gérer les travaux dans Planificateur de tâches, les activer et les désactiver si nécessaire, les exécuter ou les utiliser en tant que modèles, établir une planification ponctuelle ou périodique pour le démarrage des travaux, ou définir des conditions sous lesquelles les travaux démarrent.

En outre, les résultats des instances de tâche planifiée sont enregistrés sur le disque dans un format facilement accessible, ce qui fournit un journal des sorties de travail. Les travaux planifiés sont fournis avec un ensemble personnalisé d’applets de commande pour les gérer. Les applets de commande vous permettent de créer, modifier, gérer, désactiver et réactiver des tâches planifiées, des déclencheurs de tâche et des options de tâche.

Cet ensemble complet et flexible d’outils fait des tâches planifiées un composant essentiel de nombreuses solutions informatiques PowerShell professionnelles.

Les applets de commande de tâche planifiée sont incluses dans le module **PSScheduledJob** qui est installé avec PowerShell. Ce module a été introduit dans PowerShell 3,0 et fonctionne dans PowerShell 3,0 et versions ultérieures de PowerShell. Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).

Pour plus d’informations sur les travaux en arrière-plan PowerShell, consultez [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).

Pour plus d’informations sur Planificateur de tâches, consultez [Planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-reference).

> [!NOTE]
> Vous pouvez afficher et gérer les tâches planifiées PowerShell dans Planificateur de tâches. Les applets de commande travaux PowerShell et tâche planifiée fonctionnent uniquement sur les tâches planifiées qui sont créées dans PowerShell.

## <a name="quick-start"></a>Démarrage rapide

Cet exemple crée une tâche planifiée qui démarre tous les jours à 3:00 AM et exécute l’applet de commande `Get-Process` . Le travail démarre même si l’ordinateur fonctionne sur batterie.

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

L' `Get-ScheduledJob` applet de commande obtient les tâches planifiées sur l’ordinateur local.

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

`Get-JobTrigger` Obtient les déclencheurs de la tâche de **ProcessJob** . Les paramètres d’entrée spécifient la tâche planifiée, et non le déclencheur, car les déclencheurs sont enregistrés dans une tâche planifiée.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

Cet exemple utilise le paramètre **ContinueIfGoingOnBattery** de l' `Set-ScheduledJob` applet de commande pour modifier la propriété **StopIfGoingOnBatteries** de **ProcessJob** en **false** .

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

L' `Get-ScheduledJob` applet de commande obtient la tâche planifiée **ProcessJob** .

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

L' `Get-Job` applet de commande obtient toutes les instances de la tâche planifiée **ProcessJob** qui ont été exécutées jusqu’à présent. L' `Get-Job` applet de commande obtient les tâches planifiées uniquement lorsque le module **PSScheduledJob** est importé dans la session active.

> [!TIP]
> Notez que vous utilisez les applets de commande Job scheduled pour gérer les tâches planifiées, mais vous utilisez les applets de commande Job pour gérer les instances de tâches planifiées.

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

L' `Receive-Job` applet de commande obtient les résultats de l’instance la plus récente de la tâche planifiée **PROCESSJOB** (ID = 51).

```powershell
Receive-Job -ID 51
```

Même si la `Receive-Job` commande n’incluait pas le paramètre **Keep** , les résultats de la tâche sont enregistrés sur le disque jusqu’à ce que vous les supprimiez ou que le nombre maximal de résultats soit dépassé.

Les résultats de la tâche ne sont plus disponibles dans cette session, mais si vous démarrez une nouvelle session ou ouvrez une nouvelle fenêtre PowerShell, les résultats du travail sont à nouveau disponibles.

La commande suivante utilise le paramètre **DefinitionName** de l' `Start-Job` applet de commande pour démarrer la tâche planifiée **ProcessJob** .

Les tâches démarrées à l’aide de l' `Start-Job` applet de commande sont des travaux en arrière-plan PowerShell standard, et non des instances de la tâche planifiée. Comme pour toutes les tâches en arrière-plan, ces travaux démarrent immédiatement, ils ne sont pas soumis à des options de travail ou affectés par des déclencheurs de tâche, et leur sortie n’est pas enregistrée dans le répertoire de sortie du répertoire de travail planifié.

```powershell
Start-Job -DefinitionName ProcessJob
```

L' `Unregister-ScheduledJob` applet de commande supprime la tâche planifiée **ProcessJob** et tous les résultats enregistrés de ses instances de travail.

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a>Concepts des tâches planifiées

Une tâche planifiée exécute des commandes ou un script. Une tâche planifiée peut inclure des déclencheurs de tâche qui démarrent les options de tâche et de travail qui définissent des conditions d’exécution du travail.

Un déclencheur de tâche démarre automatiquement une tâche planifiée. Un déclencheur de tâche peut inclure une planification ponctuelle ou périodique, ou spécifier un événement, par exemple lorsqu’un utilisateur ouvre une session ou que Windows démarre. Une tâche planifiée peut avoir un ou plusieurs déclencheurs de tâche, et vous pouvez créer, ajouter, activer, désactiver et obtenir des déclencheurs de tâche.

Les déclencheurs de tâche sont facultatifs. Vous pouvez démarrer des tâches planifiées immédiatement à l’aide de l' `Start-Job cmdlet` ou en ajoutant le paramètre **RunNow** à votre `Register-ScheduledJob` commande.

Les options de travail définissent les conditions d’exécution d’une tâche planifiée. Chaque tâche planifiée a un objet d’options de tâche. Vous pouvez créer et modifier des objets d’options de tâche et les ajouter à une ou plusieurs tâches planifiées.

Chaque fois qu’une tâche planifiée démarre, une instance de tâche est créée. Utilisez les applets de commande PowerShell Job pour afficher et gérer l’instance de tâche.

Les tâches planifiées sont enregistrées sur le disque et utilisent le verbe d’applet de commande, `Register` , au lieu de `New` . Les fichiers XML se trouvent sur l’ordinateur local dans le répertoire `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .

PowerShell crée un répertoire pour chaque tâche planifiée et enregistre les commandes de travail, les déclencheurs de tâche, les options de tâche et les résultats de travail dans le répertoire de travail planifié. Les déclencheurs de tâche et les options de tâche ne sont pas enregistrés sur le disque indépendamment.
Elles sont enregistrées dans le fichier XML de tâches planifiées de chaque tâche planifiée à laquelle elles sont associées.

Les tâches planifiées, les déclencheurs de tâche et les options de tâche s’affichent dans PowerShell en tant qu’objets.
Les objets sont liés entre eux, ce qui facilite leur découverte et leur utilisation dans les commandes et les scripts.

Les tâches planifiées apparaissent en tant qu’objets **ScheduledJobDefinition** . L’objet **ScheduledJobDefinition** a une propriété **JobTriggers** qui contient les déclencheurs de la tâche planifiée et une propriété **options** qui contient les options du travail. Les objets **ScheduledJobTriggers** et **ScheduledJobOptions** qui représentent les déclencheurs de tâche et les options de tâche, respectivement, ont chacun une propriété **JobDefinition** qui contient la tâche planifiée à laquelle ils sont associés. Cette interconnexion récursive permet de trouver facilement les déclencheurs et les options d’une tâche planifiée, ainsi que de rechercher, de générer un script et d’afficher la tâche planifiée à laquelle n’importe quel déclencheur de tâche ou option de travail est associé.

## <a name="see-also"></a>Voir aussi

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)

[Planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-reference)
