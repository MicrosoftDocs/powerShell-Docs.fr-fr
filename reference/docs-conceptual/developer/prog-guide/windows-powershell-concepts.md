---
title: Concepts de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366678"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="24d23-102">Concepts de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="24d23-103">Cette section contient des informations conceptuelles qui vous aideront à comprendre PowerShell du point de vue d’un développeur.</span><span class="sxs-lookup"><span data-stu-id="24d23-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="24d23-104">Nom de la rubrique</span><span class="sxs-lookup"><span data-stu-id="24d23-104">Topic Name</span></span>|<span data-ttu-id="24d23-105">Description</span><span class="sxs-lookup"><span data-stu-id="24d23-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="24d23-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="24d23-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="24d23-107">Description des objets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d23-107">Description of PowerShell objects.</span></span> <span data-ttu-id="24d23-108">Pour plus d’informations, consultez [à propos](/powershell/module/microsoft.powershell.core/about/about_object_creation) de la création d’objets</span><span class="sxs-lookup"><span data-stu-id="24d23-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="24d23-109">Création de instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="24d23-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="24d23-110">Les environnements d’exploitation où les commandes sont traitées.</span><span class="sxs-lookup"><span data-stu-id="24d23-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="24d23-111">Pour plus d’informations, consultez [Runspace, classe](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="24d23-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="24d23-112">Extension d’objets de sortie</span><span class="sxs-lookup"><span data-stu-id="24d23-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="24d23-113">Comment étendre des objets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d23-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="24d23-114">Pour plus d’informations, consultez [à propos des types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="24d23-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="24d23-115">Inscription des applets de commande</span><span class="sxs-lookup"><span data-stu-id="24d23-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="24d23-116">Comment rendre des modules et des composants logiciels enfichables disponibles dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d23-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="24d23-117">Pour plus d’informations, consultez [modules et composants logiciels enfichables](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="24d23-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="24d23-118">Demande de confirmation à partir des applets de commande</span><span class="sxs-lookup"><span data-stu-id="24d23-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="24d23-119">Comment les applets de commande et les fournisseurs demandent des commentaires à l’utilisateur avant qu’une action soit entreprise.</span><span class="sxs-lookup"><span data-stu-id="24d23-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="24d23-120">RuntimeDefinedParameter, classe</span><span class="sxs-lookup"><span data-stu-id="24d23-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="24d23-121">Déclarations des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="24d23-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="24d23-122">Espace de noms System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="24d23-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="24d23-123">Vue d’ensemble des espaces de noms d’API PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d23-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="24d23-124">Vue d’ensemble du fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="24d23-125">Vue d’ensemble des fournisseurs PowerShell utilisés pour accéder aux magasins de données.</span><span class="sxs-lookup"><span data-stu-id="24d23-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="24d23-126">Écriture de l’aide pour les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="24d23-127">Comment écrire l’aide sur les applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d23-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="24d23-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24d23-128">See also</span></span>

[<span data-ttu-id="24d23-129">Classe PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="24d23-130">Informations de référence sur l’API PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="24d23-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="24d23-131">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="24d23-132">Écriture de l’aide pour les modules Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="24d23-133">Écriture d’un fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="24d23-134">Informations de référence sur l’API Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="24d23-135">Informations de référence sur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24d23-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)