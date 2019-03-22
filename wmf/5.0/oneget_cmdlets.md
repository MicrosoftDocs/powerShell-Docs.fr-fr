---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 042e9a30068d32dc5860255bdec960371121d866
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795094"
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="e2aff-102">Applets de commande PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e2aff-102">PackageManagement Cmdlets</span></span>

<span data-ttu-id="e2aff-103">Il s’agit du noyau de PackageManagement pour prendre en charge la découverte, l’installation et l’inventaire des logiciels.</span><span class="sxs-lookup"><span data-stu-id="e2aff-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="e2aff-104">Essayez les applets de commande pour effectuer ces opérations :</span><span class="sxs-lookup"><span data-stu-id="e2aff-104">Try out the cmdlets for these operations:</span></span>

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

<span data-ttu-id="e2aff-105">PackageManagement étant un module PowerShell, vous pouvez effectuer les opérations suivantes pour mettre à jour PackageManagement lui-même :</span><span class="sxs-lookup"><span data-stu-id="e2aff-105">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>

```powershell
Install-Module PackageManagement –Force
```

<span data-ttu-id="e2aff-106">Dans ce cas, vous devrez réaccéder à la session PowerShell pour basculer vers la nouvelle version de PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="e2aff-106">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[<span data-ttu-id="e2aff-107">Applet de commande Find-Package</span><span class="sxs-lookup"><span data-stu-id="e2aff-107">Find-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Find-Package)

<span data-ttu-id="e2aff-108">Cette applet de commande permet de détecter des packages logiciels dans les sources de packages disponibles à l’aide des fournisseurs de packages chargés.</span><span class="sxs-lookup"><span data-stu-id="e2aff-108">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[<span data-ttu-id="e2aff-109">Applet de commande Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e2aff-109">Find-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Find-PackageProvider)

<span data-ttu-id="e2aff-110">L’applet de commande `Find-PackageProvider` recherche les fournisseurs PackageManagement correspondants qui sont disponibles dans les sources de packages inscrites auprès de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="e2aff-110">The `Find-PackageProvider` cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="e2aff-111">Il s’agit de fournisseurs de packages disponibles pour l’installation avec l’applet de commande `Install-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="e2aff-111">These are package providers available for installation with the `Install-PackageProvider` cmdlet.</span></span> <span data-ttu-id="e2aff-112">Par défaut, cela comprend les modules disponibles dans PowerShell Gallery avec les balises « PackageManagement » et « Provider ».</span><span class="sxs-lookup"><span data-stu-id="e2aff-112">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span>

<span data-ttu-id="e2aff-113">`Find-PackageProvider` recherche également les fournisseurs PackageManagement correspondants qui sont disponibles dans le magasin d’objets blob Azure PackageManagement où nous utilisons le fournisseur de programme d’amorçage PackageManagement pour les rechercher et les installer.</span><span class="sxs-lookup"><span data-stu-id="e2aff-113">`Find-PackageProvider` also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[<span data-ttu-id="e2aff-114">Applet de commande Get-Package</span><span class="sxs-lookup"><span data-stu-id="e2aff-114">Get-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Get-Package)

<span data-ttu-id="e2aff-115">Cette applet de commande retourne une liste de tous les packages logiciels qui ont été installés à l’aide de PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="e2aff-115">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[<span data-ttu-id="e2aff-116">Applet de commande Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e2aff-116">Get-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageProvider)

<span data-ttu-id="e2aff-117">Vous pouvez inventorier les fournisseurs de packages qui sont chargés et prêts à être utilisés sur l’ordinateur local à l’aide de cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2aff-117">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[<span data-ttu-id="e2aff-118">Applet de commande Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e2aff-118">Get-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageSource)

<span data-ttu-id="e2aff-119">Cette applet de commande obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="e2aff-119">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[<span data-ttu-id="e2aff-120">Applet de commande Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e2aff-120">Import-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Import-PackageProvider)

<span data-ttu-id="e2aff-121">Cette applet de commande ajoute des packages Package Management à la session active.</span><span class="sxs-lookup"><span data-stu-id="e2aff-121">This cmdlet adds Package Management package providers to the current session.</span></span>

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[<span data-ttu-id="e2aff-122">Applet de commande Install-Package</span><span class="sxs-lookup"><span data-stu-id="e2aff-122">Install-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Install-Package)

<span data-ttu-id="e2aff-123">Cette applet de commande permet d’installer des packages logiciels dans les sources de packages disponibles à l’aide des fournisseurs de packages chargés.</span><span class="sxs-lookup"><span data-stu-id="e2aff-123">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[<span data-ttu-id="e2aff-124">Applet de commande Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e2aff-124">Install-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Install-PackageProvider)

<span data-ttu-id="e2aff-125">Cette applet de commande installe un ou plusieurs fournisseurs de packages PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="e2aff-125">This cmdlet installs one or more Package Management package providers.</span></span>

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[<span data-ttu-id="e2aff-126">Applet de commande Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e2aff-126">Register-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Register-PackageSource)

<span data-ttu-id="e2aff-127">Cette applet de commande ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="e2aff-127">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="e2aff-128">Chaque fournisseur PackageManagement peut avoir une ou plusieurs sources de logiciels, ou dépôts.</span><span class="sxs-lookup"><span data-stu-id="e2aff-128">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="e2aff-129">PackageManagement fournit des applets de commande PowerShell pour ajouter/supprimer/interroger la source.</span><span class="sxs-lookup"><span data-stu-id="e2aff-129">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="e2aff-130">Par exemple, vous pouvez inscrire une source de package pour le fournisseur NuGet :</span><span class="sxs-lookup"><span data-stu-id="e2aff-130">For example, you can register a package source for the NuGet provider:</span></span>

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[<span data-ttu-id="e2aff-131">Applet de commande Save-Package</span><span class="sxs-lookup"><span data-stu-id="e2aff-131">Save-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Save-Package)

<span data-ttu-id="e2aff-132">Cette applet de commande enregistre des packages sur l’ordinateur local sans les installer.</span><span class="sxs-lookup"><span data-stu-id="e2aff-132">This cmdlet saves packages to the local computer without installing them.</span></span>

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[<span data-ttu-id="e2aff-133">Applet de commande Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e2aff-133">Set-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Set-PackageSource)

<span data-ttu-id="e2aff-134">Cette applet de commande modifie les informations relatives à une source de package existante.</span><span class="sxs-lookup"><span data-stu-id="e2aff-134">This cmdlet changes information about an existing package source.</span></span>

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[<span data-ttu-id="e2aff-135">Applet de commande Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="e2aff-135">Uninstall-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Uninstall-Package)

<span data-ttu-id="e2aff-136">Cette applet de commande désinstalle des packages installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e2aff-136">This cmdlet uninstalls packages installed on the local computer.</span></span>

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[<span data-ttu-id="e2aff-137">Applet de commande Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e2aff-137">Unregister-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```