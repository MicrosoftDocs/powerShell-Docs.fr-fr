---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 0d4e5e26184558055a17f99bd5321aaf3f3789f7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99597982"
---
# <span data-ttu-id="0d5f3-102">Module PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="0d5f3-102">PowerShellGet Module</span></span>

## <span data-ttu-id="0d5f3-103">Description</span><span class="sxs-lookup"><span data-stu-id="0d5f3-103">Description</span></span>

<span data-ttu-id="0d5f3-104">PowerShellGet est un module avec des commandes permettant de détecter, d’installer, de mettre à jour et de publier des artefacts PowerShell tels que des modules, des ressources DSC, des fonctionnalités de rôle et des scripts.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-104">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d5f3-105">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="0d5f3-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0d5f3-106">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0d5f3-107">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="0d5f3-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0d5f3-108">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0d5f3-109">Applets de commande PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="0d5f3-109">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="0d5f3-110">Find-Command</span><span class="sxs-lookup"><span data-stu-id="0d5f3-110">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="0d5f3-111">Recherche des commandes PowerShell dans des modules.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-111">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="0d5f3-112">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="0d5f3-112">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="0d5f3-113">Recherche les ressources de configuration d’état souhaité (DSC).</span><span class="sxs-lookup"><span data-stu-id="0d5f3-113">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="0d5f3-114">Find-Module</span><span class="sxs-lookup"><span data-stu-id="0d5f3-114">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="0d5f3-115">Recherche les modules dans un référentiel qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-115">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="0d5f3-116">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="0d5f3-116">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="0d5f3-117">Recherche les capacités de rôle dans des modules.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-117">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="0d5f3-118">Find-Script</span><span class="sxs-lookup"><span data-stu-id="0d5f3-118">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="0d5f3-119">Recherche un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-119">Finds a script.</span></span>

### [<span data-ttu-id="0d5f3-120">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="0d5f3-120">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="0d5f3-121">Obtient une liste de modules sur l’ordinateur qui ont été installés par PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-121">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="0d5f3-122">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="0d5f3-122">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="0d5f3-123">Obtient un script installé.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-123">Gets an installed script.</span></span>

### [<span data-ttu-id="0d5f3-124">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0d5f3-124">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="0d5f3-125">Obtient les référentiels PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-125">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="0d5f3-126">Install-Module</span><span class="sxs-lookup"><span data-stu-id="0d5f3-126">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="0d5f3-127">Télécharge un ou plusieurs modules à partir d’un référentiel et les installe sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-127">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="0d5f3-128">Install-Script</span><span class="sxs-lookup"><span data-stu-id="0d5f3-128">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="0d5f3-129">Installe un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-129">Installs a script.</span></span>

### [<span data-ttu-id="0d5f3-130">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0d5f3-130">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="0d5f3-131">Crée un fichier de script avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-131">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="0d5f3-132">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="0d5f3-132">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="0d5f3-133">Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-133">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="0d5f3-134">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0d5f3-134">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="0d5f3-135">Publie un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-135">Publishes a script.</span></span>

### [<span data-ttu-id="0d5f3-136">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0d5f3-136">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="0d5f3-137">Inscrit un référentiel PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-137">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="0d5f3-138">Save-Module</span><span class="sxs-lookup"><span data-stu-id="0d5f3-138">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="0d5f3-139">Enregistre un module et ses dépendances sur l’ordinateur local, mais n’installe pas le module.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-139">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="0d5f3-140">Save-Script</span><span class="sxs-lookup"><span data-stu-id="0d5f3-140">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="0d5f3-141">Enregistre un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-141">Saves a script.</span></span>

### [<span data-ttu-id="0d5f3-142">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0d5f3-142">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="0d5f3-143">Définit des valeurs pour un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-143">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="0d5f3-144">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0d5f3-144">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="0d5f3-145">Valide un bloc de commentaires pour un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-145">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="0d5f3-146">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="0d5f3-146">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="0d5f3-147">Désinstalle un module.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-147">Uninstalls a module.</span></span>

### [<span data-ttu-id="0d5f3-148">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="0d5f3-148">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="0d5f3-149">Désinstalle un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-149">Uninstalls a script.</span></span>

### [<span data-ttu-id="0d5f3-150">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0d5f3-150">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="0d5f3-151">Annule l’enregistrement d’un référentiel.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-151">Unregisters a repository.</span></span>

### [<span data-ttu-id="0d5f3-152">Update-Module</span><span class="sxs-lookup"><span data-stu-id="0d5f3-152">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="0d5f3-153">Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-153">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="0d5f3-154">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="0d5f3-154">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="0d5f3-155">Met à jour un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-155">Updates a module manifest file.</span></span>

### [<span data-ttu-id="0d5f3-156">Update-Script</span><span class="sxs-lookup"><span data-stu-id="0d5f3-156">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="0d5f3-157">Met à jour un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-157">Updates a script.</span></span>

### [<span data-ttu-id="0d5f3-158">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0d5f3-158">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="0d5f3-159">Met à jour les informations d’un script.</span><span class="sxs-lookup"><span data-stu-id="0d5f3-159">Updates information for a script.</span></span>
