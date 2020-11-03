---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: a6ed76164dbc2773393211ad8474becb499986a3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201437"
---
# Register-ObjectEvent

## SYNOPSIS
S'abonne aux événements générés par un objet Microsoft .NET Framework.

## SYNTAX

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## Description

L' `Register-ObjectEvent` applet de commande s’abonne aux événements qui sont générés par les objets .net sur l’ordinateur local ou sur un ordinateur distant.

Quand l'événement auquel vous êtes abonné est déclenché, il est ajouté à la file d'attente d'événements dans votre session. Pour récupérer des événements dans la file d’attente d’événements, utilisez l’applet de commande `Get-Event` .

Vous pouvez utiliser les paramètres de `Register-ObjectEvent` pour spécifier les valeurs de propriété des événements qui peuvent vous aider à identifier l’événement dans la file d’attente. Vous pouvez également utiliser le paramètre **action** pour spécifier les actions à entreprendre lorsqu’un événement abonné est déclenché et le paramètre **Forward** pour envoyer des événements distants à la file d’attente d’événements dans la session locale.

Lorsque vous vous abonnez à un événement, un abonné est ajouté à votre session. Pour obtenir les abonnés aux événements dans la session, utilisez l'applet de commande `Get-EventSubscriber`. Pour annuler l'abonnement, utilisez l'applet de commande `Unregister-Event`, ce qui supprime l'abonné aux événements de la session.

## EXEMPLES

### Exemple 1 : s’abonner à des événements lors du démarrage d’un nouveau processus

Cet exemple s'abonne aux événements générés au démarrage d'un nouveau processus.

La commande utilise l’objet **ManagementEventWatcher** pour récupérer les événements **EventArrived** . Un objet de requête spécifie que les événements sont des événements de création d’instance pour la classe **Win32_Process** .

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### Exemple 2 : spécifier une action pour répondre à un événement

Lorsque vous spécifiez une action, les événements déclenchés ne sont pas ajoutés à la file d'attente des événements. À la place, l'action répond à l'événement. Dans cet exemple, lorsqu’un événement de création d’instance est déclenché, indiquant qu’un nouveau processus est démarré, un nouvel événement **ProcessCreated** est déclenché.

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

L’action utilise les `$Sender` `$EventArgs` variables automatiques et, qui sont remplies uniquement pour les actions d’événement.

La `Register-ObjectEvent` commande retourne un objet de traitement qui représente l’action, qui s’exécute en tant que tâche en arrière-plan. Vous pouvez utiliser les applets de commande Job, telles que `Get-Job` et `Receive-Job` , pour gérer la tâche en arrière-plan. Pour plus d’informations, consultez [à propos des_tâches](../Microsoft.PowerShell.Core/About/about_Jobs.md).

### Exemple 3 : s’abonner à des événements d’objet sur des ordinateurs distants

Cet exemple montre comment s'abonner aux événements d'objet sur des ordinateurs distants. Cet exemple utilise la `Enable-ProcessCreationEvent` fonction définie dans le fichier de `ProcessCreationEvent.ps1` script. Ce script est disponible pour tous les ordinateurs de l’exemple.

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

La première consiste à créer **sessions PSSession** sur deux ordinateurs distants et à les enregistrer dans la `$S` variable. Ensuite, l' `Invoke-Command` applet de commande exécute le `ProcessCreationEvent.ps1` script dans chacun des sessions PSSession dans `$S` . Cette action crée la `Enable-ProcessCreationEvent` fonction dans les sessions à distance.
Enfin, nous exécutons la `Enable-ProcessCreationEvent` fonction dans les sessions à distance.

 La fonction comprend une `Register-ObjectEvent` commande qui s’abonne aux événements de création d’instance sur l’objet **Win32_Process** par le biais de l’objet **ManagementEventWatcher** et de son événement **EventArrived** .

### Exemple 4 : utiliser le module dynamique dans l’objet PSEventJob

