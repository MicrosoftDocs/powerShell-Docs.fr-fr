---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: acf01415c9722b6da95e70a8db1b558c3e14662b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202642"
---
# Wait-Job

## SYNOPSIS
Supprime l’invite de commandes jusqu’à ce qu’une ou toutes les tâches en arrière-plan Windows PowerShell en cours d’exécution dans la session soient terminées.

## SYNTAX

### SessionIdParameterSet (par défaut)

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### JobParameterSet

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### NameParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### StateParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## Description
L’applet de commande **Wait-Job** attend que les tâches en arrière-plan Windows PowerShell se terminent avant d’afficher l’invite de commandes.
Vous pouvez attendre la fin d'une tâche en arrière-plan donnée ou de toutes les tâches en arrière-plan, et vous pouvez définir un délai d'attente maximal pour la tâche.

Quand les commandes figurant dans la tâche sont terminées, **Wait-Job** affiche l'invite de commandes et retourne un objet de traitement pour que vous puissiez la diriger vers une autre commande.

Vous pouvez utiliser l’applet de commande **Wait-Job** pour attendre des tâches en arrière-plan, telles que celles qui ont été démarrées à l’aide de l’applet de commande Start-Job ou du paramètre *AsJob* de l’applet de commande Invoke-Command.
Pour plus d'informations sur les tâches en arrière-plan Windows PowerShell, consultez about_Jobs.

À compter de Windows PowerShell 3,0, l’applet de commande **Wait-Job** attend également des types de tâches personnalisés, tels que les tâches de workflow et les instances de tâches planifiées.
Pour permettre à **Wait-Job** d’attendre des tâches d’un type particulier, importez le module qui prend en charge le type de tâche personnalisé dans la session avant d’exécuter l’applet de commande Get-Job, à l’aide de l’applet de commande Import-Module ou à l’aide de ou de l’obtention d’une applet de commande dans le module.
Pour plus d'informations sur un type de tâche personnalisé particulier, consultez la documentation sur la fonctionnalité de type de tâche personnalisé.

## EXEMPLES

### Exemple 1 : attendre tous les travaux

```
PS C:\> Get-Job | Wait-Job
```

Cette commande attend la fin de toutes les tâches en arrière-plan en cours d’exécution dans la session.

### Exemple 2 : attente des tâches démarrées sur des ordinateurs distants à l’aide de Start-Job

```
PS C:\> $s = New-PSSession Server01, Server02, Server03
PS C:\> Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
PS C:\> $done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
PS C:\> $done.Count
3
```

Cet exemple montre comment utiliser l’applet de commande **Wait-Job** avec des tâches démarrées sur des ordinateurs distants à l’aide de l’applet de commande **Start-Job** .
Les commandes **Start-Job** et **Wait-Job** sont envoyées à l’ordinateur distant à l’aide de l’applet de **commande Invoke-Command** .

Cet exemple utilise **Wait-Job** pour déterminer si une commande Get-Date s’exécutant en tant que tâche en arrière-plan sur trois ordinateurs différents est terminée.

La première commande crée une session Windows PowerShell ( **PSSession** ) sur chacun des trois ordinateurs distants et les stocke dans la variable $s.

La deuxième commande utilise **Invoke-Command** pour exécuter **Start-Job** dans chacune des trois sessions dans $s.
Toutes les tâches sont nommées date1.

La troisième commande utilise **Invoke-Command** pour exécuter **Wait-Job** .
Cette commande attend la fin des tâches date1 sur chaque ordinateur.
Elle stocke la collection résultante (tableau) des objets de traitement dans la variable $done.

La quatrième commande utilise la propriété **Count** du tableau d’objets de traitement dans la variable $done pour déterminer le nombre de travaux terminés.

### Exemple 3 : déterminer à quel moment la première tâche en arrière-plan se termine

