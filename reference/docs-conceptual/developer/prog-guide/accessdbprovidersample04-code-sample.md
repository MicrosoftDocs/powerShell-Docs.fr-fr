---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code AccessDbProviderSample04
description: Exemple de code AccessDbProviderSample04
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647557"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="cc0ad-103">Exemple de code AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="cc0ad-103">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="cc0ad-104">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="cc0ad-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="cc0ad-105">Ce fournisseur fonctionne sur les magasins de données multicouches.</span><span class="sxs-lookup"><span data-stu-id="cc0ad-105">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="cc0ad-106">Pour ce type de banque de données, le niveau supérieur du magasin contient les éléments racine et chaque niveau suivant est désigné sous le terme de nœud d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="cc0ad-106">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="cc0ad-107">En permettant à l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir hiérarchiquement via le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="cc0ad-107">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cc0ad-108">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="cc0ad-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="cc0ad-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc0ad-109">See Also</span></span>

[<span data-ttu-id="cc0ad-110">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cc0ad-110">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
