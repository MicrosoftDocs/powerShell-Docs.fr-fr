---
ms.date: 07/16/2020
ms.topic: reference
title: Ressources WindowsFeatureSet dans DSC
description: Ressources WindowsFeatureSet dans DSC
ms.openlocfilehash: 327c5e907e9b100f42b6a15684f8b131c1f20a41
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143073"
---
# <a name="dsc-windowsfeatureset-resource"></a>Ressources WindowsFeatureSet dans DSC

> S’applique à : Windows PowerShell 5.x

La ressource **WindowsFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible. Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la [ressource WindowsFeature](windowsfeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété **Name** .

Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités de Windows au même état.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
|Nom |Nom des rôles ou fonctionnalités dont vous voulez garantir l’ajout ou la suppression. Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature), et non du nom d’affichage des rôles ou des fonctionnalité. |
|Source |Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire. |
|IncludeAllSubFeature |Affectez la valeur `$true` à cette propriété pour inclure toutes les sous-fonctionnalités requises avec les fonctionnalités que vous spécifiez avec la propriété **Name** . |
|Informations d'identification |Informations d’identification à utiliser pour ajouter ou supprimer les rôles ou les fonctionnalités. |
|LogPath |Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si les rôles ou fonctionnalités sont ajoutés. Pour faire en sorte que les rôles ou les fonctionnalités soient ajoutés, définissez cette propriété sur **Present** . Pour faire en sorte que les rôles ou les fonctionnalités soient supprimés, définissez cette propriété sur **Absent** . La valeur par défaut est **Present** . |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

La configuration suivante garantit que les fonctionnalités **Serveur Web** (IIS) et **Serveur SMTP** , et toutes leurs sous-fonctionnalités, sont installées.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
