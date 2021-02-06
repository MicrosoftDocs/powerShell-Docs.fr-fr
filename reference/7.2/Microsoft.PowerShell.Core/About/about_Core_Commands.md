---
description: Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 1f023c5a66265f561ef6644afdc45cd0149f35b7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599169"
---
# <a name="about-core-commands"></a><span data-ttu-id="43366-103">À propos des commandes principales</span><span class="sxs-lookup"><span data-stu-id="43366-103">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="43366-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="43366-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="43366-105">Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43366-105">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="43366-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="43366-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="43366-107">PowerShell comprend un ensemble d’applets de commande spécialement conçues pour gérer les éléments des magasins de données exposés par les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43366-107">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="43366-108">Vous pouvez utiliser ces applets de commande de la même manière pour gérer tous les différents types de données que les fournisseurs mettent à votre disposition.</span><span class="sxs-lookup"><span data-stu-id="43366-108">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="43366-109">Pour plus d’informations sur les fournisseurs, tapez « obtenir-aide about_providers ».</span><span class="sxs-lookup"><span data-stu-id="43366-109">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="43366-110">Par exemple, vous pouvez utiliser l’applet de commande Get-ChildItem pour répertorier les fichiers dans un répertoire du système de fichiers, les clés sous une clé de registre ou les éléments qui sont exposés par un fournisseur que vous écrivez ou téléchargez.</span><span class="sxs-lookup"><span data-stu-id="43366-110">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="43366-111">La liste suivante répertorie les applets de commande PowerShell conçues pour être utilisées avec les fournisseurs :</span><span class="sxs-lookup"><span data-stu-id="43366-111">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="43366-112">Applets de commande ChildItem</span><span class="sxs-lookup"><span data-stu-id="43366-112">ChildItem cmdlets</span></span>

- <span data-ttu-id="43366-113">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="43366-113">Get-ChildItem</span></span>

<span data-ttu-id="43366-114">Applets de commande de contenu</span><span class="sxs-lookup"><span data-stu-id="43366-114">Content cmdlets</span></span>

- <span data-ttu-id="43366-115">Add-Content</span><span class="sxs-lookup"><span data-stu-id="43366-115">Add-Content</span></span>
- <span data-ttu-id="43366-116">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="43366-116">Clear-Content</span></span>
- <span data-ttu-id="43366-117">Get-Content</span><span class="sxs-lookup"><span data-stu-id="43366-117">Get-Content</span></span>
- <span data-ttu-id="43366-118">Set-Content</span><span class="sxs-lookup"><span data-stu-id="43366-118">Set-Content</span></span>

<span data-ttu-id="43366-119">Applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="43366-119">Item cmdlets</span></span>

- <span data-ttu-id="43366-120">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="43366-120">Clear-Item</span></span>
- <span data-ttu-id="43366-121">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="43366-121">Copy-Item</span></span>
- <span data-ttu-id="43366-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="43366-122">Get-Item</span></span>
- <span data-ttu-id="43366-123">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="43366-123">Invoke-Item</span></span>
- <span data-ttu-id="43366-124">Move-Item</span><span class="sxs-lookup"><span data-stu-id="43366-124">Move-Item</span></span>
- <span data-ttu-id="43366-125">New-Item</span><span class="sxs-lookup"><span data-stu-id="43366-125">New-Item</span></span>
- <span data-ttu-id="43366-126">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="43366-126">Remove-Item</span></span>
- <span data-ttu-id="43366-127">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="43366-127">Rename-Item</span></span>
- <span data-ttu-id="43366-128">Set-Item</span><span class="sxs-lookup"><span data-stu-id="43366-128">Set-Item</span></span>

<span data-ttu-id="43366-129">Applets de commande ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-129">ItemProperty cmdlets</span></span>

- <span data-ttu-id="43366-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-130">Clear-ItemProperty</span></span>
- <span data-ttu-id="43366-131">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-131">Copy-ItemProperty</span></span>
- <span data-ttu-id="43366-132">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-132">Get-ItemProperty</span></span>
- <span data-ttu-id="43366-133">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-133">Move-ItemProperty</span></span>
- <span data-ttu-id="43366-134">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-134">New-ItemProperty</span></span>
- <span data-ttu-id="43366-135">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-135">Remove-ItemProperty</span></span>
- <span data-ttu-id="43366-136">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-136">Rename-ItemProperty</span></span>
- <span data-ttu-id="43366-137">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="43366-137">Set-ItemProperty</span></span>

<span data-ttu-id="43366-138">Applets de commande Location</span><span class="sxs-lookup"><span data-stu-id="43366-138">Location cmdlets</span></span>

- <span data-ttu-id="43366-139">Get-Location</span><span class="sxs-lookup"><span data-stu-id="43366-139">Get-Location</span></span>
- <span data-ttu-id="43366-140">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="43366-140">Pop-Location</span></span>
- <span data-ttu-id="43366-141">Push-Location</span><span class="sxs-lookup"><span data-stu-id="43366-141">Push-Location</span></span>
- <span data-ttu-id="43366-142">Set-Location</span><span class="sxs-lookup"><span data-stu-id="43366-142">Set-Location</span></span>

<span data-ttu-id="43366-143">Applets de commande Path</span><span class="sxs-lookup"><span data-stu-id="43366-143">Path cmdlets</span></span>

- <span data-ttu-id="43366-144">Join-Path</span><span class="sxs-lookup"><span data-stu-id="43366-144">Join-Path</span></span>
- <span data-ttu-id="43366-145">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="43366-145">Convert-Path</span></span>
- <span data-ttu-id="43366-146">Split-Path</span><span class="sxs-lookup"><span data-stu-id="43366-146">Split-Path</span></span>
- <span data-ttu-id="43366-147">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="43366-147">Resolve-Path</span></span>
- <span data-ttu-id="43366-148">Test-Path</span><span class="sxs-lookup"><span data-stu-id="43366-148">Test-Path</span></span>

<span data-ttu-id="43366-149">PSDrive, applets de commande</span><span class="sxs-lookup"><span data-stu-id="43366-149">PSDrive cmdlets</span></span>

- <span data-ttu-id="43366-150">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="43366-150">Get-PSDrive</span></span>
- <span data-ttu-id="43366-151">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="43366-151">New-PSDrive</span></span>
- <span data-ttu-id="43366-152">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="43366-152">Remove-PSDrive</span></span>

<span data-ttu-id="43366-153">Applets de commande PSProvider</span><span class="sxs-lookup"><span data-stu-id="43366-153">PSProvider cmdlets</span></span>

- <span data-ttu-id="43366-154">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="43366-154">Get-PSProvider</span></span>

<span data-ttu-id="43366-155">Pour plus d’informations sur une applet de commande, tapez `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="43366-155">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="43366-156">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="43366-156">SEE ALSO</span></span>

[<span data-ttu-id="43366-157">about_Providers</span><span class="sxs-lookup"><span data-stu-id="43366-157">about_Providers</span></span>](about_Providers.md)

