---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: a1a8c6fcc16bcddc3bfcdade56cd75aadd179b74
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603661"
---
# Exit-PSHostProcess

## SYNOPSIS
Ferme une session interactive avec un processus local.

## SYNTAXE

```
Exit-PSHostProcess [<CommonParameters>]
```

## Description

L' `Exit-PSHostProcess` applet de commande ferme une session interactive avec un processus local que vous avez ouvert en exécutant l’applet de commande `Enter-PSHostProcess` . Vous exécutez l' `Exit-PSHostProcess` applet de commande à partir du processus, lorsque vous avez terminé le débogage ou que vous dépannez un script qui s’exécute dans un processus. À compter de PowerShell 6,2, cette applet de commande est prise en charge sur les plateformes non-Windows.

## EXEMPLES

### Exemple 1 : quitter un processus

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

Dans cet exemple, vous avez travaillé dans un processus actif pour déboguer un script qui s’exécute dans une instance d’exécution dans le processus, comme décrit dans `Enter-PSHostProcess` . Une fois que vous avez tapé la `exit` commande pour quitter le débogueur, exécutez l' `Exit-PSHostProcess` applet de commande pour fermer votre session interactive avec le processus.
L’applet de commande ferme votre session dans le processus et vous renvoie à l' `PS C:\>` invite.

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Enter-PSHostProcess](Enter-PSHostProcess.md)

