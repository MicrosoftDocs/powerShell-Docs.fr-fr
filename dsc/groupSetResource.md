---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: Fournit un mécanisme permettant de gérer des groupes locaux sur le nœud cible.
title: Ressources GroupSet dans DSC
ms.openlocfilehash: 6fa8e9637da896848e859dc60a42add12e973b34
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226115"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="4bd64-104">Ressources GroupSet dans DSC</span><span class="sxs-lookup"><span data-stu-id="4bd64-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="4bd64-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4bd64-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4bd64-106">La ressource **GroupSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="4bd64-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="4bd64-107">Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [Group resource](groupResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="4bd64-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="4bd64-108">Utilisez cette ressource quand vous souhaitez ajouter ou supprimer la même liste de membres dans plusieurs groupes, supprimer plusieurs groupes, ou ajouter plusieurs groupes avec la même liste de membres.</span><span class="sxs-lookup"><span data-stu-id="4bd64-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bd64-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bd64-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="4bd64-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4bd64-110">Properties</span></span>

|  <span data-ttu-id="4bd64-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="4bd64-111">Property</span></span>  |  <span data-ttu-id="4bd64-112">Description</span><span class="sxs-lookup"><span data-stu-id="4bd64-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="4bd64-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="4bd64-113">GroupName</span></span>| <span data-ttu-id="4bd64-114">Noms des groupes pour lesquels vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="4bd64-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="4bd64-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="4bd64-115">MembersToExclude</span></span>| <span data-ttu-id="4bd64-116">Utilisez cette propriété pour supprimer des membres de l’appartenance existante des groupes.</span><span class="sxs-lookup"><span data-stu-id="4bd64-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="4bd64-117">La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="4bd64-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="4bd64-118">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="4bd64-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4bd64-119">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="4bd64-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="4bd64-120">Credential</span><span class="sxs-lookup"><span data-stu-id="4bd64-120">Credential</span></span>| <span data-ttu-id="4bd64-121">Les informations d’identification devant être fournies pour accéder aux ressources distantes.</span><span class="sxs-lookup"><span data-stu-id="4bd64-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="4bd64-122">**Remarque** : Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="4bd64-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="4bd64-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="4bd64-123">Ensure</span></span>| <span data-ttu-id="4bd64-124">Indique si les groupes existent.</span><span class="sxs-lookup"><span data-stu-id="4bd64-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="4bd64-125">Affectez la valeur « Absent » à cette propriété pour vous assurer que les groupes n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="4bd64-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="4bd64-126">La valeur « Present » (valeur par défaut) permet de s’assurer que les groupes existent.</span><span class="sxs-lookup"><span data-stu-id="4bd64-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="4bd64-127">Members</span><span class="sxs-lookup"><span data-stu-id="4bd64-127">Members</span></span>| <span data-ttu-id="4bd64-128">Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4bd64-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="4bd64-129">La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="4bd64-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="4bd64-130">Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="4bd64-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="4bd64-131">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="4bd64-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="4bd64-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="4bd64-132">MembersToInclude</span></span>| <span data-ttu-id="4bd64-133">Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="4bd64-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="4bd64-134">La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="4bd64-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="4bd64-135">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="4bd64-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4bd64-136">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="4bd64-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="4bd64-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4bd64-137">DependsOn</span></span> | <span data-ttu-id="4bd64-138">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="4bd64-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4bd64-139">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"</span><span class="sxs-lookup"><span data-stu-id="4bd64-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="4bd64-140">Exemple 1 : S’assurer que les groupes sont présents</span><span class="sxs-lookup"><span data-stu-id="4bd64-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="4bd64-141">L’exemple suivant montre comment s’assurer que les deux groupes « myGroup » et « myOtherGroup » sont présents.</span><span class="sxs-lookup"><span data-stu-id="4bd64-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="4bd64-142">Cet exemple utilise des informations d’identification en texte clair par souci de simplicité.</span><span class="sxs-lookup"><span data-stu-id="4bd64-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="4bd64-143">Pour plus d’informations sur la façon de chiffrer des informations d’identification dans le fichier MOF de configuration, consultez [Sécurisation du fichier MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="4bd64-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>
