---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202986"
---
# Set-JobTrigger

## SYNOPSIS
Modifie le déclencheur d'une tâche planifiée.

## SYNTAX

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## Description
L'applet de commande **Set-JobTrigger** modifie les propriétés des déclencheurs des tâches planifiées.
Vous pouvez l'utiliser pour modifier l'heure ou la fréquence à laquelle les tâches démarrent ou pour passer des planifications basées sur l'heure à des planifications qui sont déclenchées par un démarrage ou une ouverture de session.

Un déclencheur de tâche définit une planification ou des conditions récurrentes pour le démarrage d’une tâche planifiée.
Même si les déclencheurs de tâche ne sont pas enregistrés sur disque, vous pouvez modifier les déclencheurs des tâches planifiées, qui sont enregistrées sur disque.

Pour modifier un déclencheur de tâche d’une tâche planifiée, commencez par utiliser l’applet de commande Get-JobTrigger pour obtenir le déclencheur d’une tâche planifiée.
Ensuite, dirigez le déclencheur vers **Set-JobTrigger** ou enregistrez-le dans une variable et utilisez le paramètre *InputObject* de l'applet de commande **Set-JobTrigger** pour identifier le déclencheur.
Utilisez les paramètres restants de **Set-JobTrigger** pour modifier le déclencheur de tâche.

Lorsque vous modifiez le type d’un déclencheur de tâche, tel que la modification d’un déclencheur de tâche d’un déclencheur quotidien ou hebdomadaire à un déclencheur *AtLogon* , les propriétés du déclencheur d’origine sont supprimées.
Toutefois, si vous modifiez les valeurs du déclencheur, mais pas son type, par exemple en modifiant les jours dans un déclencheur hebdomadaire, seules les propriétés que vous spécifiez sont modifiées.
Toutes les autres propriétés du déclencheur de tâche d'origine sont conservées.

