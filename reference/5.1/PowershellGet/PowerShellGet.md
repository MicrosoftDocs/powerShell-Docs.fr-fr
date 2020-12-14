---
Download Help Link: https://go.microsoft.com/fwlink/?LinkId=393271
Help Version: 5.2.0.0
keywords: powershell,applet de commande
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 130582b1b9f18a8f6ada7c009c6d25a7dab75e46
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890710"
---
# <span data-ttu-id="da492-103">Module PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="da492-103">PowerShellGet Module</span></span>

## <span data-ttu-id="da492-104">Description</span><span class="sxs-lookup"><span data-stu-id="da492-104">Description</span></span>

<span data-ttu-id="da492-105">PowerShellGet est un module avec des commandes permettant de détecter, d’installer, de mettre à jour et de publier des artefacts PowerShell tels que des modules, des ressources DSC, des fonctionnalités de rôle et des scripts.</span><span class="sxs-lookup"><span data-stu-id="da492-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="da492-106">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="da492-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="da492-107">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="da492-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="da492-108">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="da492-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="da492-109">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da492-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="da492-110">Applets de commande PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="da492-110">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="da492-111">Find-Command</span><span class="sxs-lookup"><span data-stu-id="da492-111">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="da492-112">Recherche des commandes PowerShell dans des modules.</span><span class="sxs-lookup"><span data-stu-id="da492-112">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="da492-113">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="da492-113">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="da492-114">Recherche une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="da492-114">Finds a DSC resource.</span></span>

### [<span data-ttu-id="da492-115">Find-Module</span><span class="sxs-lookup"><span data-stu-id="da492-115">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="da492-116">Recherche les modules dans un référentiel qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="da492-116">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="da492-117">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="da492-117">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="da492-118">Recherche les capacités de rôle dans des modules.</span><span class="sxs-lookup"><span data-stu-id="da492-118">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="da492-119">Find-Script</span><span class="sxs-lookup"><span data-stu-id="da492-119">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="da492-120">Recherche un script.</span><span class="sxs-lookup"><span data-stu-id="da492-120">Finds a script.</span></span>

### [<span data-ttu-id="da492-121">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="da492-121">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="da492-122">Obtient une liste de modules sur l’ordinateur qui ont été installés par PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="da492-122">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="da492-123">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="da492-123">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="da492-124">Obtient un script installé.</span><span class="sxs-lookup"><span data-stu-id="da492-124">Gets an installed script.</span></span>

### [<span data-ttu-id="da492-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="da492-125">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="da492-126">Obtient les référentiels PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da492-126">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="da492-127">Install-Module</span><span class="sxs-lookup"><span data-stu-id="da492-127">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="da492-128">Télécharge un ou plusieurs modules à partir d’un référentiel et les installe sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="da492-128">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="da492-129">Install-Script</span><span class="sxs-lookup"><span data-stu-id="da492-129">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="da492-130">Installe un script.</span><span class="sxs-lookup"><span data-stu-id="da492-130">Installs a script.</span></span>

### [<span data-ttu-id="da492-131">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="da492-131">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="da492-132">Crée un fichier de script avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="da492-132">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="da492-133">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="da492-133">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="da492-134">Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="da492-134">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="da492-135">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="da492-135">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="da492-136">Publie un script.</span><span class="sxs-lookup"><span data-stu-id="da492-136">Publishes a script.</span></span>

### [<span data-ttu-id="da492-137">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="da492-137">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="da492-138">Inscrit un référentiel PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da492-138">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="da492-139">Save-Module</span><span class="sxs-lookup"><span data-stu-id="da492-139">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="da492-140">Enregistre un module et ses dépendances sur l’ordinateur local, mais n’installe pas le module.</span><span class="sxs-lookup"><span data-stu-id="da492-140">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="da492-141">Save-Script</span><span class="sxs-lookup"><span data-stu-id="da492-141">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="da492-142">Enregistre un script.</span><span class="sxs-lookup"><span data-stu-id="da492-142">Saves a script.</span></span>

### [<span data-ttu-id="da492-143">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="da492-143">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="da492-144">Définit des valeurs pour un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="da492-144">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="da492-145">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="da492-145">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="da492-146">Valide un bloc de commentaires pour un script.</span><span class="sxs-lookup"><span data-stu-id="da492-146">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="da492-147">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="da492-147">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="da492-148">Désinstalle un module.</span><span class="sxs-lookup"><span data-stu-id="da492-148">Uninstalls a module.</span></span>

### [<span data-ttu-id="da492-149">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="da492-149">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="da492-150">Désinstalle un script.</span><span class="sxs-lookup"><span data-stu-id="da492-150">Uninstalls a script.</span></span>

### [<span data-ttu-id="da492-151">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="da492-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="da492-152">Annule l’enregistrement d’un référentiel.</span><span class="sxs-lookup"><span data-stu-id="da492-152">Unregisters a repository.</span></span>

### [<span data-ttu-id="da492-153">Update-Module</span><span class="sxs-lookup"><span data-stu-id="da492-153">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="da492-154">Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="da492-154">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="da492-155">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="da492-155">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="da492-156">Met à jour un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="da492-156">Updates a module manifest file.</span></span>

### [<span data-ttu-id="da492-157">Update-Script</span><span class="sxs-lookup"><span data-stu-id="da492-157">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="da492-158">Met à jour un script.</span><span class="sxs-lookup"><span data-stu-id="da492-158">Updates a script.</span></span>

### [<span data-ttu-id="da492-159">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="da492-159">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="da492-160">Met à jour les informations d’un script.</span><span class="sxs-lookup"><span data-stu-id="da492-160">Updates information for a script.</span></span>
