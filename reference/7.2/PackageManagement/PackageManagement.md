---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99599143"
---
# <span data-ttu-id="47212-102">Module PackageManagement</span><span class="sxs-lookup"><span data-stu-id="47212-102">PackageManagement Module</span></span>

## <span data-ttu-id="47212-103">Description</span><span class="sxs-lookup"><span data-stu-id="47212-103">Description</span></span>

<span data-ttu-id="47212-104">Cette rubrique affiche les rubriques d’aide pour les applets de commande Package Management.</span><span class="sxs-lookup"><span data-stu-id="47212-104">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47212-105">Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS).</span><span class="sxs-lookup"><span data-stu-id="47212-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="47212-106">Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="47212-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="47212-107">Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :</span><span class="sxs-lookup"><span data-stu-id="47212-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="47212-108">Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47212-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="47212-109">Applets de commande PackageManagement</span><span class="sxs-lookup"><span data-stu-id="47212-109">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="47212-110">Find-Package</span><span class="sxs-lookup"><span data-stu-id="47212-110">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="47212-111">Recherche les packages de logiciels dans les sources de package disponibles.</span><span class="sxs-lookup"><span data-stu-id="47212-111">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="47212-112">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="47212-112">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="47212-113">Retourne une liste de Package Management fournisseurs de packages disponibles pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="47212-113">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="47212-114">Get-Package</span><span class="sxs-lookup"><span data-stu-id="47212-114">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="47212-115">Retourne une liste de tous les packages logiciels qui ont été installés avec **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="47212-115">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="47212-116">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="47212-116">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="47212-117">Retourne une liste des fournisseurs de packages qui sont connectés à Package Management.</span><span class="sxs-lookup"><span data-stu-id="47212-117">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="47212-118">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="47212-118">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="47212-119">Obtient une liste des sources de packages qui sont inscrites pour un fournisseur de package.</span><span class="sxs-lookup"><span data-stu-id="47212-119">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="47212-120">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="47212-120">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="47212-121">Ajoute Package Management fournisseurs de package à la session active.</span><span class="sxs-lookup"><span data-stu-id="47212-121">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="47212-122">Install-Package</span><span class="sxs-lookup"><span data-stu-id="47212-122">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="47212-123">Installe un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="47212-123">Installs one or more software packages.</span></span>

### [<span data-ttu-id="47212-124">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="47212-124">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="47212-125">Installe un ou plusieurs fournisseurs de packages Package Management.</span><span class="sxs-lookup"><span data-stu-id="47212-125">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="47212-126">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="47212-126">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="47212-127">Ajoute une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="47212-127">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="47212-128">Save-Package</span><span class="sxs-lookup"><span data-stu-id="47212-128">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="47212-129">Enregistre les packages sur l’ordinateur local sans les installer.</span><span class="sxs-lookup"><span data-stu-id="47212-129">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="47212-130">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="47212-130">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="47212-131">Remplace une source de package pour un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="47212-131">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="47212-132">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="47212-132">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="47212-133">Désinstalle un ou plusieurs packages logiciels.</span><span class="sxs-lookup"><span data-stu-id="47212-133">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="47212-134">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="47212-134">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="47212-135">Supprime une source de package inscrite.</span><span class="sxs-lookup"><span data-stu-id="47212-135">Removes a registered package source.</span></span>
