---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 0f076d21ce590b4f1d3eb5b06e891d753dbea638
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200841"
---
# Exit-PSHostProcess

## SYNOPSIS
Ferme une session interactive avec un processus local.

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## Description

L’applet de commande **Exit-PSHostProcess** ferme une session interactive avec un processus local que vous avez ouvert en exécutant l’applet de commande Enter-PSHostProcess. Vous exécutez l’applet de commande **Exit-PSHostProcess** à partir du processus, lorsque vous avez terminé le débogage ou que vous dépannez un script qui s’exécute dans un processus.

## EXEMPLES

### Exemple 1 : quitter un processus

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

Dans cet exemple, vous avez travaillé dans un processus actif pour déboguer un script qui s’exécute dans une instance d’exécution dans le processus, comme décrit dans Enter-PSHostProcess. Une fois que vous avez tapé la commande **Exit** pour quitter le débogueur, exécutez l’applet de commande **Exit-PSHostProcess** pour fermer votre session interactive avec le processus.
L’applet de commande ferme votre session dans le processus et vous renvoie à l’invite PS C : \\ \> .

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Enter-PSHostProcess](Enter-PSHostProcess.md)
