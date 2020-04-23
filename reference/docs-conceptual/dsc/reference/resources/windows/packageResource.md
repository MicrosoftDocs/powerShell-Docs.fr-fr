---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource Package dans DSC
ms.openlocfilehash: efac07b4b051564cadd5aa1542a6afda6cd453ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953146"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="0f967-103">Ressource Package dans DSC</span><span class="sxs-lookup"><span data-stu-id="0f967-103">DSC Package Resource</span></span>

> <span data-ttu-id="0f967-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0f967-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="0f967-105">La ressource **Package** dans DSC Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages, tels que les packages Windows Installer et setup.exe, sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="0f967-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f967-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f967-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0f967-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0f967-107">Properties</span></span>

|<span data-ttu-id="0f967-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="0f967-108">Property</span></span> |<span data-ttu-id="0f967-109">Description</span><span class="sxs-lookup"><span data-stu-id="0f967-109">Description</span></span> |
|---|---|
|<span data-ttu-id="0f967-110">Name</span><span class="sxs-lookup"><span data-stu-id="0f967-110">Name</span></span> |<span data-ttu-id="0f967-111">Indique le nom du package pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="0f967-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="0f967-112">Path</span><span class="sxs-lookup"><span data-stu-id="0f967-112">Path</span></span> |<span data-ttu-id="0f967-113">Indique le chemin où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="0f967-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="0f967-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="0f967-114">ProductId</span></span> |<span data-ttu-id="0f967-115">Indique l’ID de produit qui identifie le package de manière unique.</span><span class="sxs-lookup"><span data-stu-id="0f967-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="0f967-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f967-116">Arguments</span></span> |<span data-ttu-id="0f967-117">Chaîne d’arguments transmise telle quelle au package.</span><span class="sxs-lookup"><span data-stu-id="0f967-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="0f967-118">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="0f967-118">Credential</span></span> |<span data-ttu-id="0f967-119">Informations d’identification permettant l’accès au package sur une source distante.</span><span class="sxs-lookup"><span data-stu-id="0f967-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="0f967-120">Cette propriété n’est pas utilisée pour installer le package.</span><span class="sxs-lookup"><span data-stu-id="0f967-120">This property is not used to install the package.</span></span> <span data-ttu-id="0f967-121">Le package est toujours installé sur le système local.</span><span class="sxs-lookup"><span data-stu-id="0f967-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="0f967-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="0f967-122">LogPath</span></span> |<span data-ttu-id="0f967-123">Indique le chemin complet où vous souhaitez que le fournisseur enregistre un fichier journal pour installer ou désinstaller le package.</span><span class="sxs-lookup"><span data-stu-id="0f967-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="0f967-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="0f967-124">ReturnCode</span></span> |<span data-ttu-id="0f967-125">Indique le code de retour attendu.</span><span class="sxs-lookup"><span data-stu-id="0f967-125">Indicates the expected return code.</span></span> <span data-ttu-id="0f967-126">Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="0f967-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0f967-127">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="0f967-127">Common properties</span></span>

|<span data-ttu-id="0f967-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="0f967-128">Property</span></span> |<span data-ttu-id="0f967-129">Description</span><span class="sxs-lookup"><span data-stu-id="0f967-129">Description</span></span> |
|---|---|
|<span data-ttu-id="0f967-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0f967-130">DependsOn</span></span> |<span data-ttu-id="0f967-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="0f967-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0f967-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0f967-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0f967-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="0f967-133">Ensure</span></span> |<span data-ttu-id="0f967-134">Indique si le package est installé.</span><span class="sxs-lookup"><span data-stu-id="0f967-134">Indicates if the package is installed.</span></span> <span data-ttu-id="0f967-135">Définissez cette propriété sur **Absent** pour faire en sorte que le package ne soit pas installé (ou désinstallé, si le package est installé).</span><span class="sxs-lookup"><span data-stu-id="0f967-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="0f967-136">Définissez-la sur **Present** pour faire en sorte que le package soit installé.</span><span class="sxs-lookup"><span data-stu-id="0f967-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="0f967-137">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="0f967-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="0f967-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0f967-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="0f967-139">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="0f967-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0f967-140">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="0f967-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0f967-141">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="0f967-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f967-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f967-142">Example</span></span>

<span data-ttu-id="0f967-143">Cet exemple exécute le programme d’installation .msi qui se trouve dans le chemin spécifié et qui possède l’ID de produit spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f967-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```