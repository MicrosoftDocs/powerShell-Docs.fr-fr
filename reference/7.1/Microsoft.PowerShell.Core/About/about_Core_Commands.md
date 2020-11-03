---
description: Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 90723e286c3cc85a9ae9196721f3c0c6909d62ab
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207349"
---
# <a name="about-core-commands"></a><span data-ttu-id="8e2b4-104">À propos des commandes principales</span><span class="sxs-lookup"><span data-stu-id="8e2b4-104">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="8e2b4-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="8e2b4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8e2b4-106">Répertorie les applets de commande conçues pour être utilisées avec les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e2b4-106">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="8e2b4-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="8e2b4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8e2b4-108">PowerShell comprend un ensemble d’applets de commande spécialement conçues pour gérer les éléments des magasins de données exposés par les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e2b4-108">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="8e2b4-109">Vous pouvez utiliser ces applets de commande de la même manière pour gérer tous les différents types de données que les fournisseurs mettent à votre disposition.</span><span class="sxs-lookup"><span data-stu-id="8e2b4-109">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="8e2b4-110">Pour plus d’informations sur les fournisseurs, tapez « obtenir-aide about_providers ».</span><span class="sxs-lookup"><span data-stu-id="8e2b4-110">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="8e2b4-111">Par exemple, vous pouvez utiliser l’applet de commande Get-ChildItem pour répertorier les fichiers dans un répertoire du système de fichiers, les clés sous une clé de registre ou les éléments qui sont exposés par un fournisseur que vous écrivez ou téléchargez.</span><span class="sxs-lookup"><span data-stu-id="8e2b4-111">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="8e2b4-112">La liste suivante répertorie les applets de commande PowerShell conçues pour être utilisées avec les fournisseurs :</span><span class="sxs-lookup"><span data-stu-id="8e2b4-112">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="8e2b4-113">Applets de commande ChildItem</span><span class="sxs-lookup"><span data-stu-id="8e2b4-113">ChildItem cmdlets</span></span>

- <span data-ttu-id="8e2b4-114">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8e2b4-114">Get-ChildItem</span></span>

<span data-ttu-id="8e2b4-115">Applets de commande de contenu</span><span class="sxs-lookup"><span data-stu-id="8e2b4-115">Content cmdlets</span></span>

- <span data-ttu-id="8e2b4-116">Add-Content</span><span class="sxs-lookup"><span data-stu-id="8e2b4-116">Add-Content</span></span>
- <span data-ttu-id="8e2b4-117">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="8e2b4-117">Clear-Content</span></span>
- <span data-ttu-id="8e2b4-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="8e2b4-118">Get-Content</span></span>
- <span data-ttu-id="8e2b4-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="8e2b4-119">Set-Content</span></span>

<span data-ttu-id="8e2b4-120">Applets de commande Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-120">Item cmdlets</span></span>

- <span data-ttu-id="8e2b4-121">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-121">Clear-Item</span></span>
- <span data-ttu-id="8e2b4-122">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-122">Copy-Item</span></span>
- <span data-ttu-id="8e2b4-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-123">Get-Item</span></span>
- <span data-ttu-id="8e2b4-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-124">Invoke-Item</span></span>
- <span data-ttu-id="8e2b4-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-125">Move-Item</span></span>
- <span data-ttu-id="8e2b4-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-126">New-Item</span></span>
- <span data-ttu-id="8e2b4-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-127">Remove-Item</span></span>
- <span data-ttu-id="8e2b4-128">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-128">Rename-Item</span></span>
- <span data-ttu-id="8e2b4-129">Set-Item</span><span class="sxs-lookup"><span data-stu-id="8e2b4-129">Set-Item</span></span>

<span data-ttu-id="8e2b4-130">Applets de commande ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-130">ItemProperty cmdlets</span></span>

- <span data-ttu-id="8e2b4-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-131">Clear-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-132">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-132">Copy-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-133">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-133">Get-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-134">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-134">Move-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-135">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-135">New-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-136">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-136">Remove-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-137">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-137">Rename-ItemProperty</span></span>
- <span data-ttu-id="8e2b4-138">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8e2b4-138">Set-ItemProperty</span></span>

<span data-ttu-id="8e2b4-139">Applets de commande Location</span><span class="sxs-lookup"><span data-stu-id="8e2b4-139">Location cmdlets</span></span>

- <span data-ttu-id="8e2b4-140">Get-Location</span><span class="sxs-lookup"><span data-stu-id="8e2b4-140">Get-Location</span></span>
- <span data-ttu-id="8e2b4-141">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="8e2b4-141">Pop-Location</span></span>
- <span data-ttu-id="8e2b4-142">Push-Location</span><span class="sxs-lookup"><span data-stu-id="8e2b4-142">Push-Location</span></span>
- <span data-ttu-id="8e2b4-143">Set-Location</span><span class="sxs-lookup"><span data-stu-id="8e2b4-143">Set-Location</span></span>

<span data-ttu-id="8e2b4-144">Applets de commande Path</span><span class="sxs-lookup"><span data-stu-id="8e2b4-144">Path cmdlets</span></span>

- <span data-ttu-id="8e2b4-145">Join-Path</span><span class="sxs-lookup"><span data-stu-id="8e2b4-145">Join-Path</span></span>
- <span data-ttu-id="8e2b4-146">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="8e2b4-146">Convert-Path</span></span>
- <span data-ttu-id="8e2b4-147">Split-Path</span><span class="sxs-lookup"><span data-stu-id="8e2b4-147">Split-Path</span></span>
- <span data-ttu-id="8e2b4-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="8e2b4-148">Resolve-Path</span></span>
- <span data-ttu-id="8e2b4-149">Test-Path</span><span class="sxs-lookup"><span data-stu-id="8e2b4-149">Test-Path</span></span>

<span data-ttu-id="8e2b4-150">PSDrive, applets de commande</span><span class="sxs-lookup"><span data-stu-id="8e2b4-150">PSDrive cmdlets</span></span>

- <span data-ttu-id="8e2b4-151">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="8e2b4-151">Get-PSDrive</span></span>
- <span data-ttu-id="8e2b4-152">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="8e2b4-152">New-PSDrive</span></span>
- <span data-ttu-id="8e2b4-153">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="8e2b4-153">Remove-PSDrive</span></span>

<span data-ttu-id="8e2b4-154">Applets de commande PSProvider</span><span class="sxs-lookup"><span data-stu-id="8e2b4-154">PSProvider cmdlets</span></span>

- <span data-ttu-id="8e2b4-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8e2b4-155">Get-PSProvider</span></span>

<span data-ttu-id="8e2b4-156">Pour plus d’informations sur une applet de commande, tapez `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="8e2b4-156">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e2b4-157">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="8e2b4-157">SEE ALSO</span></span>

[<span data-ttu-id="8e2b4-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8e2b4-158">about_Providers</span></span>](about_Providers.md)

