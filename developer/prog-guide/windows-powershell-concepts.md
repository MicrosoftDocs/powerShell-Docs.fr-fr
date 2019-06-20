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
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263849"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="125ac-102">Concepts de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="125ac-103">Cette section contient des informations conceptuelles qui vous aideront à comprendre PowerShell à partir du point de vue du développeur.</span><span class="sxs-lookup"><span data-stu-id="125ac-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="125ac-104">Nom de la rubrique</span><span class="sxs-lookup"><span data-stu-id="125ac-104">Topic Name</span></span>|<span data-ttu-id="125ac-105">Description</span><span class="sxs-lookup"><span data-stu-id="125ac-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="125ac-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="125ac-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="125ac-107">Description des objets de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="125ac-107">Description of PowerShell objects.</span></span> <span data-ttu-id="125ac-108">Pour plus d’informations, consultez [sur la création d’objets](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="125ac-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="125ac-109">Création d’instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="125ac-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="125ac-110">Les environnements d’exploitation dans lequel les commandes sont traitées.</span><span class="sxs-lookup"><span data-stu-id="125ac-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="125ac-111">Pour plus d’informations, consultez [classe d’instance d’exécution](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="125ac-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="125ac-112">Extension des objets de sortie</span><span class="sxs-lookup"><span data-stu-id="125ac-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="125ac-113">Comment étendre les objets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="125ac-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="125ac-114">Pour plus d’informations, consultez [sur Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="125ac-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="125ac-115">L’inscription des applets de commande</span><span class="sxs-lookup"><span data-stu-id="125ac-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="125ac-116">Comment rendre les modules et composants logiciel enfichables disponibles dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="125ac-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="125ac-117">Pour plus d’informations, consultez [Modules et composants logiciel enfichables](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="125ac-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="125ac-118">Demander Confirmation à partir des applets de commande</span><span class="sxs-lookup"><span data-stu-id="125ac-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="125ac-119">Comment applets de commande et des fournisseurs de demander des commentaires à l’utilisateur avant d’effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="125ac-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="125ac-120">Classe de RuntimeDefinedParameter</span><span class="sxs-lookup"><span data-stu-id="125ac-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="125ac-121">Déclarations de paramètre d’exécution.</span><span class="sxs-lookup"><span data-stu-id="125ac-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="125ac-122">System.Management.Automation Namespace</span><span class="sxs-lookup"><span data-stu-id="125ac-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="125ac-123">Vue d’ensemble des espaces de noms API PowerShell.</span><span class="sxs-lookup"><span data-stu-id="125ac-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="125ac-124">Vue d’ensemble du fournisseur PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="125ac-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="125ac-125">Vue d’ensemble sur les fournisseurs PowerShell qui sont utilisés pour accéder aux données stocke.</span><span class="sxs-lookup"><span data-stu-id="125ac-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="125ac-126">Aide d’écriture pour les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="125ac-127">Comment écrire l’aide d’applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="125ac-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="125ac-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="125ac-128">See also</span></span>

[<span data-ttu-id="125ac-129">Classe de PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="125ac-130">Référence de l’API PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="125ac-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="125ac-131">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="125ac-132">Écriture de l’aide pour les Modules de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="125ac-133">Écriture d’un fournisseur Powershell de Windows</span><span class="sxs-lookup"><span data-stu-id="125ac-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="125ac-134">Référence de l’API Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="125ac-135">Informations de référence sur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="125ac-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)