---
description: Décrit l' `Suspend-Workflow` activité, qui suspend le workflow dans lequel l’activité s’affiche.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Flux de travail about_Suspend
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207218"
---
# <a name="about-suspend-workflow"></a>À propos de Suspend-Workflow

## <a name="short-description"></a>Description courte

Décrit l' `Suspend-Workflow` activité, qui suspend le workflow dans lequel l’activité s’affiche.

## <a name="long-description"></a>Description longue

L' `Suspend-Workflow` activité arrête temporairement le traitement du workflow à partir du flux de travail. Avant la suspension, le workflow Windows PowerShell prend un point de contrôle afin que l’État et les données du workflow soient conservés et que le flux de travail puisse reprendre à partir du point de suspension.

Pour reprendre le workflow, l’utilisateur qui exécute le workflow utilise l’applet de commande `Resume-Job` . Vous ne pouvez pas reprendre un workflow à partir du flux de travail.

## <a name="syntax"></a>Syntaxe

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a>Description détaillée

Le `Suspend-Workflow` interrompt temporairement le workflow et retourne un objet de traitement qui représente la tâche de Workflow. Un objet de traitement est retourné même si vous n’avez pas exécuté le workflow en tant que tâche. Par exemple, en utilisant le paramètre commun de workflow **AsJob** . L’état de la tâche est **suspendu** .

Vous pouvez utiliser les applets de commande Job pour gérer la tâche de workflow suspendue. Pour reprendre la tâche de workflow, utilisez l’applet de commande `Resume-Job` .

Lorsque vous reprenez la tâche de workflow, le workflow reprend à la commande qui suit l' `Suspend-Workflow` activité.

Par exemple, le flux de travail suivant comprend l' `Suspend-Workflow` activité.
Lorsque vous exécutez le workflow, celui-ci exécute l' `Get-Date` activité, enregistre sa sortie dans la `$a` variable, puis suspend le workflow et retourne un objet de traitement qui représente le workflow suspendu. Le type de tâche est **PSWorkflowJob** .

Vous pouvez utiliser les applets de commande Job, telles que `Get-Job` , pour gérer la tâche de Workflow.

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a>Reprise d’une tâche de workflow

Pour reprendre la tâche de workflow, utilisez l’applet de commande `Resume-Job` . L’applet de commande `Resume-Job` renvoie l’objet de traitement de workflow immédiatement, même si le workflow n’a pas encore repris. Pour attendre la reprise de la tâche, utilisez le paramètre **Wait** ou utilisez l' `Get-Job` applet de commande pour obtenir l’objet de traitement actuel.

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a>Obtention de la sortie d’une tâche de workflow

Pour obtenir la sortie d’une tâche de workflow, utilisez l’applet de commande `Receive-Job` . La sortie indique que le flux de travail a repris au niveau de la commande qui a suivi l’applet de commande `Suspend-Workflow` . La valeur de la `$a` variable, qui a été remplie avant la suspension, est disponible pour le workflow lorsqu’elle reprend.

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a>Voir aussi

[about_Workflows](about_Workflows.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

Applets de commande [PSWorkflow](xref:PSWorkflow)

[Guide des workflows](/previous-versions/powershell/scripting/components/workflows-guide)

[Écriture d'un workflow Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
