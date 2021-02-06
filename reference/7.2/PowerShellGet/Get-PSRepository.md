---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: 66f840d99b107da22b6771e6327ab68d33a1b368
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595931"
---
# Get-PSRepository

## SYNOPSIS
Obtient les référentiels PowerShell.

## SYNTAXE

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-PSRepository** obtient les référentiels de module PowerShell qui sont inscrits pour l’utilisateur actuel.

## EXEMPLES

### Exemple 1 : récupération de tous les référentiels de modules

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

Cette commande obtient tous les référentiels de module inscrits pour l’utilisateur actuel.

### Exemple 2 : récupérer des référentiels de module par nom

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

Cette commande obtient tous les référentiels de modules qui incluent NuGet dans leur nom.

### Exemple 3 : obtenir un référentiel de module et mettre en forme la sortie

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

Cette commande obtient le référentiel nommé Local01 et utilise l’opérateur de pipeline pour passer cet objet à l’applet de commande Format-List.

## PARAMETERS

### -Name

Spécifie les noms des référentiels à récupérer.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)

