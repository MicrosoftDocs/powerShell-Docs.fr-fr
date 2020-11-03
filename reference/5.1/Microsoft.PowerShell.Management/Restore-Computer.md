---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203525"
---
# Restore-Computer

## SYNOPSIS
Démarre une restauration système sur l'ordinateur local.

## SYNTAX

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Restore-Computer** restaure l’ordinateur local à partir du point de restauration système spécifié.

**Restore-Computer** redémarre l’ordinateur.
La restauration s'effectue pendant l'opération de redémarrage.

Les points de restauration système et **Restore-Computer** sont pris en charge uniquement sur les systèmes d’exploitation clients, tels que Windows 7, Windows Vista et Windows XP.

## EXEMPLES

### Exemple 1 : restaurer l’ordinateur local

```
PS C:\> Restore-Computer -RestorePoint 253
```

Cette commande restaure l’ordinateur local au point de restauration qui a le numéro de séquence 253.

### Exemple 2 : restaurer l’ordinateur local à l’aide de la confirmation

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Cette commande restaure l’ordinateur local au point de restauration qui a le numéro de séquence 255.
Elle utilise le paramètre *Confirm* pour demander à l’utilisateur avant d’effectuer l’opération.

### Exemple 3 : restaurer un ordinateur et vérifier l’État

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

Ces commandes exécutent une restauration système, puis vérifient son état.

La première commande utilise la commande **ComputerRestorePoint** pour récupérer les points de restauration sur l’ordinateur local.

La deuxième commande restaure l’ordinateur sur le point de restauration avec le numéro de séquence 255.

La troisième commande utilise le paramètre *LastStatus* de l’applet de commande *ComputerRestorePoint* pour vérifier l’état de l’opération de restauration.
Étant donné que **Restore-Computer** force un redémarrage, cette commande est entrée après le redémarrage de l’ordinateur.

## PARAMETERS

### -RestorePoint
Spécifie le numéro de séquence du point de restauration.
Pour rechercher le numéro de séquence, utilisez l’applet de commande Get-ComputerRestorePoint.
Ce paramètre est obligatoire.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour exécuter une commande Restore-Computer sur Windows Vista et les versions ultérieures du système d’exploitation Windows, ouvrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.
* Cette applet Windows Management Instrumentation de commande utilise la classe **SystemRestore** (WMI).

## LIENS CONNEXES

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)
