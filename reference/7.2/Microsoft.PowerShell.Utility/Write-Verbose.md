---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 177e32106f37c59593bbecac13843f6603327cc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595932"
---
# Write-Verbose

## SYNOPSIS
Écrit du texte dans le flux de message détaillé.

## SYNTAXE

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## Description

L' `Write-Verbose` applet de commande écrit du texte dans le flux de message détaillé dans PowerShell. En règle générale, le flux de messages détaillé est utilisé pour fournir des informations plus détaillées sur le traitement des commandes.

Par défaut, le flux de message détaillé n’est pas affiché, mais vous pouvez l’afficher en modifiant la valeur de la `$VerbosePreference` variable ou en utilisant le paramètre commun **Verbose** dans n’importe quelle commande.

## EXEMPLES

### Exemple 1 : écrire un message d’État

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

Ces commandes utilisent l' `Write-Verbose` applet de commande pour afficher un message d’État. Par défaut, le message n'est pas affiché.

La deuxième commande utilise le paramètre commun **Verbose** , qui affiche tous les messages détaillés, quelle que soit la valeur de la `$VerbosePreference` variable.

### Exemple 2 : définir $VerbosePreference et écrire un message d’État

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

Ces commandes utilisent l' `Write-Verbose` applet de commande pour afficher un message d’État. Par défaut, le message n'est pas affiché.

La première commande attribue la valeur continue à la `$VerbosePreference` variable de préférence. La valeur par défaut, `SilentlyContinue` , supprime les messages détaillés. La deuxième commande écrit un message détaillé.

## PARAMETERS

### -Message

Spécifie le message à afficher. Ce paramètre est obligatoire. Vous pouvez également diriger une chaîne de message vers `Write-Verbose` .

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient le message vers `Write-Verbose` .

## SORTIES

### None

`Write-Verbose` écrit uniquement dans le flux de message détaillé.

## REMARQUES

- Les messages détaillés sont retournés uniquement quand la commande utilise le paramètre commun **Verbose**. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).
- Dans les tâches en arrière-plan Windows PowerShell et les commandes distantes, la `$VerbosePreference` variable de la session de travail et de la session à distance détermine si le message détaillé est affiché par défaut.
  Pour plus d’informations sur la `$VerbosePreference` variable, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

## LIENS CONNEXES

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Warning](Write-Warning.md)
