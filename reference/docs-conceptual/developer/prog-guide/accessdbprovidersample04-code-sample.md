---
title: Exemple de code AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366968"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="a81b1-102">Exemple de code AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="a81b1-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="a81b1-103">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a81b1-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="a81b1-104">Ce fournisseur fonctionne sur les magasins de données multicouches.</span><span class="sxs-lookup"><span data-stu-id="a81b1-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="a81b1-105">Pour ce type de banque de données, le niveau supérieur du magasin contient les éléments racine et chaque niveau suivant est désigné sous le terme de nœud d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="a81b1-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="a81b1-106">En permettant à l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir hiérarchiquement via le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="a81b1-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a81b1-107">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="a81b1-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="a81b1-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a81b1-108">See Also</span></span>

[<span data-ttu-id="a81b1-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a81b1-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
