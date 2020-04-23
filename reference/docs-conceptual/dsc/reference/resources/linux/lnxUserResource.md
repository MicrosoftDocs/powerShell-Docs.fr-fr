---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource nxUser dans DSC pour Linux
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954796"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="c7da7-103">Ressource nxUser dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="c7da7-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="c7da7-104">La ressource **nxUser** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des utilisateurs locaux sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="c7da7-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7da7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7da7-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="c7da7-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c7da7-106">Properties</span></span>

|<span data-ttu-id="c7da7-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="c7da7-107">Property</span></span> |<span data-ttu-id="c7da7-108">Indique le nom du compte pour lequel vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="c7da7-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="c7da7-109">UserName</span><span class="sxs-lookup"><span data-stu-id="c7da7-109">UserName</span></span> |<span data-ttu-id="c7da7-110">Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.</span><span class="sxs-lookup"><span data-stu-id="c7da7-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="c7da7-111">FullName</span><span class="sxs-lookup"><span data-stu-id="c7da7-111">FullName</span></span> |<span data-ttu-id="c7da7-112">Chaîne contenant le nom complet à utiliser pour le compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7da7-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="c7da7-113">Description</span><span class="sxs-lookup"><span data-stu-id="c7da7-113">Description</span></span> |<span data-ttu-id="c7da7-114">Description du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7da7-114">The description for the user account.</span></span> |
|<span data-ttu-id="c7da7-115">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="c7da7-115">Password</span></span> |<span data-ttu-id="c7da7-116">Hachage du mot de passe de l’utilisateur dans le format approprié pour l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="c7da7-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="c7da7-117">En règle générale, il s’agit d’un hachage salt SHA-256 ou SHA-512.</span><span class="sxs-lookup"><span data-stu-id="c7da7-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="c7da7-118">Pour Debian et Ubuntu Linux, cette valeur peut être générée avec la commande `mkpasswd`</span><span class="sxs-lookup"><span data-stu-id="c7da7-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="c7da7-119">Pour les autres versions de Linux, vous pouvez générer la valeur de hachage à l’aide de la méthode crypt disponible dans la bibliothèque de cryptage de Python.</span><span class="sxs-lookup"><span data-stu-id="c7da7-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="c7da7-120">Désactivé</span><span class="sxs-lookup"><span data-stu-id="c7da7-120">Disabled</span></span> |<span data-ttu-id="c7da7-121">Indique si le compte est activé.</span><span class="sxs-lookup"><span data-stu-id="c7da7-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="c7da7-122">Affectez la valeur `$true` à cette propriété pour vous assurer que ce compte est désactivé, ou `$false` pour vous assurer qu’il est activé.</span><span class="sxs-lookup"><span data-stu-id="c7da7-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="c7da7-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c7da7-123">PasswordChangeRequired</span></span> |<span data-ttu-id="c7da7-124">Indique si l’utilisateur peut modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c7da7-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="c7da7-125">Affectez la valeur `$true` à cette propriété pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou `$false` pour permettre à l’utilisateur de modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c7da7-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="c7da7-126">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="c7da7-126">The default value is `$false`.</span></span> <span data-ttu-id="c7da7-127">Cette propriété est évaluée uniquement si le compte d’utilisateur en cours de création n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="c7da7-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="c7da7-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="c7da7-128">HomeDirectory</span></span> |<span data-ttu-id="c7da7-129">Indique le répertoire racine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7da7-129">The home directory for the user.</span></span> |
|<span data-ttu-id="c7da7-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="c7da7-130">GroupID</span></span> |<span data-ttu-id="c7da7-131">Indique l’ID de groupe principal de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7da7-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c7da7-132">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="c7da7-132">Common properties</span></span>

|<span data-ttu-id="c7da7-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="c7da7-133">Property</span></span> |<span data-ttu-id="c7da7-134">Description</span><span class="sxs-lookup"><span data-stu-id="c7da7-134">Description</span></span> |
|---|---|
|<span data-ttu-id="c7da7-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c7da7-135">DependsOn</span></span> |<span data-ttu-id="c7da7-136">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="c7da7-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c7da7-137">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c7da7-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c7da7-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="c7da7-138">Ensure</span></span> |<span data-ttu-id="c7da7-139">Spécifie si le compte existe.</span><span class="sxs-lookup"><span data-stu-id="c7da7-139">Specifies whether the account exists.</span></span> <span data-ttu-id="c7da7-140">Définissez cette propriété sur **Present** pour faire en sorte que le compte existe ; définissez-la sur **Absent** pour faire en sorte qu’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="c7da7-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="c7da7-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7da7-141">Example</span></span>

<span data-ttu-id="c7da7-142">L’exemple suivant vérifie que l’utilisateur « monuser » existe et qu’il est membre du groupe « DBusers ».</span><span class="sxs-lookup"><span data-stu-id="c7da7-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
   nxUser UserExample{
      UserName = "monuser"
      Description = "Monitoring user"
      Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
      Ensure = "Present"
      HomeDirectory = "/home/monuser"
   }

   nxGroup GroupExample{
      GroupName = "DBusers"
      Ensure = "Present"
      MembersToInclude = "monuser"
      DependsOn = "[nxUser]UserExample"
   }
}
```