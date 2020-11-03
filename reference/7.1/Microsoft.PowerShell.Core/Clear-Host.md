---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ''
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 452e0e66cf6db746469247bf68552960517f6c32
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200962"
---
# Clear-Host

## SYNOPSIS

Efface l'affichage dans le programme hôte.

## SYNTAX

```
Clear-Host [<CommonParameters>]
```

## Description

La `Clear-Host` fonction supprime tout le texte de l’affichage actuel, y compris les commandes et la sortie qui ont pu être accumulées. Une fois la fonction terminée, l'invite de commandes apparaît. Vous pouvez utiliser le nom de la fonction ou son alias, `cls` .

`Clear-Host` affecte uniquement l’affichage actuel. Elle ne supprime ni les résultats enregistrés ni les éléments de la session. Les éléments spécifiques à la session, comme les variables et les fonctions, ne sont pas affectés par cette fonction.

Étant donné que le comportement de la `Clear-Host` fonction est déterminé par le programme hôte, `Clear-Host` peut fonctionner différemment dans différents programmes hôtes.

## EXEMPLES

### Exemple 1

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

Cette commande utilise l' `cls` alias de `Clear-Host` pour effacer l’affichage actuel.

## PARAMETERS

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d’entrée vers `Clear-Host` .

## SORTIES

### Aucun

`Clear-Host` ne génère pas de sortie

## REMARQUES

`Clear-Host` est une fonction simple, et non une fonction avancée. Par conséquent, vous ne pouvez pas utiliser de paramètres communs, tels que **Debug** , dans une `Clear-Host` commande.

## LIENS CONNEXES

[Get-Host](../Microsoft.PowerShell.Utility/Get-Host.md)

[Out-Host](Out-Host.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)

