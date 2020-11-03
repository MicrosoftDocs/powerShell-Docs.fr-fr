---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: a222044b9dc62a7b0834f7350fd32bed2e95d9a9
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208625"
---
# ConvertFrom-Json

## SYNOPSIS
Convertit une chaîne au format JSON en un objet personnalisé ou une table de hachage.

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## Description

L' `ConvertFrom-Json` applet de commande convertit une chaîne au format JSON (JavaScript Object Notation) en un objet **PSCustomObject** personnalisé qui a une propriété pour chaque champ de la chaîne JSON. JSON est couramment utilisé par les sites web pour fournir une représentation textuelle des objets. La norme JSON n’interdit pas l’utilisation interdite avec un **PSCustomObject** . Par exemple, si la chaîne JSON contient des clés dupliquées, seule la dernière clé est utilisée par cette applet de commande. Consultez les autres exemples ci-dessous.

Pour générer une chaîne JSON à partir de n’importe quel objet, utilisez l’applet de commande `ConvertTo-Json` .

Cette applet de commande a été introduite dans PowerShell 3,0.

> [!NOTE]
> À partir de PowerShell 6, cette applet de commande prend en charge JSON avec des commentaires. Les commentaires acceptés sont démarrés avec deux barres obliques ( `//` ). Le commentaire n’est pas représenté dans les données et peut être écrit dans le fichier sans altérer les données ou lever une erreur comme dans PowerShell 5,1.

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

### Exemple 4 : convertir une chaîne JSON en une table de hachage

Cette commande montre un exemple dans lequel le `-AsHashtable` commutateur peut surmonter les limitations de la commande.

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

La chaîne JSON contient deux paires clé-valeur avec des clés qui diffèrent uniquement par la casse. Sans le commutateur, la commande aurait renvoyé une erreur.

### Exemple 5 : aller-retour d’un tableau à un seul élément

Cette commande montre un exemple où le `-NoEnumerate` commutateur est utilisé pour effectuer un aller-retour d’un tableau JSON à élément unique.

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

La chaîne JSON contient un tableau avec un seul élément. Sans le commutateur, la conversion de JSON en PSObject, puis sa reconversion avec la `ConvertTo-Json` commande produit un entier unique.

## PARAMETERS

### -AsHashtable

Convertit le JSON en un objet de table de hachage. Ce commutateur a été introduit dans PowerShell 6,0. Il existe plusieurs scénarios dans lesquels il peut surmonter certaines limitations de l’applet de commande `ConvertFrom-Json` .

- Si le JSON contient une liste avec des clés qui diffèrent uniquement par la casse. Sans le commutateur, ces clés sont considérées comme des clés identiques et, par conséquent, seule la dernière est utilisée.
- Si le JSON contient une clé qui est une chaîne vide. Sans le commutateur, l’applet de commande génère une erreur, car un `PSCustomObject` n’autorise pas cela, contrairement à une table de hachage. Voici un exemple de cas d’utilisation où cela peut se produire `project.lock.json` : fichiers.
- Les tables de hachage peuvent être traitées plus rapidement pour certaines structures de données.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Profondeur

Obtient ou définit la profondeur maximale autorisée par l’entrée JSON. Par défaut, il s’agit de 1024.

Ce paramètre a été introduit dans PowerShell 6,2.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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

### -Noenumerate

Spécifie que la sortie n’est pas énumérée.

La définition de ce paramètre entraîne l’envoi de tableaux sous la forme d’un objet unique au lieu d’envoyer chaque élément séparément. Cela garantit que JSON peut être un aller-retour via `ConvertTo-Json` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne JSON vers `ConvertFrom-Json` .

## SORTIES

### PSCustomObject

### System.Collections.Hashtable

## REMARQUES

Cette applet de commande est implémentée à l’aide de [Newtonsoft JSON.net](https://www.newtonsoft.com/json).

À compter de PowerShell 6, `ConvertTo-Json` tente de convertir les chaînes mises en forme en horodateur en valeurs **DateTime** . La valeur convertie est une `[datetime]` instance avec une `Kind` propriété définie comme suit :

- `Unspecified`, s’il n’y a pas d’informations de fuseau horaire dans la chaîne d’entrée.
- `Utc`, si les informations de fuseau horaire sont à la fin `Z` .
- `Local`, si les informations de fuseau horaire sont fournies sous la forme d’un _offset_ UTC de fin comme `+02:00` . Le décalage est correctement converti dans le fuseau horaire configuré de l’appelant. La mise en forme de sortie par défaut n’indique pas le décalage de fuseau horaire d’origine.

## LIENS CONNEXES

[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)

