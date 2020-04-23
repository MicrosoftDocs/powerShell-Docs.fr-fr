---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource User dans DSC
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953006"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="96299-103">Ressource User dans DSC</span><span class="sxs-lookup"><span data-stu-id="96299-103">DSC User Resource</span></span>

> <span data-ttu-id="96299-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="96299-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="96299-105">La ressource **User** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des comptes d’utilisateur locaux sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="96299-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="96299-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96299-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="96299-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="96299-107">Properties</span></span>

|<span data-ttu-id="96299-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="96299-108">Property</span></span> |<span data-ttu-id="96299-109">Description</span><span class="sxs-lookup"><span data-stu-id="96299-109">Description</span></span> |
|---|---|
|<span data-ttu-id="96299-110">UserName</span><span class="sxs-lookup"><span data-stu-id="96299-110">UserName</span></span> |<span data-ttu-id="96299-111">Indique le nom du compte pour lequel vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="96299-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="96299-112">Description</span><span class="sxs-lookup"><span data-stu-id="96299-112">Description</span></span> |<span data-ttu-id="96299-113">Indique la description que vous voulez utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="96299-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="96299-114">Désactivé</span><span class="sxs-lookup"><span data-stu-id="96299-114">Disabled</span></span> |<span data-ttu-id="96299-115">Indique si le compte est activé.</span><span class="sxs-lookup"><span data-stu-id="96299-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="96299-116">Affectez la valeur `$true` à cette propriété pour vous assurer que ce compte est désactivé, ou `$false` pour vous assurer qu’il est activé.</span><span class="sxs-lookup"><span data-stu-id="96299-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="96299-117">FullName</span><span class="sxs-lookup"><span data-stu-id="96299-117">FullName</span></span> |<span data-ttu-id="96299-118">Représente une chaîne avec le nom complet que vous voulez utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="96299-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="96299-119">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="96299-119">Password</span></span> |<span data-ttu-id="96299-120">Indique le mot de passe que vous voulez utiliser pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="96299-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="96299-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="96299-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="96299-122">Indique si l’utilisateur peut modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="96299-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="96299-123">Affectez la valeur `$true` à cette propriété pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou `$false` pour permettre à l’utilisateur de modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="96299-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="96299-124">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="96299-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="96299-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="96299-125">PasswordChangeRequired</span></span> |<span data-ttu-id="96299-126">Indique si l’utilisateur doit changer de mot de passe à la prochaine connexion.</span><span class="sxs-lookup"><span data-stu-id="96299-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="96299-127">Affectez la valeur `$true` à cette propriété si l’utilisateur doit changer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="96299-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="96299-128">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="96299-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="96299-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="96299-129">PasswordNeverExpires</span></span> |<span data-ttu-id="96299-130">Indique si le mot de passe doit expirer.</span><span class="sxs-lookup"><span data-stu-id="96299-130">Indicates if the password will expire.</span></span> <span data-ttu-id="96299-131">Pour faire en sorte que le mot de passe de ce compte n’expire jamais, définissez cette propriété sur `$true`.</span><span class="sxs-lookup"><span data-stu-id="96299-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="96299-132">Définissez-la sur `$false` si le mot de passe doit expirer.</span><span class="sxs-lookup"><span data-stu-id="96299-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="96299-133">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="96299-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="96299-134">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="96299-134">Common properties</span></span>

|<span data-ttu-id="96299-135">Propriété</span><span class="sxs-lookup"><span data-stu-id="96299-135">Property</span></span> |<span data-ttu-id="96299-136">Description</span><span class="sxs-lookup"><span data-stu-id="96299-136">Description</span></span> |
|---|---|
|<span data-ttu-id="96299-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="96299-137">DependsOn</span></span> |<span data-ttu-id="96299-138">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="96299-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="96299-139">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="96299-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="96299-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="96299-140">Ensure</span></span> |<span data-ttu-id="96299-141">Indique si le compte existe.</span><span class="sxs-lookup"><span data-stu-id="96299-141">Indicates if the account exists.</span></span> <span data-ttu-id="96299-142">Définissez cette propriété sur **Present** pour faire en sorte que le compte existe ; définissez-la sur **Absent** pour faire en sorte qu’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="96299-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="96299-143">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="96299-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="96299-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="96299-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="96299-145">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="96299-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="96299-146">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="96299-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="96299-147">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="96299-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="96299-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="96299-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```