---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 3cc2983def049e705a67bad05ee39bdbd71d3888
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344420"
---
# Unregister-Event

## SYNOPSIS
Annule un abonnement aux événements.

## SYNTAXE

### BySource (par défaut)

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Méthode BYID

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Unregister-Event` applet de commande annule un abonnement aux événements qui a été créé à l’aide de l’applet de commande `Register-EngineEvent` , `Register-ObjectEvent` ou `Register-WmiEvent` .

Quand un abonnement aux événements est annulé, l'abonné aux événements est supprimé de la session et les événements ayant fait l'objet d'un abonnement ne sont plus ajoutés à la file d'attente d'événements. Lorsque vous annulez un abonnement à un événement créé à l’aide de l’applet de commande `New-Event` , le nouvel événement est également supprimé de la session.

`Unregister-Event` ne supprime pas les événements de la file d’attente d’événements. Pour supprimer des événements, utilisez l’applet de commande `Remove-Event` .

## EXEMPLES

### Exemple 1 : annuler un abonnement à un événement par identificateur de source

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

Cette commande annule l’abonnement aux événements qui a un identificateur source de ProcessStarted.

Pour Rechercher l’identificateur source d’un événement, utilisez l’applet de commande `Get-Event` . Pour Rechercher l’identificateur source d’un abonnement aux événements, utilisez l' `Get-EventSubscriber` applet de commande.

### Exemple 2 : annuler un abonnement aux événements par identificateur d’abonnement

```
PS C:\> Unregister-Event -SubscriptionId 2
```

Cette commande annule l'abonnement aux événements qui a l'identificateur d'abonnement 2.

Pour Rechercher l’identificateur d’abonnement d’un abonnement aux événements, utilisez l’applet de commande `Get-EventSubscriber` .

### Exemple 3 : annuler tous les abonnements aux événements

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

Cette commande annule tous les abonnements aux événements dans la session.

La commande utilise l' `Get-EventSubscriber` applet de commande pour récupérer tous les objets d’abonné aux événements dans la session, y compris les abonnés qui sont masqués à l’aide du paramètre **SupportEvent** des applets de commande d’inscription d’événement.

Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les objets de l’abonné à `Unregister-Event` , qui les supprime de la session. Pour effectuer la tâche, le paramètre **force** est également requis sur `Unregister-Event` .

## PARAMÈTRES

### -Force

Annule tous les abonnements aux événements, y compris les abonnements qui ont été masqués à l’aide du paramètre **SupportEvent** de `Register-ObjectEvent` , `Register-WmiEvent` et `Register-EngineEvent` .

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

### -SourceIdentifier

Spécifie un identificateur de source que cette applet de commande annule les abonnements aux événements.

Un paramètre **SourceIdentifier** ou **SubscriptionId** doit être inclus dans chaque commande.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId

Spécifie un ID d’identificateur de source que cette applet de commande annule les abonnements aux événements.

Un paramètre **SourceIdentifier** ou **SubscriptionId** doit être inclus dans chaque commande.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Management. Automation. PSEventSubscriber

Vous pouvez diriger la sortie de `Get-EventSubscriber` vers `Unregister-Event` .

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES


Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

`Unregister-Event` Impossible de supprimer les événements créés à l’aide de l’applet de commande `New-Event` , sauf si vous êtes abonné à l’événement à l’aide de l’applet de commande `Register-EngineEvent` . Pour supprimer un événement personnalisé de la session, vous devez le supprimer par programmation ou fermer la session.

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
