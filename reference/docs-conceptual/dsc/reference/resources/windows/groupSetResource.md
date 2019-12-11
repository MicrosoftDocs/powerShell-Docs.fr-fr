---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
description: Fournit un mécanisme permettant de gérer des groupes locaux sur le nœud cible.
title: Ressources GroupSet dans DSC
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953176"
---
# <a name="dsc-groupset-resource"></a>Ressources GroupSet dans DSC

> S’applique à : Windows PowerShell 5.x

La ressource **GroupSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible. Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la ressource [Group resource](groupResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.

Utilisez cette ressource quand vous souhaitez ajouter ou supprimer la même liste de membres dans plusieurs groupes, supprimer plusieurs groupes, ou ajouter plusieurs groupes avec la même liste de membres.

## <a name="syntax"></a>Syntaxe

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|GroupName |Noms des groupes pour lesquels vous souhaitez garantir un état spécifique. |
|Members |Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés. La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`. Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**. Cela générera une erreur. |
|Description |La description du groupe. |
|MembersToInclude |Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe. La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`. Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**. Cela générera une erreur. |
|MembersToExclude |Utilisez cette propriété pour supprimer des membres de l’appartenance existante des groupes. La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`. Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**. Cela générera une erreur. |
|Credential |Les informations d’identification devant être fournies pour accéder aux ressources distantes. Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si les groupes existent. Définissez cette propriété sur **Absent** pour faire en sorte que les groupes n’existent pas. La valeur **Present** garantit l’existence du groupe. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example-1-ensuring-groups-are-present"></a>Exemple 1 : S’assurer que des groupes sont présents

L’exemple suivant montre comment s’assurer que les deux groupes « myGroup » et « myOtherGroup » sont présents.

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> Cet exemple utilise des informations d’identification en texte clair par souci de simplicité. Pour plus d’informations sur la façon de chiffrer des informations d’identification dans le fichier MOF de configuration, consultez [Sécurisation du fichier MOF](../../../pull-server/secureMOF.md).