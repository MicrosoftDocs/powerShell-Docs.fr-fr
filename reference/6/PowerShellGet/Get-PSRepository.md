---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: b4d786cdac183917428b0846ad3c88d41b083ac5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204281"
---
# Get-PSRepository

## SYNOPSIS
Obtient les référentiels PowerShell.

## SYNTAX

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
