---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387904"
---
# Set-ScheduledJob

## SYNOPSIS
Modifie les tâches planifiées.

## SYNTAXE

### ScriptBlock (valeur par défaut)

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### FilePath

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### Exécution

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## DESCRIPTION
L'applet de commande **Set-ScheduledJob** modifie les propriétés des tâches planifiées, telles que les commandes exécutées par les tâches ou les informations d'identification requises pour exécuter la tâche.
Vous pouvez également l'utiliser pour effacer l'historique d'exécution de la tâche planifiée.

Pour utiliser cette applet de commande, commencez par utiliser l’applet de commande Get-ScheduledJob pour accéder à la tâche planifiée.
Ensuite, dirigez la tâche planifiée vers **Set-ScheduledJob** ou enregistrez la tâche dans une variable et utilisez le paramètre *InputObject* pour identifier la tâche.
Utilisez les paramètres restants de **Set-ScheduledJob** pour modifier les propriétés de la tâche ou effacer l'historique d'exécution.

Bien que vous puissiez utiliser **Set-ScheduledJob** pour modifier les déclencheurs et les options d’une tâche planifiée, les applets de commande Add-JobTrigger, Set-JobTrigger et Set-ScheduledJobOption fournissent des méthodes beaucoup plus faciles pour accomplir ces tâches.
Pour créer une nouvelle tâche planifiée, utilisez l’applet de commande Register-ScheduledJob.

Le paramètre *Trigger* de **Set-ScheduledJob** ajoute un ou plusieurs déclencheurs de tâche qui démarrent le travail.
Le paramètre de *déclencheur* étant facultatif, vous pouvez ajouter des déclencheurs quand vous créez la tâche planifiée, ajouter des déclencheurs de tâche ultérieurement, ajouter le paramètre *RunNow* pour démarrer la tâche immédiatement, utiliser l’applet de commande Start-Job pour démarrer la tâche immédiatement à tout moment, ou enregistrer la tâche planifiée non déclenchée comme modèle pour d’autres travaux.

**Set-ScheduledJob** fait partie d’une collection d’applets de commande de planification des travaux dans le module PSScheduledJob inclus dans Windows PowerShell.

Pour plus d'informations sur les tâches planifiées, consultez les rubriques À propos dans le module PSScheduledJob.
Importez le module PSScheduledJob, puis tapez : `Get-Help about_Scheduled*` ou consultez about_Scheduled_Jobs.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : modifier le script exécuté par un travail

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

Cet exemple montre comment modifier le script qui est exécuté dans une tâche planifiée.

La première commande utilise l’applet de commande Get-ScheduledJob pour récupérer la tâche planifiée Inventory.
La sortie indique que la tâche exécute le script Get-Inventory.ps1.

Cette commande n'est pas obligatoire ; elle est incluse uniquement pour montrer l'effet de la modification du script.

### Exemple 2 : supprimer l’historique d’exécution d’une tâche planifiée

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

Cette commande supprime l'historique d'exécution actuel et les résultats enregistrés pour la tâche planifiée BackupArchive.

La commande utilise l’applet de commande Get-ScheduledJob pour récupérer la tâche planifiée BackupArchive.
Un opérateur pipeline (|) envoie la tâche à l'applet de commande **Set-ScheduledJob** pour la modifier.
L’applet de commande **Set-ScheduledJob** utilise le paramètre *ClearExecutionHistory* pour supprimer l’historique d’exécution et les résultats enregistrés.

Pour plus d'informations sur l'historique d'exécution et les résultats enregistrés des tâches planifiées, consultez about_Scheduled_Jobs.

### Exemple 3 : modification des tâches planifiées sur un ordinateur distant

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

Cette commande modifie le script d'initialisation dans toutes les tâches planifiées sur les ordinateurs Server01 et Server02.

La commande utilise l’applet de commande Invoke-Command pour exécuter une commande sur les ordinateurs SERVEUR01 et Server02.

La commande distante commence par une commande Get-ScheduledJob qui obtient toutes les tâches planifiées sur l’ordinateur.
Les tâches planifiées sont dirigées vers l’applet de commande **Set-ScheduledJob** , qui modifie le script d’initialisation en SetForRun.ps1.

