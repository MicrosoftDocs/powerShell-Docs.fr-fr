---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource WindowsFeature dans DSC
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954626"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="9dca3-103">Ressource WindowsFeature dans DSC</span><span class="sxs-lookup"><span data-stu-id="9dca3-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="9dca3-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="9dca3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="9dca3-105">La ressource **WindowsFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="9dca3-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9dca3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dca3-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="9dca3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9dca3-107">Properties</span></span>

|<span data-ttu-id="9dca3-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="9dca3-108">Property</span></span> |<span data-ttu-id="9dca3-109">Description</span><span class="sxs-lookup"><span data-stu-id="9dca3-109">Description</span></span> |
|---|---|
|<span data-ttu-id="9dca3-110">Name</span><span class="sxs-lookup"><span data-stu-id="9dca3-110">Name</span></span> |<span data-ttu-id="9dca3-111">Indique le nom du rôle ou de la fonctionnalité dont vous voulez garantir l’ajout ou la suppression.</span><span class="sxs-lookup"><span data-stu-id="9dca3-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="9dca3-112">Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) et non du nom d’affichage du rôle ou de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="9dca3-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="9dca3-113">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="9dca3-113">Credential</span></span> |<span data-ttu-id="9dca3-114">Indique les informations d’identification à utiliser pour ajouter ou supprimer le rôle ou la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="9dca3-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="9dca3-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="9dca3-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="9dca3-116">Définissez cette propriété sur `$true` pour faire en sorte que l’état de toutes les sous-fonctionnalités nécessaires soit l’état de la fonctionnalité que vous spécifiez avec la propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="9dca3-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="9dca3-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="9dca3-117">LogPath</span></span> |<span data-ttu-id="9dca3-118">Indique le chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.</span><span class="sxs-lookup"><span data-stu-id="9dca3-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="9dca3-119">Source</span><span class="sxs-lookup"><span data-stu-id="9dca3-119">Source</span></span> |<span data-ttu-id="9dca3-120">Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9dca3-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9dca3-121">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="9dca3-121">Common properties</span></span>

|<span data-ttu-id="9dca3-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="9dca3-122">Property</span></span> |<span data-ttu-id="9dca3-123">Description</span><span class="sxs-lookup"><span data-stu-id="9dca3-123">Description</span></span> |
|---|---|
|<span data-ttu-id="9dca3-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9dca3-124">DependsOn</span></span> |<span data-ttu-id="9dca3-125">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="9dca3-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9dca3-126">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9dca3-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="9dca3-127">Ensure</span><span class="sxs-lookup"><span data-stu-id="9dca3-127">Ensure</span></span> |<span data-ttu-id="9dca3-128">Indique si le rôle ou la fonctionnalité sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="9dca3-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="9dca3-129">Pour faire en sorte que le rôle ou la fonctionnalité soient ajoutés, définissez cette propriété sur **Present**.</span><span class="sxs-lookup"><span data-stu-id="9dca3-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="9dca3-130">Pour faire en sorte que le rôle ou la fonctionnalité soient supprimés, définissez cette propriété sur **Absent**.</span><span class="sxs-lookup"><span data-stu-id="9dca3-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="9dca3-131">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="9dca3-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="9dca3-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9dca3-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="9dca3-133">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="9dca3-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="9dca3-134">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="9dca3-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="9dca3-135">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="9dca3-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="9dca3-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="9dca3-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```