Cet exemple montre comment utiliser le module dynamique dans l’objet **PSEventJob** créé lorsque vous incluez une **action** dans une inscription d’événement. Tout d’abord, nous createand et activons un objet de minuteur, puis nous définissons l’intervalle du minuteur sur 500 (millisecondes). L' `Register-ObjectEvent` applet de commande enregistre l’événement **Elapsed** de l’objet Timer. L’objet **PSEventJob** est enregistré dans la `$Job` variable et est également disponible dans la propriété **action** de l’abonné aux événements. Pour plus d’informations, consultez la page [obtenir-EventSubscriber](Get-EventSubscriber.md).

Chaque fois que l’intervalle de la minuterie est écoulé, un événement est déclenché et l’action est exécutée. Dans ce cas, l' `Get-Random` applet de commande génère un nombre aléatoire compris entre 0 et 100 et l’enregistre dans la `$Random` variable.

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

**PSEventJob** a une propriété **module** qui contient un module de script dynamique qui implémente l’action. À l’aide de l’opérateur d’appel ( `&` ), nous appelons la commande dans le module pour afficher la valeur de la `$Random` variable.

Pour plus d’informations sur les modules, consultez [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

## PARAMETERS

### -Action

Spécifie les commandes pour gérer l’événement. Les commandes dans **Action** s'exécutent quand un événement est déclenché, au lieu d'envoyer l'événement à la file d'attente d'événements. Placez les commandes entre accolades ( { } ) pour créer un bloc de script.

La valeur du paramètre d' **action** peut inclure les `$Event` variables automatiques,,, `$EventSubscriber` `$Sender` `$EventArgs` et `$Args` . Ces variables fournissent des informations sur l’événement au bloc de script de l' **action** . Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

Lorsque vous spécifiez une action, `Register-ObjectEvent` retourne un objet de tâche d’événement qui représente cette action. Vous pouvez utiliser les applets de commande Job pour gérer la tâche de l'événement.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventName

Spécifie l'événement auquel vous vous abonnez.

La valeur de ce paramètre doit être le nom de l’événement que l’objet .NET expose. Par exemple, la classe **ManagementEventWatcher** a des événements nommés **EventArrived** et **Stopped** . Pour rechercher le nom d’événement d’un événement, utilisez l’applet de commande `Get-Member` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Suivant

Indique que l’applet de commande envoie des événements pour cet abonnement à une session à distance. Utilisez ce paramètre lorsque vous vous inscrivez aux événements sur un ordinateur distant ou dans une session à distance.

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

### -InputObject

Spécifie l’objet .NET qui génère les événements. Entrez une variable contenant l'objet, ou tapez une commande ou une expression qui l'obtient.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

Spécifie le nombre maximal de fois où un événement peut être déclenché.

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

### -MessageData

Spécifie toutes les données supplémentaires à associer à cet abonnement aux événements. La valeur de ce paramètre apparaît dans la propriété MessageData de tous les événements associés à cet abonnement.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie un nom que vous sélectionnez pour l'abonnement. Le nom que vous sélectionnez doit être unique dans la session active. La valeur par défaut est le GUID assigné par PowerShell.

La valeur de ce paramètre apparaît dans la valeur de la propriété **SourceIdentifier** de l’objet abonné et de tous les objets événement associés à cet abonnement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Indique que l’applet de commande masque l’abonnement aux événements. Utilisez ce paramètre lorsque l’abonnement actuel fait partie d’un mécanisme d’inscription d’événement plus complexe et ne doit pas être découvert indépendamment.

Pour afficher ou annuler un abonnement qui a été créé avec le paramètre **SupportEvent** , utilisez le paramètre **force** des `Get-EventSubscriber` applets de commande et `Unregister-Event` .

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’objets vers `Register-ObjectEvent` .

## SORTIES

### None ou System. Management. Automation. PSEventJob

Quand vous utilisez le paramètre **action** , `Register-ObjectEvent` retourne un objet **System. Management. Automation. PSEventJob** . Sinon, elle ne génère aucune sortie.

## REMARQUES

Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
