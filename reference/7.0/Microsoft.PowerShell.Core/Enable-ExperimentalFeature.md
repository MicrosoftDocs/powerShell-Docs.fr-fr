---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 79884c73bc6e010eb218f1b722d26e0aaa05ef53
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201778"
---
# Enable-ExperimentalFeature

## SYNOPSIS
Activez une fonctionnalité expérimentale au démarrage de la nouvelle instance de PowerShell.

## SYNTAX

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Enable-ExperimentalFeature` applet de commande active les fonctionnalités expérimentales en ajoutant les fonctionnalités expérimentales nommées au `powershell.config.json` fichier de paramètres lu au démarrage de PowerShell.

Cette applet de commande a été introduite dans PowerShell 6,2.

> [!NOTE]
> Les modifications apportées à l’état de la fonctionnalité expérimentale prennent effet uniquement au redémarrage de PowerShell

## EXEMPLES

### Exemple 1 : activer une fonctionnalité expérimentale

Dans cet exemple, si cette fonctionnalité expérimentale était précédemment désactivée, le `powershell.config.json` fichier est mis à jour pour permettre à l’utilisateur d’activer cette fonctionnalité une fois PowerShell redémarré.
En cas de réussite, rien n’est affiché dans le pipeline et un seul message d’avertissement s’affiche.

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## PARAMETERS

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Nom ou noms des fonctionnalités expérimentales à activer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Étendue

Détermine `powershell.config.json` la mise à jour qui affecte tous les utilisateurs ou uniquement l’utilisateur actuel.

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### ExperimentalFeature

Les instances de canal de ExperimentalFeature à partir de l' `Get-ExperimentalFeature` applet de commande pour activer.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

Les modifications apportées à l’état d’une fonctionnalité expérimentale prennent uniquement effet au redémarrage de PowerShell.

## LIENS CONNEXES

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)
