---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: fd617cd145c4f36ceede9898de93cbad33cb4bf3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201310"
---
# Wait-Event

## SYNOPSIS
Attend qu'un événement particulier soit déclenché avant de poursuivre son exécution.

## SYNTAX

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## Description

L' `Wait-Event` applet de commande suspend l’exécution d’un script ou d’une fonction jusqu’à ce qu’un événement particulier soit déclenché. L'exécution reprend quand l'événement est détecté. Pour annuler l’attente, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>.

Cette fonctionnalité fournit une alternative à l'interrogation d'un événement. Elle vous permet également de déterminer la réponse à un événement de deux façons différentes :

- utilisation du paramètre **action** de l’abonnement aux événements
- attente du retour d’un événement, puis réponse avec une action

## EXEMPLES

### Exemple 1 : attendre l’événement suivant

Cet exemple attend la levée de l’événement suivant.

```powershell
Wait-Event
```

### Exemple 2 : attendre un événement avec un identificateur source spécifié

Cet exemple attend l’événement suivant qui est déclenché et qui a un identificateur source de ProcessStarted.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### Exemple 3 : attendre un événement de minuteur écoulé

Cet exemple utilise l' `Wait-Event` applet de commande pour attendre un événement de minuterie sur un minuteur défini pour 2000 millisecondes.

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### Exemple 4 : attendre un événement après un délai d’attente spécifié

Cet exemple attend jusqu’à 90 secondes pour l’événement suivant qui est déclenché et qui a un identificateur source de **ProcessStarted** . Si le délai spécifié expire, l'attente se termine.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## PARAMETERS

### -SourceIdentifier

Spécifie l’identificateur source que cette applet de commande attend pour les événements.
Par défaut, `Wait-Event` attend un événement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

Spécifie la durée maximale, en secondes, pendant laquelle `Wait-Event` attend que l’événement se produise. La valeur par défaut, -1, stipule d'attendre indéfiniment. Le minutage démarre lorsque vous envoyez la `Wait-Event` commande.

Si la durée spécifiée est dépassée, l'attente se termine et l'invite de commandes réapparaît, même si l'événement n'a pas été déclenché. Aucun message d'erreur ne s'affiche.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

## SORTIES

### System. Management. Automation. PSEventArgs

## REMARQUES

Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
