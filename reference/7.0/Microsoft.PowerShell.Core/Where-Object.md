---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: 0d9101c751e9ebc0b0c6fe80564bb76524de8bb6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201201"
---
# Where-Object

## SYNOPSIS
Sélectionne les objets d'une collection en fonction de leurs valeurs de propriété.

## SYNTAX

### EqualSet (par défaut)

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### ScriptBlockSet

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### MatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### CaseSensitiveEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### NotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### CaseSensitiveNotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### GreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### CaseSensitiveGreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### LessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### CaseSensitiveLessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### GreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### CaseSensitiveGreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### LessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### CaseSensitiveLessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### LikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### CaseSensitiveLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### NotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### CaseSensitiveNotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### CaseSensitiveMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### NotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### CaseSensitiveNotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### ContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### CaseSensitiveContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### NotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### CaseSensitiveNotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### Incrustation

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### CaseSensitiveInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### NotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### CaseSensitiveNotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### IsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### IsNotSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### Not

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## Description

L' `Where-Object` applet de commande sélectionne des objets qui ont des valeurs de propriété particulières de la collection d’objets qui lui sont passés. Par exemple, vous pouvez utiliser l' `Where-Object` applet de commande pour sélectionner des fichiers qui ont été créés après une certaine date, des événements avec un ID particulier ou des ordinateurs qui utilisent une version particulière de Windows.

À compter de Windows PowerShell 3,0, il existe deux façons de construire une `Where-Object` commande.

- **Bloc de script** . Vous pouvez utiliser un bloc de script pour spécifier le nom de propriété, un opérateur de comparaison et une valeur de propriété. `Where-Object` retourne tous les objets pour lesquels l’instruction de bloc de script a la valeur true.

  Par exemple, la commande suivante obtient les processus dans la classe de priorité normale, autrement dit, les processus où la valeur de la propriété **PriorityClass** est égale à normal.

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  Tous les opérateurs de comparaison PowerShell sont valides dans le format de bloc de script. Pour plus d’informations sur les opérateurs de comparaison, consultez [about_Comparison_Operators](./About/about_Comparison_Operators.md).

- **Instruction de comparaison** . Vous pouvez également écrire une instruction de comparaison, laquelle se rapproche beaucoup plus du langage naturel. Les instructions de comparaison ont été introduites dans Windows PowerShell 3.0.

  Par exemple, les commandes suivantes obtiennent également les processus dont la classe de priorité est normal. Ces commandes sont équivalentes et peuvent être utilisées de manière interchangeable.

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  À compter de Windows PowerShell 3,0, `Where-Object` ajoute des opérateurs de comparaison comme paramètres dans une `Where-Object` commande. Sauf indication contraire, tous les opérateurs respectent la casse. Avant Windows PowerShell 3,0, les opérateurs de comparaison dans le langage PowerShell pouvaient être utilisés uniquement dans les blocs de script.

Lorsque vous fournissez une **propriété** unique à `Where-Object` , la valeur de la propriété est traitée comme une expression booléenne. Lorsque la valeur de **Length** n’est pas égale à zéro, l’expression prend la valeur **true** . Par exemple : `('hi', '', 'there') | Where-Object Length`

L’exemple précédent est fonctionnellement équivalent à :

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## EXEMPLES

### Exemple 1 : accéder aux services arrêtés

Ces commandes obtiennent une liste de tous les services qui sont actuellement arrêtés. La `$_` variable automatique représente chaque objet passé à l’applet de commande `Where-Object` .

La première commande utilise le format de bloc de script, la deuxième commande utilise le format d’instruction de comparaison. Les commandes sont équivalentes et peuvent être utilisées indifféremment.

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### Exemple 2 : récupérer des processus en fonction de la plage de travail

Ces commandes répertorient les processus dont la plage de travail est supérieure à 250 mégaoctets (Ko). La syntaxe du scriptblock et de l’instruction sont équivalentes et peuvent être utilisées indifféremment.

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### Exemple 3 : récupérer des processus en fonction du nom du processus

