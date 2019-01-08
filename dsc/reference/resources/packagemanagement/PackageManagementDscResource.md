---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: Ressource DSC PackageManagement
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047367"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="1bebe-103">Ressource DSC PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1bebe-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="1bebe-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="1bebe-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="1bebe-105">La ressource **PackageManagement** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de gestion des packages sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="1bebe-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="1bebe-106">Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site [http://PowerShellGallery.com](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="1bebe-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bebe-107">Le module **PackageManagement** doit être au moins de version 1.1.7.0 pour que les informations de propriétés suivantes soient correctes.</span><span class="sxs-lookup"><span data-stu-id="1bebe-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="1bebe-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bebe-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="1bebe-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1bebe-109">Properties</span></span>

| <span data-ttu-id="1bebe-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="1bebe-110">Property</span></span> | <span data-ttu-id="1bebe-111">Description</span><span class="sxs-lookup"><span data-stu-id="1bebe-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="1bebe-112">Name</span><span class="sxs-lookup"><span data-stu-id="1bebe-112">Name</span></span>| <span data-ttu-id="1bebe-113">Spécifie le nom du package à installer ou à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="1bebe-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="1bebe-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="1bebe-114">AdditionalParameters</span></span>| <span data-ttu-id="1bebe-115">Table de hachage spécifique du fournisseur, contenant les paramètres passés à `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="1bebe-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="1bebe-116">Par exemple, pour le fournisseur NuGet, vous pouvez passer des paramètres supplémentaires tels que DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="1bebe-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="1bebe-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="1bebe-117">Ensure</span></span>| <span data-ttu-id="1bebe-118">Détermine si le package doit être installé ou désinstallé.</span><span class="sxs-lookup"><span data-stu-id="1bebe-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="1bebe-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1bebe-119">MaximumVersion</span></span>|<span data-ttu-id="1bebe-120">Spécifie la version maximale autorisée du package à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1bebe-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="1bebe-121">Si vous n’ajoutez pas ce paramètre, la ressource recherche la version disponible la plus récente du package.</span><span class="sxs-lookup"><span data-stu-id="1bebe-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="1bebe-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1bebe-122">MinimumVersion</span></span>|<span data-ttu-id="1bebe-123">Spécifie la version minimale autorisée du package à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1bebe-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="1bebe-124">Si vous n’ajoutez pas ce paramètre, la ressource recherche la version la plus élevée du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre _MaximumVersion_.</span><span class="sxs-lookup"><span data-stu-id="1bebe-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="1bebe-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="1bebe-125">ProviderName</span></span>| <span data-ttu-id="1bebe-126">Spécifie un nom de fournisseur de package auquel vous souhaitez limiter votre recherche de package.</span><span class="sxs-lookup"><span data-stu-id="1bebe-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="1bebe-127">Vous obtenez les noms des fournisseurs de package en exécutant l’applet de commande `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="1bebe-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="1bebe-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1bebe-128">RequiredVersion</span></span>| <span data-ttu-id="1bebe-129">Spécifie la version exacte du package à installer.</span><span class="sxs-lookup"><span data-stu-id="1bebe-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="1bebe-130">Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus récente du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre _MaximumVersion_.</span><span class="sxs-lookup"><span data-stu-id="1bebe-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="1bebe-131">Source</span><span class="sxs-lookup"><span data-stu-id="1bebe-131">Source</span></span>| <span data-ttu-id="1bebe-132">Spécifie le nom de la source du package où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="1bebe-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="1bebe-133">Il peut s’agir d’un URI ou d’une source inscrite avec `Register-PackageSource` ou une ressource DSC PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="1bebe-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="1bebe-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="1bebe-134">SourceCredential</span></span> | <span data-ttu-id="1bebe-135">Spécifie un compte d’utilisateur disposant des droits nécessaires pour installer un package pour une source ou un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="1bebe-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="1bebe-136">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1bebe-136">Additional Parameters</span></span>

<span data-ttu-id="1bebe-137">Le tableau suivant répertorie les options de la propriété AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="1bebe-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="1bebe-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="1bebe-138">Parameter</span></span> | <span data-ttu-id="1bebe-139">Description</span><span class="sxs-lookup"><span data-stu-id="1bebe-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="1bebe-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="1bebe-140">DestinationPath</span></span>| <span data-ttu-id="1bebe-141">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="1bebe-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="1bebe-142">Spécifie un emplacement de fichier où vous souhaitez installer le package.</span><span class="sxs-lookup"><span data-stu-id="1bebe-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="1bebe-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="1bebe-143">InstallationPolicy</span></span>| <span data-ttu-id="1bebe-144">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="1bebe-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="1bebe-145">Détermine si vous faites confiance à la source du package.</span><span class="sxs-lookup"><span data-stu-id="1bebe-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="1bebe-146">Valeurs possibles : `Untrusted` ou `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="1bebe-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="1bebe-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="1bebe-147">Example</span></span>

<span data-ttu-id="1bebe-148">Cet exemple installe le package NuGet **JQuery** et le module PowerShell **GistProvider** à l’aide de la ressource DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="1bebe-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="1bebe-149">Cet exemple vérifie d’abord que les sources de package nécessaires sont disponibles, puis définit l’état attendu des packages **JQuery** et **GistProvider** (NuGet et PowerShell, respectivement).</span><span class="sxs-lookup"><span data-stu-id="1bebe-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```