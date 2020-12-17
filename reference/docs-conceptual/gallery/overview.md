---
ms.date: 12/01/2020
title: PowerShell Gallery
description: PowerShell Gallery est le référentiel central pour les modules PowerShell, les scripts et les ressources DSC.
ms.openlocfilehash: f1ce6a8e2d5d72ac14cf3e4854626ef612d27891
ms.sourcegitcommit: 62282bb9c36fea3b4290b9263c1cd8e9ac216e29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96470313"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="48f98-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="48f98-103">The PowerShell Gallery</span></span>

<span data-ttu-id="48f98-104">PowerShell Gallery est le référentiel central pour le contenu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48f98-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="48f98-105">Vous pouvez y trouver des modules PowerShell utiles contenant les commandes PowerShell et les ressources DSC (Configuration de l’état souhaité).</span><span class="sxs-lookup"><span data-stu-id="48f98-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="48f98-106">Vous pouvez également trouver des scripts PowerShell, certains d’entre eux peuvent contenir des workflows PowerShell qui présentent une série de tâches et donnent le séquencement de ces tâches.</span><span class="sxs-lookup"><span data-stu-id="48f98-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="48f98-107">Certains de ces packages sont créés par Microsoft, d’autres par la communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48f98-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="48f98-108">Vue d’ensemble de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="48f98-108">PowerShellGet Overview</span></span>

<span data-ttu-id="48f98-109">Le module PowerShellGet contient des applets de commande permettant de détecter, d’installer, de mettre à jour et de publier des packages PowerShell contenant des artefacts tels que les modules, les ressources DSC, les fonctionnalités de rôle et les scripts à partir du référentiel [PowerShell Gallery](https://www.PowerShellGallery.com) et d’autres référentiels privés.</span><span class="sxs-lookup"><span data-stu-id="48f98-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="48f98-110">Prise en main de la galerie</span><span class="sxs-lookup"><span data-stu-id="48f98-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="48f98-111">L’installation de packages de la galerie nécessite la dernière version du module PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="48f98-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span> <span data-ttu-id="48f98-112">Pour des instructions complètes, consultez [Installation de PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="48f98-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="48f98-113">Pour plus d’informations sur l’utilisation des commandes PowerShellGet avec la galerie, consultez la page [Getting Started](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="48f98-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="48f98-114">Vous pouvez également exécuter *Update-Help-Module PowerShellGet* pour installer l’aide locale sur ces commandes.</span><span class="sxs-lookup"><span data-stu-id="48f98-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="48f98-115">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="48f98-115">Supported Operating Systems</span></span>

<span data-ttu-id="48f98-116">Le module **PowerShellGet** nécessite **PowerShell 3.0 ou ultérieur**.</span><span class="sxs-lookup"><span data-stu-id="48f98-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="48f98-117">**PowerShellGet** nécessite .NET Framework 4.5 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="48f98-117">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="48f98-118">Pour plus d'informations, voir [Installation de .NET Framework pour les développeurs](/dotnet/framework/install/guide-for-developers).</span><span class="sxs-lookup"><span data-stu-id="48f98-118">For more information, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers).</span></span>

<span data-ttu-id="48f98-119">Dans la mesure où **PowerShell Core** est multiplateforme et qu’il fonctionne sous Windows, Linux et macOS, **PowerShellGet** est également disponible sur ces systèmes.</span><span class="sxs-lookup"><span data-stu-id="48f98-119">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="48f98-120">Pour obtenir une liste complète des systèmes pris en charge par **PowerShell Core** consultez [Installation de PowerShell](/powershell/scripting/install/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="48f98-120">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/install/installing-powershell).</span></span>

<span data-ttu-id="48f98-121">De nombreux modules hébergés dans la galerie prendront en charge différents systèmes d’exploitation en imposant des exigences supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="48f98-121">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span>
<span data-ttu-id="48f98-122">Pour plus d’informations, voir la documentation des modules.</span><span class="sxs-lookup"><span data-stu-id="48f98-122">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="48f98-123">Vous avez une question ?</span><span class="sxs-lookup"><span data-stu-id="48f98-123">Got a question?</span></span> <span data-ttu-id="48f98-124">Vous voulez donner votre avis ?</span><span class="sxs-lookup"><span data-stu-id="48f98-124">Have feedback?</span></span>

<span data-ttu-id="48f98-125">Des informations supplémentaires relatives à PowerShell Gallery et PowerShellGet sont disponibles dans la page [Getting Started](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="48f98-125">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span>

<span data-ttu-id="48f98-126">Pour afficher l’état actuel des services PowerShell Gallery, consultez la page [État de PowerShell Gallery](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="48f98-126">To see the current status of the PowerShell Gallery services, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>

<span data-ttu-id="48f98-127">Envoyez vos commentaires et signalez les problèmes à l’aide du [référentiel GitHub](https://github.com/PowerShell/PowerShellGallery/issues).</span><span class="sxs-lookup"><span data-stu-id="48f98-127">Please provide feedback and report issues the [GitHub repository](https://github.com/PowerShell/PowerShellGallery/issues).</span></span>
