---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685906"
---
# Clear-EventLog

## SYNOPSIS
Efface toutes les entrées des journaux des événements spécifiés sur les ordinateurs locaux ou distants.

## SYNTAX

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Clear-EventLog` applet de commande supprime toutes les entrées des journaux des événements spécifiés sur l’ordinateur local ou sur des ordinateurs distants. Pour utiliser `Clear-EventLog` , vous devez être membre du groupe Administrateurs sur l’ordinateur concerné.

Les applets de commande qui contiennent le nom **EventLog** (les applets de commande EventLog) fonctionnent uniquement sur les journaux des événements classiques. Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures de Windows, utilisez l’applet de commande Get-WinEvent.

## EXEMPLES

### Exemple 1 : effacer des types de journaux des événements spécifiques de l’ordinateur local

```powershell
Clear-EventLog "Windows PowerShell"
```

Cette commande efface les entrées du journal des événements Windows PowerShell sur l’ordinateur local.

### Exemple 2 : Effacer plusieurs types de journaux spécifiques des ordinateurs locaux et distants

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

Cette commande efface toutes les entrées dans les journaux Microsoft Office Diagnostics (ODiag) et Microsoft Office sessions (OSession) sur l’ordinateur local et l’ordinateur distant SERVER02.

### Exemple 3 : effacer tous les journaux sur les ordinateurs spécifiés, puis afficher la liste des journaux des événements

```powershell
Clear-EventLog -LogName application, system -confirm
```

Cette commande vous invite à confirmer la suppression des entrées dans les journaux des événements spécifiés.

### Exemple 4 : effacer tous les journaux sur les ordinateurs spécifiés, puis afficher la liste des journaux des événements

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

Cette fonction efface tous les journaux des événements sur les ordinateurs spécifiés, puis affiche la liste des journaux des événements résultante.

Notez que quelques entrées ont été ajoutées au journal système et au journal de sécurité après l’effacement des journaux mais avant leur affichage.

## PARAMETERS

### -ComputerName

Spécifie un ordinateur distant. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou le nom de domaine complet d'un ordinateur distant. Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, un point (.) ou « localhost ».

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell. Vous pouvez utiliser le paramètre **ComputerName** de `Get-EventLog` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LogName

Spécifie les journaux des événements. Entrez le nom du journal (la valeur de la propriété **log** n’est pas **et non LogDisplayName**) d’un ou plusieurs journaux des événements, séparés par des virgules. Les caractères génériques ne sont pas autorisés. Ce paramètre est obligatoire.

> [!IMPORTANT]
> Ce paramètre est supposé accepter les valeurs du pipeline par nom de propriété. Toutefois, il existe un bogue qui empêche cela de fonctionner. Vous devez passer une valeur directement à l’aide du paramètre.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’objets vers `Clear-EventLog` .

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- Pour utiliser `Clear-EventLog` sur Windows Vista et les versions ultérieures de Windows, démarrez Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».

## LIENS CONNEXES

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
