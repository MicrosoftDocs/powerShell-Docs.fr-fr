---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 77a89a9189d3ae8f7c3450bdddbe9456b4e941c7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202597"
---
# Uninstall-Module

## SYNOPSIS
Désinstalle un module.

## SYNTAX

### NameParameterSet (par défaut)

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### InputObject

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Uninstall-Module` applet de commande désinstalle un module spécifié de l’ordinateur local. Vous ne pouvez pas désinstaller un module s’il contient d’autres modules en tant que dépendances.

## EXEMPLES

### Exemple 1 : désinstaller un module

Cet exemple désinstalle un module.

```powershell
Uninstall-Module -Name SpeculationControl
```

`Uninstall-Module` utilise le paramètre **Name** pour spécifier le module à désinstaller à partir de l’ordinateur local.

### Exemple 2 : utiliser le pipeline pour désinstaller un module

Dans cet exemple, le pipeline est utilisé pour désinstaller un module.

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

`Get-InstalledModule` utilise le paramètre **Name** pour spécifier le module. L’objet est envoyé dans le pipeline à `Uninstall-Module` et est désinstallé.

## PARAMETERS

### -AllowPrerelease

Vous permet de désinstaller un module marqué comme version préliminaire.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Spécifie que vous souhaitez inclure toutes les versions disponibles d’un module. Vous ne pouvez pas utiliser le paramètre **AllVersions** avec les paramètres **MinimumVersion** , **MaximumVersion** ou **RequiredVersion** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer l’exécution de l' `Uninstall-Module` .

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

### -Force

Force l' `Uninstall-Module` exécution sans demander la confirmation de l’utilisateur.

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

### -InputObject

Accepte un objet **PSRepositoryItemInfo** . Par exemple, `Get-InstalledModule` la sortie vers une variable et l’utilisation de cette variable en tant qu’argument **InputObject** .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

Spécifie la version maximale ou la plus récente du module à désinstaller. Les paramètres **MaximumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie la version minimale du module à désinstaller. Les paramètres **MinimumVersion** et **RequiredVersion** ne peuvent pas être utilisés dans la même commande.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms de modules à désinstaller.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Spécifie le numéro de version exact du module à désinstaller.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe si `Uninstall-Module` s’exécute. L’applet de commande n’est pas exécutée.

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

### System.String[]

### System. Management. Automation. PSObject []

### System.String

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Update-Module](Update-Module.md)