**Set-JobTrigger** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*`  ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : modifier les jours dans un déclencheur de tâche

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

Cet exemple montre comment modifier les jours dans un déclencheur de tâche hebdomadaire.

La première commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de la tâche planifiée DeployPackage.
La sortie indique que le déclencheur démarre la tâche à minuit le mercredi et le samedi.

Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification du déclencheur.

### Exemple 2 : modifier le type de déclencheur de tâche

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

Cet exemple montre comment modifier le type de déclencheur de tâche qui démarre une tâche.
Les commandes de cet exemple remplacent un déclencheur de tâche AtStartup par un déclencheur hebdomadaire.

La première commande utilise l’applet de commande Get-JobTrigger pour recevoir le déclencheur de la tâche planifiée Inventory.
La sortie indique que la tâche a deux déclencheurs : un déclencheur quotidien et un déclencheur *AtStartup* .

Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification du déclencheur.

### Exemple 3 : modifier l’utilisateur sur un déclencheur de tâche à distance

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

Cette commande modifie l’utilisateur dans tous les déclencheurs de tâche *AtLogon* des tâches planifiées sur l’ordinateur SERVEUR01.

La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur l’ordinateur SERVEUR01.

La commande distante commence par une commande Get-ScheduledJob qui obtient toutes les tâches planifiées sur l’ordinateur.
Les tâches planifiées sont dirigées vers l’applet de commande Get-JobTrigger, qui obtient les déclencheurs des tâches planifiées.
Chaque déclencheur de tâche contenant une propriété JobDefinition qui inclut la tâche planifiée, le déclencheur reste associé à la tâche planifiée, même en cas de modification.

Les déclencheurs de tâche sont dirigés vers l’applet de commande Where-Object, qui obtient les déclencheurs de tâche qui ont la propriété User.
Les déclencheurs de tâche sélectionnés sont dirigés vers l'applet de commande **Set-JobTrigger** , qui remplace l'utilisateur par Domain01\Admin02.

### Exemple 4 : modifier l’un des nombreux déclencheurs de tâche

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Les commandes de cet exemple remplacent l'intervalle de répétition du déclencheur de tâche *Once* de la tâche planifiée SecurityCheck « toutes les 60 minutes » par « toutes les 90 minutes ».
La tâche planifiée SecurityCheck a trois déclencheurs de tâche, donc les commandes utilisent le paramètre *TriggerId* de l’applet de commande Get-JobTrigger pour identifier le déclencheur de tâche en cours de modification.

La première commande utilise l'applet de commande **Get-JobTrigger** pour obtenir tous les déclencheurs de la tâche planifiée SecurityCheck.
La sortie, qui affiche les ID des déclencheurs de tâche, indique que le déclencheur de tâche *Once* a un ID de 3.

## PARAMETERS

### -À
Démarre la tâche à la date et à l'heure spécifiées.
Entrez un objet **DateTime** , tel que celui retourné par l’applet de commande Get-Date, ou une chaîne qui peut être convertie en une heure, telle que « 19 avril, 2012 15:00 », « 12/31/2013 9:00 PM » ou « 3:00 ».

Si vous ne spécifiez pas un élément de l’objet **DateTime** , tel que seconds, cet élément du déclencheur de tâche n’est pas modifié.
Si le déclencheur de tâche d’origine n’inclut pas d’objet **DateTime** et que vous omettez un élément, le déclencheur de tâche est créé avec l’élément correspondant à partir de la date et de l’heure actuelles.

Quand vous utilisez le paramètre *Once* , affectez au paramètre *At* une date et une heure spécifiques.
Comme la date par défaut dans un objet **DateTime** est la date actuelle, la définition d'une heure antérieure à l'heure actuelle sans une date explicite génère un déclencheur de tâche pour une heure dans le passé.

Les objets **DateTime** , et les chaînes converties en objets **DateTime** , sont automatiquement ajustées pour être compatibles avec les formats de date et d’heure sélectionnés pour l’ordinateur local dans région et langue dans le panneau de configuration.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
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
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
Démarre la tâche planifiée au démarrage de Windows.

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

### -Tous les jours
Spécifie une planification de tâche quotidienne périodique.
Utilisez les autres paramètres du jeu de paramètres *Daily* pour spécifier les détails de la planification.

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

### -DaysInterval
Spécifie le nombre de jours entre les occurrences d'une planification quotidienne.
Par exemple, une valeur de 3 démarre la tâche planifiée les jours 1, 4, 7 et ainsi de suite.
La valeur par défaut est 1.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
Spécifie les jours de la semaine qu'une tâche planifiée hebdomadaire s'exécute.
Entrez les noms des jours, tels que lundi, jeudi, entiers 0-6, où 0 représente dimanche, ou un astérisque ( \* ) pour représenter tous les jours.
Ce paramètre est obligatoire dans le jeu de paramètres Weekly.

Les noms de jours sont convertis dans leurs valeurs entières dans le déclencheur de tâche.
Lorsque vous placez les noms de jours entre guillemets droits dans une commande, faites-le séparément, par exemple "Lundi", "Mardi".
Si vous incluez plusieurs noms de jours dans une seule paire de guillemets droits, les valeurs entières correspondantes sont additionnées.
Par exemple, "Lundi, Mardi" (1, 2) donne la valeur "Mercredi" (3).

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie les déclencheurs de tâche.
Entrez une variable qui contient des objets **ScheduledJobTrigger** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobTrigger** , par exemple une commande Get-JobTrigger.
Vous pouvez également diriger un objet **ScheduledJobTrigger** vers **Set-JobTrigger** .

Si vous spécifiez plusieurs déclencheurs de tâche, **Set-JobTrigger** apporte les mêmes modifications à tous les déclencheurs de tâche.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Une fois
Spécifie une planification non périodique (unique).

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

### -PassThru
Retourne les déclencheurs de tâche modifiés.
Par défaut, cette applet de commande ne génère aucun résultat.

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

### -RandomDelay
Active un délai aléatoire qui commence à l'heure de début planifiée et définit la valeur maximale du délai.
La longueur du délai est définie de manière pseudo-aléatoire pour chaque démarrage et elle varie entre aucun délai et la durée spécifiée par la valeur de ce paramètre.
La valeur par défaut, zéro (00:00:00), désactive le délai aléatoire.

Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan, ou entrez une valeur au \<hours\> \<minutes\> format :: \<seconds\> format, qui est automatiquement convertie en objet TimeSpan.

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
Parameter Sets: (All)
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
Par exemple, si la valeur de **RepetitionInterval** est égale à 5 minutes et la valeur de *RepetitionDuration* à 2 heures, la tâche se déclenche toutes les cinq minutes pendant deux heures.

Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».

Pour exécuter une tâche indéfiniment, ajoutez plutôt le paramètre *RepeatIndefinitely* .

Pour arrêter une tâche avant l'expiration de la durée de répétition de déclencheur de tâche, affectez à **RepetitionDuration** la valeur zéro (0).

Pour modifier la durée de répétition ou l'intervalle de répétition d'un déclencheur de tâche *Once* , la commande doit inclure les paramètres **RepetitionInterval** et **RepetitionDuration** .
Pour modifier la durée de répétition ou les intervalles de répétition d'autres types de déclencheur de tâche, la commande doit inclure les paramètres *Once* , *At* , *RepetitionInterval* et *RepetitionDuration* .

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

### -RepetitionInterval
Répète la tâche à l'intervalle de temps spécifié.
Par exemple, si la valeur de ce paramètre est de 2 heures, la tâche est déclenchée toutes les deux heures.
La valeur par défaut, 0, ne répète pas la tâche.

Entrez un objet TimeSpan, tel que celui retourné par l’applet de commande New-TimeSpan ou une chaîne qui peut être convertie en un objet TimeSpan, tel que « 1:05:30 ».

Pour modifier la durée de répétition ou l'intervalle de répétition d'un déclencheur de tâche **Once** , la commande doit inclure les paramètres **RepetitionInterval** et **RepetitionDuration** .
Pour modifier la durée de répétition ou les intervalles de répétition d'autres types de déclencheur de tâche, la commande doit inclure les paramètres **Once** , **At** , **RepetitionInterval** et **RepetitionDuration** .

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

### -User
Spécifie les utilisateurs qui déclenchent un démarrage *AtLogon* d'une tâche planifiée.
Entrez le nom d’un utilisateur au \<UserName\> format ou, \<Domain\Username\> ou entrez un astérisque ( \* ) pour représenter tous les utilisateurs.
La valeur par défaut est tous les utilisateurs.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hebdomadaire
Spécifie une planification de tâche hebdomadaire périodique.
Utilisez les autres paramètres du jeu de paramètres *Weekly* pour spécifier les détails de la planification.

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

### -WeeksInterval
Spécifie le nombre de semaines entre les occurrences d'une planification de tâche hebdomadaire.
Par exemple, une valeur de 3 démarre la tâche planifiée les semaines 1, 4, 7 et ainsi de suite.
La valeur par défaut est 1.

```yaml
Type: System.Int32
Parameter Sets: (All)
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger
Vous pouvez diriger plusieurs déclencheurs de tâche vers **Set-JobTrigger** .

## SORTIES

### Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger
Quand vous utilisez le paramètre *Passthru* , **Set-JobTrigger** retourne les déclencheurs de tâche modifiés.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* Les déclencheurs de tâche ont une propriété JobDefintion qui les associe à la tâche planifiée. Quand vous modifiez le déclencheur d'une tâche planifiée, la tâche est modifiée. Vous n’avez pas besoin d’utiliser une commande Set-ScheduledJob pour appliquer le déclencheur modifié à la tâche planifiée.

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
