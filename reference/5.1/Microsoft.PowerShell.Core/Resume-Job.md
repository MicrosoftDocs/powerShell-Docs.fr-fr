---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388533"
---
# Resume-Job

## SYNOPSIS
Redémarre une tâche suspendue.

## SYNTAXE

### SessionIdParameterSet (par défaut)

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Resume-Job` applet de commande reprend une tâche de workflow qui a été suspendue, par exemple à l’aide de l’applet de commande `Suspend-Job` ou de l’activité [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) . Lors de la reprise d’une tâche de workflow, le moteur de tâche reconstruit l’État, les métadonnées et la sortie à partir des ressources enregistrées, telles que les points de contrôle. La tâche est redémarrée sans perte de données ou d’État.
L'état de la tâche est changé de **Suspended** en **Running**.

Utilisez les paramètres de `Resume-Job` pour sélectionner des travaux par nom, ID, ID d’instance ou diriger un objet de traitement, tel que celui retourné par l' `Get-Job` applet de commande, à `Resume-Job` . Vous pouvez aussi utiliser un filtre de propriété pour sélectionner une tâche à reprendre.

Par défaut, `Resume-Job` retourne immédiatement, même si tous les travaux peuvent ne pas être encore repris. Pour supprimer l'invite de commandes jusqu'à ce que toutes les tâches spécifiées aient repris, utilisez le paramètre **Wait**.

L' `Resume-Job` applet de commande fonctionne uniquement sur les types de tâches personnalisées, tels que les tâches de Workflow. Il ne fonctionne pas sur les tâches en arrière-plan standard, telles que celles qui sont démarrées à l’aide de l’applet de commande `Start-Job` . Si vous envoyez un travail d’un type non pris en charge, `Resume-Job` génère une erreur de fin et arrête l’exécution.

Pour identifier une tâche de workflow, recherchez la valeur de **PSWorkflowJob** dans la propriété **PSJobTypeName** de la tâche. Pour déterminer si un type de tâche personnalisé particulier prend en charge l' `Resume-Job` applet de commande, consultez les rubriques d’aide relatives au type de tâche personnalisé.

Avant d’utiliser une applet de commande de tâche sur un type de tâche personnalisé, importez le module qui prend en charge le type de tâche personnalisé, soit à l’aide de l’applet de commande, soit en `Import-Module` obtenant ou en utilisant une applet de commande dans le module.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : reprendre un travail par ID

Les commandes de cet exemple vérifient que la tâche est une tâche de workflow suspendue, puis reprennent la tâche. La première commande utilise l' `Get-Job` applet de commande pour récupérer le travail. La sortie montre que la tâche est une tâche de workflow suspendue. La deuxième commande utilise le paramètre **ID** de l' `Resume-Job` applet de commande pour reprendre la tâche avec une valeur d' **ID** de 4.

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### Exemple 2 : reprendre une tâche par son nom

Cette commande utilise le paramètre **Name** pour reprendre plusieurs tâches de workflow sur l'ordinateur local.

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### Exemple 3 : utiliser des valeurs de propriétés personnalisées

Cette commande utilise la valeur d'une propriété personnalisée pour identifier la tâche de workflow à reprendre. Elle utilise le paramètre **Filter** pour identifier la tâche de workflow par sa propriété **CustomID**. Elle utilise également le paramètre **State** pour vérifier que la tâche de workflow est suspendue, avant d'essayer de la reprendre.

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### Exemple 4 : reprendre toutes les tâches suspendues sur un ordinateur distant

Cette commande reprend toutes les tâches suspendues sur l'ordinateur distant Srv01.

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

La commande utilise l' `Invoke-Command` applet de commande pour exécuter une commande sur l’ordinateur Srv01. La commande distante utilise le paramètre **State** de l’applet de commande `Get-Job` pour récupérer toutes les tâches suspendues sur l’ordinateur. Un opérateur de pipeline ( `|` ) envoie les tâches suspendues à l’applet de commande `Resume-Job` , qui les reprend.

### Exemple 5 : attendre la reprise des tâches

Cette commande utilise le paramètre **Wait** pour diriger le `Resume-Job` retour uniquement après la reprise de toutes les tâches spécifiées. Le paramètre **Wait** est particulièrement utile dans les scripts qui supposent que les tâches soient reprises avant que le script puisse continuer.

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### Exemple 6 : reprendre un flux de travail qui s’interrompt

Cet exemple de code montre l' `Suspend-Workflow` activité dans un flux de travail.

`Test-Suspend`Flux de travail sur l’ordinateur SERVEUR01. Lorsque vous exécutez le workflow, le workflow exécute l' `Get-Date` activité et stocke le résultat dans la `$a` variable. Ensuite, il exécute l' `Suspend-Workflow` activité. En réponse, il prend un point de contrôle, suspend le workflow et retourne un objet de tâche de workflow. `Suspend-Workflow` retourne un objet de tâche de workflow même si le workflow n’est pas explicitement exécuté en tant que tâche.

`Resume-Job` reprend le `Test-Suspend` Workflow dans Job8. Elle utilise le paramètre **Wait** pour suspendre l'invite de commandes jusqu'à ce que la tâche soit reprise.

L' `Receive-Job` applet de commande obtient les résultats du `Test-Suspend` flux de travail. La commande finale du workflow retourne un objet **TimeSpan** qui représente le temps écoulé entre la date et l’heure actuelles et la date et l’heure qui ont été enregistrées dans la `$a` variable avant la suspension du Workflow.

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

PS C:\> Receive-Job -Name Job8
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
        PSComputerName    : Server01
```

