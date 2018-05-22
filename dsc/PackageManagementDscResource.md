---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource DSC PackageManagement
ms.openlocfilehash: f850c389214fe5adf139c3bd01fb60addc5ec238
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagement-resource"></a>Ressource DSC PackageManagement

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **PackageManagement** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de gestion des packages sur un nœud cible. Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site http://PowerShellGallery.com.

## <a name="syntax"></a>Syntaxe

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Propriétés
|  Propriété  |  Description   |
|---|---|
| Name| Spécifie le nom du package à installer ou à désinstaller.|
| Source| Spécifie le nom de la source du package où se trouve le package. Il peut s’agir d’un URI ou d’une source inscrite avec une ressource DSC Register-PackageSource ou PackageManagementSource. La ressource DSC MSFT_PackageManagementSource peut également inscrire une source de package.|
| Ensure| Détermine si le package doit être installé ou désinstallé.|
| RequiredVersion| Spécifie la version exacte du package à installer. Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus récente du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre MaximumVersion.|
| MinimumVersion| Spécifie la version minimale autorisée du package à installer. Si vous n’ajoutez pas ce paramètre, cette ressource DSC installe la version la plus élevée du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre MaximumVersion.|
| MaximumVersion| Spécifie la version maximale autorisée du package à installer. Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus élevée du package parmi celles disponibles.|
| SourceCredential | Spécifie un compte d’utilisateur disposant des droits nécessaires pour installer un package pour une source ou un fournisseur de package spécifié.|
| ProviderName| Spécifie un nom de fournisseur de package auquel vous souhaitez limiter votre recherche de package. Pour obtenir les noms des fournisseurs de package, exécutez l’applet de commande Get-PackageProvider.|
| AdditionalParameters| Paramètres spécifiques à un fournisseur passés sous forme d’une table de hachage. Par exemple, pour le fournisseur NuGet, vous pouvez passer des paramètres supplémentaires tels que DestinationPath.|

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
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
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