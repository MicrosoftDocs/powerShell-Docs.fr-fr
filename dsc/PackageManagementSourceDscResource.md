---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: Ressources DSC PackageManagementSource
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753768"
---
# <a name="dsc-packagemanagementsource-resource"></a>Ressources DSC PackageManagementSource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

La ressource **PackageManagementSource** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’inscrire ou de désinscrire des sources de gestion des packages sur un nœud cible. **Les sources de gestion des packages inscrites de cette façon sont inscrites sous le contexte système et peuvent être utilisées par le compte système ou le moteur DSC.** Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site http://PowerShellGallery.com.

> [!IMPORTANT]
> Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.

## <a name="syntax"></a>Syntaxe

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| Name| Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système.|
| ProviderName| Spécifie le nom du fournisseur OneGet par le biais duquel vous pouvez interagir avec la source du package.|
| SourceLocation| Spécifie l’URI de la source du package.|
| Ensure| Détermine si la source du package doit être inscrite ou désinscrite.|
| InstallationPolicy| Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré. Détermine si vous faites confiance à la source du package. Valeurs disponibles : « Untrusted », « Trusted ».|
| SourceCredential| Informations d’identification permettant l’accès au package sur une source distante.|

## <a name="example"></a>Exemple

Cet exemple inscrit la source du package http://nuget.org à l’aide de la ressource DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```