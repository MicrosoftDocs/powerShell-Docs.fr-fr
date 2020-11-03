---
description: Explique comment créer et gérer des tâches planifiées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207250"
---
# <a name="about-scheduled-jobs-basics"></a>À propos des notions de base des tâches planifiées

## <a name="short-description"></a>Description courte

Explique comment créer et gérer des tâches planifiées.

## <a name="long-description"></a>Description longue

Ce document montre comment effectuer des tâches de base pour créer et gérer des tâches planifiées. Pour plus d’informations sur les tâches plus avancées, consultez [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).

Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).

## <a name="how-to-create-a-scheduled-job"></a>Comment créer une tâche planifiée

Pour créer une tâche planifiée, utilisez l’applet de commande `Register-ScheduledJob` . L’applet de commande requiert un nom et les commandes ou le script exécutés par la tâche. Vous pouvez exécuter la tâche immédiatement en ajoutant le paramètre **RunNow** , ou créer un déclencheur de tâche et définir les options de travail lorsque vous créez le travail, ou modifier un travail existant.

Pour créer un travail qui exécute un script, utilisez le paramètre **filePath** pour spécifier le chemin d’accès au fichier de script. Pour créer un travail qui exécute des commandes, utilisez le paramètre **scriptblock** .

L' `Register-ScheduledJob` applet de commande crée le **ProcessJob** , qui exécute une `Get-Process` commande. Cette tâche planifiée a les options de travail par défaut et aucun déclencheur de tâche.

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a>Comment créer un déclencheur de tâche

Les déclencheurs de tâche démarrent automatiquement une tâche planifiée. Un déclencheur de tâche peut être une planification ponctuelle ou périodique, ou un événement, par exemple lorsqu’un utilisateur ouvre une session ou que Windows démarre. Chaque travail peut avoir zéro, un ou plusieurs déclencheurs de tâche.

Pour créer un déclencheur de tâche, utilisez l’applet de commande `New-JobTrigger` . La commande suivante crée un déclencheur de tâche qui démarre une tâche tous les lundis et jeudi à 5:00 AM.
La commande enregistre le déclencheur de tâche dans la `$T` variable.

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

Les déclencheurs de tâche sont facultatifs. Vous pouvez démarrer une tâche planifiée à tout moment en ajoutant le paramètre **RunNow** à votre `Register-ScheduledJob` commande ou en utilisant les `Start-Job` applets de commande.

## <a name="how-to-add-a-job-trigger"></a>Ajout d’un déclencheur de tâche

Lorsque vous ajoutez un déclencheur de tâche à une tâche planifiée, le déclencheur de tâche est ajouté au fichier XML de la tâche planifiée pour la tâche planifiée et devient partie intégrante de la tâche planifiée.

Vous pouvez ajouter un déclencheur de tâche à une tâche planifiée lorsque vous créez la tâche planifiée, ou modifier un travail existant. Vous pouvez modifier le déclencheur d’une tâche planifiée à tout moment.

PowerShell utilise certains des déclencheurs de tâche que Planificateur de tâches utilise. Pour plus d’informations sur les déclencheurs de tâche, consultez la rubrique d’aide de l’applet de commande [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) .

L’exemple suivant utilise la projection pour créer `$JobParms` des valeurs de paramètre qui sont passées à l’applet de commande `Register-ScheduledJob` . Pour plus d’informations, consultez [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).
Le `Register-ScheduledJob` utilise `@JobParms` pour créer une tâche planifiée. Elle utilise le paramètre **Trigger** pour spécifier le déclencheur de tâche dans la `$T` variable.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

Vous pouvez également ajouter un déclencheur de tâche à une tâche planifiée existante à tout moment. L' `Add-JobTrigger` applet de commande ajoute le déclencheur de tâche dans la `$T` variable à la tâche planifiée **ProcessJob** .

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

Par conséquent, le déclencheur de tâche démarre automatiquement le **ProcessJob** tous les lundis et jeudi à 5:00 AM.

## <a name="how-to-get-a-job-trigger"></a>Obtention d’un déclencheur de tâche

Pour obtenir le déclencheur d’une tâche planifiée, utilisez l’applet de commande `Get-JobTrigger` . Utilisez les paramètres **Name** , **ID** et **InputObject** pour spécifier la tâche planifiée, et non le déclencheur de tâche.

`Get-JobTrigger` Obtient le déclencheur de la tâche du **ProcessJob** .

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a>Comment créer des options de tâche

Les options de tâche établissent des conditions de démarrage et d’exécution du travail. Chaque travail dispose des options de travail par défaut, sauf si vous les modifiez. Étant donné que les options de tâche peuvent empêcher l’exécution d’un travail à l’heure planifiée, il est important de comprendre les options des tâches et de les utiliser avec précaution.