```
PS C:\> $s = New-PSSession (Get-Content Machines.txt)
PS C:\> $c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
PS C:\> Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
PS C:\> Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

Cet exemple utilise le paramètre *any* d' **Wait-Job** pour déterminer quand la première des nombreuses tâches en arrière-plan en cours d’exécution dans la session active est terminée.
Il montre également comment utiliser l’applet de commande **Wait-Job** pour attendre la fin des travaux distants.

La première commande crée une **session PSSession** sur chacun des ordinateurs listés dans le fichier Machines.txt et stocke les objets **PSSession** dans la variable $s.
La commande utilise l’applet de commande Get-Content pour récupérer le contenu du fichier.
La commande d' **extraction de contenu** est placée entre parenthèses pour s’assurer qu’elle s’exécute avant la commande New-PSSession.

La deuxième commande stocke une chaîne de commande **obtenir-EventLog** , entre guillemets, dans la variable $c.

La troisième commande utilise Invoke-Command applet de commande pour exécuter **Start-Job** dans chacune des sessions dans $s.
La commande **Start-Job** démarre une tâche en arrière-plan qui exécute la commande **obtenir-EventLog** dans la variable $c.

La commande utilise le modificateur d'étendue **Using** pour indiquer que la variable $c a été définie sur l'ordinateur local.
Le modificateur d'étendue **Using** a été introduit pour la première fois dans Windows PowerShell 3.0.
Pour plus d’informations sur le modificateur d’étendue **using** , consultez about_Remote_Variables ( https://go.microsoft.com/fwlink/?LinkID=252653) .

La quatrième commande utilise **Invoke-Command** pour exécuter une commande **Wait-Job** dans les sessions.
Elle utilise le paramètre *any* pour attendre la fin de la première tâche sur les ordinateurs distants.

### Exemple 4 : définir un délai d’attente pour des travaux sur des ordinateurs distants

```
PS C:\> $s = New-PSSession Server01, Server02, Server03
PS C:\> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS C:\> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

Cet exemple montre comment utiliser le paramètre *timeout* de **Wait-Job** pour définir un délai d’attente maximal pour les tâches en cours d’exécution sur des ordinateurs distants.

La première commande crée une **session PSSession** sur chacun des trois ordinateurs distants (SERVEUR01, Server02 et Server03), puis stocke les objets **PSSession** dans la variable $s.

La deuxième commande utilise **Invoke-Command** pour exécuter **Start-Job** dans chacun des objets **PSSession** dans $s.
Elle stocke les objets de traitement résultants dans la variable $jobs.

La troisième commande utilise **Invoke-Command** pour exécuter **Wait-Job** dans chacune des sessions dans $s.
La commande **Wait-Job** détermine si toutes les commandes sont terminées dans un délai de 30 secondes.
Elle utilise le paramètre *timeout* avec la valeur 30 pour établir le délai d’attente maximal, puis stocke les résultats de la commande dans la variable $done.

Dans ce cas, après 30 secondes, seule la commande sur l'ordinateur Server02 s'est terminée.
**Wait-Job** met fin à l’attente, affiche l’invite de commandes et retourne l’objet qui représente le travail terminé.

La variable $done contient un objet de traitement qui représente la tâche qui s'exécutait sur Server02.

### Exemple 5 : attendre la fin de l’exécution de l’une des tâches suivantes

```
PS C:\> Wait-Job -id 1,2,5 -Any
```

Cette commande identifie trois tâches par leur ID et attend la fin de l’une d’entre elles.
L’invite de commandes s’affiche lorsque la première tâche se termine.

### Exemple 6 : attendre un point, puis autoriser la tâche à continuer en arrière-plan

```
PS C:\> Wait-Job -Name "DailyLog" -Timeout 120
```

Cette commande attend 120 secondes (deux minutes) que la tâche Dailyjob se se termine.
Si la tâche ne se termine pas dans les deux minutes qui suivent, l’invite de commandes réapparaît et la tâche continue de s’exécuter en arrière-plan.

### Exemple 7 : attendre un travail par nom

```
PS C:\> Wait-Job -Name "Job3"
```

Cette commande utilise le nom du travail pour identifier le travail à attendre.

### Exemple 8 : attente des travaux sur l’ordinateur local démarrés avec Start-Job

```
PS C:\> $j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
PS C:\> $j | Wait-Job
```

Cet exemple montre comment utiliser l’applet de commande **Wait-Job** avec des tâches démarrées sur l’ordinateur local à l’aide de **Start-Job** .

Ces commandes démarrent une tâche qui obtient les fichiers de script Windows PowerShell qui ont été ajoutés ou mis à jour au cours de la semaine précédente.

La première commande utilise **Start-Job** pour démarrer une tâche en arrière-plan sur l’ordinateur local.
La tâche exécute une commande Get-ChildItem qui obtient tous les fichiers ayant une extension de nom de fichier. ps1 qui ont été ajoutés ou mis à jour au cours de la semaine dernière.

La troisième commande utilise **Wait-Job** pour attendre la fin du travail.
Une fois la tâche terminée, la commande affiche l’objet de traitement, qui contient des informations sur le travail.

### Exemple 9 : attente des tâches démarrées sur des ordinateurs distants à l’aide de Invoke-Command

```
PS C:\> $s = New-PSSession Server01, Server02, Server03
PS C:\> $j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
PS C:\> $j | Wait-Job
```

