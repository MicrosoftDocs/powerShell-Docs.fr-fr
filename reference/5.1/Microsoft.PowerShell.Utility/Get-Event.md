---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: e8f61d0c897c5ece7071ff982eb141079c8c88b9
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344692"
---
# Get-Event

## SYNOPSIS
Obtient les événements présents dans la file d'attente des événements.

## SYNTAXE

### BySource (par défaut)

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### Méthode BYID

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## DESCRIPTION

L' `Get-Event` applet de commande obtient les événements de la file d’attente des événements PowerShell pour la session active. Vous pouvez récupérer tous les événements ou utiliser le paramètre **EventIdentifier** ou **SourceIdentifier** pour spécifier les événements.

Quand un événement se produit, il est ajouté à la file d'attente des événements. La file d’attente d’événements comprend les événements que vous avez enregistrés, les événements créés à l’aide de l’applet de commande `New-Event` et l’événement qui est déclenché lorsque PowerShell se ferme. Vous pouvez utiliser `Get-Event` ou `Wait-Event` pour récupérer les événements.

Cette applet de commande n'obtient pas les événements des journaux de l'Observateur d'événements. Pour accéder à ces événements, utilisez `Get-WinEvent` ou `Get-EventLog` .

## EXEMPLES

### Exemple 1 : récupération de tous les événements

```
PS C:\> Get-Event
```

Cette commande obtient tous les événements de la file d'attente des événements.

### Exemple 2 : récupérer des événements par identificateur de source

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

Cette commande obtient les événements dans lesquels la valeur de la propriété SourceIdentifier est PowerShell. ProcessCreated.

### Exemple 3 : récupération d’un événement en fonction de l’heure à laquelle il a été généré

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

Cet exemple montre comment obtenir des événements à l'aide d'autres propriétés que SourceIdentifier.

La première commande récupère tous les événements dans la file d’attente d’événements et les enregistre dans la `$Events` variable.

La deuxième commande utilise la notation de tableau pour récupérer le premier événement (index 0) dans le tableau de la `$Events` variable. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer l’événement à la `Format-List` commande, qui affiche toutes les propriétés de l’événement dans une liste. Cela vous permet d'examiner les propriétés de l'objet d'événement.

La troisième commande montre comment utiliser l' `Where-Object` applet de commande pour récupérer un événement en fonction de l’heure à laquelle il a été généré.

### Exemple 4 : récupération d’un événement à l’aide de son identificateur

```
PS C:\> Get-Event -EventIdentifier 2
```

Cette commande obtient l'événement ayant l'identificateur d'événement 2.

## PARAMÈTRES

### -EventIdentifier

Spécifie les identificateurs d’événements pour lesquels cette applet de commande obtient des événements.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie les identificateurs sources pour lesquels cette applet de commande obtient des événements. La valeur par défaut correspond à l'ensemble des événements de la file d'attente des événements. Les caractères génériques ne sont pas autorisés.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSEventArgs

`Get-Event` retourne un objet **PSEventArgs** pour chaque événement. Pour afficher une description de cet objet, tapez `Get-Help Get-Event -Full` et consultez la section Remarques de la rubrique d’aide.

## REMARQUES

Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

L' `Get-Event` applet de commande retourne un objet **PSEventArgs** ( **System. Management. Automation. PSEventArgs** ) avec les propriétés suivantes :

- Nomd’ordinateur. nom de l'ordinateur sur lequel l'événement s'est produit. La valeur de cette propriété est renseignée uniquement quand l'événement est transféré à partir d'un ordinateur distant.

- RunspaceId. GUID qui identifie de façon unique la session dans laquelle l'événement s'est produit. La valeur de cette propriété est renseignée uniquement quand l'événement est transféré à partir d'un ordinateur distant.

- EventIdentifier. entier (Int32) qui identifie de façon unique la notification d'événements dans la session active.

- Expéditeur. objet qui a généré l'événement. Dans la valeur du paramètre **action** , la `$Sender` variable automatique contient l’objet sender.

- SourceEventArgs. premier paramètre qui dérive d'EventArgs, s'il existe. Par exemple, dans un événement de minuteur écoulé dans lequel la signature a le formulaire sender Object sender, **Timers. ElapsedEventArgs** e, la propriété **SourceEventArgs** contient **Timers. ElapsedEventArgs**. Dans la valeur du paramètre **action** , la `$EventArgs` variable automatique contient cette valeur.

- SourceArgs. tous les paramètres de la signature d'événement d'origine. Pour une signature d’événement standard, `$Args[0]` représente l’expéditeur et `$Args[1]` représente le **SourceEventArgs**. Dans la valeur du paramètre **action** , la `$Args` variable automatique contient cette valeur.

- SourceIdentifier. chaîne qui identifie l'abonnement à l'événement. Dans la valeur du paramètre **action** , la propriété **SourceIdentifier** de la `$Event` variable Automatic contient cette valeur.

- TimeGenerated. Objet **DateTime** qui représente l’heure à laquelle l’événement a été généré.
  Dans la valeur du paramètre **action** , la propriété **TimeGenerated** de la `$Event` variable Automatic contient cette valeur.

- MessageData. données associées à l'abonnement à l'événement. Les utilisateurs spécifient ces données quand ils s'inscrivent à un événement. Dans la valeur du paramètre **action** , la propriété **MessageData** de la `$Event` variable Automatic contient cette valeur.

## LIENS CONNEXES

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
