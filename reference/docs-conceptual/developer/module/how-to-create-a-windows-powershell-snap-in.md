---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour créer un composant logiciel enfichable Windows PowerShell
description: Guide pratique pour créer un composant logiciel enfichable Windows PowerShell
ms.openlocfilehash: 29394ebcd2f7c4a547aabcb88685ff494b2c381d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657268"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="90aba-103">Guide pratique pour créer un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90aba-103">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="90aba-104">Un composant logiciel enfichable Windows PowerShell fournit un mécanisme permettant d’inscrire des ensembles d’applets de commande et un autre fournisseur Windows PowerShell avec l’interpréteur de commandes, étendant ainsi les fonctionnalités de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="90aba-104">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="90aba-105">Un composant logiciel enfichable Windows PowerShell peut inscrire toutes les applets de commande et tous les fournisseurs dans un assembly unique, ou il peut inscrire une liste spécifique d’applets de commande et de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="90aba-105">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="90aba-106">Les assemblys de composant logiciel enfichable doivent être installés dans un répertoire protégé, de la même façon qu’avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="90aba-106">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="90aba-107">Dans le cas contraire, les utilisateurs malveillants peuvent remplacer un assembly par du code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="90aba-107">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="90aba-108">Classes du composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90aba-108">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="90aba-109">Toutes les classes de composant logiciel enfichable Windows PowerShell dérivent des classes [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="90aba-109">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="90aba-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="90aba-110">Examples</span></span>

<span data-ttu-id="90aba-111">[Écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable qui est utilisé pour inscrire toutes les applets de commande et tous les fournisseurs dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="90aba-111">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="90aba-112">[Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé](./writing-a-custom-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable personnalisé qui est utilisé pour inscrire un ensemble spécifique d’applets de commande et de fournisseurs qui peuvent ou non exister dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="90aba-112">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="90aba-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90aba-113">See Also</span></span>

[<span data-ttu-id="90aba-114">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="90aba-114">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="90aba-115">System. Management. Automation. CustomPSSnapIn</span><span class="sxs-lookup"><span data-stu-id="90aba-115">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="90aba-116">Inscription des applets de commande</span><span class="sxs-lookup"><span data-stu-id="90aba-116">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="90aba-117">Kit SDK Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90aba-117">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
