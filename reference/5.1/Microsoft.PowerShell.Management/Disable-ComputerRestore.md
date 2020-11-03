---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204034"
---
# Disable-ComputerRestore

## SYNOPSIS
Désactive la fonctionnalité Restauration du système sur le lecteur du système de fichiers spécifié.

## SYNTAX

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Disable-ComputerRestore** désactive la fonctionnalité Restauration du système sur un ou plusieurs lecteurs de système de fichiers.
Le lecteur spécifié n’est par conséquent pas concerné en cas de tentative de restauration de l’ordinateur.

Pour désactiver la fonctionnalité Restauration du système sur un lecteur, celle-ci doit d’abord être désactivée sur le lecteur système.

Pour réactiver la fonctionnalité Restauration du système, utilisez l’applet de commande Enable-ComputerRestore.
Pour rechercher l’état de la fonctionnalité Restauration du système pour chaque lecteur, utilisez Rstrui.exe.

Les points de restauration système et les applets de commande ComputerRestore ne sont pris en charge que sur les systèmes d’exploitation clients, tels que Windows 7, Windows Vista et Windows XP.

## EXEMPLES

### Exemple 1 : désactiver la restauration du système sur le lecteur spécifié

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

Cette commande désactive la fonctionnalité Restauration du système sur le lecteur C:.

### Exemple 2 : désactiver la restauration du système sur plusieurs lecteurs

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

Cette commande désactive la fonctionnalité Restauration du système sur les lecteurs C: et D:.
La commande utilise le paramètre *Drive* , mais omet le nom du paramètre Drive.

## PARAMETERS

### -Lecteur
Spécifie les lecteurs de système de fichiers.
Entrez une ou plusieurs lettres de lecteur du système de fichiers, chacune suivie d’un signe deux-points et d’une barre oblique inverse, entre guillemets, par exemple C:\ ou D:\.
Ce paramètre est obligatoire.

Vous ne pouvez pas utiliser cette applet de commande pour désactiver la fonctionnalité Restauration du système sur un lecteur réseau distant, même si ce lecteur est mappé à l’ordinateur local. Vous ne pouvez pas non plus désactiver la fonctionnalité Restauration du système sur les lecteurs qui ne sont pas concernés par la fonctionnalité Restauration du système (lecteurs externes, par exemple).

Pour désactiver la fonctionnalité Restauration du système sur un lecteur, celle-ci doit d’abord être désactivée sur le lecteur système.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

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

* Pour exécuter cette applet de commande sur Windows Vista et les versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.

  Pour rechercher les lecteurs de système de fichiers éligibles à la restauration du système, dans le panneau de configuration système, consultez l’onglet protection du système. Pour ouvrir cet onglet dans Windows PowerShell, tapez `SystemPropertiesProtection` .

  Cette applet Windows Management Instrumentation de commande utilise la classe **SystemRestore** (WMI).

*

## LIENS CONNEXES

[Checkpoint-Computer](Checkpoint-Computer.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)
