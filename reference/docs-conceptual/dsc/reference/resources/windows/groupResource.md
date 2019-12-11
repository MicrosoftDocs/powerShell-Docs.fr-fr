---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource Group DSC
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954656"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="2e226-103">Ressource Group DSC</span><span class="sxs-lookup"><span data-stu-id="2e226-103">DSC Group Resource</span></span>

> <span data-ttu-id="2e226-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="2e226-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="2e226-105">La ressource **Group** dans DSC Windows PowerShell propose un mécanisme qui permet de gérer des groupes locaux sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="2e226-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e226-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e226-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2e226-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2e226-107">Properties</span></span>

|<span data-ttu-id="2e226-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="2e226-108">Property</span></span> |<span data-ttu-id="2e226-109">Description</span><span class="sxs-lookup"><span data-stu-id="2e226-109">Description</span></span> |
|---|---|
|<span data-ttu-id="2e226-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="2e226-110">GroupName</span></span> |<span data-ttu-id="2e226-111">Le nom du groupe pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="2e226-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="2e226-112">Credential</span><span class="sxs-lookup"><span data-stu-id="2e226-112">Credential</span></span> |<span data-ttu-id="2e226-113">Les informations d’identification devant être fournies pour accéder aux ressources distantes.</span><span class="sxs-lookup"><span data-stu-id="2e226-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="2e226-114">Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit quand la configuration est exécutée sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="2e226-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="2e226-115">Description</span><span class="sxs-lookup"><span data-stu-id="2e226-115">Description</span></span> |<span data-ttu-id="2e226-116">La description du groupe.</span><span class="sxs-lookup"><span data-stu-id="2e226-116">The description of the group.</span></span> |
|<span data-ttu-id="2e226-117">Members</span><span class="sxs-lookup"><span data-stu-id="2e226-117">Members</span></span> |<span data-ttu-id="2e226-118">Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2e226-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="2e226-119">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="2e226-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="2e226-120">Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="2e226-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="2e226-121">Sinon, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="2e226-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="2e226-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="2e226-122">MembersToExclude</span></span> |<span data-ttu-id="2e226-123">Utilisez cette propriété pour supprimer des appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="2e226-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="2e226-124">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="2e226-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="2e226-125">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="2e226-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="2e226-126">Sinon, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="2e226-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="2e226-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="2e226-127">MembersToInclude</span></span> |<span data-ttu-id="2e226-128">Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="2e226-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="2e226-129">La valeur de cette propriété est un tableau de chaînes au format `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="2e226-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="2e226-130">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="2e226-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="2e226-131">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="2e226-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2e226-132">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="2e226-132">Common properties</span></span>

|<span data-ttu-id="2e226-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="2e226-133">Property</span></span> |<span data-ttu-id="2e226-134">Description</span><span class="sxs-lookup"><span data-stu-id="2e226-134">Description</span></span> |
|---|---|
|<span data-ttu-id="2e226-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2e226-135">DependsOn</span></span> |<span data-ttu-id="2e226-136">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="2e226-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2e226-137">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2e226-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2e226-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="2e226-138">Ensure</span></span> |<span data-ttu-id="2e226-139">Indique si le groupe existe.</span><span class="sxs-lookup"><span data-stu-id="2e226-139">Indicates if the group exists.</span></span> <span data-ttu-id="2e226-140">Définissez cette propriété sur **Absent** pour faire en sorte que le groupe n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="2e226-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="2e226-141">Définissez-la sur **Present** pour faire en sorte que le groupe existe.</span><span class="sxs-lookup"><span data-stu-id="2e226-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="2e226-142">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="2e226-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="2e226-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2e226-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="2e226-144">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="2e226-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="2e226-145">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="2e226-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="2e226-146">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="2e226-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="2e226-147">Exemple 1 : Vérifier que le groupe n’est pas présent</span><span class="sxs-lookup"><span data-stu-id="2e226-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="2e226-148">L’exemple suivant montre comment s’assurer qu’un groupe nommé « TestGroup » est absent.</span><span class="sxs-lookup"><span data-stu-id="2e226-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="2e226-149">Exemple 2 : Ajouter un utilisateur de domaine à un groupe local</span><span class="sxs-lookup"><span data-stu-id="2e226-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="2e226-150">L’exemple suivant montre comment ajouter un utilisateur Active Directory au groupe Administrateurs local dans le cadre d’une build de laboratoire avec plusieurs ordinateurs où vous utilisez déjà un PSCredential pour le compte d’administrateur Local.</span><span class="sxs-lookup"><span data-stu-id="2e226-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="2e226-151">Comme il est également utilisé pour le compte d’administrateur de domaine (après la promotion de domaine), nous devons convertir ce PSCredential existant en informations d’identification conviviales du domaine.</span><span class="sxs-lookup"><span data-stu-id="2e226-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="2e226-152">Ensuite, nous pouvons ajouter un utilisateur de domaine au groupe Administrateurs local sur le serveur membre.</span><span class="sxs-lookup"><span data-stu-id="2e226-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="2e226-153">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="2e226-153">Example 3</span></span>

<span data-ttu-id="2e226-154">L’exemple suivant montre comment faire en sorte qu’un groupe local, TigerTeamAdmins, situé sur le serveur TigerTeamSource.Contoso.Com, ne contienne pas le compte de domaine Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="2e226-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```