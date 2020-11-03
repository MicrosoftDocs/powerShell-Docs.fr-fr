---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 8b900f8e7ff2583e20d359fd3d15aee653b9c1d6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202722"
---
# Import-PackageProvider

## SYNOPSIS
Ajoute Package Management fournisseurs de package à la session active.

## SYNTAX

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## Description

L' `Import-PackageProvider` applet de commande ajoute un ou plusieurs fournisseurs de package à la session active.
Le fournisseur que vous importez doit être installé sur l’ordinateur local.

Pour obtenir la liste des fournisseurs disponibles, exécutez `Get-PackageProvider -ListAvailable` .
Notez qu’un nom de fournisseur de package peut être différent de son nom de module.

Pour des raisons de sécurité, **PackageManagement** requiert que les fournisseurs C# contiennent un `provider.manifest` . Pour plus d’informations sur la façon de générer un fournisseur avec `provider.manifest` injecté, consultez les `.csproj` fichiers projet sur [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .

## EXEMPLES

### Exemple 1 : importer un fournisseur de package à partir de l’ordinateur local

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

Cette commande importe le fournisseur NuGet une fois qu’il a été installé sur l’ordinateur local.

### Exemple 2 : importer une version spécifique d’un fournisseur de packages

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

Cette commande recherche, installe et importe une version spécifique du fournisseur de package NuGet.

## PARAMETERS

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.
Réimporte un fournisseur de packages.

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

### -MaximumVersion

Spécifie la version maximale autorisée du fournisseur de packages que vous souhaitez importer. Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du fournisseur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Spécifie la version minimale autorisée du fournisseur de packages que vous souhaitez importer. Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du package qui satisfait également à toute version maximale spécifiée à l’aide du paramètre *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un ou plusieurs noms de fournisseurs de packages. Les caractères génériques ne sont pas autorisés.

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

### -RequiredVersion

Spécifie la version exacte du fournisseur de packages que vous souhaitez importer. Si vous n’ajoutez pas ce paramètre, `Import-PackageProvider` importe la version disponible la plus élevée du fournisseur qui satisfait également à toute version maximale spécifiée à l’aide du paramètre **MaximumVersion** .

```yaml
Type: System.String
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

### Microsoft. PackageManagement. implementation. PackageProvider

Vous pouvez diriger un objet **PackageProvider** retourné par `Get-PackageProvider` dans `Import-PackageProvider` .

## SORTIES

## REMARQUES

## LIENS CONNEXES

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Get-PackageProvider](Get-PackageProvider.md)

