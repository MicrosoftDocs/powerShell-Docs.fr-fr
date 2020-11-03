---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202654"
---
# Start-Job

## SYNOPSIS
Démarre une tâche en arrière-plan PowerShell.

## SYNTAX

### ComputerName (par défaut)

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### DefinitionName

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### FilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### LiteralFilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## Description

L' `Start-Job` applet de commande démarre une tâche en arrière-plan PowerShell sur l’ordinateur local.

Une tâche en arrière-plan PowerShell exécute une commande sans interagir avec la session active. Lorsque vous démarrez une tâche en arrière-plan, un objet de tâche est retourné immédiatement, même si le travail prend une durée prolongée. Vous pouvez continuer à travailler dans la session sans interruption pendant l'exécution de la tâche.

L’objet de traitement contient des informations utiles sur le travail, mais il ne contient pas les résultats du travail.
Une fois le travail terminé, utilisez l' `Receive-Job` applet de commande pour obtenir les résultats du travail. Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs](./About/about_Jobs.md).

Pour exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez le paramètre **AsJob** qui est disponible sur de nombreuses applets de commande, ou utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande sur l’ordinateur distant. Pour plus d’informations, consultez [about_Remote_Jobs](./About/about_Remote_Jobs.md).

À compter de PowerShell 3,0, `Start-Job` peut démarrer des instances de types de tâches personnalisées, telles que les tâches planifiées. Pour plus d’informations sur l’utilisation `Start-Job` de pour démarrer des travaux avec des types personnalisés, consultez les documents d’aide pour la fonctionnalité de type de tâche.

Le répertoire de travail par défaut pour les travaux est codé en dur. La valeur par défaut `$HOME\Documents` de Windows est et sur Linux ou MacOS, la valeur par défaut est `$HOME` . Le code de script qui s’exécute dans la tâche en arrière-plan doit gérer le répertoire de travail en fonction des besoins.

## EXEMPLES

### Exemple 1 : démarrer une tâche en arrière-plan

Cet exemple démarre une tâche en arrière-plan qui s’exécute sur l’ordinateur local.

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Process` en tant que tâche en arrière-plan. Le paramètre **Name** spécifie de rechercher les processus PowerShell, `powershell` . Les informations sur le travail s’affichent et PowerShell retourne à une invite pendant l’exécution de la tâche en arrière-plan.

Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande. Par exemple : `Receive-Job -Id 1`.

### Exemple 2 : démarrer un travail à l’aide de Invoke-Command

Cet exemple exécute un travail sur plusieurs ordinateurs. Le travail est stocké dans une variable et est exécuté à l’aide du nom de variable sur la ligne de commande PowerShell.

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

Un travail qui utilise `Invoke-Command` est créé et stocké dans la `$jobWRM` variable. `Invoke-Command` utilise le paramètre **ComputerName** pour spécifier les ordinateurs sur lesquels le travail s’exécute. `Get-Content` Obtient les noms de serveur à partir du `C:\Servers.txt` fichier.

Le paramètre **scriptblock** spécifie une commande qui `Get-Service` obtient le service **WinRM** . Le paramètre **JobName** spécifie un nom convivial pour le travail, **WinRM** . Le paramètre **ThrottleLimit** limite le nombre de commandes simultanées à 16. Le paramètre **AsJob** démarre une tâche en arrière-plan qui exécute la commande sur les serveurs.

### Exemple 3 : récupérer des informations sur un travail

Cet exemple obtient des informations sur un travail et affiche les résultats d’une tâche terminée qui a été exécutée sur l’ordinateur local.

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` utilise le paramètre **scriptblock** pour exécuter une commande qui spécifie `Get-WinEvent` d’obtenir le journal **système** . Le paramètre **Credential** spécifie un compte d’utilisateur de domaine autorisé à exécuter la tâche sur l’ordinateur. L’objet de traitement est stocké dans la `$j` variable.

L’objet dans la `$j` variable est envoyé dans le pipeline à `Select-Object` . Le paramètre **Property** spécifie un astérisque ( `*` ) pour afficher toutes les propriétés de l’objet de tâche.

### Exemple 4 : exécuter un script en tant que tâche en arrière-plan

