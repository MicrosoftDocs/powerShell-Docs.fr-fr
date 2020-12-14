---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 43958b376123202e152ceb2da3223cc2f22b0687
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96935899"
---
# Measure-Command

## SYNOPSIS
Mesure le temps nécessaire pour exécuter des applets de commande et des blocs de script.

## SYNTAXE

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## Description

L' `Measure-Command` applet de commande exécute un bloc de script ou une applet de commande en interne, le temps d’exécution de l’opération et retourne la durée d’exécution.

> [!NOTE]
> Les blocs de script s’exécutent `Measure-Command` dans l’étendue actuelle, et non dans une portée enfant.

## EXEMPLES

### Exemple 1 : mesurer une commande

Cet exemple mesure le temps nécessaire à l’exécution d’une `Get-EventLog` commande qui obtient les événements dans le journal des événements Windows PowerShell.

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### Exemple 2 : Comparaison de deux sorties à partir de Measure-Command

La première commande mesure le temps nécessaire pour traiter une `Get-ChildItem` commande récursive qui utilise le paramètre **path** pour obtenir uniquement les `.txt` fichiers du `C:\Windows` répertoire et de ses sous-répertoires.

La deuxième commande mesure le temps nécessaire pour traiter une `Get-ChildItem` commande récursive qui utilise le paramètre spécifique au fournisseur.

Ces commandes montrent la valeur de l’utilisation d’un filtre spécifique au fournisseur dans les commandes PowerShell.

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### Exemple 3 : entrée de canalisation dans Measure-Command

Les objets qui sont dirigés vers `Measure-Command` sont disponibles pour le bloc de script qui est passé au paramètre d' **expression** . Le bloc de script est exécuté une fois pour chaque objet sur le pipeline.

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### Exemple 4 : affichage de la sortie de la commande mesurée

Pour afficher la sortie de l’expression dans, `Measure-Command` vous pouvez utiliser un canal vers `Out-Default` .

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### Exemple 5 : mesure de l’exécution dans une étendue enfant

`Measure-Command` exécute le bloc de script dans l’étendue actuelle, afin que le bloc de script puisse modifier les valeurs dans l’étendue actuelle. Pour éviter toute modification de l’étendue actuelle, vous devez encapsuler le bloc de script entre accolades ( `{}` ) et utiliser l’opérateur d’appel ( `&` ) pour exécuter le bloc dans une portée enfant.

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

Pour plus d’informations sur l’opérateur d’appel, consultez [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).

## PARAMETERS

### -Expression

Spécifie l'expression à chronométrer. Mettez l’expression entre accolades ( `{}` ).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Les objets liés au paramètre **InputObject** sont des entrées facultatives pour le bloc de script passé au paramètre **expression** . Dans le bloc de script, `$_` peut être utilisé pour référencer l’objet actuel dans le pipeline.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger un objet vers `Measure-Command` .

## SORTIES

### System.TimeSpan

`Measure-Command` retourne un objet d’intervalle de temps qui représente le résultat.

## REMARQUES

## LIENS CONNEXES

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Trace-Command](Trace-Command.md)

