---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: deade7eb36b93dc6eef4bdd1ff1fd3ef46cffc75
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203169"
---
# Register-EngineEvent

## SYNOPSIS
S’abonne aux événements qui sont générés par le moteur PowerShell et par l’applet de commande `New-Event` .

## SYNTAX

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## Description

L' `Register-EngineEvent` applet de commande s’abonne aux événements générés par le moteur PowerShell et l’applet de commande `New-Event` . Utilisez le paramètre **SourceIdentifier** pour spécifier l'événement.

Vous pouvez utiliser cette applet de commande pour vous abonner à l’événement et aux événements du moteur de **sortie** générés par l’applet de commande `New-Event` . Ces événements sont automatiquement ajoutés à la file d'attente d'événements de votre session sans abonnement. Toutefois, l'abonnement vous permet de transférer les événements, de spécifier une action pour répondre aux événements et d'annuler l'abonnement.

Quand l'événement auquel vous êtes abonné est déclenché, il est ajouté à la file d'attente d'événements dans votre session. Pour récupérer des événements dans la file d’attente d’événements, utilisez l’applet de commande `Get-Event` .

Lorsque vous vous abonnez à un événement, un abonné aux événements est ajouté à votre session. Pour obtenir les abonnés aux événements dans la session, utilisez l'applet de commande `Get-EventSubscriber`. Pour annuler l'abonnement, utilisez l'applet de commande `Unregister-Event`, ce qui supprime l'abonné aux événements de la session.

## EXEMPLES

### Exemple 1 : inscrire un événement de moteur PowerShell sur des ordinateurs distants

Cet exemple s’inscrit à un événement de moteur PowerShell sur deux ordinateurs distants.

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S { Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward }
```

`New-PSSession` crée une session gérée par l’utilisateur (PSSession) sur chacun des ordinateurs distants. L' `Invoke-Command` applet `Register-EngineEvent` de commande exécute la commande dans les sessions à distance.
`Register-EngineEvent` utilise le paramètre **SourceIdentifier** pour identifier l’événement. Le paramètre **Forward** indique au moteur de transférer les événements de la session à distance vers la session locale.

### Exemple 2 : prendre une mesure spécifiée lorsque l’événement de sortie se produit

Cet exemple montre comment exécuter `Register-EngineEvent` pour effectuer une action spécifique lorsque l’événement **PowerShell. Exiting** se produit.

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

Le paramètre **SupportEvent** est ajouté pour masquer l’abonnement aux événements. À la sortie de PowerShell, dans ce cas, l’historique de commande de la session de sortie est exporté d’un fichier XML dans l’annuaire de l’utilisateur `$Home` .

### Exemple 3 : créer et s’abonner à un événement défini par l’utilisateur

Cet exemple crée un abonnement pour les événements à partir de la source **MyEventSource** . Il s’agit d’une source arbitraire que nous allons utiliser pour surveiller la progression d’un travail. `Register-EngineEvent` est utilisé pour créer l’abonnement. Le bloc de script du paramètre **action** enregistre les données d’événement dans un fichier texte.

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

`Register-EngineEvent` ID de tâche 18 créé. `Start-Job` ID de tâche 19 créé. Dans l’exemple #4, nous supprimons l’abonnement aux événements et les travaux, puis nous inspectons le fichier journal.

### Exemple 4 : annuler l’inscription des événements et nettoyer les travaux

Il s’agit de la suite de l’exemple 3. Dans cet exemple, nous attendons 10 secondes pour permettre à plusieurs événements de se produire. Ensuite, nous annulons l’inscription de l’abonnement aux événements.

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

L' `Unregister-Event` applet de commande arrête le travail associé à l’abonnement aux événements (ID de tâche 18). L’ID de tâche 19 est toujours en cours d’exécution et crée des événements. Nous utilisons les applets de commande **Job** pour arrêter la tâche et supprimer les objets de travail inutiles. `Get-Content` affiche le contenu du fichier journal.

## PARAMETERS

### -Action

Spécifie les commandes qui gèrent les événements. Les commandes dans **Action** s'exécutent quand un événement est déclenché, au lieu d'envoyer l'événement à la file d'attente d'événements. Placez les commandes entre accolades ( { } ) pour créer un bloc de script.

La valeur du paramètre d' **action** peut inclure les `$Event` `$EventSubscriber` variables automatiques,,, `$Sender` `$EventArgs` et `$Args` , qui fournissent des informations sur l’événement au bloc de script de l' **action** . Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

Lorsque vous spécifiez une action, `Register-EngineEvent` retourne un objet de tâche d’événement qui représente cette action. Vous pouvez utiliser les applets de commande Job pour gérer la tâche de l'événement.

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

### -Suivant

Indique que l’applet de commande envoie des événements pour cet abonnement à la session sur l’ordinateur local.
Utilisez ce paramètre lorsque vous vous inscrivez aux événements sur un ordinateur distant ou dans une session à distance.

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

### -MaxTriggerCount

Spécifie le nombre maximal de fois où l’action sera exécutée pour l’abonnement aux événements.

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

Spécifie des données supplémentaires associées à l'événement. La valeur de ce paramètre apparaît dans la propriété **MessageData** de l'objet d'événement.

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

Spécifie l'identificateur source de l'événement auquel vous vous abonnez. L'identificateur source doit être unique dans la session active. Ce paramètre est obligatoire.

La valeur de ce paramètre apparaît dans la valeur de la propriété **SourceIdentifier** de l'objet d'abonné et de tous les objets d'événements associés à cet abonnement.

La valeur est spécifique à la source de l’événement. Il peut s’agir d’une valeur arbitraire que vous avez créée à utiliser avec l’applet de commande `New-Event` . Le moteur PowerShell prend en charge les valeurs **EngineEvent** **PowerShell. Exiting** et **PowerShell. OnIdle** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Indique que l’applet de commande masque l’abonnement aux événements. Ajoutez ce paramètre lorsque l’abonnement actuel fait partie d’un mécanisme d’inscription d’événement plus complexe et qu’il ne doit pas être découvert indépendamment.

Pour afficher ou annuler un abonnement qui a été créé avec le paramètre **SupportEvent** , ajoutez le paramètre **force** aux `Get-EventSubscriber` applets de commande ou `Unregister-Event` .

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

Vous ne pouvez pas diriger d’entrée vers `Register-EngineEvent` .

## SORTIES

### None ou System. Management. Automation. PSEventJob

Si vous utilisez le paramètre **action** , `Register-EngineEvent` retourne un objet **System. Management. Automation. PSEventJob** . Sinon, elle ne génère aucune sortie.

## REMARQUES

Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
