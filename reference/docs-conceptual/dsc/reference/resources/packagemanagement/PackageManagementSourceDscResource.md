---
ms.date: 07/15/2020
ms.topic: reference
title: Ressources DSC PackageManagementSource
description: Ressources DSC PackageManagementSource
ms.openlocfilehash: 495b6548ef86f639e93b914ec8bd8ea7818ff8dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142852"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="51cd3-103">Ressources DSC PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="51cd3-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="51cd3-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="51cd3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="51cd3-105">La ressource **PackageManagementSource** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’inscrire ou de désinscrire des sources de gestion des packages sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="51cd3-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="51cd3-106">**Les sources de gestion des packages inscrites de cette façon sont inscrites sous le contexte système et peuvent être utilisées par le compte système ou le moteur DSC.**</span><span class="sxs-lookup"><span data-stu-id="51cd3-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="51cd3-107">Cette ressource nécessite le module **PackageManagement** , qui est disponible dans [PowerShell Gallery](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="51cd3-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51cd3-108">Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.</span><span class="sxs-lookup"><span data-stu-id="51cd3-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="51cd3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51cd3-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="51cd3-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="51cd3-110">Properties</span></span>

|<span data-ttu-id="51cd3-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="51cd3-111">Property</span></span> |<span data-ttu-id="51cd3-112">Description</span><span class="sxs-lookup"><span data-stu-id="51cd3-112">Description</span></span> |
|---|---|
|<span data-ttu-id="51cd3-113">Nom</span><span class="sxs-lookup"><span data-stu-id="51cd3-113">Name</span></span> |<span data-ttu-id="51cd3-114">Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système.</span><span class="sxs-lookup"><span data-stu-id="51cd3-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="51cd3-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="51cd3-115">ProviderName</span></span> |<span data-ttu-id="51cd3-116">Spécifie le nom du fournisseur OneGet par le biais duquel vous pouvez interagir avec la source du package.</span><span class="sxs-lookup"><span data-stu-id="51cd3-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="51cd3-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="51cd3-117">SourceLocation</span></span> |<span data-ttu-id="51cd3-118">Spécifie l’URI de la source du package.</span><span class="sxs-lookup"><span data-stu-id="51cd3-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="51cd3-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="51cd3-119">InstallationPolicy</span></span> |<span data-ttu-id="51cd3-120">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="51cd3-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="51cd3-121">Détermine si vous faites confiance à la source du package.</span><span class="sxs-lookup"><span data-stu-id="51cd3-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="51cd3-122">Valeurs possibles : **Untrusted** ou **Trusted** .</span><span class="sxs-lookup"><span data-stu-id="51cd3-122">One of: **Untrusted** or **Trusted** .</span></span> |
|<span data-ttu-id="51cd3-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="51cd3-123">SourceCredential</span></span> |<span data-ttu-id="51cd3-124">Informations d’identification permettant l’accès au package sur une source distante.</span><span class="sxs-lookup"><span data-stu-id="51cd3-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="51cd3-125">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="51cd3-125">Common properties</span></span>

|<span data-ttu-id="51cd3-126">Propriété</span><span class="sxs-lookup"><span data-stu-id="51cd3-126">Property</span></span> |<span data-ttu-id="51cd3-127">Description</span><span class="sxs-lookup"><span data-stu-id="51cd3-127">Description</span></span> |
|---|---|
|<span data-ttu-id="51cd3-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="51cd3-128">DependsOn</span></span> |<span data-ttu-id="51cd3-129">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="51cd3-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51cd3-130">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="51cd3-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="51cd3-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="51cd3-131">Ensure</span></span> |<span data-ttu-id="51cd3-132">Détermine si la source du package doit être inscrite ou désinscrite.</span><span class="sxs-lookup"><span data-stu-id="51cd3-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="51cd3-133">La valeur par défaut est **Present** .</span><span class="sxs-lookup"><span data-stu-id="51cd3-133">The default value is **Present** .</span></span> |
|<span data-ttu-id="51cd3-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="51cd3-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="51cd3-135">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="51cd3-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="51cd3-136">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="51cd3-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="51cd3-137">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="51cd3-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="51cd3-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="51cd3-138">Example</span></span>

<span data-ttu-id="51cd3-139">Cet exemple inscrit la source du package `https://nuget.org` à l’aide de la ressource DSC **PackageManagementSource** .</span><span class="sxs-lookup"><span data-stu-id="51cd3-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
