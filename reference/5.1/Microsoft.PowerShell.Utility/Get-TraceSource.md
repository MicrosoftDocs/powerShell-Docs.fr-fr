---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 7d57e7cff0dc3ca0eff36dbe38e240efdd324060
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203253"
---
# Get-TraceSource

## SYNOPSIS
Obtient les composants PowerShell instrumentés pour le suivi.

## SYNTAX

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-TraceSource** obtient les sources de suivi pour les composants PowerShell en cours d’utilisation.
Vous pouvez utiliser les données pour déterminer les composants PowerShell que vous pouvez tracer.
Pendant le suivi, le composant génère des messages détaillés sur chaque étape du traitement interne.
Les développeurs utilisent les données de suivi pour surveiller les flux de données, l'exécution des programmes et les erreurs.

Les applets de commande de suivi ont été conçues pour les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.

## EXEMPLES

### Exemple 1 : récupérer les sources de suivi par nom

```
PS C:\> Get-TraceSource -Name "*provider*"
```

Cette commande obtient toutes les sources de suivi dont le nom inclut le fournisseur.

### Exemple 2 : récupération de toutes les sources de suivi

```
PS C:\> Get-TraceSource
```

Cette commande obtient tous les composants PowerShell qui peuvent être suivis.

## PARAMETERS

### -Name

Spécifie les sources de suivi à récupérer.
Les caractères génériques sont autorisés.
Le *nom du paramètre est facultatif* .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient le nom d’une source de suivi vers **obtenir-TraceSource** .

## SORTIES

### System. Management. Automation. PSTraceSource

La méthode **obten-TraceSource retourne des** objets qui représentent les sources de suivi.

## REMARQUES

## LIENS CONNEXES

[Set-TraceSource](Set-TraceSource.md)

[Trace-Command](Trace-Command.md)
