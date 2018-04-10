---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Get-InstalledModule
ms.openlocfilehash: f82d8f3b6b6a9283deef44c2705b97d4717b634c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="get-installedmodule"></a>Get-InstalledModule

Obtient les modules installés sur un ordinateur.

## <a name="description"></a>Description

L’applet de commande Get-InstalledModule obtient les modules PowerShell qui ont été installés sur un ordinateur à l’aide de l’applet de commande Install-Module.

Pour chaque module installé, Get-InstalledModule retourne un objet PSRepositoryItemInfo qui peut éventuellement être transmis à Uninstall-Module pour désinstaller les modules installés.

- Get-InstalledModule peut filtrer les modules installés selon le nom ou les paramètres de version.
- Get-InstalledModule permet de filtrer avec des paramètres de version : MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Ces paramètres sont mutuellement exclusifs, sauf MinmimumVersion et MaximumVersion.
  - Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.
  - Si le paramètre RequiredVersion n’est pas spécifié, Get-InstalledModule retourne la dernière version du module installé qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.
  - Si le paramètre RequiredVersion est spécifié, Get-InstalledModule retourne uniquement la version du module installé qui correspond exactement à la version spécifiée.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande
```powershell
Get-Command -Name Get-InstalledModule -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Get-InstalledModule](http://go.microsoft.com/fwlink/?LinkId=526863)

## <a name="example-commands"></a>Exemples de commandes

```powershell

# Get all modules installed using PowerShellGet cmdlets
Get-InstalledModule

# Get a specific installed module
Get-InstalledModule DJoin

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        DJoin                               PSGallery            This is a PowerShell frontend to the DJOIN.exe c...

# Get installed module with wildcards
Get-InstalledModule -Name AzureRM*

# Get all versions of an installed module
Get-InstalledModule -Name AzureRM.Automation -AllVersions

# Get installed module with MinimumVersion
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0

# Get installed module with MaximumVersion
Get-InstalledModule -Name AzureRM.Automation -MaximumVersion 1.0.8

# Get installed module with version range
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0 -MaximumVersion 1.0.8

# Get installed module with RequiredVersion
Get-InstalledScript -Name AzureRM.Automation -RequiredVersion 1.0.3

# Properties of Get-InstalledModule returned object
Get-InstalledModule DJoin | Format-List * -Force

Name                       : DJoin
Version                    : 1.0
Type                       : Module
Description                : This is a PowerShell frontend to the DJOIN.exe command which provides better
                             discoverability and usability.
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 7:12:37 PM
InstalledDate              : 4/5/2016 4:13:39 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Modules\DJoin\1.0

```



## <a name="installeddate-and-updateddate-properties-in-psgetrepositoryiteminfo-object"></a>Propriétés InstalledDate et UpdatedDate dans l’objet PSGetRepositoryItemInfo

    During the install operation:
        InstalledDate: current DateTime (Get-Date) value
        UpdatedDate: null

    During the Update operation:
        InstalledDate: InstalledDate from the previous installation otherwise current DateTime (Get-Date) value
        UpdatedDate: current DateTime (Get-Date) value

```powershell
Install-Module -Name ContosoServer -RequiredVersion 1.0 -Repository INT
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM


\Update-Module -Name ContosoServer
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM 2/29/2016 12:00:15 PM
```