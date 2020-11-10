---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 63742cf1cc7431668a769bec5d4798b23db8c2ae
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386892"
---
# Set-Date

## SYNOPSIS
Définit l'heure système sur l'ordinateur sur une heure que vous spécifiez.

## SYNTAXE

### Date (par défaut)

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Réglage

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Set-Date` applet de commande remplace la date et l’heure système de l’ordinateur par une date et une heure que vous spécifiez.
Vous pouvez spécifier une nouvelle date et/ou heure en tapant une chaîne ou en passant un objet **DateTime** ou **TimeSpan** à `Set-Date` . Pour spécifier une nouvelle date ou heure, utilisez le paramètre **Date** .
Pour spécifier un intervalle de modification, utilisez le paramètre **Adjust** .

## EXEMPLES

### Exemple 1 : ajouter trois jours à la date système

Cette commande ajoute trois jours à la date système actuelle.
Elle n'affecte pas l'heure.
La commande utilise le paramètre **Date** pour spécifier la date.

L' `Get-Date` applet de commande retourne la date actuelle sous la forme d’un objet **DateTime** . La méthode **AddDays** de l’objet **DateTime** ajoute un nombre spécifié de jours (3) à l’objet **DateTime** actuel.

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### Exemple 2 : définir l’horloge système à 10 minutes

Cet exemple rétablit l’heure système actuelle de 10 minutes.

Le paramètre de **réglage** vous permet de spécifier un intervalle de modification (moins dix minutes) au format d’heure standard pour les paramètres régionaux.

Le paramètre **DisplayHint** indique à PowerShell d’afficher uniquement l’heure, mais il n’affecte pas l’objet **DateTime** `Set-Date` retourné par.

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### Exemple 3 : définir la date et l’heure sur une valeur de variable

Ces commandes modifient la date et l’heure système sur l’ordinateur local en fonction de la date et de l’heure enregistrées dans la variable `$T` . La première commande obtient la date et la stocke dans `$T` .

La deuxième commande utilise le paramètre **Date** pour passer l’objet **DateTime** dans `$T` l’applet de commande `Set-Date` .

```powershell
$T = Get-Date
Set-Date -Date $T
```

### Exemple 4 : ajouter 90 minutes à l’horloge système

Ces commandes avancent de 90 minutes l'heure système sur l'ordinateur local.

La première commande utilise l' `New-TimeSpan` applet de commande pour créer un objet **TimeSpan** avec un intervalle de 90 minutes, puis l’enregistre dans la `$90mins` variable.

La deuxième commande utilise le paramètre **Adjust** de `Set-Date` pour ajuster la date en utilisant la valeur de l’objet **TimeSpan** dans la `$90mins` variable.

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## PARAMÈTRES

### -Ajuster

Spécifie la valeur que cette applet de commande ajoute ou soustrait de la date et de l’heure actuelles.
peut taper un ajustement au format de date et d’heure standard pour vos paramètres régionaux ou utiliser le paramètre **Adjust** pour passer un objet **TimeSpan** de `New-TimeSpan` à `Set-Date` .

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Date

Modifie la date et l'heure en leur affectant les valeurs spécifiées.
Vous pouvez taper une nouvelle date au format de date courte et une heure au format d'heure standard correspondant aux paramètres régionaux. Ou, vous pouvez passer un objet **DateTime** à partir de `Get-Date` .

Si vous spécifiez une date, mais pas une heure, `Set-Date` remplace l’heure par minuit à la date spécifiée. Si vous spécifiez uniquement une heure, la date n'est pas modifiée.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DisplayHint

Spécifie les éléments de la date et de l’heure affichés. Les valeurs acceptables pour ce paramètre sont les suivantes :

- **Date** : affiche uniquement la date.
- **Time** : affiche uniquement l’heure.
- **DateTime** : affiche la date et l’heure.

Ce paramètre affecte uniquement l'affichage.
Elle n’affecte pas l’objet **DateTime** que `Get-Date` récupère.

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.DateTime

Vous pouvez diriger une date vers `Set-Date` .

## SORTIES

### System.DateTime

`Set-Date` retourne un objet qui représente la date à laquelle il est défini.

## REMARQUES

- Utilisez cette applet de commande avec précaution lors de la modification de la date et de l’heure sur l’ordinateur. la modification peut empêcher l'ordinateur de recevoir des mises à jour et des événements système qui sont déclenchés par une date ou une heure. Utilisez les paramètres **WhatIf** et **Confirm** pour éviter les erreurs.
- Vous pouvez utiliser des méthodes .NET standard avec les objets **DateTime** et **TimeSpan** utilisés avec `Set-Date` , tels que **AddDays** , **AddMonths** et **FromFileTime**. Pour plus d’informations, consultez [DateTime, méthodes](/dotnet/api/system.datetime) et

  Les [méthodes TimeSpan](/dotnet/api/system.timespan) dans le kit de développement logiciel (SDK) .net.

## LIENS CONNEXES

[Obtient la date](Get-Date.md)

[New-TimeSpan](New-TimeSpan.md)
