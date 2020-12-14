---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,applet de commande
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 88dcb47bee268af3553bb797aaa264e27ed8c51c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889638"
---
# <span data-ttu-id="0d10e-103">Module PackageManagement</span><span class="sxs-lookup"><span data-stu-id="0d10e-103">PackageManagement Module</span></span>

## <span data-ttu-id="0d10e-104">Description</span><span class="sxs-lookup"><span data-stu-id="0d10e-104">Description</span></span>

<span data-ttu-id="0d10e-105">Cette rubrique affiche les rubriques d’aide pour les applets de commande Package Management.</span><span class="sxs-lookup"><span data-stu-id="0d10e-105">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d10e-106">Depuis le 2020 avril, le PowerShell Gallery ne prend plus en charge les versions 1,0 et 1,1 du protocole TLS (Transport Layer Security).</span><span class="sxs-lookup"><span data-stu-id="0d10e-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0d10e-107">Si vous n’utilisez pas TLS 1,2 ou une version ultérieure, vous recevrez une erreur lors de la tentative d’accès au PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="0d10e-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0d10e-108">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1,2 :</span><span class="sxs-lookup"><span data-stu-id="0d10e-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0d10e-109">Pour plus d’informations, consultez l' [annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) dans le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d10e-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="0d10e-110">Applets de commande PackageManagement</span><span class="sxs-lookup"><span data-stu-id="0d10e-110">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="0d10e-111">Find-Package</span><span class="sxs-lookup"><span data-stu-id="0d10e-111">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="0d10e-112">Recherche les packages de logiciels dans les sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="0d10e-112">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="0d10e-113">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="0d10e-113">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="0d10e-114">Retourne une liste de Package Management fournisseurs de packages disponibles pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="0d10e-114">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="0d10e-115">Get-Package</span><span class="sxs-lookup"><span data-stu-id="0d10e-115">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="0d10e-116">Retourne une liste de tous les packages logiciels qui ont été installés avec **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="0d10e-116">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="0d10e-117">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="0d10e-117">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="0d10e-118">Retourne une liste des fournisseurs de packages qui sont connectés à Package Management.</span><span class="sxs-lookup"><span data-stu-id="0d10e-118">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="0d10e-119">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0d10e-119">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="0d10e-120">Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="0d10e-120">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="0d10e-121">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="0d10e-121">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="0d10e-122">Ajoute Package Management fournisseurs de package à la session active.</span><span class="sxs-lookup"><span data-stu-id="0d10e-122">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="0d10e-123">Install-Package</span><span class="sxs-lookup"><span data-stu-id="0d10e-123">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="0d10e-124">Installe un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="0d10e-124">Installs one or more software packages.</span></span>

### [<span data-ttu-id="0d10e-125">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="0d10e-125">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="0d10e-126">Installe un ou plusieurs fournisseurs de packages Package Management.</span><span class="sxs-lookup"><span data-stu-id="0d10e-126">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="0d10e-127">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0d10e-127">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="0d10e-128">Ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d10e-128">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="0d10e-129">Save-Package</span><span class="sxs-lookup"><span data-stu-id="0d10e-129">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="0d10e-130">Enregistre les packages sur l’ordinateur local sans les installer.</span><span class="sxs-lookup"><span data-stu-id="0d10e-130">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="0d10e-131">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0d10e-131">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="0d10e-132">Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d10e-132">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="0d10e-133">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="0d10e-133">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="0d10e-134">Désinstalle un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="0d10e-134">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="0d10e-135">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="0d10e-135">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="0d10e-136">Supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="0d10e-136">Removes a registered package source.</span></span>