PowerShell utilise les mêmes options de travail que celles que Planificateur de tâches utilise. Pour plus d’informations sur les options de tâche, consultez la rubrique d’aide [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).

Les options de tâche sont stockées dans le fichier XML de la tâche planifiée. Vous pouvez définir des options de tâche lorsque vous créez une tâche planifiée ou que vous modifiez à tout moment.

L' `New-ScheduledJobOption` applet de commande crée une option de tâche planifiée dans laquelle l’option de tâche planifiée **WakeToRun** a la valeur true. L’option **WakeToRun** exécute la tâche planifiée même si l’ordinateur est en mode veille ou veille prolongée à l’heure de début planifiée. La commande enregistre les options de tâche dans la `$O` variable.

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a>Comment récupérer des options de tâche

Pour obtenir les options de tâche d’une tâche planifiée, utilisez l’applet de commande `Get-ScheduledJobOption` . Utilisez les paramètres **Name** , **ID** et **InputObject** pour spécifier la tâche planifiée, et non les options du travail.

`Get-ScheduledJobOption` Obtient les options de tâche du **ProcessJob** .

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
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
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

## <a name="how-to-change-job-options"></a>Comment modifier les options d’un travail

Vous pouvez modifier les options de tâche d’une tâche planifiée lorsque vous créez une tâche planifiée ou modifiez une tâche existante.

Le `$JobParms` projet de tâche est passé à l' `Add-JobTrigger` applet de commande pour créer le travail de processus. Elle utilise le paramètre **ScheduledJobOption** pour spécifier les options de tâche dans la `$O` variable.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

Vous pouvez également modifier les options de travail en fonction d’une tâche planifiée existante à tout moment.
La commande suivante utilise l' `Set-ScheduledJobOption` applet de commande pour modifier la valeur de l’option **WakeToRun** de **ProcessJob** scheduledJob sur **true** .

Les `Set` applets de commande du module **PSScheduledJob** , telles que l’applet de commande `Set-ScheduledJobOption` , n’ont pas de paramètres **Name** ou **ID** . Vous pouvez utiliser le paramètre **InputObject** pour spécifier les options de tâche planifiée ou diriger une tâche planifiée de l' `Get-ScheduledJobOption` applet de commande vers `Set-ScheduledJobOption` .

Cet exemple utilise l' `Get-ScheduledJob` applet de commande pour récupérer ProcessJob. Elle utilise l' `Get-ScheduledJobOption` applet de commande pour récupérer les options de tâche dans le **ProcessJob** et l' `Set-ScheduledJobOption` applet de commande pour remplacer l’option de tâche **WakeToRun** dans le ProcessJob par true.

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a>Procédure d’obtention d’instances de tâche planifiée

Lorsqu’une tâche planifiée est démarrée, PowerShell crée une instance de tâche similaire à une tâche en arrière-plan PowerShell standard. Vous pouvez utiliser les applets de commande Job, telles que `Get-Job` , `Stop-Job` et `Receive-Job` pour gérer les instances de tâche.

> [!NOTE]
> Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session. Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .

Pour récupérer toutes les instances de tâches planifiées PowerShell et tous les travaux standard actifs, utilisez l’applet de commande `Get-Job` . L' `Import-Module` applet de commande importe le module **PSScheduledJob** et `Get-Job` obtient les tâches sur l’ordinateur local.

```powershell
Import-Module PSScheduledJob
Get-Job
```

`Get-Job` obtient des instances de **ProcessJob** sur l’ordinateur local.

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

L’affichage par défaut n’affiche pas l’heure de début, ce qui fait généralement la distinction entre les instances de la même tâche planifiée.

L' `Get-Job` applet de commande envoie des objets dans le pipeline. L' `Format-Table` applet de commande affiche les propriétés **Name** , **ID** et **BeginTime** de la tâche planifiée.

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

## <a name="get-scheduled-job-results"></a>Obtenir les résultats de la tâche planifiée

Pour obtenir les résultats d’une instance d’une tâche planifiée, utilisez l’applet de commande `Receive-Job` .

> [!NOTE]
> Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session. Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .

Cet exemple obtient les résultats de l’instance la plus récente de la tâche planifiée **ProcessJob** (ID = 51).

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

Les résultats des tâches planifiées sont enregistrés sur le disque, donc le paramètre **Keep** de `Receive-Job` n’est pas obligatoire. Toutefois, sans le paramètre **Keep** , vous pouvez obtenir les résultats d’une tâche planifiée une seule fois dans chaque session PowerShell. Pour démarrer une nouvelle session PowerShell, tapez `PowerShell` ou ouvrez une nouvelle fenêtre PowerShell.

## <a name="see-also"></a>Voir aussi

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)

[Planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-reference)
