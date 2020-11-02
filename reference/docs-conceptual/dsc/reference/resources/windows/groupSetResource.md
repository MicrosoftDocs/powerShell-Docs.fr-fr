---
ms.date: 09/20/2019
ms.topic: reference
title: Ressources GroupSet dans DSC
description: Ressources GroupSet dans DSC
ms.openlocfilehash: a9d1803aca40ac3571d42a5fd762489c03ed274e
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142886"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="43358-103">Ressources GroupSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="43358-103">DSC GroupSet Resource</span></span>

> <span data-ttu-id="43358-104">S’applique à : Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="43358-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="43358-105">La ressource **GroupSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="43358-105">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="43358-106">Cette ressource est une [ressource composite](../../../resources/authoringResourceComposite.md) qui appelle la ressource [Group resource](groupResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="43358-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="43358-107">Utilisez cette ressource quand vous souhaitez ajouter ou supprimer la même liste de membres dans plusieurs groupes, supprimer plusieurs groupes, ou ajouter plusieurs groupes avec la même liste de membres.</span><span class="sxs-lookup"><span data-stu-id="43358-107">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="43358-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43358-108">Syntax</span></span>

```Syntax
GroupSet [string] #ResourceName
{
    GroupName = [string[]]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="43358-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="43358-109">Properties</span></span>

|<span data-ttu-id="43358-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="43358-110">Property</span></span> |<span data-ttu-id="43358-111">Description</span><span class="sxs-lookup"><span data-stu-id="43358-111">Description</span></span> |
|---|---|
|<span data-ttu-id="43358-112">GroupName</span><span class="sxs-lookup"><span data-stu-id="43358-112">GroupName</span></span> |<span data-ttu-id="43358-113">Noms des groupes pour lesquels vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="43358-113">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="43358-114">Membres</span><span class="sxs-lookup"><span data-stu-id="43358-114">Members</span></span> |<span data-ttu-id="43358-115">Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="43358-115">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="43358-116">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="43358-116">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="43358-117">Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude** .</span><span class="sxs-lookup"><span data-stu-id="43358-117">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="43358-118">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="43358-118">Doing so will generate an error.</span></span> |
|<span data-ttu-id="43358-119">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="43358-119">MembersToInclude</span></span> |<span data-ttu-id="43358-120">Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="43358-120">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="43358-121">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="43358-121">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="43358-122">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members** .</span><span class="sxs-lookup"><span data-stu-id="43358-122">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="43358-123">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="43358-123">Doing so will generate an error.</span></span> |
|<span data-ttu-id="43358-124">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="43358-124">MembersToExclude</span></span> |<span data-ttu-id="43358-125">Utilisez cette propriété pour supprimer des membres de l’appartenance existante des groupes.</span><span class="sxs-lookup"><span data-stu-id="43358-125">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="43358-126">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="43358-126">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="43358-127">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members** .</span><span class="sxs-lookup"><span data-stu-id="43358-127">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="43358-128">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="43358-128">Doing so will generate an error.</span></span> |
|<span data-ttu-id="43358-129">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="43358-129">Credential</span></span> |<span data-ttu-id="43358-130">Les informations d’identification devant être fournies pour accéder aux ressources distantes.</span><span class="sxs-lookup"><span data-stu-id="43358-130">The credentials required to access remote resources.</span></span> <span data-ttu-id="43358-131">Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="43358-131">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="43358-132">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="43358-132">Common properties</span></span>

|<span data-ttu-id="43358-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="43358-133">Property</span></span> |<span data-ttu-id="43358-134">Description</span><span class="sxs-lookup"><span data-stu-id="43358-134">Description</span></span> |
|---|---|
|<span data-ttu-id="43358-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="43358-135">DependsOn</span></span> |<span data-ttu-id="43358-136">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="43358-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="43358-137">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="43358-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="43358-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="43358-138">Ensure</span></span> |<span data-ttu-id="43358-139">Indique si les groupes existent.</span><span class="sxs-lookup"><span data-stu-id="43358-139">Indicates whether the groups exist.</span></span> <span data-ttu-id="43358-140">Définissez cette propriété sur **Absent** pour faire en sorte que les groupes n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="43358-140">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="43358-141">La valeur **Present** garantit l’existence du groupe.</span><span class="sxs-lookup"><span data-stu-id="43358-141">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="43358-142">La valeur par défaut est **Present** .</span><span class="sxs-lookup"><span data-stu-id="43358-142">The default value is **Present** .</span></span> |
|<span data-ttu-id="43358-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="43358-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="43358-144">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="43358-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="43358-145">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="43358-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="43358-146">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="43358-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="43358-147">Exemple 1 : S’assurer que les groupes sont présents</span><span class="sxs-lookup"><span data-stu-id="43358-147">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="43358-148">L’exemple suivant montre comment s’assurer que les deux groupes « myGroup » et « myOtherGroup » sont présents.</span><span class="sxs-lookup"><span data-stu-id="43358-148">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="43358-149">Cet exemple utilise des informations d’identification en texte clair par souci de simplicité.</span><span class="sxs-lookup"><span data-stu-id="43358-149">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="43358-150">Pour plus d’informations sur la façon de chiffrer des informations d’identification dans le fichier MOF de configuration, consultez [Sécurisation du fichier MOF](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="43358-150">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
