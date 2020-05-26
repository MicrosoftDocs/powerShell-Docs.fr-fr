---
title: Comment créer un composant logiciel enfichable Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811328"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="2e9c6-102">Guide pratique pour créer un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e9c6-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="2e9c6-103">Un composant logiciel enfichable Windows PowerShell fournit un mécanisme permettant d’inscrire des ensembles d’applets de commande et un autre fournisseur Windows PowerShell avec l’interpréteur de commandes, étendant ainsi les fonctionnalités de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="2e9c6-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="2e9c6-104">Un composant logiciel enfichable Windows PowerShell peut inscrire toutes les applets de commande et tous les fournisseurs dans un assembly unique, ou il peut inscrire une liste spécifique d’applets de commande et de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="2e9c6-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="2e9c6-105">Les assemblys de composant logiciel enfichable doivent être installés dans un répertoire protégé, de la même façon qu’avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="2e9c6-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="2e9c6-106">Dans le cas contraire, les utilisateurs malveillants peuvent remplacer un assembly par du code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="2e9c6-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="2e9c6-107">Classes du composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e9c6-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="2e9c6-108">Toutes les classes de composant logiciel enfichable Windows PowerShell dérivent des classes [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="2e9c6-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="2e9c6-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="2e9c6-109">Examples</span></span>

<span data-ttu-id="2e9c6-110">[Écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable qui est utilisé pour inscrire toutes les applets de commande et tous les fournisseurs dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="2e9c6-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="2e9c6-111">[Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé](./writing-a-custom-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable personnalisé qui est utilisé pour inscrire un ensemble spécifique d’applets de commande et de fournisseurs qui peuvent ou non exister dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="2e9c6-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e9c6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e9c6-112">See Also</span></span>

[<span data-ttu-id="2e9c6-113">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="2e9c6-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="2e9c6-114">System. Management. Automation. CustomPSSnapIn</span><span class="sxs-lookup"><span data-stu-id="2e9c6-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="2e9c6-115">Inscription des applets de commande</span><span class="sxs-lookup"><span data-stu-id="2e9c6-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="2e9c6-116">Kit de développement logiciel Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="2e9c6-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
