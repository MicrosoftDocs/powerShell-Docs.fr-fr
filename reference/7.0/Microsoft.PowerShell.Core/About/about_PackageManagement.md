---
description: PackageManagement est un agrégateur pour les gestionnaires de packages de logiciels.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 5b4b42dfce03831da5cc317276e78e0777ff73d6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208193"
---
# <a name="about-packagemanagement"></a><span data-ttu-id="43038-104">À propos de PackageManagement</span><span class="sxs-lookup"><span data-stu-id="43038-104">About PackageManagement</span></span>

## <a name="short-description"></a><span data-ttu-id="43038-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="43038-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="43038-106">PackageManagement est un agrégateur pour les gestionnaires de packages de logiciels.</span><span class="sxs-lookup"><span data-stu-id="43038-106">PackageManagement is an aggregator for software package managers.</span></span>

## <a name="long-description"></a><span data-ttu-id="43038-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="43038-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="43038-108">La fonctionnalité PackageManagement a été introduite dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="43038-108">PackageManagement functionality was introduced in Windows PowerShell 5.0.</span></span>

<span data-ttu-id="43038-109">PackageManagement est une interface unifiée pour les systèmes de gestion des packages logiciels ; vous pouvez exécuter les applets de commande PackageManagement pour effectuer des tâches de détection, d’installation et d’inventaire de logiciels (gestion).</span><span class="sxs-lookup"><span data-stu-id="43038-109">PackageManagement is a unified interface for software package management systems; you can run PackageManagement cmdlets to perform software discovery, installation, and inventory (SDII) tasks.</span></span> <span data-ttu-id="43038-110">Quelle que soit la technologie d’installation sous-jacente, vous pouvez exécuter les applets de commande courantes dans le module PackageManagement pour rechercher, installer ou désinstaller des packages. Ajouter, supprimer et interroger des dépôts de packages ; et exécuter des requêtes sur un ordinateur pour déterminer quels packages logiciels sont installés.</span><span class="sxs-lookup"><span data-stu-id="43038-110">Regardless of the underlying installation technology, you can run the common cmdlets in the PackageManagement module to search for, install, or uninstall packages; add, remove, and query package repositories; and run queries on a computer to determine which software packages are installed.</span></span>

<span data-ttu-id="43038-111">PackageManagement prend en charge un modèle de plug-in flexible qui permet la prise en charge d’autres systèmes de gestion de packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="43038-111">PackageManagement supports a flexible plug-in model that enables support for other software package management systems.</span></span>

<span data-ttu-id="43038-112">Le module PackageManagement est inclus dans Windows PowerShell 5,0 et versions ultérieures de PowerShell, et fonctionne sur trois niveaux de la structure de gestion des packages : les fournisseurs de package, les sources de package et les packages eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="43038-112">The PackageManagement module is included with Windows PowerShell 5.0 and later releases of PowerShell, and works on three levels of package management structure: package providers, package sources, and the packages themselves.</span></span> <span data-ttu-id="43038-113">Nous allons définir des termes :</span><span class="sxs-lookup"><span data-stu-id="43038-113">Let us define some terms:</span></span>

- <span data-ttu-id="43038-114">Gestionnaire de package : système de gestion des packages logicielles.</span><span class="sxs-lookup"><span data-stu-id="43038-114">Package manager: Software package management system.</span></span> <span data-ttu-id="43038-115">En termes de PackageManagement, il s’agit d’un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="43038-115">In PackageManagement terms, this is a package provider.</span></span>
- <span data-ttu-id="43038-116">Fournisseur de package : terme PackageManagement pour un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="43038-116">Package provider: PackageManagement term for a package manager.</span></span> <span data-ttu-id="43038-117">Les exemples peuvent inclure des Windows Installer, du chocolat et d’autres.</span><span class="sxs-lookup"><span data-stu-id="43038-117">Examples can include Windows Installer, Chocolatey, and others.</span></span>
- <span data-ttu-id="43038-118">Source du package : URL, dossier local ou dossier partagé sur le réseau que vous configurez en tant que référentiel à l’aide des fournisseurs de package.</span><span class="sxs-lookup"><span data-stu-id="43038-118">Package source: A URL, local folder, or network shared folder that you configure package providers to use as a repository.</span></span>
- <span data-ttu-id="43038-119">Package : élément logiciel géré par un fournisseur de package et stocké dans une source de package spécifique.</span><span class="sxs-lookup"><span data-stu-id="43038-119">Package: A piece of software that a package provider manages, and that is stored in a specific package source.</span></span>

