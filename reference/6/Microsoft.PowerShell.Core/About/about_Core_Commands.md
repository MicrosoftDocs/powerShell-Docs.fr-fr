---
description: Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: d02067bca8f66c61a66ff121521a49668f32d839
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207145"
---
# <a name="about-core-commands"></a><span data-ttu-id="73d91-104">À propos des commandes principales</span><span class="sxs-lookup"><span data-stu-id="73d91-104">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="73d91-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="73d91-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="73d91-106">Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73d91-106">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="73d91-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="73d91-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="73d91-108">PowerShell comprend un ensemble d’applets de commande spécialement conçues pour gérer les éléments des magasins de données exposés par les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73d91-108">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="73d91-109">Vous pouvez utiliser ces applets de commande de la même manière pour gérer tous les différents types de données que les fournisseurs mettent à votre disposition.</span><span class="sxs-lookup"><span data-stu-id="73d91-109">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="73d91-110">Pour plus d’informations sur les fournisseurs, tapez « obtenir-aide about_providers ».</span><span class="sxs-lookup"><span data-stu-id="73d91-110">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="73d91-111">Par exemple, vous pouvez utiliser l’applet de commande Get-ChildItem pour répertorier les fichiers dans un répertoire du système de fichiers, les clés sous une clé de registre ou les éléments qui sont exposés par un fournisseur que vous écrivez ou téléchargez.</span><span class="sxs-lookup"><span data-stu-id="73d91-111">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="73d91-112">La liste suivante répertorie les applets de commande PowerShell conçues pour être utilisées avec les fournisseurs :</span><span class="sxs-lookup"><span data-stu-id="73d91-112">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="73d91-113">Applets de commande ChildItem</span><span class="sxs-lookup"><span data-stu-id="73d91-113">ChildItem cmdlets</span></span>

- <span data-ttu-id="73d91-114">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="73d91-114">Get-ChildItem</span></span>

<span data-ttu-id="73d91-115">Applets de commande de contenu</span><span class="sxs-lookup"><span data-stu-id="73d91-115">Content cmdlets</span></span>

- <span data-ttu-id="73d91-116">Add-Content</span><span class="sxs-lookup"><span data-stu-id="73d91-116">Add-Content</span></span>
- <span data-ttu-id="73d91-117">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="73d91-117">Clear-Content</span></span>
- <span data-ttu-id="73d91-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="73d91-118">Get-Content</span></span>
- <span data-ttu-id="73d91-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="73d91-119">Set-Content</span></span>

<span data-ttu-id="73d91-120">Applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="73d91-120">Item cmdlets</span></span>

- <span data-ttu-id="73d91-121">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-121">Clear-Item</span></span>
- <span data-ttu-id="73d91-122">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-122">Copy-Item</span></span>
- <span data-ttu-id="73d91-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-123">Get-Item</span></span>
- <span data-ttu-id="73d91-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-124">Invoke-Item</span></span>
- <span data-ttu-id="73d91-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-125">Move-Item</span></span>
- <span data-ttu-id="73d91-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-126">New-Item</span></span>
- <span data-ttu-id="73d91-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-127">Remove-Item</span></span>
- <span data-ttu-id="73d91-128">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-128">Rename-Item</span></span>
- <span data-ttu-id="73d91-129">Set-Item</span><span class="sxs-lookup"><span data-stu-id="73d91-129">Set-Item</span></span>

<span data-ttu-id="73d91-130">Applets de commande ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-130">ItemProperty cmdlets</span></span>

- <span data-ttu-id="73d91-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-131">Clear-ItemProperty</span></span>
- <span data-ttu-id="73d91-132">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-132">Copy-ItemProperty</span></span>
- <span data-ttu-id="73d91-133">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-133">Get-ItemProperty</span></span>
- <span data-ttu-id="73d91-134">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-134">Move-ItemProperty</span></span>
- <span data-ttu-id="73d91-135">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-135">New-ItemProperty</span></span>
- <span data-ttu-id="73d91-136">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-136">Remove-ItemProperty</span></span>
- <span data-ttu-id="73d91-137">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-137">Rename-ItemProperty</span></span>
- <span data-ttu-id="73d91-138">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="73d91-138">Set-ItemProperty</span></span>

<span data-ttu-id="73d91-139">Applets de commande Location</span><span class="sxs-lookup"><span data-stu-id="73d91-139">Location cmdlets</span></span>

- <span data-ttu-id="73d91-140">Get-Location</span><span class="sxs-lookup"><span data-stu-id="73d91-140">Get-Location</span></span>
- <span data-ttu-id="73d91-141">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="73d91-141">Pop-Location</span></span>
- <span data-ttu-id="73d91-142">Push-Location</span><span class="sxs-lookup"><span data-stu-id="73d91-142">Push-Location</span></span>
- <span data-ttu-id="73d91-143">Set-Location</span><span class="sxs-lookup"><span data-stu-id="73d91-143">Set-Location</span></span>

<span data-ttu-id="73d91-144">Applets de commande Path</span><span class="sxs-lookup"><span data-stu-id="73d91-144">Path cmdlets</span></span>

- <span data-ttu-id="73d91-145">Join-Path</span><span class="sxs-lookup"><span data-stu-id="73d91-145">Join-Path</span></span>
- <span data-ttu-id="73d91-146">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="73d91-146">Convert-Path</span></span>
- <span data-ttu-id="73d91-147">Split-Path</span><span class="sxs-lookup"><span data-stu-id="73d91-147">Split-Path</span></span>
- <span data-ttu-id="73d91-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="73d91-148">Resolve-Path</span></span>
- <span data-ttu-id="73d91-149">Test-Path</span><span class="sxs-lookup"><span data-stu-id="73d91-149">Test-Path</span></span>

<span data-ttu-id="73d91-150">PSDrive, applets de commande</span><span class="sxs-lookup"><span data-stu-id="73d91-150">PSDrive cmdlets</span></span>

- <span data-ttu-id="73d91-151">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="73d91-151">Get-PSDrive</span></span>
- <span data-ttu-id="73d91-152">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="73d91-152">New-PSDrive</span></span>
- <span data-ttu-id="73d91-153">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="73d91-153">Remove-PSDrive</span></span>

<span data-ttu-id="73d91-154">Applets de commande PSProvider</span><span class="sxs-lookup"><span data-stu-id="73d91-154">PSProvider cmdlets</span></span>

- <span data-ttu-id="73d91-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="73d91-155">Get-PSProvider</span></span>

<span data-ttu-id="73d91-156">Pour plus d’informations sur une applet de commande, tapez `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="73d91-156">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="73d91-157">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="73d91-157">SEE ALSO</span></span>

[<span data-ttu-id="73d91-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="73d91-158">about_Providers</span></span>](about_Providers.md)
