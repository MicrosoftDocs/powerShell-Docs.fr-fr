---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203618"
---
# Limit-EventLog

## SYNOPSIS
Définit les propriétés de journal des événements qui limitent la taille du journal des événements et l'ancienneté de ses entrées.

## SYNTAX

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Limit-EventLog** définit la taille maximale d’un journal des événements classique, la durée pendant laquelle chaque événement doit être conservé et ce qui se produit lorsque le journal atteint sa taille maximale.
Vous pouvez l'utiliser pour limiter les journaux des événements sur les ordinateurs locaux ou distants.

Les applets de commande contenant le nom EventLog (les applets de commande EventLog) fonctionnent uniquement sur les journaux des événements classiques.
Pour obtenir des événements à partir des journaux qui utilisent la technologie Journal des événements Windows sous Windows Vista et les versions ultérieures de Windows, utilisez Get-WinEvent.

## EXEMPLES

### Exemple 1 : augmenter la taille d’un journal des événements

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

Cette commande augmente la taille maximale du journal des événements Windows PowerShell sur l'ordinateur local jusqu'à 20 480 octets (20 Ko).

### Exemple 2 : conserver un journal des événements pour une durée spécifiée

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

Grâce à cette commande, les événements qui figurent dans le journal de sécurité des ordinateurs Server01 et Server02 sont assurés d'être conservés pendant au moins 7 jours.

### Exemple 3 : modifier l’action de dépassement de capacité de tous les journaux des événements

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

Cet exemple modifie l’action de dépassement de capacité de tous les journaux des événements sur l’ordinateur local en OverwriteOlder.

La première commande obtient le nom de tous les journaux présents sur l'ordinateur local.
La deuxième commande définit l'action de dépassement de capacité.
La troisième commande affiche les résultats.

## PARAMETERS

### -ComputerName
Spécifie les ordinateurs distants.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN) d’un ordinateur distant.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.
Vous pouvez utiliser le paramètre *ComputerName* de **Limit-EventLog** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Spécifie les journaux des événements.
Entrez le nom du journal (la valeur de la propriété log et non le et non LogDisplayName) d’un ou plusieurs journaux des événements, séparés par des virgules.
Les caractères génériques ne sont pas autorisés.
Ce paramètre est obligatoire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumSize
Spécifie la taille maximale des journaux des événements (en octets).
Entrez une valeur comprise entre 64 kilo-octets (Ko) et 4 gigaoctets (Go).
La valeur doit être divisible par 64 Ko (65 536).

Ce paramètre spécifie la valeur de la propriété **MaximumKilobytes** de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OverflowAction
Spécifie l'action prévue lorsque le journal des événements atteint sa taille maximale.

Les valeurs valides pour ce paramètre sont :

- DoNotOverwrite : les entrées existantes sont conservées et les nouvelles entrées sont ignorées.
- OverwriteAsNeeded : chaque nouvelle entrée remplace l’entrée la plus ancienne.
- OverwriteOlder : les nouveaux événements remplacent les événements antérieurs à la valeur spécifiée par la propriété **MinimumRetentionDays** . S’il n’y a pas d’événements antérieurs à spécifié par la valeur de la propriété **MinimumRetentionDays** , les nouveaux événements sont ignorés.

Ce paramètre spécifie la valeur de la propriété **OverflowAction** de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RetentionDays
Spécifie le nombre minimal de jours pendant lesquels un événement doit rester dans le journal des événements.

Ce paramètre spécifie la valeur de la propriété **MinimumRetentionDays** de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

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

### -WhatIf
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour utiliser cette applet de commande sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.

  Cette applet de commande modifie les propriétés de l’objet **System. Diagnostics. EventLog** qui représente un journal des événements classique.
Pour afficher les paramètres actuels des propriétés du journal des événements, tapez `Get-EventLog -List` .

*

## LIENS CONNEXES

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
