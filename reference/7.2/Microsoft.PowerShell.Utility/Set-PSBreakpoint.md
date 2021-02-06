---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5e2bdf435bf7cb9da3f31712c346beff29a11baf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595936"
---
# Set-PSBreakpoint

## SYNOPSIS
Définit un point d'arrêt sur une ligne, une commande ou une variable.

## SYNTAXE

### Line (par défaut)

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### Commande

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### Variable

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## Description

L' `Set-PSBreakpoint` applet de commande définit un point d’arrêt dans un script ou une commande exécutée dans la session active. Vous pouvez utiliser `Set-PSBreakpoint` pour définir un point d’arrêt avant d’exécuter un script ou d’exécuter une commande, ou pendant le débogage, lorsqu’il est arrêté à un autre point d’arrêt.

`Set-PSBreakpoint` Impossible de définir un point d’arrêt sur un ordinateur distant. Pour déboguer un script sur un ordinateur distant, copiez le script sur l'ordinateur local, puis déboguez-le localement.

Chaque `Set-PSBreakpoint` commande crée l’un des trois types de points d’arrêt suivants :

- Point d’arrêt de ligne : définit les points d’arrêt à des coordonnées de ligne et de colonne particulières.
- Point d’arrêt de commande-définit des points d’arrêt sur les commandes et les fonctions.
- Point d’arrêt de variable-définit des points d’arrêt sur des variables.

Vous pouvez définir un point d’arrêt sur plusieurs lignes, commandes ou variables dans une même `Set-PSBreakpoint` commande, mais chaque `Set-PSBreakpoint` commande ne définit qu’un seul type de point d’arrêt.

À un point d’arrêt, PowerShell arrête temporairement l’exécution et donne le contrôle au débogueur. L’invite de commandes devient `DBG\>` , et un ensemble de commandes du débogueur peut être utilisé. Toutefois, vous pouvez utiliser le paramètre **action** pour spécifier une autre réponse, telle que les conditions pour le point d’arrêt ou les instructions pour effectuer des tâches supplémentaires telles que la journalisation ou les Diagnostics.

L' `Set-PSBreakpoint` applet de commande est l’une des différentes applets de commande conçues pour le débogage des scripts PowerShell.
Pour plus d’informations sur le débogueur PowerShell, consultez [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).

## EXEMPLES

### Exemple 1 : définir un point d’arrêt sur une ligne

Cet exemple définit un point d’arrêt à la ligne 5 dans le script Sample.ps1. Lorsque le script s’exécute, l’exécution s’arrête immédiatement avant l’exécution de la ligne 5.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Lorsque vous définissez un nouveau point d’arrêt par numéro de ligne, l’applet de commande `Set-PSBreakpoint` génère un objet de point d’arrêt de ligne (**System. Management. Automation. LineBreakpoint**) qui comprend l’ID du point d’arrêt et le nombre d’accès.

### Exemple 2 : définir un point d’arrêt sur une fonction

Cet exemple crée un point d’arrêt de commande sur la `Increment` fonction dans l’applet de commande Sample.ps1. Le script arrête l'exécution juste avant chaque appel à la fonction spécifiée.

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Le résultat est un objet point d'arrêt de commande. Avant l’exécution du script, la valeur de la propriété **HitCount** est 0.

### Exemple 3 : définir un point d’arrêt sur une variable

Cet exemple définit un point d’arrêt sur la variable **serveur** dans le script Sample.ps1. Elle utilise le paramètre **mode** avec la valeur **ReadWrite** pour arrêter l’exécution lorsque la valeur de la variable est lue et juste avant que la valeur ne change.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### Exemple 4 : définir un point d’arrêt pour chaque commande qui commence par le texte spécifié

Cet exemple définit un point d’arrêt sur chaque commande dans le script Sample.ps1 qui commence par « Write », comme `Write-Host` .

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### Exemple 5 : définir un point d’arrêt en fonction de la valeur d’une variable

Cet exemple arrête l’exécution au niveau de la `DiskTest` fonction dans le script Test.ps1 uniquement lorsque la valeur de la `$Disk` variable est supérieure à 2.

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

La valeur de l' **action** est un bloc de script qui teste la valeur de la `$Disk` variable dans la fonction.

L’action utilise le `break` mot clé pour arrêter l’exécution si la condition est remplie. L’alternative (et la valeur par défaut) est **Continuer**.

### Exemple 6 : définir un point d’arrêt sur une fonction

Cet exemple définit un point d’arrêt sur la `CheckLog` fonction. Comme la commande ne spécifie pas de script, le point d'arrêt est défini sur n'importe quel élément qui s'exécute dans la session active. Le débogueur s'arrête quand la fonction est appelée, et non quand elle est déclarée.

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### Exemple 7 : définir des points d’arrêt sur plusieurs lignes

Cet exemple définit trois points d’arrêt de ligne dans le script Sample.ps1. Elle définit un point d'arrêt sur la colonne 2 de chacune des lignes spécifiées dans le script. L’action spécifiée dans le paramètre **action** s’applique à tous les points d’arrêt.

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## PARAMETERS

### -Action

Spécifie les commandes qui s'exécutent à chaque point d'arrêt au lieu de s'arrêter. Entrez un bloc de script qui contient les commandes. Vous pouvez utiliser ce paramètre pour définir des points d'arrêt conditionnels ou exécuter d'autres tâches, comme les tests ou la journalisation.

