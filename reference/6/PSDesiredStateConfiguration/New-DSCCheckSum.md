---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 2637cc092d3be2bb3bff051268ef288c81ef3ad7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202526"
---
# New-DscChecksum

## SYNOPSIS
Crée des fichiers de somme de contrôle pour les documents DSC et les ressources DSC.

## SYNTAX

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L’applet **de commande New-DSCCheckSum** génère des fichiers de somme de contrôle pour les documents DSC (Desired State Configuration) PowerShell et les ressources DSC compressées.
Cette applet de commande génère un fichier de somme de contrôle pour chaque configuration et ressource à utiliser en mode par extraction.
Le service DSC utilise les sommes de contrôle pour s’assurer que la configuration et les ressources correctes existent sur le nœud cible.
Placez les sommes de contrôle avec les documents DSC associés et les ressources DSC compressées dans le magasin de services DSC.

## EXEMPLES

### Exemple 1 : créer des fichiers de somme de contrôle pour toutes les configurations dans un chemin d’accès spécifique

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

Cette commande crée des fichiers de somme de contrôle pour toutes les configurations dans le chemin d'accès C:\DSC\Configurations.
Tous les fichiers de somme de contrôle qui existent déjà sont ignorés.

### Exemple 2 : créer des fichiers de somme de contrôle pour toutes les configurations dans un chemin d’accès spécifique et remplacer les fichiers de somme de contrôle existants

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

Cette commande crée des fichiers de somme de contrôle pour toutes les configurations dans le chemin d'accès C:\DSC\Configurations.
Si vous spécifiez le paramètre *force* , la commande remplace les fichiers de somme de contrôle qui existent déjà.

## PARAMETERS

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

### -Force

Indique que l'applet de commande remplace le fichier de sortie spécifié s'il existe déjà.

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

### -Chemin d’accès

Spécifie le chemin d'accès et le nom de fichier de somme de contrôle de sortie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès du fichier d’entrée.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
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

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)
