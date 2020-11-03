---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202994"
---
# Register-ScheduledJob

## SYNOPSIS
Crée une tâche planifiée.

## SYNTAX

### ScriptBlock (valeur par défaut)

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilePath

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## Description

L' `Register-ScheduledJob` applet de commande crée des tâches planifiées sur l’ordinateur local.

Une tâche planifiée est une tâche en arrière-plan Windows PowerShell qui peut être démarrée automatiquement selon une planification ponctuelle ou périodique. Les tâches planifiées sont stockées sur le disque et enregistrées dans Planificateur de tâches.
Les tâches peuvent être gérées dans Planificateur de tâches ou à l’aide des applets de commande de tâche planifiée dans Windows PowerShell.

Lorsqu’une tâche planifiée démarre, elle crée une instance de la tâche planifiée. Les instances de tâche planifiée sont identiques aux tâches en arrière-plan Windows PowerShell, sauf que les résultats sont enregistrés sur le disque. Utilisez les applets de commande Job, telles que `Start-Job` , `Get-Job` et `Receive-Job` pour démarrer, afficher et obtenir les résultats des instances de tâche.

Utilisez `Register-ScheduledJob` pour créer une nouvelle tâche planifiée. Pour spécifier les commandes exécutées par la tâche planifiée, utilisez le paramètre **scriptblock** . Pour spécifier un script exécuté par la tâche, utilisez le paramètre **filePath** .

Windows PowerShell-les tâches planifiées utilisent les mêmes déclencheurs et options de tâche que ceux utilisés par Planificateur de tâches pour les tâches planifiées.

Le paramètre **Trigger** de `Register-ScheduledJob` ajoute un ou plusieurs déclencheurs de tâche qui démarrent le travail. Le paramètre de **déclencheur** étant facultatif, vous pouvez ajouter des déclencheurs quand vous créez la tâche planifiée, ajouter des déclencheurs de tâche ultérieurement, ajouter le paramètre **RunNow** pour démarrer la tâche immédiatement, utiliser l' `Start-Job` applet de commande pour démarrer la tâche immédiatement à tout moment, ou enregistrer la tâche planifiée non déclenchée comme modèle pour d’autres travaux.

Le paramètre **Options** vous permet de personnaliser les paramètres des options pour la tâche planifiée. Le paramètre **options** est facultatif, ce qui vous permet de définir des options de tâche lorsque vous créez la tâche planifiée ou de les modifier à tout moment. Comme les paramètres d'options de tâche peuvent empêcher l'exécution de la tâche planifiée, passez en revue les options de tâche et définissez-les avec soin.

`Register-ScheduledJob` est l’une des collections d’applets de commande de planification des travaux dans le module **PSScheduledJob** inclus dans Windows PowerShell.