Si ce paramètre est omis ou qu'aucune action n'est spécifiées, l'exécution s'arrête au point d'arrêt et le débogueur démarre.

Lorsque le paramètre d' **action** est utilisé, le bloc de script d’action s’exécute à chaque point d’arrêt. L'exécution ne s'interrompt pas, à moins que le bloc de script ne comporte le mot clé Break. Si vous utilisez le mot clé Continue dans le bloc de script, l'exécution reprend jusqu'au point d'arrêt suivant.

Pour plus d’informations, consultez [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)et [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Colonne

Spécifie le numéro de colonne du fichier de script sur lequel l'exécution s'arrête. Entrez un seul numéro de colonne. La valeur par défaut est la colonne 1.

La valeur de la colonne est utilisée avec la valeur du paramètre **line** pour spécifier le point d’arrêt. Si le paramètre **line** spécifie plusieurs lignes, le paramètre **Column** définit un point d’arrêt au niveau de la colonne spécifiée sur chacune des lignes spécifiées. PowerShell arrête l’exécution avant l’instruction ou l’expression qui contient le caractère à la position de ligne et de colonne spécifiée.

Les colonnes sont numérotées à partir de la marge gauche en commençant par le numéro 1 (pas 0). Si vous spécifiez une colonne qui n'existe pas dans le script, aucune erreur n'est déclarée, mais le point d'arrêt n'est jamais exécuté.

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

Définit un point d'arrêt de commande. Entrez des noms d’applet de commande, tels que `Get-Process` , ou des noms de fonction. Les caractères génériques sont autorisés.

L'exécution s'arrête juste avant l'exécution de chaque instance de chaque commande. Si la commande est une fonction, l'exécution s'arrête chaque fois que la fonction est appelée, ainsi que sur chaque section BEGIN, PROCESS et END.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Ligne

Définit un point d'arrêt de ligne dans un script. Entrez un ou plusieurs numéros de ligne, séparés par une virgule. PowerShell s’arrête immédiatement avant l’exécution de l’instruction qui commence sur chacune des lignes spécifiées.

Les lignes sont numérotées à partir de la marge gauche du fichier de script en commençant par le numéro 1 (pas 0).
Si vous spécifiez une ligne vierge, l'exécution s'arrête avant la prochaine ligne non vide. Si la ligne est en dehors de la plage, le point d'arrêt n'est jamais atteint.

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mode

Spécifie le mode d’accès qui déclenche les points d’arrêt de variable. La valeur par défaut est **Write**.

Ce paramètre n’est valide que lorsque le paramètre **variable** est utilisé dans la commande. Le mode s'applique à tous les points d'arrêt définis dans la commande. Les valeurs valides pour ce paramètre sont :

- **Write** : arrête l’exécution immédiatement avant qu’une nouvelle valeur ne soit écrite dans la variable.
- **Lecture** : arrête l’exécution lorsque la variable est lue, c’est-à-dire lorsque sa valeur est accédée, affichée ou utilisée. En mode lecture, l'exécution ne s'arrête pas lorsque la valeur de la variable change.
- **ReadWrite** : arrête l’exécution lorsque la variable est lue ou écrite.

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script

Spécifie un tableau de fichiers de script dans lequel cette applet de commande définit un point d’arrêt. Entrez les chemins d'accès et les noms de fichiers d'un ou de plusieurs fichiers de script. Si les fichiers se trouvent dans le répertoire actif, vous pouvez ignorer le chemin d'accès.
Les caractères génériques sont autorisés.

Par défaut, les points d'arrêt de variable ou de commande sont définis sur une commande qui s'exécute dans la session active. Ce paramètre n'est obligatoire que lors de la définition d'un point d'arrêt de ligne.

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

Spécifie un tableau de variables sur lesquelles cette cmdlet définit des points d’arrêt. Entrez une liste de variables séparées par des virgules sans signe dollar ( `$` ).

Utilisez le paramètre **mode** pour déterminer le mode d’accès qui déclenche les points d’arrêt. Le mode par défaut, Write, arrête l'exécution avant qu'une nouvelle valeur ne soit écrite dans la variable.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### None
Vous ne pouvez pas diriger d’entrée vers `Set-PSBreakpoint` .

## SORTIES

### Objet point d’arrêt (System. Management. Automation. LineBreakpoint, System. Management. Automation. VariableBreakpoint, System. Management. Automation. CommandBreakpoint)

`Set-PSBreakpoint` retourne un objet qui représente chaque point d’arrêt qu’il définit.

## REMARQUES

- `Set-PSBreakpoint` Impossible de définir un point d’arrêt sur un ordinateur distant. Pour déboguer un script sur un ordinateur distant, copiez le script sur l'ordinateur local, puis déboguez-le localement.
- Lorsque vous définissez un point d’arrêt sur plusieurs lignes, commandes ou variables, `Set-PSBreakpoint` génère un objet de point d’arrêt pour chaque entrée.
- Lors de la définition d'un point d'arrêt sur une fonction ou une variable à l'invite de commandes, vous pouvez définir le point d'arrêt avant ou après la création de la fonction ou variable.

## LIENS CONNEXES

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

