---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: b551f50b024e5fd8083d853195eb9992587ca16c
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200978"
---
# Get-PSCallStack

## SYNOPSIS
Affiche la pile des appels actuelle.

## SYNTAX

```
Get-PSCallStack [<CommonParameters>]
```

## Description

L’applet de commande **PsCallStack** affiche la pile des appels actuelle.

Bien qu’elle soit conçue pour être utilisée avec le débogueur PowerShell, vous pouvez utiliser cette applet de commande pour afficher la pile des appels dans un script ou une fonction en dehors du débogueur.

Pour exécuter une commande **obtenir-PsCallStack** dans le débogueur, tapez `k` ou `Get-PSCallStack` .

## EXEMPLES

### Exemple 1 : obtenir la pile des appels d’une fonction

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

Cette commande utilise l’applet de commande **PsCallStack** pour afficher la pile des appels pour My-alias, une fonction simple qui obtient les alias d’un nom d’applet de commande.

La première commande entre la fonction à l’invite PowerShell.
La deuxième commande utilise l'applet de commande Set-PSBreakpoint pour définir un point d'arrêt sur la fonction My-Alias.
La troisième commande utilise la fonction My-Alias pour obtenir tous les alias dans la session active de l'applet de commande Get-Content.

Le débogueur s'arrête à l'appel de la fonction.
Deux commandes (s) pas à pas d'entrée consécutives commencent à exécuter la fonction ligne par ligne.
Ensuite, une commande **PsCallStack** est utilisée pour récupérer la pile des appels.

La dernière commande est une commande pas à pas de sortie (o) qui quitte le débogueur et continue d'exécuter le script jusqu'à la fin.

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### System. Management. Automation. CallStackFrame

La méthode **obtient-PsCallStack** retourne un objet qui représente les éléments de la pile des appels.

## REMARQUES

## LIENS CONNEXES

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Format-Table](Format-Table.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

