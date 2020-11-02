---
ms.date: 07/17/2020
ms.topic: reference
title: Ressource nxGroup dans DSC pour Linux
description: Ressource nxGroup dans DSC pour Linux
ms.openlocfilehash: 3544bee763c0a4456002f9a02fde38de5d4fb65c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664262"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="e95aa-103">Ressource nxGroup dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="e95aa-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="e95aa-104">La ressource **nxGroup** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="e95aa-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e95aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e95aa-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="e95aa-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e95aa-106">Properties</span></span>

|<span data-ttu-id="e95aa-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="e95aa-107">Property</span></span> |<span data-ttu-id="e95aa-108">Description</span><span class="sxs-lookup"><span data-stu-id="e95aa-108">Description</span></span> |
|---|---|
|<span data-ttu-id="e95aa-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="e95aa-109">GroupName</span></span> |<span data-ttu-id="e95aa-110">Spécifie le nom du groupe pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="e95aa-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="e95aa-111">Membres</span><span class="sxs-lookup"><span data-stu-id="e95aa-111">Members</span></span> |<span data-ttu-id="e95aa-112">Spécifie les membres qui constituent le groupe.</span><span class="sxs-lookup"><span data-stu-id="e95aa-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="e95aa-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="e95aa-113">MembersToInclude</span></span> |<span data-ttu-id="e95aa-114">Spécifie les utilisateurs qui doivent faire partie du groupe.</span><span class="sxs-lookup"><span data-stu-id="e95aa-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="e95aa-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="e95aa-115">MembersToExclude</span></span> |<span data-ttu-id="e95aa-116">Spécifie les utilisateurs qui ne doivent pas faire partie du groupe.</span><span class="sxs-lookup"><span data-stu-id="e95aa-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="e95aa-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="e95aa-117">PreferredGroupID</span></span> |<span data-ttu-id="e95aa-118">Définit l’ID de groupe à la valeur fournie, si possible.</span><span class="sxs-lookup"><span data-stu-id="e95aa-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="e95aa-119">Si l’ID de groupe est déjà utilisé, l’ID de groupe disponible suivant est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e95aa-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e95aa-120">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="e95aa-120">Common properties</span></span>

|<span data-ttu-id="e95aa-121">Propriété</span><span class="sxs-lookup"><span data-stu-id="e95aa-121">Property</span></span> |<span data-ttu-id="e95aa-122">Description</span><span class="sxs-lookup"><span data-stu-id="e95aa-122">Description</span></span> |
|---|---|
|<span data-ttu-id="e95aa-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e95aa-123">DependsOn</span></span> |<span data-ttu-id="e95aa-124">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="e95aa-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e95aa-125">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e95aa-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e95aa-126">Ensure</span><span class="sxs-lookup"><span data-stu-id="e95aa-126">Ensure</span></span> |<span data-ttu-id="e95aa-127">Détermine si l’existence du groupe doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="e95aa-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="e95aa-128">Définissez cette propriété sur **Present** pour vous assurer que le groupe existe.</span><span class="sxs-lookup"><span data-stu-id="e95aa-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="e95aa-129">Définissez la propriété sur **Absent** pour vous assurer que le groupe n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="e95aa-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="e95aa-130">La valeur par défaut est **Present** .</span><span class="sxs-lookup"><span data-stu-id="e95aa-130">The default value is **Present** .</span></span> |

## <a name="example"></a><span data-ttu-id="e95aa-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="e95aa-131">Example</span></span>

<span data-ttu-id="e95aa-132">L’exemple suivant vérifie que l’utilisateur 'monuser' existe et qu’il est membre du groupe 'DBusers'.</span><span class="sxs-lookup"><span data-stu-id="e95aa-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```
