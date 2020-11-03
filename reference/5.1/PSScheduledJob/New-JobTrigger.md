---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202998"
---
# New-JobTrigger

## SYNOPSIS
Crée un déclencheur pour une tâche planifiée.

## SYNTAX

### Une fois (valeur par défaut)

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### Quotidien

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### Hebdomadaire

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### AtStartup

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### AtLogon

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## Description
L’applet **de commande New-JobTrigger** crée un déclencheur de tâche qui démarre une tâche planifiée selon une planification ponctuelle ou périodique, ou lorsqu’un événement se produit.

Vous pouvez utiliser l'objet **ScheduledJobTrigger** retourné par **New-JobTrigger** pour définir un déclencheur de tâche pour une tâche planifiée nouvelle ou existante.
Vous pouvez également créer un déclencheur de tâche à l’aide de l’applet de commande Get-JobTrigger pour obtenir le déclencheur d’une tâche planifiée existante, ou en utilisant une valeur de table de hachage pour représenter un déclencheur de tâche.

Lorsque vous créez un déclencheur de tâche, passez en revue les valeurs par défaut des options spécifiées par l’applet de commande New-ScheduledJobOption.
Ces options, qui ont les mêmes valeurs valides et par défaut que les options correspondantes dans **Task Scheduler** , affectent la planification et la durée des tâches planifiées.

**New-JobTrigger** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : planification

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

Cette commande utilise l'applet de commande **New-JobTrigger** pour créer un déclencheur de tâche qui démarre une tâche planifiée une seule fois.
La valeur du paramètre *At* est une chaîne que Windows PowerShell convertit en un objet **DateTime** .
La valeur du paramètre *At* inclut une date explicite, et pas seulement une heure.
Si la date a été omise, le déclencheur est créé avec la date actuelle et l'heure 3:00, qui est susceptible de représenter une heure dans le passé.

### Exemple 2 : planification quotidienne

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée tous les 3 jours à 4:15.

Étant donné que la valeur du paramètre *At* n'inclut pas de date, la date actuelle est utilisée comme valeur de date dans l'objet **DateTime** .
Si la date et l'heure sont passées, la tâche planifiée est démarrée à l'occurrence suivante, qui a lieu 3 jours plus tard à partir de la valeur du paramètre *At* .

### Exemple 3 : planification hebdomadaire

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée toutes les 4 semaines les lundi, mercredi et vendredi à 23:00.

Vous pouvez également entrer la valeur du paramètre *DaysOfWeek* dans des entiers, par exemple `-DaysOfWeek 1, 5` .

### Exemple 4 : planification de l’ouverture de session

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée chaque fois que l'administrateur de domaine ouvre une session sur l'ordinateur.

### Exemple 5 : utilisation d’un délai aléatoire

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

Cette commande crée un déclencheur de tâche qui démarre une tâche planifiée chaque jour à 1:00.
La commande utilise le paramètre *RandomDelay* pour définir 20 minutes comme délai maximal.
Par conséquent, la tâche est exécutée chaque jour entre 1:00 et 1:20, avec l'intervalle qui varie de manière pseudo-aléatoire.

Vous pouvez utiliser un délai aléatoire pour l'échantillonnage, l'équilibrage de charge et d'autres tâches d'administration.
Lors de la définition de la valeur de délai, examinez les valeurs effectives et par défaut de l’applet de commande New-ScheduledJobOption et coordonnez le délai avec les paramètres d’option.

### Exemple 6 : créer un déclencheur de tâche pour une nouvelle tâche planifiée

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

Ces commandes utilisent un déclencheur de tâche pour créer une tâche planifiée.

### Exemple 7 : ajouter un déclencheur de tâche à une tâche planifiée

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

Cet exemple montre comment ajouter un déclencheur de tâche à une tâche planifiée existante.
Vous pouvez ajouter plusieurs déclencheurs de tâche à n'importe quelle tâche planifiée.

