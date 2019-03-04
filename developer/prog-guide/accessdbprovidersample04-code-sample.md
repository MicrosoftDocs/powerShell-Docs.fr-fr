---
title: Exemple de Code AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853605"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="5a6ac-102">Exemple de code AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="5a6ac-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="5a6ac-103">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5a6ac-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="5a6ac-104">Ce fournisseur fonctionne sur les magasins de données de plusieurs couches.</span><span class="sxs-lookup"><span data-stu-id="5a6ac-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="5a6ac-105">Pour ce type de magasin de données, le niveau supérieur de la banque contient les éléments racine et chaque niveau suivant est appelé un nœud d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="5a6ac-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="5a6ac-106">En autorisant l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir de façon hiérarchique via le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="5a6ac-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a6ac-107">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="5a6ac-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="5a6ac-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a6ac-108">See Also</span></span>

[<span data-ttu-id="5a6ac-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5a6ac-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)