Dans cet exemple, un script sur l’ordinateur local est exécuté en tant que tâche en arrière-plan.

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

`Start-Job` utilise le paramètre **filePath** pour spécifier un fichier de script stocké sur l’ordinateur local.

### Exemple 5 : obtenir un processus à l’aide d’une tâche en arrière-plan

Cet exemple utilise une tâche en arrière-plan pour obtenir un processus spécifié par son nom.

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **PShellJob** . Le paramètre **scriptblock** spécifie `Get-Process` d’extraire les processus avec le nom **PowerShell** .

### Exemple 6 : collecter et enregistrer des données à l’aide d’une tâche en arrière-plan

Cet exemple démarre un travail qui collecte une grande quantité de données cartographiques, puis l’enregistre dans un `.tif` fichier.

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

`Start-Job` utilise le paramètre **Name** pour spécifier un nom de travail convivial, **GetMappingFiles** . Le paramètre **initializationScript** exécute un bloc de script qui importe le module **MapFunctions** . Le paramètre **scriptblock** s’exécute `Get-Map` et `Set-Content` enregistre les données à l’emplacement spécifié par le paramètre **path** . Le paramètre **RunAs32** exécute le processus comme 32 bits, même sur un système d’exploitation 64 bits.

### Exemple 7 : passer une entrée à une tâche en arrière-plan

Cet exemple utilise la `$input` variable Automatic pour traiter un objet d’entrée. Utilisez `Receive-Job` pour afficher la sortie du travail.

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

`Start-Job` utilise le paramètre **scriptblock** pour s’exécuter `Get-Content` avec la `$input` variable automatique. La `$input` variable récupère des objets à partir du paramètre **InputObject** . `Receive-Job` utilise le paramètre **Name** pour spécifier le travail et renvoie les résultats. Le paramètre **Keep** enregistre la sortie du travail afin qu’il puisse être affiché à nouveau pendant la session PowerShell.

### Exemple 8 : utiliser le paramètre ArgumentList pour spécifier un tableau

Cet exemple utilise le paramètre **argumentlist** pour spécifier un tableau d’arguments. Le tableau est une liste séparée par des virgules de noms de processus.

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

L' `Start-Job` applet de commande utilise le paramètre **scriptblock** pour exécuter une commande. `Get-Process` utilise le paramètre **Name** pour spécifier la variable automatique `$args` . Le paramètre **argumentlist** passe le tableau de noms de processus à `$args` . Les noms de processus PowerShell, pwsh et Notepad sont des processus en cours d’exécution sur l’ordinateur local.

Pour afficher la sortie du travail, utilisez l' `Receive-Job` applet de commande. Par exemple : `Receive-Job -Id 1`.

## PARAMETERS

### -ArgumentList

Spécifie un tableau d’arguments ou de valeurs de paramètre pour le script spécifié par le paramètre **filePath** ou une commande spécifiée avec le paramètre **scriptblock** .

Les arguments doivent être passés à **argumentlist** comme argument de tableau à une seule dimension. Par exemple, une liste séparée par des virgules. Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentification

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- Default
- Basic
- CredSSP
- Digest
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

La valeur par défaut est Default.

L’authentification CredSSP est disponible uniquement dans Windows Vista, Windows Server 2008 et les versions ultérieures du système d’exploitation Windows.