La commande utilise l’applet de commande Add-JobTrigger pour ajouter le déclencheur de tâche à la tâche planifiée SynchronizeApps.
La valeur du paramètre *Trigger* est une commande **New-JobTrigger** qui exécute la tâche chaque jour à 3:10.

Quand l'exécution de la commande est terminée, SynchronizeApps est une tâche planifiée qui s'exécute aux heures spécifiées par le déclencheur de tâche.

### Exemple 8 : créer un déclencheur de tâche répétée

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

Cette commande crée un déclencheur de tâche qui exécute une tâche toutes les 60 minutes pendant 48 heures à compter du 12 septembre 2013 à 1:00.

### Exemple 9 : arrêter un déclencheur de tâche répétée

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

Cette commande arrête de force la tâche SecurityCheck, dont l'exécution est déclenchée toutes les 60 minutes jusqu'à l'expiration de son déclencheur de tâche.

Pour empêcher la répétition du travail, la commande utilise la Get-JobTrigger pour recevoir le déclencheur de la tâche SecurityCheck et l’applet de commande Set-JobTrigger pour modifier l’intervalle de répétition et la durée de répétition du déclencheur de tâche sur zéro (0).

### Exemple 10 : créer un déclencheur de travail horaire

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

La commande suivante crée un déclencheur de tâche qui exécute une tâche planifiée toutes les 12 heures pendant une durée indéterminée.
La planification commence demain (21/9/2012) à minuit (0:00).

## PARAMETERS

### -À
Démarre la tâche à la date et à l'heure spécifiées.
Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date, ou une chaîne pouvant être convertie en date et heure, telle que « April 19, 2012 15:00 », « 12/31 » ou « 3:00 ».
Si vous ne spécifiez pas un élément de la date, par exemple l'année, la date dans le déclencheur a l'élément correspondant de la date actuelle.

Quand vous utilisez le paramètre *Once* , affectez au paramètre *At* une date et une heure futures.
Comme la date par défaut dans un objet **DateTime** est la date actuelle, la définition d'une heure antérieure à l'heure actuelle sans une date explicite crée un déclencheur de tâche pour une heure dans le passé.

Les objets **DateTime** , et les chaînes converties en objets **DateTime** , sont automatiquement ajustées pour être compatibles avec les formats de date et d’heure sélectionnés pour l’ordinateur local dans région et langue dans le panneau de configuration.

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtLogOn
Démarre la tâche planifiée quand les utilisateurs spécifiés se connectent à l'ordinateur.
Pour spécifier un utilisateur, utilisez le paramètre *User* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
Démarre la tâche planifiée au démarrage de Windows.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tous les jours
Spécifie une planification de tâche quotidienne périodique.
Utilisez les autres paramètres du jeu de paramètres *Daily* pour spécifier les détails de la planification.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysInterval
Spécifie le nombre de jours entre les occurrences d'une planification quotidienne.
Par exemple, une valeur de 3 démarre la tâche planifiée les jours 1, 4, 7 et ainsi de suite.
La valeur par défaut est 1.

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
Spécifie les jours de la semaine qu'une tâche planifiée hebdomadaire s'exécute.
Entrez les noms des jours, par exemple « Lundi », ou des entiers de 0 à 6, où 0 représente Dimanche.
Ce paramètre est obligatoire dans le jeu de paramètres Weekly.

