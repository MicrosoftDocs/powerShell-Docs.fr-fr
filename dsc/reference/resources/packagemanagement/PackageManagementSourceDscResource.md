---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: Ressources DSC PackageManagementSource
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077583"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="eb103-103">Ressources DSC PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="eb103-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="eb103-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0 et Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="eb103-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="eb103-105">La ressource **PackageManagementSource** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’inscrire ou de désinscrire des sources de gestion des packages sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="eb103-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="eb103-106">**Les sources de gestion des packages inscrites de cette façon sont inscrites sous le contexte système et peuvent être utilisées par le compte système ou le moteur DSC.**</span><span class="sxs-lookup"><span data-stu-id="eb103-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="eb103-107">Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="eb103-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb103-108">Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.</span><span class="sxs-lookup"><span data-stu-id="eb103-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb103-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb103-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="eb103-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="eb103-110">Properties</span></span>

|  <span data-ttu-id="eb103-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="eb103-111">Property</span></span>  |  <span data-ttu-id="eb103-112">Description</span><span class="sxs-lookup"><span data-stu-id="eb103-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="eb103-113">Name</span><span class="sxs-lookup"><span data-stu-id="eb103-113">Name</span></span>| <span data-ttu-id="eb103-114">Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système.</span><span class="sxs-lookup"><span data-stu-id="eb103-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="eb103-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="eb103-115">ProviderName</span></span>| <span data-ttu-id="eb103-116">Spécifie le nom du fournisseur OneGet par le biais duquel vous pouvez interagir avec la source du package.</span><span class="sxs-lookup"><span data-stu-id="eb103-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="eb103-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="eb103-117">SourceLocation</span></span>| <span data-ttu-id="eb103-118">Spécifie l’URI de la source du package.</span><span class="sxs-lookup"><span data-stu-id="eb103-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="eb103-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="eb103-119">Ensure</span></span>| <span data-ttu-id="eb103-120">Détermine si la source du package doit être inscrite ou désinscrite.</span><span class="sxs-lookup"><span data-stu-id="eb103-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="eb103-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="eb103-121">InstallationPolicy</span></span>| <span data-ttu-id="eb103-122">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="eb103-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="eb103-123">Détermine si vous faites confiance à la source du package.</span><span class="sxs-lookup"><span data-stu-id="eb103-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="eb103-124">Valeurs possibles : Untrusted et Trusted.</span><span class="sxs-lookup"><span data-stu-id="eb103-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="eb103-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="eb103-125">SourceCredential</span></span>| <span data-ttu-id="eb103-126">Informations d’identification permettant l’accès au package sur une source distante.</span><span class="sxs-lookup"><span data-stu-id="eb103-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="eb103-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb103-127">Example</span></span>

<span data-ttu-id="eb103-128">Cet exemple inscrit la source du package http://nuget.org à l’aide de la ressource DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="eb103-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```