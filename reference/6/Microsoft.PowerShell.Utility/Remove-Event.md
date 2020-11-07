---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: fb5c6761427ea3c79075a18e551bfa7b39f72dc3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343417"
---
# Remove-Event

## SYNOPSIS
Supprime les événements de la file d'attente des événements.

## SYNTAXE

### BySource (par défaut)

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByIdentifier

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Remove-Event` applet de commande supprime les événements de la file d’attente d’événements dans la session active.

Cette applet de commande ne supprime que les événements actuellement dans la file d'attente. Pour annuler les inscriptions d’événements ou vous désabonner, utilisez l’applet de commande `Unregister-Event` .

## EXEMPLES

### Exemple 1 : supprimer un événement par identificateur de source

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

Cette commande supprime les événements avec un identificateur de source de processus démarré à partir de la file d’attente d’événements.

### Exemple 2 : supprimer un événement par identificateur d’événement

```
PS C:\> Remove-Event -EventIdentifier 30
```

Cette commande supprime l'événement avec un ID d'événement égal à 30 de la file d'attente des événements.

### Exemple 3 : supprimer tous les événements

```
PS C:\> Get-Event | Remove-Event
```

Cette commande supprime tous les événements de la file d'attente des événements.

## PARAMÈTRES

### -EventIdentifier

Spécifie l’identificateur d’événement pour lequel l’applet de commande est supprimée. Un paramètre **EventIdentifier** ou **SourceIdentifier** est requis dans chaque commande.

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie l’identificateur source pour lequel cette applet de commande supprime les événements. Les caractères génériques ne sont pas autorisés. Un paramètre **EventIdentifier** ou **SourceIdentifier** est requis dans chaque commande.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
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

### System. Management. Automation. PSEventArgs

Vous pouvez diriger les événements de `Get-Event` vers `Remove-Event` .

## SORTIES

### Aucun

L'applet de commande ne génère pas de résultat.

## REMARQUES

Aucune source d’événements disponible sur les plateformes Linux ou macOS.

Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

## LIENS CONNEXES

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
