---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: b0fd03a62be21736a5d30e8ed4760dba300258ce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202377"
---
# Start-Trace

## SYNOPSIS
Démarrez une session de journalisation de suivi des événements.

## SYNTAX

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## Description
Cette applet de commande démarre une session de journalisation de suivi d’événements Windows.

Cette applet de commande est utilisée par les applets de commande suivantes :

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.

## EXEMPLES

### Exemple 1 : démarrer une session de journalisation de suivi WSMan

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## PARAMETERS

### -BufferSizeInKB
Taille de la mémoire tampon de la session de suivi d’événements en kilo-octets (Ko).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -ETS
Envoyer des commandes aux sessions de suivi d’événements directement sans enregistrement ou planification.

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

### -Format
Spécifie le format du journal pour le collecteur de données. Pour le format de base de données SQL, vous devez utiliser l’option **OutputFilePath** dans la ligne de commande avec la `dsn!log` valeur. La valeur par défaut est Binary (bin). Les valeurs possibles sont les suivantes :

- bin-binaire
- bincirc-binaire avec journalisation circulaire
- CSV-valeurs séparées par des virgules
- valeurs séparées par des tabulations TSV
- SQL-SQL Database

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxBuffers
Définit le nombre maximal de mémoires tampons de session de suivi d’événements.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxLogFileSizeInMB
Définit la taille maximale du fichier journal en mégaoctets (Mo) ou le nombre d’enregistrements pour les journaux SQL.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinBuffers
Définit le nombre minimal de mémoires tampons de session de suivi d’événements.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputFilePath
Chemin d’accès du fichier journal de sortie ou nom de l’ensemble de journaux et du journal dans une base de données SQL. Le chemin d’accès par défaut est : `$env:systemdrive\PerfLogs\Admin`.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderFilePath
Fichier répertoriant plusieurs fournisseurs de suivi d’événements à activer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nom_session
Nom de la session de suivi d’événements. Pour arrêter une session de trace, vous devez connaître le nom de la session.

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

## SORTIES

### Aucun

## REMARQUES

## LIENS CONNEXES

[Suivi d’événements](/windows/desktop/ETW/event-tracing-portal)

[Stop-Trace](stop-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)
