---
title: Exemple de code AccessDbProviderSample04 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 05509c5b36475bcd3f91c9ab7413974994d668d6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787272"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="723f2-102">Exemple de code AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="723f2-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="723f2-103">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="723f2-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="723f2-104">Ce fournisseur fonctionne sur les magasins de données multicouches.</span><span class="sxs-lookup"><span data-stu-id="723f2-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="723f2-105">Pour ce type de banque de données, le niveau supérieur du magasin contient les éléments racine et chaque niveau suivant est désigné sous le terme de nœud d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="723f2-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="723f2-106">En permettant à l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir hiérarchiquement via le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="723f2-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="723f2-107">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="723f2-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="723f2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="723f2-108">See Also</span></span>

[<span data-ttu-id="723f2-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="723f2-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
