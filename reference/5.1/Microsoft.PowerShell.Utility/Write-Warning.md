---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 52f060b0dd0364b1c930cd27a4bba280e467cff4
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208429"
---
# Write-Warning

## SYNOPSIS
Écrit un message d'avertissement.

## SYNTAX

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## Description

L' `Write-Warning` applet de commande écrit un message d’avertissement sur l’hôte PowerShell. La réponse à l’avertissement dépend de la valeur de la variable de l’utilisateur `$WarningPreference` et de l’utilisation du paramètre commun **WarningAction** .

## EXEMPLES

### Exemple 1 : écrire un message d’avertissement

Cette commande affiche le message « AVERTISSEMENT : il s’agit uniquement d’un avertissement de test ».

```powershell
Write-Warning "This is only a test warning."
```

### Exemple 2 : passer une chaîne à Write-Warning

Cette commande montre que vous pouvez utiliser un opérateur de pipeline ( `|` ) pour envoyer une chaîne à `Write-Warning` .
Vous pouvez enregistrer la chaîne dans une variable, comme indiqué dans cette commande, ou diriger la chaîne directement vers `Write-Warning` .

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### Exemple 3 : définir la variable $WarningPreference et écrire un avertissement

Cet exemple montre l’effet de la valeur de la `$WarningPreference` variable sur une `Write-Warning` commande.

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

La première commande affiche la valeur par défaut de la `$WarningPreference` variable, qui est `Continue` . Par conséquent, lorsque vous écrivez un avertissement, le message d'avertissement s'affiche et l'exécution se poursuit.

Lorsque vous modifiez la valeur de la `$WarningPreference` variable, l’effet de la `Write-Warning` commande change de nouveau. `SilentlyContinue`La valeur supprime l’avertissement. `Stop`La valeur affiche l’avertissement et arrête l’exécution de la commande.

Pour plus d’informations sur la `$WarningPreference` variable, consultez [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).

### Exemple 4 : définir le paramètre WarningAction et écrire un avertissement

Cet exemple montre l’effet du paramètre commun **WarningAction** sur une `Write-Warning` commande. Vous pouvez utiliser le paramètre commun **WarningAction** avec n’importe quelle applet de commande pour déterminer comment PowerShell répond aux avertissements résultant de cette commande. Le paramètre commun **WarningAction** remplace la valeur du `$WarningPreference` seul pour cette commande particulière.

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

Cette commande utilise l' `Write-Warning` applet de commande pour afficher un avertissement. Le paramètre commun **WarningAction** avec la valeur inquire indique au système d’inviter l’utilisateur lorsque la commande affiche un avertissement.

Pour plus d’informations sur le paramètre commun **WarningAction** , consultez [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).

## PARAMETERS

### -Message
Spécifie le message d'avertissement.

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

Vous pouvez diriger une chaîne qui contient l’avertissement vers `Write-Warning` .

## SORTIES

### Aucun

`Write-Warning` écrit uniquement dans le flux d’avertissement. Aucune autre sortie n'est générée.

## REMARQUES

La valeur par défaut de la `$WarningPreference` variable est `Continue` , qui affiche l’avertissement et poursuit l’exécution de la commande. Pour déterminer les valeurs valides d’une variable de préférence, par exemple `$WarningPreference` , définissez-la sur une chaîne de caractères aléatoires, telle que « ABC ». Le message d’erreur résultant répertorie les valeurs valides.

## LIENS CONNEXES

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Écriture-erreur](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)