Ces commandes obtiennent les processus qui ont une valeur de propriété **ProcessName** qui commence par la lettre `p` . L’opérateur **match** vous permet d’utiliser des correspondances d’expressions régulières.

La syntaxe du scriptblock et de l’instruction sont équivalentes et peuvent être utilisées indifféremment.

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### Exemple 4 : utiliser le format d’instruction de comparaison

Cet exemple montre comment utiliser le nouveau format d’instruction de comparaison de l’applet de commande `Where-Object` .

La première commande utilise le format d'instruction de comparaison.
Dans cette commande, aucun alias n'est utilisé. En outre, tous les paramètres incluent le nom de paramètre.

La deuxième commande représente l'utilisation la plus naturelle du format de commande de comparaison. L' `where` alias est remplacé par le nom de l’applet de commande `Where-Object` et tous les noms de paramètres facultatifs sont omis.

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### Exemple 5 : récupérer des commandes basées sur des propriétés

Cet exemple montre comment écrire des commandes qui retournent des éléments ayant la valeur true ou false, ou ayant une valeur correspondant à une propriété spécifique. Chaque exemple montre les formats de bloc de script et d’instruction de comparaison pour la commande.

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### Exemple 6 : utiliser plusieurs conditions

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

Cet exemple montre comment créer une `Where-Object` commande avec plusieurs conditions.

Cette commande obtient les modules qui ne sont pas des modules de base et qui prennent en charge la fonctionnalité d'aide actualisable. La commande utilise le paramètre **listAvailable** de l' `Get-Module` applet de commande pour récupérer tous les modules sur l’ordinateur. Un opérateur de pipeline ( `|` ) envoie les modules à l’applet de commande `Where-Object` , qui obtient les modules dont les noms ne commencent pas par Microsoft ou PS, et qui ont une valeur pour la propriété **HelpInfoURI** , qui indique à PowerShell où trouver les fichiers d’aide mis à jour pour le module. Les instructions de comparaison sont connectées par l’opérateur logique **and** .

L'exemple utilise le format de commande de bloc de script. Les opérateurs logiques, tels que **and** et **or** , sont valides uniquement dans les blocs de script. Vous ne pouvez pas les utiliser dans le format d’instruction de comparaison d’une `Where-Object` commande.

- Pour plus d’informations sur les opérateurs logiques PowerShell, consultez [about_Logical_Operators](./About/about_logical_operators.md).
- Pour plus d’informations sur la fonctionnalité d’aide actualisable, consultez [about_Updatable_Help](./About/about_Updatable_Help.md).

## PARAMETERS

### -Contient

Indique que cette applet de commande obtient des objets d’une collection si la valeur de propriété de l’objet correspond exactement à la valeur spécifiée. Cette opération respecte la casse.

Par exemple : `Get-Process | where ProcessName -CContains "svchost"`

**Contient** fait référence à une collection de valeurs et a la valeur true si la collection contient un élément qui correspond exactement à la valeur spécifiée. Si l’entrée est un objet unique, PowerShell la convertit en collection d’un seul objet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CEQ

Indique que cette applet de commande obtient des objets si la valeur de propriété est identique à la valeur spécifiée.
Cette opération respecte la casse.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGE MySQL

Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure ou égale à la valeur spécifiée. Cette opération respecte la casse.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGT

Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure à la valeur spécifiée.
Cette opération respecte la casse.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CIn

Indique que cette applet de commande obtient des objets si la valeur de propriété comprend la valeur spécifiée. Cette opération respecte la casse.

Par exemple : `Get-Process | where -Value "svchost" -CIn ProcessName`

**CIN** ressemble à **contient** , à ceci près que les positions des propriétés et des valeurs sont inversées. Par exemple, les instructions suivantes sont toutes les deux vraies.

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLE

Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure ou égale à la valeur spécifiée. Cette opération respecte la casse.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLik

Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à une valeur qui comprend des caractères génériques. Cette opération respecte la casse.

