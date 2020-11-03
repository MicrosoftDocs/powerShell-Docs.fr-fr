---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: cae34c4cf942d9aa4abb9a2d716ef9854f70de2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203434"
---
# Write-EventLog

## SYNOPSIS
Écrit un événement dans un journal des événements.

## SYNTAX

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## Description
L’applet de commande **Write-EventLog** écrit un événement dans un journal des événements.

Pour écrire un événement dans un journal des événements, le journal des événements doit exister sur l'ordinateur et la source du journal des événements doit être inscrite.

Les applets de commande qui contiennent le nom **EventLog** (les applets de commande **EventLog** ) fonctionnent uniquement sur les journaux des événements classiques.
Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures du système d’exploitation Windows, utilisez l’applet de commande Get-WinEvent.

## EXEMPLES

### Exemple 1 : écrire un événement dans le journal des événements de l’application

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

Cette commande écrit un événement à partir de la source MyApp dans le journal des événements Application.

### Exemple 2 : écrire un événement dans le journal des événements d’application d’un ordinateur distant

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

Cette commande écrit un événement à partir de la source MyApp dans le journal des événements Application sur l'ordinateur distant Server01.

## PARAMETERS

### -Catégorie
Spécifie une catégorie de tâche pour l'événement.
Entrez un entier qui est associé aux chaînes figurant dans le fichier de messages des catégories pour le journal des événements.

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
Spécifie un ordinateur distant.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* de l’applet de commande Get-EventLog même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EntryType
Spécifie le type d'entrée de l'événement.
Les valeurs acceptables pour ce paramètre sont les suivantes : Error, Warning, information, SuccessAudit et FailureAudit.
La valeur par défaut est Information.

Pour obtenir une description des valeurs, consultez [EventLogEntryType, énumération](https://go.microsoft.com/fwlink/?LinkId=143599) dans MSDN Library.

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventId
Spécifie l'identificateur de l'événement.
Ce paramètre est obligatoire.
La valeur maximale du paramètre *eventID* est 65535.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Spécifie le nom du journal dans lequel l'événement est écrit.
Entrez le nom du journal.
Le nom du journal est la valeur de la propriété **log** , et non **et non LogDisplayName** .
Les caractères génériques ne sont pas autorisés.
Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message
Spécifie le message de l'événement.
Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RawData
Spécifie les données binaires qui sont associées à l'événement (en octets).

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
Spécifie la source d'événement, qui correspond en général au nom de l'application qui écrit l'événement dans le journal.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
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

### System. Diagnostics. EventLogEntry
Cette applet de commande retourne des objets qui représentent les événements dans les journaux.

## REMARQUES

* Pour utiliser **Write-EventLog** , démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.

*

## LIENS CONNEXES

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
