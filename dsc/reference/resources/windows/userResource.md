---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource User dans DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047449"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="e4453-103">Ressource User dans DSC</span><span class="sxs-lookup"><span data-stu-id="e4453-103">DSC User Resource</span></span>

<span data-ttu-id="e4453-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4453-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e4453-105">La ressource **User** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des comptes d’utilisateur locaux sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="e4453-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4453-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4453-106">Syntax</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e4453-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e4453-107">Properties</span></span>

|  <span data-ttu-id="e4453-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="e4453-108">Property</span></span>  |  <span data-ttu-id="e4453-109">Description</span><span class="sxs-lookup"><span data-stu-id="e4453-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="e4453-110">UserName</span><span class="sxs-lookup"><span data-stu-id="e4453-110">UserName</span></span>| <span data-ttu-id="e4453-111">Indique le nom du compte pour lequel vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="e4453-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="e4453-112">Description</span><span class="sxs-lookup"><span data-stu-id="e4453-112">Description</span></span>| <span data-ttu-id="e4453-113">Indique la description que vous voulez utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e4453-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="e4453-114">Désactivé</span><span class="sxs-lookup"><span data-stu-id="e4453-114">Disabled</span></span>| <span data-ttu-id="e4453-115">Indique si le compte est activé.</span><span class="sxs-lookup"><span data-stu-id="e4453-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="e4453-116">Affectez la valeur `$true` à cette propriété pour vous assurer que ce compte est désactivé, ou `$false` pour vous assurer qu’il est activé.</span><span class="sxs-lookup"><span data-stu-id="e4453-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="e4453-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="e4453-117">Ensure</span></span>| <span data-ttu-id="e4453-118">Indique si le compte existe.</span><span class="sxs-lookup"><span data-stu-id="e4453-118">Indicates if the account exists.</span></span> <span data-ttu-id="e4453-119">Définissez cette propriété sur « Present » pour vous assurer que le compte existe, ou sur « Absent » pour vous assurer que le compte n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="e4453-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="e4453-120">FullName</span><span class="sxs-lookup"><span data-stu-id="e4453-120">FullName</span></span>| <span data-ttu-id="e4453-121">Représente une chaîne avec le nom complet que vous voulez utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e4453-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="e4453-122">Password</span><span class="sxs-lookup"><span data-stu-id="e4453-122">Password</span></span>| <span data-ttu-id="e4453-123">Indique le mot de passe que vous voulez utiliser pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="e4453-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="e4453-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="e4453-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="e4453-125">Indique si l’utilisateur peut modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e4453-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="e4453-126">Affectez la valeur `$true` à cette propriété pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou `$false` pour permettre à l’utilisateur de modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e4453-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="e4453-127">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="e4453-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="e4453-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="e4453-128">PasswordChangeRequired</span></span>| <span data-ttu-id="e4453-129">Indique si l’utilisateur doit changer de mot de passe à la prochaine connexion.</span><span class="sxs-lookup"><span data-stu-id="e4453-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="e4453-130">Affectez la valeur `$true` à cette propriété si l’utilisateur doit changer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e4453-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="e4453-131">La valeur par défaut est `$true`.</span><span class="sxs-lookup"><span data-stu-id="e4453-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="e4453-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="e4453-132">PasswordNeverExpires</span></span>| <span data-ttu-id="e4453-133">Indique si le mot de passe doit expirer.</span><span class="sxs-lookup"><span data-stu-id="e4453-133">Indicates if the password will expire.</span></span> <span data-ttu-id="e4453-134">Pour vous assurer que le mot de passe pour ce compte n’expire jamais, affectez la valeur `$true` à cette propriété, et affectez-lui la valeur `$false` si le mot de passe doit expirer.</span><span class="sxs-lookup"><span data-stu-id="e4453-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="e4453-135">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="e4453-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="e4453-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e4453-136">DependsOn</span></span> | <span data-ttu-id="e4453-137">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e4453-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e4453-138">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e4453-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="e4453-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4453-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```