Les noms de jours sont convertis dans leurs valeurs entières dans le déclencheur de tâche.
Lorsque vous placez les noms de jours entre guillemets droits dans une commande, faites-le séparément, par exemple "Lundi", "Mardi".
Si vous incluez plusieurs noms de jours dans une seule paire de guillemets droits, les valeurs entières correspondantes sont additionnées.
Par exemple, "Lundi, Mardi" (1, 2) donne la valeur "Mercredi" (3).

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Une fois
Spécifie une planification non périodique (unique) ou récurrente personnalisée.
Pour créer une planification récurrente, utilisez le paramètre *Once* avec les paramètres *RepetitionDuration* et *RepetitionInterval* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RandomDelay
Active un délai aléatoire qui commence à l'heure de début planifiée et définit la valeur maximale du délai.
La longueur du délai est définie de manière pseudo-aléatoire pour chaque démarrage et elle varie entre aucun délai et la durée spécifiée par la valeur de ce paramètre.
La valeur par défaut, zéro (00:00:00), désactive le délai aléatoire.

Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> format, qui est automatiquement convertie en objet **TimeSpan** .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepeatIndefinitely
Ce paramètre, disponible à partir de Windows PowerShell 4.0, élimine le besoin de spécifier une valeur **TimeSpan.MaxValue** pour le paramètre *RepetitionDuration* pour exécuter une tâche planifiée à plusieurs reprises, pendant une durée indéterminée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepetitionDuration
Répète la tâche jusqu'à ce que le délai spécifié expire.
La fréquence de répétition est déterminée par la valeur du paramètre *RepetitionInterval* .
Par exemple, si la valeur de **RepetitionInterval** est égale à 5 minutes et la valeur de **RepetitionDuration** à 2 heures, la tâche se déclenche toutes les cinq minutes pendant deux heures.

Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».

Pour exécuter une tâche indéfiniment, ajoutez plutôt le paramètre *RepeatIndefinitely* .

Pour arrêter un travail avant l’expiration de la durée de répétition du déclencheur de tâche, utilisez l’applet de commande Set-JobTrigger pour définir la valeur *RepetitionDuration* sur zéro (0).

Ce paramètre est valide uniquement quand les paramètres *Once* , *At* et *RepetitionInterval* sont utilisés dans la commande.

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RepetitionInterval
Répète la tâche à l'intervalle de temps spécifié.
Par exemple, si la valeur de ce paramètre est de 2 heures, la tâche est déclenchée toutes les deux heures.
La valeur par défaut, 0, ne répète pas la tâche.

Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».

Ce paramètre est valide uniquement quand les paramètres *Once* , *At* et *RepetitionDuration* sont utilisés dans la commande.

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -User
Spécifie les utilisateurs qui déclenchent un démarrage *AtLogon* d'une tâche planifiée.
Entrez le nom d’un utilisateur au \<UserName\> format ou, \<Domain\Username\> ou entrez un astérisque ( \* ) pour représenter tous les utilisateurs.
La valeur par défaut est tous les utilisateurs.

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hebdomadaire
Spécifie une planification de tâche hebdomadaire périodique.
Utilisez les autres paramètres du jeu de paramètres Weekly pour spécifier les détails de la planification.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WeeksInterval
Spécifie le nombre de semaines entre les occurrences d'une planification de tâche hebdomadaire.
Par exemple, une valeur de 3 démarre la tâche planifiée les semaines 1, 4, 7 et ainsi de suite.
La valeur par défaut est 1.

```yaml
Type: System.Int32
Parameter Sets: Weekly
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger

## REMARQUES

* Les déclencheurs de tâche ne sont pas enregistrés sur disque. Toutefois, les tâches planifiées sont enregistrées sur le disque, et vous pouvez utiliser la Get-JobTrigger pour recevoir le déclencheur d’une tâche planifiée.
* **New-JobTrigger** ne vous empêche pas de créer un déclencheur de tâche qui n’exécutera pas de tâche planifiée, comme un déclencheur à usage unique pour une date dans le passé.
* L’applet de commande Register-ScheduledJob accepte un objet ScheduledJobTrigger, tel que celui retourné par les applets de commande **New-JobTrigger** ou Get-JobTrigger, ou une table de hachage avec des valeurs de déclencheur.

  Pour envoyer une table de hachage, utilisez les clés suivantes.

  `@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (ou toute chaîne d’heure valide); `DaysOfWeek="Monday", "Wednesday"` (ou toute combinaison de noms de jours); `Interval=2` (ou n’importe quel intervalle de fréquence valide); `RandomDelay="30minutes"` (ou toute chaîne TimeSpan valide); `User="Domain1\User01` (ou tout utilisateur valide ; utilisé uniquement avec la valeur de fréquence *AtLogon* )}

## LIENS CONNEXES

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