Par exemple : `Get-Process | where ProcessName -CLike "*host"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLT

Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure à la valeur spécifiée. Cette opération respecte la casse.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CMatch

Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à l’expression régulière spécifiée. Cette opération respecte la casse. Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.

Par exemple : `Get-Process | where ProcessName -CMatch "Shell"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNE

Indique que cette applet de commande obtient des objets si la valeur de propriété est différente de la valeur spécifiée.
Cette opération respecte la casse.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cnotcontains font

Indique que cette applet de commande obtient des objets si la valeur de propriété de l’objet ne correspond pas exactement à la valeur spécifiée. Cette opération respecte la casse.

Par exemple : `Get-Process | where ProcessName -CNotContains "svchost"`

**NotContains** et **cnotcontains font** font référence à une collection de valeurs et ont la valeur true lorsque la collection ne contient aucun élément qui correspond exactement à la valeur spécifiée. Si l’entrée est un objet unique, PowerShell la convertit en collection d’un seul objet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotIn

Indique que cette applet de commande obtient des objets si la valeur de propriété n’est pas une correspondance exacte pour la valeur spécifiée. Cette opération respecte la casse.

Par exemple : `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`

Les opérateurs **NotIn** et **CNotIn** ressemblent à **NotContains** et **cnotcontains font** , à ceci près que les positions des propriétés et des valeurs sont inversées. Par exemple, les instructions suivantes sont vraies.

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotLike

Indique que cette applet de commande obtient des objets si la valeur de propriété ne correspond pas à une valeur qui comprend des caractères génériques. Cette opération respecte la casse.

Par exemple : `Get-Process | where ProcessName -CNotLike "*host"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotMatch

Indique que cette applet de commande obtient des objets si la valeur de propriété ne correspond pas à l’expression régulière spécifiée. Cette opération respecte la casse. Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.

Par exemple : `Get-Process | where ProcessName -CNotMatch "Shell"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Contient

Indique que cette applet de commande obtient des objets si un élément de la valeur de propriété de l’objet correspond exactement à la valeur spécifiée.

Par exemple : `Get-Process | where ProcessName -Contains "Svchost"`

Si la valeur de propriété contient un objet unique, PowerShell la convertit en une collection d’un objet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EQ

Indique que cette applet de commande obtient des objets si la valeur de propriété est identique à la valeur spécifiée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterScript

Spécifie le bloc de script utilisé pour filtrer les objets. Placez le bloc de script entre accolades ( `{}` ).

Le nom de paramètre, **FilterScript** , est facultatif.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GE

Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure ou égale à la valeur spécifiée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GT

Indique que cette applet de commande obtient des objets si la valeur de propriété est supérieure à la valeur spécifiée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -In

Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à l’une des valeurs spécifiées.
Par exemple :

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

Si la valeur du paramètre de **valeur** est un objet unique, PowerShell le convertit en une collection d’un objet.

Si la valeur de propriété d’un objet est un tableau, PowerShell utilise l’égalité des références pour déterminer une correspondance. `Where-Object` retourne l’objet uniquement si la valeur du paramètre de **propriété** et toute valeur de **valeur** sont la même instance d’un objet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à filtrer. Vous pouvez également diriger les objets vers `Where-Object` .

Quand vous utilisez le paramètre **InputObject** avec `Where-Object` , au lieu de rediriger les résultats de la commande vers `Where-Object` , la valeur **InputObject** est traitée comme un objet unique. Cela est vrai même si la valeur est une collection qui est le résultat d’une commande, telle que `-InputObject (Get-Process)` . Étant donné que **InputObject** ne peut pas retourner des propriétés individuelles d’un tableau ou d’une collection d’objets, nous vous recommandons, si vous utilisez `Where-Object` pour filtrer une collection d’objets pour les objets qui ont des valeurs spécifiques dans les propriétés définies, d’utiliser `Where-Object` dans le pipeline, comme indiqué dans les exemples de cette rubrique.

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

