---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,installation
title: Ressource WindowsFeature dans DSC
ms.openlocfilehash: b15b267c6898697816b386a381e5a6d59acd492a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464109"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="d53c1-103">Ressource WindowsFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="d53c1-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="d53c1-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d53c1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d53c1-105">La ressource **WindowsFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="d53c1-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d53c1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d53c1-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d53c1-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d53c1-107">Properties</span></span>

|<span data-ttu-id="d53c1-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="d53c1-108">Property</span></span> |<span data-ttu-id="d53c1-109">Description</span><span class="sxs-lookup"><span data-stu-id="d53c1-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d53c1-110">Name</span><span class="sxs-lookup"><span data-stu-id="d53c1-110">Name</span></span> |<span data-ttu-id="d53c1-111">Indique le nom du rôle ou de la fonctionnalité dont vous voulez garantir l’ajout ou la suppression.</span><span class="sxs-lookup"><span data-stu-id="d53c1-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="d53c1-112">Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) et non du nom d’affichage du rôle ou de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d53c1-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="d53c1-113">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="d53c1-113">Credential</span></span> |<span data-ttu-id="d53c1-114">Indique les informations d’identification à utiliser pour ajouter ou supprimer le rôle ou la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d53c1-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="d53c1-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="d53c1-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="d53c1-116">Définissez cette propriété sur `$true` pour faire en sorte que l’état de toutes les sous-fonctionnalités nécessaires soit l’état de la fonctionnalité que vous spécifiez avec la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="d53c1-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="d53c1-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="d53c1-117">LogPath</span></span> |<span data-ttu-id="d53c1-118">Indique le chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="d53c1-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d53c1-119">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="d53c1-119">Common properties</span></span>

|<span data-ttu-id="d53c1-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="d53c1-120">Property</span></span> |<span data-ttu-id="d53c1-121">Description</span><span class="sxs-lookup"><span data-stu-id="d53c1-121">Description</span></span> |
|---|---|
|<span data-ttu-id="d53c1-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d53c1-122">DependsOn</span></span> |<span data-ttu-id="d53c1-123">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="d53c1-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d53c1-124">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d53c1-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d53c1-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="d53c1-125">Ensure</span></span> |<span data-ttu-id="d53c1-126">Indique si le rôle ou la fonctionnalité sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="d53c1-126">Indicates if the role or feature is added.</span></span> <span data-ttu-id="d53c1-127">Pour faire en sorte que le rôle ou la fonctionnalité soient ajoutés, définissez cette propriété sur **Present**.</span><span class="sxs-lookup"><span data-stu-id="d53c1-127">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="d53c1-128">Pour faire en sorte que le rôle ou la fonctionnalité soient supprimés, définissez cette propriété sur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="d53c1-128">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="d53c1-129">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="d53c1-129">The default value is **Present**.</span></span> |
|<span data-ttu-id="d53c1-130">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d53c1-130">PsDscRunAsCredential</span></span> |<span data-ttu-id="d53c1-131">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="d53c1-131">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d53c1-132">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="d53c1-132">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d53c1-133">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="d53c1-133">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d53c1-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="d53c1-134">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
