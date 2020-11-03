---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 8c96b4cd56073a9185ca4b0f0f13b866b839931d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201409"
---
# Get-InstalledModule

## SYNOPSIS
Obtient une liste de modules sur l’ordinateur qui ont été installés par PowerShellGet.

## SYNTAX

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## Description

L' `Get-InstalledModule` applet de commande obtient les modules PowerShell qui sont installés sur un ordinateur à l’aide de PowerShellGet. Pour afficher tous les modules installés sur le système, utilisez la `Get-Module -ListAvailable` commande.

## EXEMPLES

### Exemple 1 : récupération de tous les modules installés

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

Cette commande obtient tous les modules installés.

### Exemple 2 : obtenir des versions spécifiques d’un module

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

Cette commande obtient les versions du module AzureRM. Automation de la version 1,0 à la version 2,0.

## PARAMETERS

### -AllowPrerelease

Comprend dans les modules de résultats marqués comme version préliminaire.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Indique que vous souhaitez obtenir toutes les versions disponibles d’un module.
Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version maximale ou la plus récente d’un module à obtenir. Les paramètres **MaximumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie la version minimale d’un module unique à obtenir. Les paramètres **MinimumVersion** et **RequiredVersion** s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms de modules à récupérer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie la version exacte d’un module à obtenir.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String[]

### System.String

## SORTIES

### System. Management. Automation. PSCustomObject

## REMARQUES

## LIENS CONNEXES
