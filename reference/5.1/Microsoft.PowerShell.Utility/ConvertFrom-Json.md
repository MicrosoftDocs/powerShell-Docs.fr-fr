---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: f2159a2de3432aec14fb395b93ed476f349616a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203358"
---
# ConvertFrom-Json

## SYNOPSIS
Convertit une chaîne au format JSON en objet personnalisé.

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## Description

L' `ConvertFrom-Json` applet de commande convertit une chaîne au format JSON (JavaScript Object Notation) en un objet **PSCustomObject** personnalisé qui a une propriété pour chaque champ de la chaîne JSON. JSON est couramment utilisé par les sites web pour fournir une représentation textuelle des objets. La norme JSON n’interdit pas l’utilisation interdite avec un **PSCustomObject** . Par exemple, si la chaîne JSON contient des clés dupliquées, seule la dernière clé est utilisée par cette applet de commande. Consultez les autres exemples ci-dessous.

Pour générer une chaîne JSON à partir de n’importe quel objet, utilisez l’applet de commande `ConvertTo-Json` .

Cette applet de commande a été introduite dans PowerShell 3,0.

> [!NOTE]
> Cette applet de commande ne prend pas en charge JSON avec des commentaires.

## EXEMPLES

### Exemple 1 : convertir un objet DateTime en objet JSON

Cette commande utilise les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet **DateTime** de l' `Get-Date` applet de commande en un objet JSON, puis en **PSCustomObject** .

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

L’exemple utilise l' `Select-Object` applet de commande pour récupérer toutes les propriétés de l’objet **DateTime** . Elle utilise l' `ConvertTo-Json` applet de commande pour convertir l’objet **DateTime** en une chaîne formatée en tant qu’objet JSON et l' `ConvertFrom-Json` applet de commande pour convertir la chaîne au format JSON en objet **PSCustomObject** .

### Exemple 2 : obtenir des chaînes JSON à partir d’un service Web et les convertir en objets PowerShell

Cette commande utilise l' `Invoke-WebRequest` applet de commande pour obtenir des chaînes JSON à partir d’un service Web, puis elle utilise l' `ConvertFrom-Json` applet de commande pour convertir le contenu JSON en objets pouvant être gérés dans PowerShell.

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

Vous pouvez également utiliser l' `Invoke-RestMethod` applet de commande, qui convertit automatiquement le contenu JSON en objets.

### Exemple 3 : convertir une chaîne JSON en un objet personnalisé

Cet exemple montre comment utiliser l' `ConvertFrom-Json` applet de commande pour convertir un fichier JSON en un objet personnalisé PowerShell.

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

La commande utilise Get-Content applet de commande pour obtenir les chaînes dans un fichier JSON. Elle utilise ensuite l’opérateur de pipeline pour envoyer la chaîne délimitée à l’applet de commande `ConvertFrom-Json` , qui la convertit en objet personnalisé.

## PARAMETERS

### -InputObject

Spécifie les chaînes JSON à convertir en objets JSON. Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne. Vous pouvez également diriger une chaîne vers `ConvertFrom-Json` .

Le paramètre **InputObject** est obligatoire, mais sa valeur peut être une chaîne vide. Lorsque l’objet d’entrée est une chaîne vide, `ConvertFrom-Json` ne génère pas de sortie. La valeur **InputObject** ne peut pas être `$null` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne JSON vers `ConvertFrom-Json` .

## SORTIES

### PSCustomObject

## REMARQUES

L' `ConvertFrom-Json` applet de commande est implémentée à l’aide de la [classe JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).

## LIENS CONNEXES

[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)