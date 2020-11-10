---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: acfeae4025b3a32d2a04307609597cf30332d708
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389451"
---
# ConvertTo-Json

## SYNOPSIS
Convertit un objet en une chaîne au format JSON.

## SYNTAXE

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## DESCRIPTION

L' `ConvertTo-Json` applet de commande convertit n’importe quel objet .net en une chaîne au format JavaScript Object Notation (JSON). Les propriétés sont converties en noms de champs et les valeurs de champ en valeurs de propriété, tandis que les méthodes sont supprimées.

Vous pouvez ensuite utiliser l' `ConvertFrom-Json` applet de commande pour convertir une chaîne au format JSON en un objet JSON, qui est facilement géré dans PowerShell.

De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

Cette commande utilise la `ConvertTo-Json` cmdlet pour convertir un objet GregorianCalendar en chaîne au format JSON.

### Exemple 2

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

Cet exemple montre la sortie de l’applet de commande `ConvertTo-Json` avec et sans le paramètre de commutateur **AsArray** . Vous pouvez voir que la deuxième partie de la sortie est incluse entre crochets de tableau.

### Exemple 3

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

Cette commande montre l’effet de l’utilisation du paramètre **Compress** de `ConvertTo-Json` . La compression affecte uniquement l'aspect de la chaîne, pas sa validité.

### Exemple 4

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

Cet exemple utilise l' `ConvertTo-Json` applet de commande pour convertir un objet **System. DateTime** de l' `Get-Date` applet de commande en chaîne au format JSON. La commande utilise l' `Select-Object` applet de commande pour récupérer tout ( `*` ) des propriétés de l’objet **DateTime** . La sortie affiche la chaîne JSON `ConvertTo-Json` retournée.

### Exemple 5

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

Cet exemple montre comment utiliser les `ConvertTo-Json` applets de commande et `ConvertFrom-Json` pour convertir un objet en une chaîne JSON et un objet JSON.

## PARAMÈTRES

### -AsArray

Renvoie l’objet entre crochets de tableau, même si l’entrée est un objet unique.

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

### -Compresser

Omet les espaces blancs et la mise en forme en retrait dans la chaîne de sortie.

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

### -Profondeur

Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation JSON. La valeur par défaut est 2.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnumsAsStrings

Fournit une autre option de sérialisation qui convertit toutes les énumérations en leur représentation sous forme de chaîne.

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

### -EscapeHandling

Contrôle la façon dont certains caractères sont placés dans une séquence d’échappement dans la sortie JSON résultante. Par défaut, seuls les caractères de contrôle (tels que les sauts de ligne) sont placés dans une séquence d’échappement.

Les valeurs possibles sont :

- Les caractères de contrôle par défaut uniquement sont placés dans une séquence d’échappement.
- EscapeNonAscii-tous les caractères de contrôle et non-ASCII sont placés dans une séquence d’échappement.
- EscapeHtml-html ( `<` , `>` , `&` , `'` , `"` ) et les caractères de contrôle sont placés dans une séquence d’échappement.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à convertir au format JSON. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets. Vous pouvez également diriger un objet vers `ConvertTo-Json` .

Le paramètre **InputObject** est obligatoire, mais sa valeur peut être null ( `$null` ) ou une chaîne vide.
Lorsque l’objet d’entrée est `$null` , `ConvertTo-Json` ne génère pas de sortie. Lorsque l’objet d’entrée est une chaîne vide, `ConvertTo-Json` retourne une chaîne vide.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.Object

Vous pouvez diriger n’importe quel objet vers `ConvertTo-Json` .

## SORTIES

### System.String

## REMARQUES

L' `ConvertTo-Json` applet de commande est implémentée à l’aide de [Newtonsoft JSON.net](https://www.newtonsoft.com/json).

## LIENS CONNEXES

[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-Json](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)

[NewtonSoft.Js. StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