<span data-ttu-id="43038-120">Le module PackageManagement comprend les applets de commande suivantes.</span><span class="sxs-lookup"><span data-stu-id="43038-120">The PackageManagement module includes the following cmdlets.</span></span> <span data-ttu-id="43038-121">Pour plus d’informations, consultez l’aide de [PackageManagement](/powershell/module/packagemanagement) .</span><span class="sxs-lookup"><span data-stu-id="43038-121">For more information, see the [PackageManagement](/powershell/module/packagemanagement) help.</span></span>

- <span data-ttu-id="43038-122">`Get-PackageProvider`: Retourne la liste des fournisseurs de packages qui sont connectés à PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="43038-122">`Get-PackageProvider`: Returns a list of package providers that are  connected to PackageManagement.</span></span>
- <span data-ttu-id="43038-123">`Get-PackageSource`: Obtient la liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="43038-123">`Get-PackageSource`: Gets a list of package sources that are registered for a package provider.</span></span>
- <span data-ttu-id="43038-124">`Register-PackageSource`: Ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="43038-124">`Register-PackageSource`: Adds a package source for a specified package provider.</span></span>
- <span data-ttu-id="43038-125">`Set-PackageSource`: Définit les propriétés sur une source de package existante.</span><span class="sxs-lookup"><span data-stu-id="43038-125">`Set-PackageSource`: Sets properties on an existing package source.</span></span>
- <span data-ttu-id="43038-126">`Unregister-PackageSource`: Supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="43038-126">`Unregister-PackageSource`: Removes a registered package source.</span></span>
- <span data-ttu-id="43038-127">`Get-Package`: Retourne la liste des packages de logiciels installés.</span><span class="sxs-lookup"><span data-stu-id="43038-127">`Get-Package`: Returns a list of installed software packages.</span></span>
- <span data-ttu-id="43038-128">`Find-Package`: Recherche les packages de logiciels dans les sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="43038-128">`Find-Package`: Finds software packages in available package sources.</span></span>
- <span data-ttu-id="43038-129">`Install-Package`: Installe un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="43038-129">`Install-Package`: Installs one or more software packages.</span></span>
- <span data-ttu-id="43038-130">`Save-Package`: Enregistre les packages sur l’ordinateur local sans les installer.</span><span class="sxs-lookup"><span data-stu-id="43038-130">`Save-Package`: Saves packages to the local computer without installing them.</span></span>
- <span data-ttu-id="43038-131">`Uninstall-Package`: Désinstalle un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="43038-131">`Uninstall-Package`: Uninstalls one or more software packages.</span></span>

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a><span data-ttu-id="43038-132">Paramètres d’applet de commande dynamique et d’amorçage du fournisseur de package</span><span class="sxs-lookup"><span data-stu-id="43038-132">Package Provider Bootstrapping and Dynamic Cmdlet Parameters</span></span>

<span data-ttu-id="43038-133">Par défaut, PackageManagement est fourni avec un fournisseur de démarrage principal.</span><span class="sxs-lookup"><span data-stu-id="43038-133">By default, PackageManagement ships with a core bootstrap provider.</span></span> <span data-ttu-id="43038-134">Vous pouvez installer des fournisseurs de packages supplémentaires en fonction de vos besoins en amorceant les fournisseurs. autrement dit, réponse à une invite pour installer le fournisseur automatiquement à partir d’un service Web.</span><span class="sxs-lookup"><span data-stu-id="43038-134">You can install additional package providers as you need them by bootstrapping the providers; that is, responding to a prompt to install the provider automatically, from a web service.</span></span> <span data-ttu-id="43038-135">Vous pouvez spécifier un fournisseur de package avec n’importe quelle applet de commande PackageManagement. Si le fournisseur spécifié n’est pas disponible, PackageManagement vous invite à démarrer (ou à installer automatiquement) le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="43038-135">You can specify a package provider with any PackageManagement cmdlet; if the specified provider is not available, PackageManagement prompts you to bootstrap (or automatically install) the provider.</span></span> <span data-ttu-id="43038-136">Dans les exemples suivants, si le fournisseur de chocolat n’est pas déjà installé, le programme d’amorçage PackageManagement installe le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="43038-136">In the following examples, if the Chocolatey provider is not already installed, PackageManagement bootstrapping installs the provider.</span></span>

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