Pour plus d’informations sur les valeurs de ce paramètre, consultez [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> l'authentification CredSSP (Credential Security Support Provider), au cours de laquelle les informations d'identification de l'utilisateur sont passées à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui nécessitent une authentification sur plusieurs ressources, telles que l'accès à un partage réseau distant. Ce mécanisme augmente le risque de sécurité lié à l'opération distante. Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. Si le paramètre **Credential** n’est pas spécifié, la commande utilise les informations d’identification de l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionName

Spécifie le nom de la définition du travail que cette applet de commande démarre. Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un nom de définition, comme les tâches planifiées.

Lorsque vous utilisez `Start-Job` pour démarrer une instance d’une tâche planifiée, le travail démarre immédiatement, quels que soient les déclencheurs ou les options de travail. L’instance de tâche qui en résulte est une tâche planifiée, mais elle n’est pas enregistrée sur le disque comme les tâches planifiées déclenchées. Vous ne pouvez pas utiliser le paramètre **argumentlist** de `Start-Job` pour fournir des valeurs pour les paramètres de scripts qui s’exécutent dans une tâche planifiée. Pour plus d’informations, consultez [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionPath

Spécifie le chemin d’accès de la définition du travail que cette applet de commande démarre. Entrez le chemin d'accès à la définition. La concaténation des valeurs des paramètres **DefinitionPath** et **DefinitionName** est le chemin d’accès complet de la définition du travail. Utilisez ce paramètre pour démarrer les types de tâche personnalisés ayant un chemin d'accès de définition, comme les tâches planifiées.

Pour les tâches planifiées, la valeur du paramètre **DefinitionPath** est `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un script local qui `Start-Job` s’exécute en tant que tâche en arrière-plan. Entrez le chemin d’accès et le nom de fichier du script ou utilisez le pipeline pour lui envoyer un chemin d’accès de script `Start-Job` . Le script doit se trouver sur l’ordinateur local ou dans un dossier accessible à l’ordinateur local.

Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script et exécute le bloc de script en tant que tâche en arrière-plan.

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Spécifie les commandes à exécuter avant le début de la tâche. Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ).

Utilisez ce paramètre pour préparer la session dans laquelle la tâche s'exécute. Par exemple, vous pouvez l'utiliser pour ajouter des fonctions, des composants logiciels enfichables et des modules à la session.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l'entrée de la commande. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui génère ces objets.

Dans la valeur du paramètre **scriptblock** , utilisez la `$input` variable Automatic pour représenter les objets d’entrée.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie un script local que cette applet de commande exécute en tant que tâche en arrière-plan. Entrez le chemin d’accès d’un script sur l’ordinateur local.

`Start-Job` utilise la valeur du paramètre **LiteralPath** exactement telle qu’elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom convivial de la nouvelle tâche. Vous pouvez utiliser le nom pour identifier le travail à d’autres applets de commande de tâche, telles que l’applet de commande `Stop-Job` .

Le nom convivial par défaut est `Job#` , où `#` est un nombre ordinal qui est incrémenté pour chaque tâche.

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSVersion

Spécifie une version. `Start-Job` exécute la tâche avec la version de PowerShell. Les valeurs acceptables pour ce paramètre sont les suivantes : `2.0` et `3.0` .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

Indique que `Start-Job` exécute la tâche dans un processus 32 bits. **RunAs32** force la tâche à s’exécuter dans un processus 32 bits, même sur un système d’exploitation 64 bits.

Sur les versions 64 bits de Windows 7 et Windows Server 2008 R2, lorsque la `Start-Job` commande comprend le paramètre **RunAs32** , vous ne pouvez pas utiliser le paramètre **Credential** pour spécifier les informations d’identification d’un autre utilisateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

Spécifie les commandes à exécuter dans la tâche en arrière-plan. Pour créer un bloc de script, placez les commandes entre accolades ( `{}` ). Utilisez la `$input` variable Automatic pour accéder à la valeur du paramètre **InputObject** . Ce paramètre est obligatoire.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

Spécifie le type personnalisé pour les travaux démarrés par `Start-Job` . Entrez un nom de type de tâche personnalisé, par exemple, PSScheduledJob pour les tâches planifiées ou PSWorkflowJob pour les tâches de workflow. Ce paramètre n’est pas valide pour les travaux en arrière-plan standard.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez utiliser le pipeline pour envoyer un objet avec la propriété **Name** au paramètre **Name** . Par exemple, vous pouvez effectuer un pipeline d’un objet **FileInfo** de `Get-ChildItem` à `Start-Job` .

## SORTIES

### System. Management. Automation. PSRemotingJob

`Start-Job` retourne un objet **PSRemotingJob** qui représente le travail qu’il a démarré.

## REMARQUES

Pour s’exécuter en arrière-plan, `Start-Job` s’exécute dans sa propre session dans la session active. Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Start-Job` commande dans une session sur un ordinateur distant, `Start-Job` s’exécute dans une session de la session à distance.

## LIENS CONNEXES

[about_Arrays](./about/about_arrays.md)

[about_Automatic_Variables](./about/about_automatic_variables.md)

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