## PARAMÈTRES

### -ArgumentList
Spécifie des valeurs pour les paramètres du script spécifié par le paramètre *FilePath* ou pour la commande spécifiée par le paramètre *ScriptBlock*.

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentification
Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur.
Les valeurs valides pour ce paramètre sont :

- Default
- De base
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default. Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) dans le kit de développement logiciel (SDK) PowerShell.

ATTENTION : l’authentification CredSSP (Credential Security Support Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.
Ce mécanisme augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClearExecutionHistory
Supprime l'historique d'exécution actuel et les résultats enregistrés de la tâche planifiée.

L'historique d'exécution des tâches et les résultats de ces dernières sont enregistrés avec la tâche planifiée dans le répertoire $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs sur l'ordinateur sur lequel la tâche est créée.
Pour afficher l’historique d’exécution, utilisez l’applet de commande Get-Job.
Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.

Ce paramètre n'affecte pas les événements écrits par le Planificateur de tâches dans les journaux des événements Windows et n'empêche pas Windows PowerShell d'enregistrer les résultats de la tâche.
Pour gérer le nombre de résultats de la tâche qui sont enregistrés, utilisez le paramètre *MaxResultCount*.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Spécifie un compte d'utilisateur qui a l'autorisation d'exécuter la tâche planifiée.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui de l’applet de commande Get-Credential.
Si vous entrez uniquement un nom d'utilisateur, vous êtes invité à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath
Spécifie un script exécuté par la tâche planifiée.
Entrez le chemin d'accès à un fichier .ps1 sur l'ordinateur local.
Pour spécifier les valeurs par défaut des paramètres de script, utilisez le paramètre *ArgumentList*.
Chaque tâche planifiée doit avoir une valeur *ScriptBlock* ou *FilePath*.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript
Spécifie le chemin d'accès complet à un script Windows PowerShell (.ps1).
Le script d'initialisation s'exécute dans la session créée pour la tâche en arrière-plan avant les commandes spécifiées par le paramètre *ScriptBlock* ou le script spécifié par le paramètre *FilePath*.
Vous pouvez utiliser le script d'initialisation pour configurer la session, par exemple, pour ajouter des fichiers, des fonctions ou des alias, pour créer des répertoires ou pour vérifier des conditions préalables.

Pour spécifier un script qui exécute les commandes de tâche principales, utilisez le paramètre *FilePath*.

Si le script d’initialisation génère une erreur, y compris une erreur sans fin d’exécution, l’instance actuelle de la tâche planifiée ne s’exécute pas et son état est failed.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Spécifie la tâche planifiée à modifier.
Entrez une variable qui contient des objets **ScheduledJobDefinition** ou tapez une commande ou une expression qui obtient des objets **ScheduledJobDefinition** , par exemple une commande Get-ScheduledJob.
Vous pouvez également diriger un objet **ScheduledJobDefinition** vers **Set-ScheduledJob**.

Si vous spécifiez plusieurs tâches planifiées, **Set-ScheduledJob** apporte les mêmes modifications à toutes les tâches.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaxResultCount
Spécifie le nombre d'entrées de résultat de tâche qui sont conservées pour la tâche planifiée.
La valeur par défaut est 32.

Windows PowerShell enregistre l'historique d'exécution et les résultats de chaque instance déclenchée de la tâche planifiée sur le disque.
La valeur de ce paramètre détermine le nombre de résultats d'instance de tâche qui sont enregistrés pour cette tâche planifiée.
Quand le nombre de résultats d'instance de tâche dépasse cette valeur, Windows PowerShell supprime les résultats de l'instance de tâche la plus ancienne pour libérer de l'espace pour les résultats de la dernière instance de tâche.

L’historique d’exécution du travail et les résultats du travail sont enregistrés dans les \\ \<JobName\> répertoires $Home \appdata\local\microsoft\windows\powershell\scheduledjobs \Output. \\ \<Timestamp\> de l’ordinateur sur lequel le travail est créé.
Pour afficher l’historique d’exécution, utilisez l’applet de commande Get-Job.
Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.

Le paramètre *MaxResultCount* définit la valeur de la propriété ExecutionHistoryLength de la tâche planifiée.

Pour supprimer l'historique d'exécution actuel et les résultats des tâches, utilisez le paramètre *ClearExecutionHistory*.

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Spécifie un nouveau nom pour la tâche planifiée et les instances de la tâche planifiée.
Le nom doit être unique sur l'ordinateur local.

Pour identifier la tâche planifiée à modifier, utilisez le paramètre *InputObject* ou dirigez une tâche planifiée à partir de Get-ScheduledJob vers **Set-ScheduledJob**.

Ce paramètre ne modifie pas les noms des instances de tâche sur le disque.
Il affecte uniquement les instances de tâche qui sont démarrées à l'issue de cette commande.

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
Retourne un objet représentant l’élément que vous utilisez.
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

### -RunAs32
Exécute la tâche planifiée dans un processus 32 bits.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunEvery

Utilisé pour spécifier la fréquence d’exécution du travail. Par exemple, utilisez cette option pour exécuter un travail toutes les 15 minutes.

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow
Démarre une tâche immédiatement, dès que l’applet de commande **Set-ScheduledJob** est exécutée.
Ce paramètre évite d'avoir à déclencher le Planificateur de tâches pour exécuter un script Windows PowerShell immédiatement après l'inscription et n'oblige pas les utilisateurs à créer un déclencheur qui spécifie une date et une heure de début.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduledJobOption
Définit les options de la tâche planifiée.
Entrez un objet **ScheduledJobOptions** , tel que celui que vous créez à l’aide de l’applet de commande New-ScheduledJobOption, ou une valeur de table de hachage.

Vous pouvez définir les options d’une tâche planifiée lorsque vous inscrivez la tâche planifiée ou utilisez les applets de commande Set-ScheduledJobOption ou **Set-ScheduledJob** pour définir ou modifier les options.

La plupart des options et leurs valeurs par défaut déterminent si et quand une tâche planifiée s'exécute.
Veillez à consulter ces options avant de planifier une tâche.
Pour obtenir une description des options de tâche planifiée, y compris les valeurs par défaut, consultez New-ScheduledJobOption.

Pour envoyer une table de hachage, utilisez les clés suivantes.
Dans la table de hachage suivante, les clés sont affichées avec leurs valeurs par défaut.

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock
Spécifie les commandes exécutées par la tâche planifiée.
Placez les commandes entre accolades ( { } ) pour créer un bloc de script.
Pour spécifier les valeurs par défaut des paramètres de commande, utilisez le paramètre *ArgumentList*.

Chaque commande Register-ScheduledJob doit utiliser les paramètres *ScriptBlock* ou *FilePath*.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Déclencheur
Spécifie les déclencheurs de la tâche planifiée.
Entrez un ou plusieurs objets **ScheduledJobTrigger** , tels que les objets retournées par l’applet de commande New-JobTrigger, ou une table de hachage des clés et des valeurs de déclencheur de tâche.

Un déclencheur de tâche démarre automatiquement une tâche planifiée sur une planification ponctuelle ou périodique, ou quand un événement se produit.

Les déclencheurs de tâche sont facultatifs.
Vous pouvez ajouter un déclencheur quand vous créez la tâche planifiée, utiliser les applets de commande Add-JobTrigger ou **Set-ScheduledJob** pour ajouter des déclencheurs ultérieurement, ou utiliser l’applet de commande Start-Job pour démarrer immédiatement la tâche planifiée.
Vous pouvez également créer et gérer une tâche planifiée qui n'a aucun déclencheur de tâche.

Pour envoyer une table de hachage, utilisez les clés suivantes.

`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (ou toute chaîne d’heure valide); `DaysOfWeek="Monday", "Wednesday"` (ou toute combinaison de noms de jours); `Interval=2` (ou n’importe quel intervalle de fréquence valide); `RandomDelay="30minutes"` (ou toute chaîne TimeSpan valide); `User="Domain1\User01"` (ou tout utilisateur valide ; utilisé uniquement avec la valeur de fréquence AtLogon)

}

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Vous pouvez diriger les tâches planifiées vers **Set-ScheduledJob**.

## SORTIES

### Aucun ou Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Si vous utilisez le paramètre *Passthru* , **Set-ScheduledJob** retourne la tâche planifiée modifiée.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

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
