---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: f6123bca498d753de1fe284d48f29407c3f8a465
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200950"
---
# Exit-PSSession

## SYNOPSIS
Termine une session interactive avec un ordinateur distant.

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## Description

L’applet de commande **Exit-PSSession** met fin aux sessions interactives que vous avez démarrées à l’aide de l’applet de commande Enter-PSSession.

Vous pouvez également utiliser le mot clé **Exit** pour mettre fin à une session interactive.
L’effet est identique à celui de **Exit-PSSession** .

## EXEMPLES

### Exemple 1 : Démarrer et arrêter une session interactive

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.

### Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session PowerShell ( **PSSession** ).

Étant donné que la session interactive a été démarrée à l’aide d’une session PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine.
Si vous utilisez le paramètre *ComputerName* , **Enter-PSSession** crée une session temporaire qu’elle ferme quand la session interactive se termine.

La première commande utilise l’applet de commande New-PSSession pour créer une **session PSSession** sur l’ordinateur SERVEUR01.
La commande enregistre la **session PSSession** dans la variable $s.

La deuxième commande utilise **Enter-PSSession** pour démarrer une session interactive à l’aide de la session **PSSession** dans $s.

La troisième commande utilise **Exit-PSSession** pour arrêter la session interactive.

La dernière commande affiche la **session PSSession** dans la variable $s.
La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.

### Exemple 3 : utiliser le mot clé Exit pour arrêter une session

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

Cet exemple utilise le mot clé **Exit** pour arrêter une session interactive démarrée à l’aide de **Enter-PSSession** .
Le mot clé **Exit** a le même effet que l’utilisation **de Exit-PSSession** .

## PARAMETERS

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

* Cette applet de commande accepte uniquement les paramètres communs.

*

## LIENS CONNEXES

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