### -Est

Indique que cette applet de commande obtient des objets si la valeur de propriété est une instance du type .NET spécifié. Placez le nom du type entre crochets.

Par exemple : `Get-Process | where StartTime -Is [DateTime]`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IsNot

Indique que cette applet de commande obtient des objets si la valeur de propriété n’est pas une instance du type .NET spécifié.

Par exemple : `Get-Process | where StartTime -IsNot [DateTime]`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LE

Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure ou égale à la valeur spécifiée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Like

Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à une valeur qui comprend des caractères génériques.

Par exemple : `Get-Process | where ProcessName -Like "*host"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LT

Indique que cette applet de commande obtient des objets si la valeur de propriété est inférieure à la valeur spécifiée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Match

Indique que cette applet de commande obtient des objets si la valeur de propriété correspond à l’expression régulière spécifiée. Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.

Par exemple : `Get-Process | where ProcessName -Match "shell"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ne

Indique que cette applet de commande obtient des objets si la valeur de propriété est différente de la valeur spécifiée.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Non

Indique que cette applet de commande obtient des objets si la propriété n’existe pas ou a une valeur null ou false.

Par exemple : `Get-Service | where -Not "DependentServices"`

Ce paramètre a été introduit dans Windows PowerShell 6,1.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotContains

Indique que cette applet de commande obtient des objets si aucun des éléments de la valeur de propriété ne correspond exactement à la valeur spécifiée.

Par exemple : `Get-Process | where ProcessName -NotContains "Svchost"`

**NotContains** fait référence à une collection de valeurs et a la valeur true si la collection ne contient aucun élément qui correspond exactement à la valeur spécifiée. Si l’entrée est un objet unique, PowerShell la convertit en collection d’un seul objet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotIn

Indique que cette applet de commande obtient des objets si la valeur de propriété n’est pas une correspondance exacte pour l’une des valeurs spécifiées.

Par exemple : `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`

Si la valeur de la **valeur** est un objet unique, PowerShell la convertit en collection d’un seul objet.

Si la valeur de propriété d’un objet est un tableau, PowerShell utilise l’égalité des références pour déterminer une correspondance. `Where-Object` retourne l’objet uniquement si la valeur de la **propriété** et toute valeur de **value** ne sont pas la même instance d’un objet.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotLike

Indique que cette applet de commande obtient des objets si la valeur de propriété ne correspond pas à une valeur qui comprend des caractères génériques.

Par exemple : `Get-Process | where ProcessName -NotLike "*host"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotMatch

Indique que cette applet de commande obtient des objets quand la valeur de propriété ne correspond pas à l’expression régulière spécifiée. Quand l’entrée est scalaire, la valeur correspondante est enregistrée dans la `$Matches` variable automatique.

Par exemple : `Get-Process | where ProcessName -NotMatch "PowerShell"`

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Spécifie le nom d'une propriété d'objet. Le nom du paramètre, **Property** , est facultatif.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: EqualSet, CaseSensitiveNotLikeSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

Spécifie une valeur de propriété. Le nom du paramètre, **value** , est facultatif. Ce paramètre accepte les caractères génériques lorsqu’il est utilisé avec les paramètres de comparaison suivants :

- **CLik**
- **CNotLike**
- **Parent**
- **NotLike**

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: Object
Parameter Sets: EqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger les objets vers cette applet de commande.

## SORTIES

### Object

Cette applet de commande retourne les éléments sélectionnés dans le jeu d’objets d’entrée.

## REMARQUES

À compter de Windows PowerShell 4,0, `Where` les `ForEach` méthodes et ont été ajoutées pour être utilisées avec les collections.

Vous pouvez en savoir plus sur ces nouvelles méthodes ici [about_Arrays](./About/about_Arrays.md)

## LIENS CONNEXES

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[ForEach-Object](ForEach-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)