Cet exemple montre comment utiliser **Wait-Job** avec les travaux démarrés sur des ordinateurs distants à l’aide du paramètre *AsJob* de **Invoke-Command** .
Lorsque vous utilisez *AsJob* , le travail est créé sur l’ordinateur local et les résultats sont automatiquement retournés à l’ordinateur local, même si le travail s’exécute sur les ordinateurs distants.

Cet exemple utilise **Wait-Job** pour déterminer si une commande d’exécution de **processus** en cours d’exécution dans les sessions sur trois ordinateurs distants est terminée.

La première commande crée des objets **PSSession** sur trois ordinateurs et les stocke dans la variable $s.

La deuxième commande utilise **Invoke-Command** pour exécuter **le processus d’extraction** dans chacune des trois sessions dans $s.
La commande utilise le paramètre *AsJob* pour exécuter la commande de façon asynchrone en tant que tâche en arrière-plan.
La commande retourne un objet de traitement, tout comme les tâches démarrées à l’aide de **Start-Job** , et l’objet de traitement est stocké dans la variable $j.

La troisième commande utilise un opérateur de pipeline (|) pour envoyer l’objet de traitement dans $j à l’applet de commande **Wait-Job** .
Dans ce cas, une commande **Invoke-Command** n’est pas requise, car le travail se trouve sur l’ordinateur local.

### Exemple 10 : attendre un travail qui a un ID

```
PS C:\> Get-Job

Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where

PS C:\> Wait-Job -Id 1
```

Cette commande attend la tâche dotée d'un ID de valeur 1.

## PARAMETERS

### -Any
Indique que cette applet de commande affiche l’invite de commandes et retourne l’objet de traitement, quand une tâche se termine.
Par défaut, **Wait-Job** attend que toutes les tâches spécifiées soient terminées avant d’afficher l’invite.

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

### -Filter
Spécifie une table de hachage de conditions.
Cette applet de commande attend des tâches qui répondent à toutes les conditions de la table de hachage.
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

### -Force
Indique que cette applet de commande continue à attendre des tâches dans l’État Suspended ou Disconnected.
Par défaut, **Wait-Job** retourne, ou met fin à l’attente, lorsque les tâches sont dans l’un des États suivants :

- Completed
- Échec
- Arrêté
- Interrompu
- Déconnecté

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

### -Id
Spécifie un tableau d’ID des travaux que cette applet de commande attend.

L’ID est un entier qui identifie de façon unique le travail dans la session active.
Il est plus facile à mémoriser et à taper que l’ID d’instance, mais il n’est unique que dans la session active.
Vous pouvez taper un ou plusieurs ID, en les séparant par des virgules.
Pour Rechercher l’ID d’un travail, tapez `Get-Job` .

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
Spécifie un tableau d’ID d’instance des travaux que cette applet de commande attend.
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

### -Travail
Spécifie les travaux que cette applet de commande attend.
Entrez une variable qui contient les objets de traitement ou une commande permettant d'obtenir ces objets de traitement.
Vous pouvez également utiliser un opérateur de pipeline pour envoyer des objets de traitement à l’applet de commande **Wait-Job** .
Par défaut, **Wait-Job** attend toutes les tâches créées dans la session active.

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
Spécifie les noms conviviaux des travaux que cette applet de commande attend.

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
Spécifie un état de travail.
Cette applet de commande attend uniquement les tâches dans l’état spécifié.
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

### -Timeout
Spécifie la durée d’attente maximale, en secondes, pour chaque travail en arrière-plan.
La valeur par défaut,-1, indique que l’applet de commande attend que la tâche se termine.
Le minutage démarre lorsque vous envoyez la commande **Wait-Job** , et non la commande **Start-Job** .

Si ce délai est dépassé, l'attente se termine et l'invite de commandes réapparaît, même si la tâche est encore en cours d'exécution.
La commande n’affiche aucun message d’erreur.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. RemotingJob
Vous pouvez diriger un objet de traitement vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSRemotingJob
Cette applet de commande retourne les objets de traitement qui représentent les tâches terminées.
Si l’attente se termine parce que la valeur du paramètre *timeout* est dépassée, **Wait-Job** ne retourne aucun objet.

## REMARQUES

* Par défaut, **Wait-Job** retourne, ou met fin à l’attente, lorsque les tâches sont dans l’un des États suivants :

- Completed
- Échec
- Arrêté
- Interrompu
- Déconnecté de l' **attente directe-travail** pour continuer à attendre les tâches interrompues et déconnectées, utilisez le paramètre *force* .

## LIENS CONNEXES

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)