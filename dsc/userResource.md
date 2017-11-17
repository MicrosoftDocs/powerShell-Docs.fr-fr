---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource User dans DSC
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
#<a name="dsc-user-resource"></a><span data-ttu-id="0fb9a-103">Ressource User dans DSC#</span><span class="sxs-lookup"><span data-stu-id="0fb9a-103">DSC User Resource#</span></span>

 
><span data-ttu-id="0fb9a-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0fb9a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="0fb9a-105">La ressource __User__ dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des comptes d’utilisateur locaux sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="0fb9a-106">Syntaxe##</span><span class="sxs-lookup"><span data-stu-id="0fb9a-106">Syntax##</span></span>

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

## <a name="properties"></a><span data-ttu-id="0fb9a-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0fb9a-107">Properties</span></span>
|  <span data-ttu-id="0fb9a-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="0fb9a-108">Property</span></span>  |  <span data-ttu-id="0fb9a-109">Description</span><span class="sxs-lookup"><span data-stu-id="0fb9a-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0fb9a-110">UserName</span><span class="sxs-lookup"><span data-stu-id="0fb9a-110">UserName</span></span>| <span data-ttu-id="0fb9a-111">Indique le nom du compte pour lequel vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-111">Indicates the account name for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="0fb9a-112">Description</span><span class="sxs-lookup"><span data-stu-id="0fb9a-112">Description</span></span>| <span data-ttu-id="0fb9a-113">Indique la description que vous voulez utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-113">Indicates the description you want to use for the user account.</span></span>| 
| <span data-ttu-id="0fb9a-114">Désactivé</span><span class="sxs-lookup"><span data-stu-id="0fb9a-114">Disabled</span></span>| <span data-ttu-id="0fb9a-115">Indique si le compte est activé.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="0fb9a-116">Définissez cette propriété sur __$true__ pour vous assurer que ce compte est désactivé, ou sur __$false__ pour vous assurer qu’il est activé.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="0fb9a-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="0fb9a-117">Ensure</span></span>| <span data-ttu-id="0fb9a-118">Indique si le compte existe.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-118">Indicates if the account exists.</span></span> <span data-ttu-id="0fb9a-119">Définissez cette propriété sur « Present » pour vous assurer que le compte existe, ou sur « Absent » pour vous assurer que le compte n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="0fb9a-120">FullName</span><span class="sxs-lookup"><span data-stu-id="0fb9a-120">FullName</span></span>| <span data-ttu-id="0fb9a-121">Représente une chaîne avec le nom complet que vous voulez utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-121">Represents a string with the full name you want to use for the user account.</span></span>| 
| <span data-ttu-id="0fb9a-122">Password</span><span class="sxs-lookup"><span data-stu-id="0fb9a-122">Password</span></span>| <span data-ttu-id="0fb9a-123">Indique le mot de passe que vous voulez utiliser pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-123">Indicates the password you want to use for this account.</span></span> | 
| <span data-ttu-id="0fb9a-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="0fb9a-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="0fb9a-125">Indique si l’utilisateur peut modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="0fb9a-126">Définissez cette propriété sur __$true__ pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou sur __$false__ pour permettre à l’utilisateur de modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="0fb9a-127">La valeur par défaut est __$false__.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-127">The default value is __$false__.</span></span>| 
| <span data-ttu-id="0fb9a-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="0fb9a-128">PasswordChangeRequired</span></span>| <span data-ttu-id="0fb9a-129">Indique si l’utilisateur doit changer de mot de passe à la prochaine connexion.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="0fb9a-130">Définissez cette propriété sur __$true__ si l’utilisateur doit changer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="0fb9a-131">La valeur par défaut est __$true__.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-131">The default value is __$true__.</span></span>| 
| <span data-ttu-id="0fb9a-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="0fb9a-132">PasswordNeverExpires</span></span>| <span data-ttu-id="0fb9a-133">Indique si le mot de passe doit expirer.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-133">Indicates if the password will expire.</span></span> <span data-ttu-id="0fb9a-134">Pour vous assurer que le mot de passe pour ce compte n’expire jamais, définissez cette propriété sur __$true__, et sur __$false__ si le mot de passe doit expirer.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="0fb9a-135">La valeur par défaut est __$false__.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-135">The default value is __$false__.</span></span>| 
| <span data-ttu-id="0fb9a-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0fb9a-136">DependsOn</span></span> | <span data-ttu-id="0fb9a-137">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0fb9a-138">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0fb9a-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="0fb9a-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fb9a-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

