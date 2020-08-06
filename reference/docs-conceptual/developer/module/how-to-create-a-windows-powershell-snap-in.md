---
title: Comment créer un composant logiciel enfichable Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.openlocfilehash: 4150ba582544d1daa4a898f0ff20b169c24a0ee0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787323"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="e3c50-102">Guide pratique pour créer un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3c50-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="e3c50-103">Un composant logiciel enfichable Windows PowerShell fournit un mécanisme permettant d’inscrire des ensembles d’applets de commande et un autre fournisseur Windows PowerShell avec l’interpréteur de commandes, étendant ainsi les fonctionnalités de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="e3c50-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="e3c50-104">Un composant logiciel enfichable Windows PowerShell peut inscrire toutes les applets de commande et tous les fournisseurs dans un assembly unique, ou il peut inscrire une liste spécifique d’applets de commande et de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="e3c50-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="e3c50-105">Les assemblys de composant logiciel enfichable doivent être installés dans un répertoire protégé, de la même façon qu’avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e3c50-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="e3c50-106">Dans le cas contraire, les utilisateurs malveillants peuvent remplacer un assembly par du code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="e3c50-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="e3c50-107">Classes du composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3c50-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="e3c50-108">Toutes les classes de composant logiciel enfichable Windows PowerShell dérivent des classes [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="e3c50-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="e3c50-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="e3c50-109">Examples</span></span>

<span data-ttu-id="e3c50-110">[Écriture d’un composant logiciel enfichable Windows PowerShell](./writing-a-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable qui est utilisé pour inscrire toutes les applets de commande et tous les fournisseurs dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="e3c50-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="e3c50-111">[Écriture d’un composant logiciel enfichable Windows PowerShell personnalisé](./writing-a-custom-windows-powershell-snap-in.md): cet exemple montre comment créer un composant logiciel enfichable personnalisé qui est utilisé pour inscrire un ensemble spécifique d’applets de commande et de fournisseurs qui peuvent ou non exister dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="e3c50-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c50-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3c50-112">See Also</span></span>

[<span data-ttu-id="e3c50-113">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e3c50-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="e3c50-114">System. Management. Automation. CustomPSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e3c50-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="e3c50-115">Inscription des applets de commande</span><span class="sxs-lookup"><span data-stu-id="e3c50-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="e3c50-116">Kit de développement logiciel Windows PowerShell Shell</span><span class="sxs-lookup"><span data-stu-id="e3c50-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
