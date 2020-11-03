---
description: Décrit les rubriques avancées sur les tâches planifiées, y compris la structure de fichier sous-jacente aux tâches planifiées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207254"
---
# <a name="about-scheduled-jobs-advanced"></a>À propos des tâches planifiées avancées

## <a name="short-description"></a>Description courte

Décrit les rubriques avancées sur les tâches planifiées, y compris la structure de fichier sous-jacente aux tâches planifiées.

## <a name="long-description"></a>Description longue

Pour plus d’informations sur les applets de commande contenues dans le module **PSScheduledJob** , consultez [PSScheduledJob](xref:PSScheduledJob).

## <a name="scheduled-job-directories-and-files"></a>Fichiers et répertoires de travail planifiés

Les tâches planifiées PowerShell sont à la fois des travaux PowerShell et des tâches de Planificateur de tâches.
Chaque tâche planifiée est enregistrée dans Planificateur de tâches et enregistrée sur le disque au format XML de sérialisation Microsoft .NET Framework.

Lorsque vous créez une tâche planifiée, PowerShell crée un répertoire pour la tâche planifiée dans le `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` Répertoire de l’ordinateur local. Le nom du répertoire est le même que le nom du travail.

Voici un exemple de répertoire **ScheduledJobs** .

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

Chaque tâche planifiée a son propre répertoire. Le répertoire contient le fichier XML de la tâche planifiée et un sous-répertoire de **sortie** .

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

Le répertoire de **sortie** d’une tâche planifiée contient son historique d’exécution.
Chaque fois qu’un déclencheur de tâche démarre une tâche planifiée, PowerShell crée un répertoire nommé timestamp dans le répertoire de sortie. Le répertoire horodateur contient les résultats de la tâche dans un fichier **Results.xml** et l’état du travail dans un fichier **Status.xml** .

La commande suivante affiche les répertoires d’historique d’exécution pour la tâche planifiée **ProcessJob** .

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

Vous pouvez ouvrir et examiner les fichiers **ScheduledJobDefinition.xml** , **Results.xml** et **Status.xml** ou utiliser l' `Select-XML` applet de commande pour analyser les fichiers.

> [!WARNING]
> Ne modifiez pas les fichiers XML. Si un fichier XML contient du code XML non valide, PowerShell supprime la tâche planifiée et son historique d’exécution, y compris les résultats de la tâche.

## <a name="start-a-scheduled-job-immediately"></a>Démarrer immédiatement une tâche planifiée

Vous pouvez démarrer une tâche planifiée immédiatement de l’une des deux manières suivantes :

- Exécutez l' `Start-Job` applet de commande pour démarrer une tâche planifiée.
- Ajoutez le paramètre **RunNow** à votre `Register-ScheduledJob` commande pour démarrer le travail dès que la commande est exécutée.

Les tâches démarrées à l’aide de l' `Start-Job` applet de commande sont des travaux en arrière-plan PowerShell standard, et non des instances de la tâche planifiée. Comme pour toutes les tâches en arrière-plan, ces travaux démarrent immédiatement, ils ne sont pas soumis à des options de travail ou affectés par des déclencheurs de tâche. La sortie du travail n’est pas enregistrée dans le répertoire de **sortie** du répertoire de travail planifié.

La commande suivante utilise le paramètre **DefinitionName** de l' `Start-Job` applet de commande pour démarrer la tâche planifiée ProcessJob.

```powershell
Start-Job -DefinitionName ProcessJob
```

Pour gérer le travail et obtenir les résultats du travail, utilisez les applets de commande Job. Pour plus d’informations sur les applets de commande Job, consultez [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).

> [!NOTE]
> Pour utiliser les applets de commande Job sur des instances de tâches planifiées, vous devez importer le module **PSScheduledJob** dans la session. Pour importer le module **PSScheduledJob** , tapez `Import-Module PSScheduledJob` ou utilisez une applet de commande de tâche planifiée, telle que `Get-ScheduledJob` .

## <a name="rename-a-scheduled-job"></a>Renommer une tâche planifiée

Pour renommer une tâche planifiée, utilisez le paramètre Name de l’applet de commande `Set-ScheduledJob` . Lorsque vous renommez une tâche planifiée, PowerShell modifie le nom de la tâche planifiée et le répertoire de travail planifié. Toutefois, il ne modifie pas les noms des instances de la tâche planifiée qui ont déjà été exécutées.

## <a name="get-start-and-end-times"></a>Obtenez des heures de début et de fin

Pour obtenir les dates et heures de début et de fin des instances de tâche, utilisez les propriétés **PSBeginTime** et **PSEndTime** de l’objet ScheduledJob qui `Get-Job` retourne pour les tâches planifiées.

L’exemple suivant utilise le paramètre **Property** de l' `Format-Table` applet de commande pour afficher les propriétés **PSBeginTime** et **PSEndTime** de chaque instance de tâche dans une table. Une propriété calculée nommée **label** affiche le temps écoulé de chaque instance de tâche.

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a>Gérer l’historique d’exécution

Vous pouvez déterminer le nombre de résultats d’instance de tâche qui sont enregistrés pour chaque tâche planifiée et supprimer l’historique d’exécution et les résultats de travail enregistrés d’une tâche planifiée.

La propriété **ExecutionHistoryLength** d’une tâche planifiée détermine le nombre de résultats d’instance de tâche qui sont enregistrés pour la tâche planifiée. Lorsque le nombre de résultats enregistrés dépasse la valeur de la propriété **ExecutionHistoryLength** , PowerShell supprime les résultats de l’instance la plus ancienne pour libérer de l’espace pour les résultats de l’instance la plus récente.

Par défaut, PowerShell enregistre l’historique d’exécution et les résultats des instances 32 de chaque tâche planifiée. Pour modifier cette valeur, utilisez les paramètres **MaxResultCount** des applets de commande `Register-ScheduledJob` ou `Set-ScheduledJob` .

Pour supprimer l’historique d’exécution et tous les résultats d’une tâche planifiée, utilisez le paramètre **ClearExecutionHistory** de l’applet de commande `Set-ScheduledJob` . La suppression de cet historique d’exécution n’empêche pas PowerShell d’enregistrer les résultats des nouvelles instances de la tâche planifiée.

L’exemple suivant utilise la projection pour créer `$JobParms` des valeurs de paramètre qui sont passées à l’applet de commande `Register-ScheduledJob` . Pour plus d’informations, consultez [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).
Le `Register-ScheduledJob` utilise `@JobParms` pour créer une tâche planifiée. La commande utilise le paramètre **MaxResultCount** avec la valeur 12 pour enregistrer uniquement les 12 résultats les plus récents de l’instance de tâche de la tâche planifiée.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

La commande suivante utilise le paramètre **MaxResultCount** de l' `Set-ScheduledJob` applet de commande pour augmenter le nombre de résultats d’instance enregistrés à
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

La commande suivante supprime l’historique d’exécution et les résultats actuellement enregistrés de la tâche planifiée **ProcessJob** .

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

La commande suivante obtient les valeurs des propriétés Name et **ExecutionHistoryLength** de toutes les tâches planifiées sur l’ordinateur et les affiche dans une table.

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a>Voir aussi

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

Applets de commande du module [PSScheduledJob](xref:PSScheduledJob)

[Planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-reference)