Pour plus d’informations sur les tâches planifiées, consultez la rubrique à propos des articles dans le module **PSScheduledJob** .
Importez le module **PSScheduledJob** , puis tapez : `Get-Help about_Scheduled*` ou consultez [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : créer une tâche planifiée

Cet exemple crée une tâche planifiée sur l’ordinateur local.

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

`Register-ScheduledJob` utilise le paramètre **Name** pour créer la tâche planifiée **Archive-scripts** .
Le paramètre **scriptblock** s’exécute `Get-ChildItem` et recherche les `$home` fichiers de manière récursive dans le répertoire `.ps1` . L' `Copy-Item` applet de commande copie les fichiers dans un répertoire spécifié par le paramètre **destination** .

Étant donné que la tâche planifiée ne contient pas de déclencheur, elle n’est pas démarrée automatiquement. Vous pouvez ajouter des déclencheurs de tâche avec `Add-JobTrigger` , utiliser l' `Start-Job` applet de commande pour démarrer le travail à la demande ou utiliser la tâche planifiée comme modèle pour d’autres tâches planifiées.

### Exemple 2 : créer une tâche planifiée avec des déclencheurs et des options personnalisées

Cet exemple montre comment créer une tâche planifiée qui a un déclencheur de tâche et des options de tâche personnalisées.

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

La `$O` variable stocke l’objet d’option de travail créé par l’applet de commande `New-ScheduledJobOption` . Les options démarrent la tâche planifiée même si l’ordinateur n’est pas inactif, sort de veille l’ordinateur pour exécuter le travail, si nécessaire, et autorise l’exécution de plusieurs instances du travail dans une série.

La `$T` variable stocke le résultat de l' `New-JobTrigger` applet de commande pour créer un déclencheur de tâche qui démarre un travail tous les autres lundis à 9:00 pm.

La `$path` variable stocke le chemin d’accès au `UpdateVersion.ps1` fichier de script.

`Register-ScheduledJob` utilise le paramètre **Name** pour créer la tâche planifiée **UpdateVersion** .
Le paramètre **filePath** utilise `$path` pour spécifier le script exécuté par le travail. Le paramètre **ScheduledJobOption** utilise les options de travail stockées dans `$O` . Le paramètre **Trigger** utilise les déclencheurs de tâche stockés dans `$T` .

### Exemple 3 : utiliser des tables de hachage pour spécifier un déclencheur et des options de tâche planifiée

Cet exemple a le même effet que la commande dans l’exemple 2. Il crée une tâche planifiée à l’aide de tables de hachage pour spécifier les valeurs des paramètres **déclencheur** et **ScheduledJobOption** . Les `$O` `$T` variables et définies dans l’exemple 2 sont remplacées par des tables de hachage.

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### Exemple 4 : créer des tâches planifiées sur des ordinateurs distants

Dans cet exemple, la tâche planifiée **EnergyData** est créée sur plusieurs ordinateurs distants. La tâche planifiée exécute un script qui recueille les données brutes et les enregistre dans un journal d’exécution sur l’ordinateur distant.

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

La `$Cred` variable stocke les informations d’identification dans un objet **PSCredential** pour un utilisateur disposant des autorisations nécessaires pour créer des tâches planifiées. La `$O` variable stocke les options de travail créées avec `New-ScheduledJobOption` . La `$T` variable stocke les déclencheurs de tâche créés avec `New-JobTrigger` .

L' `Invoke-Command` applet de commande utilise le paramètre **ComputerName** pour obtenir une liste de noms de serveurs à partir du `Servers.txt` fichier. Le paramètre **Credential** obtient l’objet Credential stocké dans `$Cred` .
Le paramètre **scriptblock** exécute une `Register-ScheduledJob` commande sur les ordinateurs du `Servers.txt` fichier.

Les paramètres de `Register-ScheduledJob` sont définis par `$params` . Les paramètres **Name** spécifient que le travail est nommé **« EnergyData »** sur chaque ordinateur distant. **FilePath** fournit l’emplacement du `EnergyData.ps1` script. Le script se trouve sur un serveur de fichiers qui est disponible pour tous les ordinateurs participants. La tâche s’exécute selon la planification spécifiée par les déclencheurs de tâche dans `$T` et les options de tâche dans `$O` .

La `Register-ScheduledJob @params` commande crée la tâche planifiée avec les paramètres du bloc de script.

### Exemple 5 : créer une tâche planifiée qui exécute un script sur des ordinateurs distants

Cet exemple crée la tâche planifiée **CollectEnergyData** sur l’ordinateur local. La tâche s’exécute sur plusieurs ordinateurs distants.

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

La `$Admin` variable stocke les informations d’identification d’un utilisateur disposant des autorisations nécessaires pour exécuter les commandes dans un objet **PSCredential** . La `$T` variable stocke les déclencheurs de tâche créés avec `New-JobTrigger` .

L' `Register-ScheduledJob` applet de commande utilise le paramètre **Name** pour créer la tâche planifiée **CollectEnergyData** sur l’ordinateur local. Le paramètre **Trigger** spécifie les déclencheurs de tâche dans `$T` et le paramètre **MaxResultCount** augmente le nombre de résultats enregistrés à 99.

Le paramètre **scriptblock** définit les `Invoke-Command` paramètres avec `$params` . Le paramètre **AsJob** crée l’objet de tâche en arrière-plan sur l’ordinateur local, même si le `Energydata.ps1` script s’exécute sur les ordinateurs distants. Le paramètre **ComputerName** obtient une liste de noms de serveurs à partir du `Servers.txt` fichier. Le paramètre **Credential** spécifie un compte d’utilisateur qui a l’autorisation d’exécuter des scripts sur les ordinateurs distants. Et, le paramètre **Authentication** spécifie la valeur **CredSSP** pour autoriser les informations d’identification déléguées.

Le `Invoke-Command @params` exécute la commande avec les paramètres du bloc de script.

## PARAMETERS

### -ArgumentList

Spécifie des valeurs pour les paramètres du script spécifié par le paramètre **FilePath** ou pour la commande spécifiée par le paramètre **ScriptBlock** .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme permettant d'authentifier les informations d'identification de l'utilisateur. La valeur par défaut est Default.

Les valeurs valides pour ce paramètre sont :

- Default
- Basic
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> L'authentification CredSSP (Credential Security Service Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

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

### -Credential

Spécifie un compte d'utilisateur qui a l'autorisation d'exécuter la tâche planifiée. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui de l’applet de commande `Get-Credential` . Si vous entrez uniquement un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un script exécuté par la tâche planifiée. Entrez le chemin d’accès à un `.ps1` fichier sur l’ordinateur local. Pour spécifier les valeurs par défaut des paramètres de script, utilisez le paramètre **ArgumentList** .
Chaque `Register-ScheduledJob` commande doit utiliser les paramètres **scriptblock** ou **filePath** .

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Spécifie le chemin d’accès complet à un script Windows PowerShell ( `.ps1` ). Le script d'initialisation s'exécute dans la session créée pour la tâche en arrière-plan avant les commandes spécifiées par le paramètre **ScriptBlock** ou le script spécifié par le paramètre **FilePath** . Vous pouvez utiliser le script d'initialisation pour configurer la session, par exemple, pour ajouter des fichiers, des fonctions ou des alias, pour créer des répertoires ou pour vérifier des conditions préalables.

Pour spécifier un script qui exécute les commandes de tâche principales, utilisez le paramètre **FilePath** .

Si le script d’initialisation génère une erreur, même une erreur sans fin d’exécution, l’instance actuelle de la tâche planifiée ne s’exécute pas et son état est **failed** .

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxResultCount

Spécifie le nombre d'entrées de résultat de tâche qui sont conservées pour la tâche planifiée. La valeur par défaut est 32.

Windows PowerShell enregistre l'historique d'exécution et les résultats de chaque instance déclenchée de la tâche planifiée sur le disque. La valeur de ce paramètre détermine le nombre de résultats d'instance de tâche qui sont enregistrés pour cette tâche planifiée. Quand le nombre de résultats d'instance de tâche dépasse cette valeur, Windows PowerShell supprime les résultats de l'instance de tâche la plus ancienne pour libérer de l'espace pour les résultats de la dernière instance de tâche.

L’historique d’exécution des travaux et les résultats des travaux sont enregistrés dans le `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`
répertoires sur l’ordinateur sur lequel le travail est créé. Pour afficher l’historique d’exécution, utilisez l’applet de commande `Get-Job` . Pour obtenir les résultats de la tâche, utilisez l'applet de commande `Receive-Job`.

Le paramètre **MaxResultCount** définit la valeur de la propriété ExecutionHistoryLength de la tâche planifiée.

Pour supprimer l’historique d’exécution actuel et les résultats des tâches, utilisez le paramètre **ClearExecutionHistory** de l’applet de commande `Set-ScheduledJob` .

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un nom pour la tâche planifiée. Le nom est également utilisé pour toutes les instances démarrées de la tâche planifiée. Le nom doit être unique sur l'ordinateur. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

Exécute la tâche planifiée dans un processus 32 bits.

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

### -RunEvery

Utilisé pour spécifier la fréquence d’exécution du travail. Par exemple, utilisez cette option pour exécuter un travail toutes les 15 minutes.

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

### -RunNow

Démarre une tâche immédiatement, dès que l' `Register-ScheduledJob` applet de commande est exécutée. Ce paramètre élimine le besoin de déclencher des Planificateur de tâches pour exécuter un script Windows PowerShell immédiatement après l’inscription et n’oblige pas les utilisateurs à créer un déclencheur qui spécifie une date et une heure de début.

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

### -ScheduledJobOption

Définit les options de la tâche planifiée. Entrez un objet **ScheduledJobOptions** , tel que celui que vous créez à l’aide de l’applet de commande `New-ScheduledJobOption` , ou une valeur de table de hachage.

Vous pouvez définir les options d’une tâche planifiée lors de l’inscription du travail de planification ou utiliser les `Set-ScheduledJobOption` `Set-ScheduledJob` applets de commande ou pour modifier les options.

La plupart des options et leurs valeurs par défaut déterminent si et quand une tâche planifiée s'exécute. Veillez à consulter ces options avant de planifier une tâche. Pour obtenir une description des options de tâche planifiée, y compris les valeurs par défaut, consultez `New-ScheduledJobOption` .

Pour envoyer une table de hachage, utilisez les clés suivantes. Dans la table de hachage suivante, les clés sont affichées avec leurs valeurs par défaut.

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

Spécifie les commandes exécutées par la tâche planifiée. Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script. Pour spécifier les valeurs par défaut des paramètres de commande, utilisez le paramètre **ArgumentList** .

Chaque `Register-ScheduledJob` commande doit utiliser les paramètres **scriptblock** ou **filePath** .

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Déclencheur

Spécifie les déclencheurs de la tâche planifiée. Entrez un ou plusieurs objets **ScheduledJobTrigger** , tels que les objets `New-JobTrigger` renvoyés par l’applet de commande, ou une table de hachage de clés et de valeurs de déclencheur de tâche.

Un déclencheur de tâche démarre le travail de planification. Le déclencheur peut spécifier une planification ponctuelle ou périodique, ou un événement, tel que le moment où un utilisateur ouvre une session ou où Windows démarre.

Le paramètre **Trigger** est facultatif. Vous pouvez ajouter un déclencheur quand vous créez la tâche planifiée, utiliser les `Add-JobTrigger` `Set-JobTrigger` `Set-ScheduledJob` applets de commande, ou pour ajouter ou modifier des déclencheurs de tâche ultérieurement, ou utiliser l' `Start-Job` applet de commande pour démarrer immédiatement la tâche planifiée. Vous pouvez également créer et gérer une tâche planifiée sans un déclencheur qui est utilisée comme modèle.

Pour envoyer une table de hachage, utilisez les clés suivantes :

- **Fréquence** : quotidienne, hebdomadaire, AtStartup, AtLogon
- **À** : toute chaîne d’heure valide
- **DaysOfWeek** -toute combinaison de noms de jours
- **Interval** -tout intervalle de fréquence valide
- **RandomDelay** : toute chaîne TimeSpan valide
- **Utilisateur** : tout utilisateur valide. Utilisé uniquement avec la valeur de fréquence AtLogon

Par exemple :

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### Aucun

Vous ne pouvez pas envoyer d’entrée dans le pipeline vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition

## REMARQUES

Chaque tâche planifiée est enregistrée dans un sous-répertoire du `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` répertoire sur l’ordinateur local.
Le sous-répertoire est nommé pour la tâche planifiée et contient un fichier XML pour la tâche planifiée et les enregistrements de son historique d’exécution. Pour plus d’informations sur les tâches planifiées sur le disque, consultez [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).

Les tâches planifiées que vous créez dans Windows PowerShell s’affichent dans Planificateur de tâches dans le `Library\Microsoft\Windows\PowerShell\ScheduledJobs` dossier planificateur de tâches. Vous pouvez utiliser le Planificateur de tâches pour afficher et modifier la tâche planifiée.

Vous pouvez utiliser Planificateur de tâches, l’outil en ligne de commande **schtasks.exe** et les applets de commande planificateur de tâches pour gérer les tâches planifiées que vous créez avec les applets de commande Job Schedule. Toutefois, vous ne pouvez pas utiliser les applets de commande Job scheduled pour gérer les tâches que vous créez dans Planificateur de tâches.

En cas d'échec d'une commande de la tâche planifiée, Windows PowerShell retourne un message d'erreur. Toutefois, si le travail échoue quand Planificateur de tâches tente de l’exécuter, l’erreur n’est pas disponible pour Windows PowerShell.

Si une tâche planifiée ne s’exécute pas, utilisez les méthodes suivantes pour rechercher la raison :

- Vérifiez que le déclencheur de tâche est correctement défini.
  - Vérifiez que les conditions définies dans les options de tâche sont satisfaites.
- Vérifiez que le compte d’utilisateur sous lequel la tâche s’exécute est autorisé à exécuter les commandes ou les scripts du travail.
- Recherchez les erreurs dans l’historique des Planificateur de tâches.
- Recherchez les erreurs dans le journal des événements Planificateur de tâches.

Pour plus d’informations, consultez [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).

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