L' `Resume-Job` applet de commande vous permet de reprendre une tâche de workflow qui a été suspendue à l’aide de l' `Suspend-Workflow` activité. Cette activité suspend un workflow depuis un workflow. Elle est valide uniquement dans les workflows.

Pour plus d’informations sur le `Suspend-Workflow` , consultez about_Suspend-Workflow] (.. /PSWorkflow/about/about_Suspend-Workflow. MD).

## PARAMÈTRES

### -Filter

Spécifie une table de hachage de conditions. Cette applet de commande reprend les travaux qui satisfont à toutes les conditions de la table de hachage. Entrez une table de hachage où les clés sont les propriétés des travaux et les valeurs celles des propriétés des travaux.

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

Spécifie un tableau d’ID pour les travaux que cette applet de commande reprend.

L’ID est un entier qui identifie de façon unique le travail dans la session active. Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active. Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules. Pour Rechercher l’ID d’un travail, exécutez `Get-Job` .

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

Spécifie un tableau d’ID d’instance des travaux que cette applet de commande reprend. Par défaut, il s'agit de toutes les tâches.

Un ID d'instance est un GUID qui identifie de façon unique la tâche sur l'ordinateur. Pour Rechercher l’ID d’instance d’un travail, exécutez `Get-Job` .

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

### -Travail

Spécifie les tâches à reprendre. Entrez une variable qui contient les tâches ou tapez une commande permettant d'obtenir ces tâches. Vous pouvez également diriger les travaux vers l’applet de commande `Resume-Job` .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms conviviaux de travaux que cette applet de commande reprend. Entrez un ou plusieurs noms de tâche.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -État

Spécifie l’état des travaux à reprendre. Les valeurs valides pour ce paramètre sont :

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

Cette applet de commande reprend uniquement les tâches dans l’état **Suspended** .

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

### -Wait

Indique que cette applet de commande supprime l’invite de commandes jusqu’au redémarrage de tous les résultats de la tâche. Par défaut, cette applet de commande retourne immédiatement les résultats disponibles.

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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

### System. Management. Automation. job

Vous pouvez diriger tous les types de travaux vers cette applet de commande. Si `Resume-Job` obtient une tâche d’un type non pris en charge, elle retourne une erreur d’arrêt.

## SORTIES

### Aucun, System. Management. Automation. job

Cette applet de commande retourne les tâches qu’elle tente de reprendre, si vous utilisez le paramètre **PassThru** .
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- `Resume-Job` peut reprendre uniquement les tâches qui sont suspendues. Si vous soumettez un travail dans un état différent, `Resume-Job` exécute l’opération de reprise sur le travail, mais génère un avertissement pour vous informer que le travail n’a pas pu être repris. Pour supprimer l’avertissement, utilisez le paramètre commun **WarningAction** avec la valeur SilentlyContinue.
- Si un travail n’est pas d’un type qui prend en charge la reprise, par exemple une tâche de workflow ( **PSWorkflowJob** ), `Resume-Job` retourne une erreur de fin.
- Le mécanisme et l'emplacement pour enregistrer une tâche suspendue peuvent varier selon le type de tâche. Par exemple, les tâches de workflow suspendues sont enregistrées par défaut dans un magasin de fichiers plats, mais elles peuvent également être enregistrées dans une base de données SQL.
- Quand vous reprenez une tâche, l'état de la tâche passe de **Suspended** à **Running**. Pour rechercher les travaux en cours d’exécution, y compris ceux qui ont été repris par cette applet de commande, utilisez le paramètre **State** de l’applet de commande `Get-Job` pour obtenir les tâches dans l’État en **cours d’exécution** .
- Certains types de tâche ont des options ou des propriétés qui empêchent Windows PowerShell de suspendre la tâche.
  Si les tentatives d’interruption de la tâche échouent, vérifiez que les options et les propriétés du travail autorisent la suspension.

## LIENS CONNEXES

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
