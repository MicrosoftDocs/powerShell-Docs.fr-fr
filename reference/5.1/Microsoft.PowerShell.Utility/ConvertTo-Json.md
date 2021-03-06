---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 9831249a9f1ffcc65fc275e44da04fde9348ae71
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388057"
---
# ConvertTo-Json

## SYNOPSIS
Convertit un objet en une chaîne au format JSON.

## SYNTAXE

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
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
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

Cette commande utilise la `ConvertTo-Json` cmdlet pour convertir un objet GregorianCalendar en chaîne au format JSON.

### Exemple 2

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

Cette commande montre l’effet de l’utilisation du paramètre **Compress** de `ConvertTo-Json` . La compression affecte uniquement l'aspect de la chaîne, pas sa validité.

### Exemple 3

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

Cet exemple utilise l' `ConvertTo-Json` applet de commande pour convertir un objet **System. DateTime** de l' `Get-Date` applet de commande en chaîne au format JSON. La commande utilise l' `Select-Object` applet de commande pour récupérer tout ( `*` ) des propriétés de l’objet **DateTime** . La sortie affiche la chaîne JSON `ConvertTo-Json` retournée.

### Exemple 4

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

L' `ConvertTo-Json` applet de commande est implémentée à l’aide de la [classe JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).

## LIENS CONNEXES

[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-Json](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
