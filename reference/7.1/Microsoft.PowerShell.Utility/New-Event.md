---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 0e7f263d309908a4a62187d3d1cc5ef08283e0c3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344403"
---
# New-Event

## SYNOPSIS
Crée un événement.

## SYNTAXE

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

L' `New-Event` applet de commande crée un nouvel événement personnalisé.

Vous pouvez utiliser des événements personnalisés pour informer les utilisateurs des changements d'état dans votre programme et de toute modification que votre programme peut détecter, y compris des conditions liées au matériel ou au système, de l'état de l'application, de l'état du disque, de l'état du réseau ou de l'achèvement d'une tâche en arrière-plan.

Les événements personnalisés sont automatiquement ajoutés à la file d'attente des événements dans votre session chaque fois qu'ils sont déclenchés. Vous n'avez pas besoin de vous y abonner. Toutefois, si vous souhaitez transférer un événement à la session locale ou spécifier une action pour répondre à l’événement, utilisez l' `Register-EngineEvent` applet de commande pour vous abonner à l’événement personnalisé.

Quand vous vous abonnez à un événement personnalisé, l'abonné aux événements est ajouté à votre session. Si vous annulez l’abonnement à un événement à l’aide de l’applet de commande `Unregister-Event` , l’abonné aux événements et l’événement personnalisé sont supprimés de la session. Si vous ne vous abonnez pas à l’événement personnalisé, vous devez modifier les conditions du programme ou fermer la session PowerShell pour supprimer l’événement.

## EXEMPLES

### Exemple 1 : créer un événement dans la file d’attente des événements

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

Cette commande crée un nouvel événement dans la file d’attente des événements PowerShell. Elle utilise un objet **Windows. Timer** pour envoyer l’événement.

### Exemple 2 : déclencher un événement en réponse à un autre événement

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

Cet exemple de fonction utilise l' `New-Event` applet de commande pour déclencher un événement en réponse à un autre événement. La commande utilise l' `Register-ObjectEvent` applet de commande pour s’abonner à l’événement Windows Management Instrumentation (WMI) qui est déclenché lors de la création d’un nouveau processus. La commande utilise le paramètre **action** de l’applet de commande pour appeler l’applet de commande `New-Event` , qui crée le nouvel événement.

Étant donné que les événements `New-Event` déclenchés sont automatiquement ajoutés à la file d’attente des événements PowerShell, vous n’avez pas besoin de vous inscrire à cet événement.

## PARAMÈTRES

### -Arguments

Spécifie un objet qui contient des options relatives à l'événement.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
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
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expéditeur

Spécifie l'objet qui déclenche l'événement. La valeur par défaut est le moteur PowerShell.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie un nom pour le nouvel événement. Ce paramètre est obligatoire et il doit être unique dans la session.

La valeur de ce paramètre apparaît dans la propriété **SourceIdentifier** des événements.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSEventArgs

## REMARQUES

Aucune source d’événements disponible sur les plateformes Linux ou macOS.

Le nouvel événement personnalisé, l'abonnement aux événements et la file d'attente d'événements existent uniquement dans la session active.
Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
