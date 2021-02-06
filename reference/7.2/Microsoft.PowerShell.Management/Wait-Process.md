---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: c469a4e9cf17b03a33bc8b9ff9b06aa95773fc02
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597540"
---
# Wait-Process

## SYNOPSIS
Attend l'arrêt des processus avant d'accepter une autre entrée.

## SYNTAXE

### Nom (par défaut)

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### Id

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### InputObject

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## Description

L’applet de commande **Wait-Process** attend l’arrêt d’un ou de plusieurs processus en cours d’exécution avant d’accepter l’entrée.
Dans la console PowerShell, cette applet de commande supprime l’invite de commandes jusqu’à ce que les processus soient arrêtés.
Vous pouvez spécifier un processus par nom de processus ou ID de processus (PID), ou diriger un objet processus vers **Wait-Process**.

**Wait-Process** fonctionne uniquement sur les processus qui s’exécutent sur l’ordinateur local.

## EXEMPLES

### Exemple 1 : arrêter un processus et attendre

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

Cet exemple arrête le processus Notepad, puis attend que le processus soit arrêté avant de continuer avec la commande suivante.

La première commande utilise l’applet de commande **« obten-process »** pour récupérer l’ID du processus du bloc-notes.
Elle stocke l’ID dans la variable $nid.

La deuxième commande utilise l’applet de commande Stop-Process pour arrêter le processus avec l’ID stocké dans $nid.

La troisième commande utilise **Wait-Process** pour attendre jusqu’à ce que le processus Notepad soit arrêté.
Elle utilise le paramètre *ID* de **Wait-Process** pour identifier le processus.

### Exemple 2 : spécification d’un processus

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

Ces commandes indiquent trois méthodes différentes pour spécifier un processus à **attendre**.
La première commande obtient le processus Notepad et le stocke dans la variable $p.

La deuxième commande utilise le paramètre *ID* , la troisième commande utilise le paramètre *Name* et la quatrième commande utilise le paramètre *InputObject* .

Ces commandes produisent les mêmes résultats et peuvent être utilisées indifféremment.

### Exemple 3 : attendre des processus pendant une période spécifiée

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

Cette commande attend l’arrêt des processus Outlook et Winword pendant 30 secondes.
Si les deux processus ne se sont pas arrêtés, l’applet de commande affiche une erreur sans fin d’exécution et l’invite de commandes.

## PARAMETERS

### -Id

Spécifie les identificateurs des processus.
Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules.
Pour rechercher le PID d’un processus, tapez `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

Spécifie les processus en envoyant des objets processus.
Entrez une variable qui contient les objets processus, ou tapez une commande ou une expression qui obtient les objets processus, tels que l’applet de commande Get-Process.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des processus.
Pour spécifier plusieurs noms, séparez-les à l’aide de virgules.
Les caractères génériques ne sont pas pris en charge.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

Spécifie la durée maximale, en secondes, pendant laquelle cette applet de commande attend que les processus spécifiés s’arrêtent.
Lorsque ce délai expire, la commande affiche une erreur sans fin d’exécution qui répertorie les processus dont l’exécution se poursuit et elle met un terme à l’attente.
Par défaut, il n’y a aucun délai d’attente.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Diagnostics.Process

Vous pouvez diriger un objet processus vers cette applet de commande.

## SORTIES

### None

Cette applet de commande ne génère aucune sortie.

## REMARQUES

L’applet de commande est uniquement prise en charge sur les plateformes Windows.

Cette applet de commande utilise la méthode **WaitForExit** de la classe **System. Diagnostics. Process** .

## LIENS CONNEXES

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
