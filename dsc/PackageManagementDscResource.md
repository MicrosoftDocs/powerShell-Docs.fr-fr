---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: Ressource DSC PackageManagement
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753785"
---
# <a name="dsc-packagemanagement-resource"></a>Ressource DSC PackageManagement

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

La ressource **PackageManagement** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de gestion des packages sur un nœud cible. Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site http://PowerShellGallery.com.

> [!IMPORTANT]
> Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.

## <a name="syntax"></a>Syntaxe

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Spécifie le nom du package à installer ou à désinstaller.|
| AdditionalParameters| Table de hachage spécifique du fournisseur, contenant les paramètres passés à `Get-Package -AdditionalArguments`. Par exemple, pour le fournisseur NuGet, vous pouvez passer des paramètres supplémentaires tels que DestinationPath.|
| Ensure| Détermine si le package doit être installé ou désinstallé.|
| MaximumVersion|Spécifie la version maximale autorisée du package à rechercher. Si vous n’ajoutez pas ce paramètre, la ressource recherche la version disponible la plus récente du package.|
| MinimumVersion|Spécifie la version minimale autorisée du package à rechercher. Si vous n’ajoutez pas ce paramètre, la ressource recherche la version la plus élevée du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre _MaximumVersion_.|
| ProviderName| Spécifie un nom de fournisseur de package auquel vous souhaitez limiter votre recherche de package. Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.|
| RequiredVersion| Spécifie la version exacte du package à installer. Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus récente du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre _MaximumVersion_.|
| Source| Spécifie le nom de la source du package où se trouve le package. Il peut s’agir d’un URI ou d’une source inscrite avec `Register-PackageSource` ou une ressource DSC PackageManagementSource.|
| SourceCredential | Spécifie un compte d’utilisateur disposant des droits nécessaires pour installer un package pour une source ou un fournisseur de package spécifié.|

## <a name="additional-parameters"></a>Paramètres supplémentaires

Le tableau suivant répertorie les options de la propriété AdditionalParameters.
|  Paramètre  | Description   |
|---|---|
| DestinationPath| Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré. Spécifie un emplacement de fichier où vous souhaitez installer le package.|
| InstallationPolicy| Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré. Détermine si vous faites confiance à la source du package. Valeurs disponibles : « Untrusted », « Trusted ».|

## <a name="example"></a>Exemple

Cet exemple installe le package NuGet **JQuery** et le module PowerShell **GistProvider** à l’aide de la ressource DSC **PackageManagement**. Cet exemple vérifie d’abord que les sources de package nécessaires sont disponibles, puis définit l’état attendu des packages **JQuery** et **GistProvider** (NuGet et PowerShell, respectivement).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```