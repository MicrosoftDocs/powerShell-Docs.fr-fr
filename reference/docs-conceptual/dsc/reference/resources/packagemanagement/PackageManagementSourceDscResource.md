---
ms.date: 07/15/2020
keywords: dsc,powershell,configuration,installation
title: Ressources DSC PackageManagementSource
ms.openlocfilehash: b24558574f192347aace5a809d57385e01d9acb3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463888"
---
# <a name="dsc-packagemanagementsource-resource"></a>Ressources DSC PackageManagementSource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **PackageManagementSource** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’inscrire ou de désinscrire des sources de gestion des packages sur un nœud cible.
**Les sources de gestion des packages inscrites de cette façon sont inscrites sous le contexte système et peuvent être utilisées par le compte système ou le moteur DSC.** Cette ressource nécessite le module **PackageManagement**, qui est disponible dans [PowerShell Gallery](https://PowerShellGallery.com).

> [!IMPORTANT]
> Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.

## <a name="syntax"></a>Syntaxe

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Nom |Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système. |
|ProviderName |Spécifie le nom du fournisseur OneGet par le biais duquel vous pouvez interagir avec la source du package. |
|SourceLocation |Spécifie l’URI de la source du package. |
|InstallationPolicy |Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré. Détermine si vous faites confiance à la source du package. Valeurs possibles : **Untrusted** ou **Trusted**. |
|SourceCredential |Informations d’identification permettant l’accès au package sur une source distante. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Détermine si la source du package doit être inscrite ou désinscrite. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

Cet exemple inscrit la source du package `https://nuget.org` à l’aide de la ressource DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
