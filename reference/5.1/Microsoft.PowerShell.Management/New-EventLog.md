---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203597"
---
# New-EventLog

## SYNOPSIS
Crée un journal des événements et une source d'événement sur un ordinateur local ou distant.

## SYNTAX

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## Description

Cette applet de commande crée un journal des événements classique sur un ordinateur local ou distant. Elle peut également inscrire une source d’événement qui écrit dans le nouveau journal ou dans un journal existant.

Les applets de commande contenant le nom EventLog (les applets de commande du journal des événements) fonctionnent uniquement sur les journaux des événements classiques.
Pour récupérer des événements à partir des journaux qui utilisent la technologie du journal des événements Windows dans Windows Vista et les versions ultérieures de Windows, utilisez `Get-WinEvent` .

## EXEMPLES

### Exemple 1 : créer un journal des événements

Cette commande crée le journal des événements TestLog sur l’ordinateur local et inscrit une nouvelle source pour lui.

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### Exemple 2 : ajouter une nouvelle source d’événement à un journal existant

Cette commande ajoute une nouvelle source d’événement (NewTestApp) au journal des applications sur l’ordinateur distant Server01.

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

La commande requiert la présence du fichier NewTestApp.dll sur l’ordinateur Server01.

## PARAMETERS

### -CategoryResourceFile

Spécifie le chemin d’accès au fichier qui contient les chaînes de catégorie des événements sources. Ce fichier est également appelé fichier de messages des catégories.

Le fichier doit être présent sur l’ordinateur sur lequel le journal des événements est créé. Ce paramètre ne crée pas ou ne déplace pas de fichiers.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Crée les journaux des événements sur les ordinateurs spécifiés. La valeur par défaut est l'ordinateur local.

Le nom NetBIOS, l’adresse IP ou le nom de domaine complet d’un ordinateur distant.
Pour spécifier l'ordinateur local, tapez le nom de l'ordinateur, un point (.) ou « localhost ».

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** de `Get-EventLog` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Spécifie le nom du journal des événements.

Si le journal n’existe pas, `New-EventLog` crée le journal et utilise cette valeur pour les propriétés **log** et **et non LogDisplayName** du nouveau journal des événements. Si le journal existe, `New-EventLog` enregistre une nouvelle source pour le journal des événements.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageResourceFile

Spécifie le chemin d’accès au fichier qui contient les chaînes de mise en forme de message des événements sources.
Ce fichier est également appelé fichier de messages des événements.

Le fichier doit être présent sur l’ordinateur sur lequel le journal des événements est créé.
Ce paramètre ne crée pas ou ne déplace pas de fichiers.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterResourceFile

Spécifie le chemin d’accès au fichier qui contient les chaînes utilisées pour les substitutions de paramètre dans les descriptions d’événement. Ce fichier est également appelé fichier de messages des paramètres.

Le fichier doit être présent sur l’ordinateur sur lequel le journal des événements est créé.
Ce paramètre ne crée pas ou ne déplace pas de fichiers.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Spécifie le nom des sources de journal des événements (programmes d’application qui écrivent dans le journal des événements, par exemple). Ce paramètre est obligatoire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
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

## REMARQUES

Pour utiliser `New-EventLog` sur Windows Vista et les versions ultérieures de Windows, ouvrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».

Pour créer une source d’événement sous Windows Vista, Windows XP Professionnel ou Windows Server 2003, vous devez être membre du groupe Administrateurs sur l’ordinateur.

Lorsque vous créez un journal des événements et une source d’événement, le système inscrit la nouvelle source du nouveau journal, mais le journal n’est pas créé tant qu’une première entrée n’y est pas écrite.

Le système d’exploitation stocke les journaux des événements sous forme de fichiers.

Lorsque vous créez un journal des événements, le fichier associé est stocké dans le `$env:SystemRoot\System32\Config` répertoire sur l’ordinateur spécifié.

Le nom de fichier est les huit premiers caractères de la propriété **log** avec l’extension de nom de fichier. evt.

## LIENS CONNEXES

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
