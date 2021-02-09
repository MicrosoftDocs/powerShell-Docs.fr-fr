---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 1e0c8413a37a9b8877b6af9089ac311459ada20d
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975105"
---
# Exit-PSSession

## Synopsis
Termine une session interactive avec un ordinateur distant.

## SYNTAXE

```
Exit-PSSession [<CommonParameters>]
```

## Description

L' `Exit-PSSession` applet de commande met fin aux sessions interactives que vous avez démarrées à l’aide de la `Enter-PSSession` cmdlet.

Vous pouvez également utiliser le `exit` mot clé pour mettre fin à une session interactive. L’effet est le même que pour l’utilisation de `Exit-PSSession` .

## Exemples

### Exemple 1 : Démarrer et arrêter une session interactive

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS C:\>
```

Ces commandes démarrent, puis arrêtent une session interactive avec l'ordinateur distant Server01.

### Exemple 2 : Démarrer et arrêter une session interactive à l’aide d’un objet PSSession

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

Ces commandes démarrent et arrêtent une session interactive avec l’ordinateur SERVEUR01 qui utilise une session Windows PowerShell (**PSSession**).

Étant donné que la session interactive a été démarrée à l’aide d’une session Windows PowerShell, la session **PSSession** est toujours disponible quand la session interactive se termine. Si vous utilisez le paramètre _ComputerName_ , `Enter-PSSession` crée une session temporaire qu’elle ferme quand la session interactive se termine.

La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01. La commande enregistre la **session PSSession** dans la `$s` variable.

La deuxième commande utilise `Enter-PSSession` pour démarrer une session interactive à l’aide de la session **PSSession** dans `$s` .

La troisième commande utilise `Exit-PSSession` pour arrêter la session interactive.

La dernière commande affiche la **session PSSession** dans la `$s` variable. La propriété **State** indique que la **session PSSession** est toujours ouverte et utilisable.

### Exemple 3 : utiliser le mot clé Exit pour arrêter une session

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS C:\>
```

Cet exemple utilise le `exit` mot clé pour arrêter une session interactive démarrée à l’aide de `Enter-PSSession` . Le `exit` mot clé a le même effet que l’utilisation de `Exit-PSSession` .

## Paramètres

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Entrées

### None

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## Sorties

### None

Cette applet de commande ne retourne aucune sortie.

## Notes

Cette applet de commande accepte uniquement les paramètres communs.

## LIENS CONNEXES

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
