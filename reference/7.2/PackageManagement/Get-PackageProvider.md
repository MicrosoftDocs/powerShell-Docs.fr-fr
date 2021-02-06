---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99595717"
---
# Get-PackageProvider

## SYNOPSIS
Retourne une liste des fournisseurs de packages qui sont connectés à Package Management.

## SYNTAXE

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## Description

L’applet de commande **PackageProvider** renvoie une liste des fournisseurs de packages qui sont connectés à Package Management.
PSModule, NuGet et Chocolated sont des exemples de ces fournisseurs.
Vous pouvez filtrer les résultats en fonction de l’ensemble ou d’une partie d’un ou plusieurs noms de fournisseurs.

## EXEMPLES

### Exemple 1 : récupération de tous les fournisseurs de packages actuellement chargés

```
PS C:\> Get-PackageProvider
```

Cette commande obtient la liste de tous les fournisseurs de packages qui sont actuellement chargés sur l’ordinateur local.

### Exemple 2 : récupération de tous les fournisseurs de packages disponibles

```
PS C:\> Get-PackageProvider -ListAvailable
```

Cette commande obtient une liste de tous les fournisseurs de packages qui sont disponibles sur l’ordinateur local.

### Exemple 3 : obtenir dynamiquement un fournisseur de packages

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

Cette commande installe automatiquement le fournisseur de Chocolate si le fournisseur de chocolat n’est pas installé sur votre ordinateur.

## PARAMETERS

### -Force

Indique que cette applet de commande force toutes les autres actions avec cette applet de commande qui peuvent être forcées.
Dans la méthode **PackageProvider**, cela signifie que le paramètre *force* agit de la même manière que le paramètre *ForceBootstrap* .

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

### -ForceBootstrap

Indique que cette applet de commande force Package Management à installer automatiquement le fournisseur de package.

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

### -ListAvailable

Obtient tous les fournisseurs installés.
La fonction **PackageProvider** obtient le fournisseur dans les chemins d’accès figurant dans la variable d’environnement **PSModulePath** , ainsi que dans les dossiers d’assembly du fournisseur de package :

**$env :P rogramFiles\PackageManagement\ProviderAssemblies * * * * $env : Localappdata\packagemanagement\providerassemblies.**

Sans ce paramètre, la **PackageProvider** obtient uniquement les fournisseurs chargés dans la session active.

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

### -Name

Spécifie un ou plusieurs noms de fournisseurs ou des noms de fournisseurs partiels.
Séparez les noms de fournisseurs multiples par des virgules.
Les valeurs valides pour ce paramètre incluent les noms des fournisseurs que vous avez installés avec des packages. PackageManagement est fourni avec un ensemble de fournisseurs par défaut, y compris les fournisseurs **PSModule** et **MSI** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

### PackageProvider []

## REMARQUES

> [!IMPORTANT]
> Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS). Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.

## LIENS CONNEXES

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Unregister-PackageSource](Unregister-PackageSource.md)
