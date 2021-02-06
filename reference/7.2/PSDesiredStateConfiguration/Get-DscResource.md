---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: dbc036562da0172dc4406f169891d2cd1c5e4098
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595722"
---
# Get-DscResource

## SYNOPSIS
Obtient les ressources DSC (Desired State Configuration) présentes sur l’ordinateur.

## SYNTAXE

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## Description

L' `Get-DscResource` applet de commande récupère les ressources DSC PowerShell présentes sur l’ordinateur. Cette applet de commande Découvre uniquement les ressources installées dans le PSModulePath. Il présente les détails des fournisseurs intégrés et personnalisés, qui sont créés par l’utilisateur. Cette applet de commande affiche également des détails sur les ressources composites, qui sont des configurations qui sont empaquetées sous forme de module ou créées au moment de l’exécution dans la session.

## EXEMPLES

### Exemple 1 : récupération de toutes les ressources sur l’ordinateur local

```powershell
Get-DscResource
```

Cette commande obtient toutes les ressources sur l'ordinateur local.

### Exemple 2 : obtenir une ressource en spécifiant le nom

```powershell
Get-DscResource -Name "WindowsFeature"
```

Cette commande obtient la ressource WindowsFeature.

### Exemple 3 : obtenir toutes les ressources d’un module

```powershell
Get-DscResource -Module "xHyper-V"
```

Cette commande obtient toutes les ressources du module xHyper-V.

### Exemple 4 : obtenir une ressource à l’aide de caractères génériques

```powershell
Get-DscResource -Name P*,r*
```

Cette commande obtient toutes les ressources qui correspondent au modèle de caractère générique spécifié par le paramètre **Name** .

### Exemple 5 : obtenir une syntaxe de ressource

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

Cette commande obtient la ressource WindowsFeature et affiche sa syntaxe.

### Exemple 6 : obtenir toutes les propriétés d’une ressource

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

Cette commande obtient la ressource User, puis utilise l'opérateur pipeline pour retourner toutes ses propriétés.

### Exemple 7 : obtenir toutes les ressources d’un module spécifié avec une version spécifiée

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

Cette commande obtient toutes les ressources du module xHyper-V avec la version 3.0.0.0.

## PARAMETERS

### -Module

Spécifie le nom ou le nom complet du module pour lequel afficher la ressource DSC.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de noms de la ressource DSC à afficher.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Syntaxe

Indique que l’applet de commande retourne la vue de la syntaxe des ressources DSC spécifiées. La syntaxe retournée montre comment utiliser les ressources dans un script PowerShell.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

### System.Object

## SORTIES

### Microsoft. PowerShell. DesiredStateConfiguration. DscResourceInfo []

### string[]

## REMARQUES

## LIENS CONNEXES

[Vue d’ensemble de la configuration d’état souhaité PowerShell](/powershell/scripting/dsc/overview/overview)

[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

