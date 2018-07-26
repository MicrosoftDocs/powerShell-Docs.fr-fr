---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Group DSC
ms.openlocfilehash: 68e0840eaeb116b92260ca697acd5796460a2909
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222069"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="34aff-103">Ressource Group DSC</span><span class="sxs-lookup"><span data-stu-id="34aff-103">DSC Group Resource</span></span>

> <span data-ttu-id="34aff-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="34aff-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="34aff-105">La ressource Group dans DSC Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="34aff-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="34aff-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34aff-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="34aff-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="34aff-107">Properties</span></span>

|  <span data-ttu-id="34aff-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="34aff-108">Property</span></span>  |  <span data-ttu-id="34aff-109">Description</span><span class="sxs-lookup"><span data-stu-id="34aff-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="34aff-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="34aff-110">GroupName</span></span>| <span data-ttu-id="34aff-111">Le nom du groupe pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="34aff-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="34aff-112">Credential</span><span class="sxs-lookup"><span data-stu-id="34aff-112">Credential</span></span>| <span data-ttu-id="34aff-113">Les informations d’identification devant être fournies pour accéder aux ressources distantes.</span><span class="sxs-lookup"><span data-stu-id="34aff-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="34aff-114">**Remarque** : Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit quand la configuration est exécutée sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="34aff-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="34aff-115">Description</span><span class="sxs-lookup"><span data-stu-id="34aff-115">Description</span></span>| <span data-ttu-id="34aff-116">La description du groupe.</span><span class="sxs-lookup"><span data-stu-id="34aff-116">The description of the group.</span></span>|
| <span data-ttu-id="34aff-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="34aff-117">Ensure</span></span>| <span data-ttu-id="34aff-118">Indique si le groupe existe.</span><span class="sxs-lookup"><span data-stu-id="34aff-118">Indicates if the group exists.</span></span> <span data-ttu-id="34aff-119">Définissez cette propriété sur Absent pour vous assurer que le groupe n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="34aff-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="34aff-120">Si vous la définissez sur Present (la valeur par défaut), vous pouvez vous assurer que le groupe existe.</span><span class="sxs-lookup"><span data-stu-id="34aff-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="34aff-121">Members</span><span class="sxs-lookup"><span data-stu-id="34aff-121">Members</span></span>| <span data-ttu-id="34aff-122">Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="34aff-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="34aff-123">La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="34aff-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="34aff-124">Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="34aff-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="34aff-125">Sinon, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="34aff-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="34aff-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="34aff-126">MembersToExclude</span></span>| <span data-ttu-id="34aff-127">Utilisez cette propriété pour supprimer des appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="34aff-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="34aff-128">La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="34aff-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="34aff-129">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="34aff-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="34aff-130">Sinon, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="34aff-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="34aff-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="34aff-131">MembersToInclude</span></span>| <span data-ttu-id="34aff-132">Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe.</span><span class="sxs-lookup"><span data-stu-id="34aff-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="34aff-133">La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="34aff-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="34aff-134">Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**.</span><span class="sxs-lookup"><span data-stu-id="34aff-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="34aff-135">Cela générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="34aff-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="34aff-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="34aff-136">DependsOn</span></span> | <span data-ttu-id="34aff-137">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="34aff-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="34aff-138">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"</span><span class="sxs-lookup"><span data-stu-id="34aff-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="34aff-139">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="34aff-139">Example 1</span></span>

<span data-ttu-id="34aff-140">L’exemple suivant montre comment s’assurer qu’un groupe nommé « TestGroup » est absent.</span><span class="sxs-lookup"><span data-stu-id="34aff-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="34aff-141">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="34aff-141">Example 2</span></span>

<span data-ttu-id="34aff-142">L’exemple suivant montre comment ajouter un utilisateur Active Directory au groupe Administrateurs local dans le cadre d’une build de laboratoire avec plusieurs ordinateurs où vous utilisez déjà un PSCredential pour le compte d’administrateur Local.</span><span class="sxs-lookup"><span data-stu-id="34aff-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="34aff-143">Comme il est également utilisé pour le compte d’administrateur de domaine (après la promotion de domaine), nous devons convertir ce PSCredential existant en informations d’identification conviviales du domaine.</span><span class="sxs-lookup"><span data-stu-id="34aff-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="34aff-144">Ensuite, nous pouvons ajouter un utilisateur de domaine au groupe Administrateurs local sur le serveur membre.</span><span class="sxs-lookup"><span data-stu-id="34aff-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

## <a name="example-3"></a><span data-ttu-id="34aff-145">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="34aff-145">Example 3</span></span>

<span data-ttu-id="34aff-146">L’exemple suivant montre comment faire en sorte qu’un groupe local, TigerTeamAdmins, situé sur le serveur TigerTeamSource.Contoso.Com, ne contienne pas le compte de domaine Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="34aff-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
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