<span data-ttu-id="43038-137">Si le fournisseur de chocolat n’est pas déjà installé, lorsque vous exécutez la commande précédente, vous êtes invité à l’installer.</span><span class="sxs-lookup"><span data-stu-id="43038-137">If the Chocolatey provider is not already installed, when you run the preceding command, you are prompted to install it.</span></span>

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

<span data-ttu-id="43038-138">Si le fournisseur de chocolat n’est pas déjà installé, lorsque vous exécutez la commande précédente, le fournisseur est installé. Toutefois, étant donné que le paramètre ForceBootstrap a été ajouté à la commande, vous n’êtes pas invité à l’installer. le fournisseur et le package sont tous deux installés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="43038-138">If the Chocolatey provider is not already installed, when you run the preceding command, the provider is installed; but because the ForceBootstrap parameter has been added to the command, you are not prompted to install it; both the provider and the package are installed automatically.</span></span>

<span data-ttu-id="43038-139">Lorsque vous essayez d’installer un package, si le fournisseur de prise en charge n’est pas déjà installé et que vous n’ajoutez pas le paramètre ForceBootstrap à votre commande, PackageManagement vous invite à installer le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="43038-139">When you try to install a package, if you do not already have the supporting provider installed, and you do not add the ForceBootstrap parameter to your command, PackageManagement prompts you to install the provider.</span></span>

<span data-ttu-id="43038-140">La spécification d’un fournisseur de package dans votre commande PackageManagement peut rendre les paramètres dynamiques disponibles qui sont spécifiques à ce fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="43038-140">Specifying a package provider in your PackageManagement command can make dynamic parameters available that are specific to that package provider.</span></span> <span data-ttu-id="43038-141">Lorsque vous exécutez Get-Help pour une applet de commande PackageManagement spécifique, une liste de jeux de paramètres est retournée, en regroupant les paramètres dynamiques des fournisseurs de packages disponibles dans des jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="43038-141">When you run Get-Help for a specific PackageManagement cmdlet, a list of parameter sets are returned, grouping dynamic parameters for available package providers in separate parameter sets.</span></span>

<span data-ttu-id="43038-142">Plus d’informations sur le projet PackageManagement</span><span class="sxs-lookup"><span data-stu-id="43038-142">More Information About the PackageManagement Project</span></span>

<span data-ttu-id="43038-143">Pour plus d’informations sur le projet de développement PackageManagement ouvert, notamment sur la création d’un fournisseur de packages PackageManagement, consultez le projet PackageManagement sur GitHub à l’adresse https://oneget.org .</span><span class="sxs-lookup"><span data-stu-id="43038-143">For more information about the PackageManagement open development project, including how to create a PackageManagement package provider, see the PackageManagement project on GitHub at https://oneget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="43038-144">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="43038-144">SEE ALSO</span></span>

[<span data-ttu-id="43038-145">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="43038-145">Get-PackageProvider</span></span>](xref:PackageManagement.Get-PackageProvider)

[<span data-ttu-id="43038-146">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="43038-146">Get-PackageSource</span></span>](xref:PackageManagement.Get-PackageSource)

[<span data-ttu-id="43038-147">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="43038-147">Register-PackageSource</span></span>](xref:PackageManagement.Register-PackageSource)

[<span data-ttu-id="43038-148">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="43038-148">Set-PackageSource</span></span>](xref:PackageManagement.Set-PackageSource)

[<span data-ttu-id="43038-149">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="43038-149">Unregister-PackageSource</span></span>](xref:PackageManagement.Unregister-PackageSource)

[<span data-ttu-id="43038-150">Get-Package</span><span class="sxs-lookup"><span data-stu-id="43038-150">Get-Package</span></span>](xref:PackageManagement.Get-Package)

[<span data-ttu-id="43038-151">Find-Package</span><span class="sxs-lookup"><span data-stu-id="43038-151">Find-Package</span></span>](xref:PackageManagement.Find-Package)

[<span data-ttu-id="43038-152">Install-Package</span><span class="sxs-lookup"><span data-stu-id="43038-152">Install-Package</span></span>](xref:PackageManagement.Install-Package)

[<span data-ttu-id="43038-153">Save-Package</span><span class="sxs-lookup"><span data-stu-id="43038-153">Save-Package</span></span>](xref:PackageManagement.Save-Package)

[<span data-ttu-id="43038-154">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="43038-154">Uninstall-Package</span></span>](xref:PackageManagement.Uninstall-Package)
