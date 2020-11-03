---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 6fb64b7e95f1f8ddfff6f1be9e880045271706fc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201513"
---
# Get-PackageSource

## SYNOPSIS
Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.

## SYNTAX

### NuGet

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### PowerShellGet

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## Description

L' `Get-PackageSource` applet de commande obtient une liste des sources de packages qui sont inscrites auprès de **PackageManagement** sur l’ordinateur local. Si vous spécifiez un fournisseur de packages, `Get-PackageSource` obtient uniquement les sources associées au fournisseur spécifié. Dans le cas contraire, la commande retourne toutes les sources de package inscrites avec **PackageManagement** .

## EXEMPLES

### Exemple 1 : récupération de toutes les sources de package

L' `Get-PackageSource` applet de commande obtient toutes les sources de package inscrites avec **PackageManagement** sur l’ordinateur local.

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### Exemple 2 : obtenir toutes les sources de package pour un fournisseur spécifique

Cette commande obtient les sources de package inscrites pour un fournisseur spécifique.

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

`Get-PackageSource` utilise le paramètre **providerName** pour obtenir les sources de package inscrites pour le fournisseur **NuGet** .

### Exemple 3 : obtenir des sources à partir d’un fournisseur de packages

Cette commande utilise un fournisseur de package pour obtenir les sources de package.

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

`Get-PackageProvider` utilise le paramètre **Name** pour spécifier le nom du fournisseur, **NuGet** . L’objet est envoyé dans le pipeline à `Get-PackageSource` .

## PARAMETERS

### -ConfigFile

Spécifie un fichier de configuration.

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

Indique que cette applet de commande force **PackageManagement** à installer automatiquement un fournisseur de package.

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

### -Location

Spécifie l’emplacement d’une source ou d’un référentiel de gestion des packages.

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

Spécifie le nom d’une source de gestion des packages.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Spécifie un fournisseur de gestion des packages.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Spécifie un ou plusieurs noms de fournisseurs de packages. Séparez les noms de plusieurs fournisseurs de packages par des virgules.
Utilisez `Get-PackageProvider` pour obtenir la liste des fournisseurs de packages disponibles.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

Spécifie l’emplacement de publication de la source du package.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Spécifie l’emplacement de publication du script.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Spécifie l’emplacement source du script.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

Commutateur qui ignore la validation des informations d’identification d’une source de package.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
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

## SORTIES

### PackageSource []

Spécifie une ou plusieurs sources de package.

## REMARQUES

## LIENS CONNEXES

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Find-Package](Find-Package.md)

[Get-Package](Get-Package.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Register-PackageSource](Register-PackageSource.md)

[Set-PackageSource](Set-PackageSource.md)

[Unregister-PackageSource](Unregister-PackageSource.md)
