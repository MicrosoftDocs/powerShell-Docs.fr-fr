---
title: Comment créer un composant logiciel enfichable PowerShell Windows | Microsoft Docs
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
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859755"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="25227-102">Guide pratique pour créer un composant logiciel enfichable Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25227-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="25227-103">Un composant logiciel enfichable Windows PowerShell fournit un mécanisme pour l’inscription des ensembles d’applets de commande et un autre fournisseur Windows PowerShell avec l’interpréteur de commandes, en étendant les fonctionnalités de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="25227-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="25227-104">Un composant logiciel enfichable Windows PowerShell peut s’inscrire les applets de commande et les fournisseurs dans un assembly unique, ou il peut s’inscrire à une liste spécifique des applets de commande et des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="25227-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="25227-105">Assemblys de composant logiciel enfichable doivent être installés dans un répertoire protégé, comme ils le seraient avec d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="25227-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="25227-106">Sinon, les utilisateurs malveillants peuvent remplacer un assembly avec du code unsafe.</span><span class="sxs-lookup"><span data-stu-id="25227-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="25227-107">Classes de composant logiciel enfichable PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="25227-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="25227-108">Windows PowerShell toutes enfichable classes dérivent les [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span><span class="sxs-lookup"><span data-stu-id="25227-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="25227-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="25227-109">Examples</span></span>

<span data-ttu-id="25227-110">[Écriture d’un composant logiciel enfichable PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Cet exemple montre comment créer un composant logiciel enfichable qui est utilisé pour inscrire les applets de commande et les fournisseurs dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="25227-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="25227-111">[Écriture d’un composant logiciel enfichable PowerShell Windows personnalisée](./writing-a-custom-windows-powershell-snap-in.md): Cet exemple montre comment créer un enfichable personnalisé qui est utilisé pour inscrire un ensemble spécifique d’applets de commande et les fournisseurs qui peuvent ou ne pas existent dans un assembly unique.</span><span class="sxs-lookup"><span data-stu-id="25227-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="25227-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25227-112">See Also</span></span>

[<span data-ttu-id="25227-113">System.Management.Automation.Pssnapin</span><span class="sxs-lookup"><span data-stu-id="25227-113">System.Management.Automation.Pssnapin</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="25227-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="25227-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="25227-115">L’inscription des applets de commande</span><span class="sxs-lookup"><span data-stu-id="25227-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="25227-116">Interpréteur de commandes Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="25227-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
