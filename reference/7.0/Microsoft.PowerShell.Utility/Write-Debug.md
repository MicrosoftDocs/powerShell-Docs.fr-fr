---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3217a3c67c262f8061963fd1302c6782620e270d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208505"
---
# Write-Debug

## SYNOPSIS
Écrit un message de débogage dans la console.

## SYNTAX

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## Description

L' `Write-Debug` applet de commande écrit des messages de débogage sur l’hôte à partir d’un script ou d’une commande.

Par défaut, les messages de débogage ne s’affichent pas dans la console, mais vous pouvez les afficher à l’aide du paramètre **Debug** ou de la `$DebugPreference` variable.

## EXEMPLES

### Exemple 1 : comprendre $DebugPreference

Cet exemple écrit un message de débogage.

```powershell
Write-Debug "Cannot open file."
```

La valeur par défaut de `$DebugPreference` est **SilentlyContinue** . Par conséquent, le message ne s’affiche pas dans la console.

### Exemple 2 : modifier la valeur de $DebugPreference

Cet exemple montre l’effet de la modification de la valeur de la `$DebugPreference` variable. Tout d’abord, nous affichons la valeur actuelle de `$DebugPreference` et nous tentons d’écrire un message de débogage. Ensuite, nous modifions la valeur de `$DebugPreference` pour **Continuer** , ce qui permet d’afficher les messages de débogage.

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

Pour plus d’informations sur `$DebugPreference` , consultez [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).

### Exemple 3 : utiliser le paramètre Debug pour remplacer $DebugPreference

La `Test-Debug` fonction écrit la valeur de la `$DebugPreference` variable dans l’hôte PowerShell et dans le flux de débogage. Dans cet exemple, nous utilisons le paramètre **Debug** pour remplacer la `$DebugPreference` valeur.

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

Notez que la valeur de `$DebugPreference` change quand vous utilisez le paramètre **Debug** . Cette modification affecte uniquement l’étendue de la fonction. La valeur n’est pas affectée en dehors de la fonction.

Pour plus d’informations sur le paramètre commun de **débogage** , consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## PARAMETERS

### -Message

Spécifie le message de débogage à envoyer à la console.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

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

Vous pouvez diriger une chaîne qui contient un message de débogage vers `Write-Debug` .

## SORTIES

### Aucun

`Write-Debug` écrit uniquement dans le flux de débogage. Il n’écrit pas d’objets dans le pipeline.

## REMARQUES

## LIENS CONNEXES

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Écriture-erreur](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
