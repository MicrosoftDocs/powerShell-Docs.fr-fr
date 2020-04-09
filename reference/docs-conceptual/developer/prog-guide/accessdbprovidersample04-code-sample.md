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
ms.openlocfilehash: 60f0ed4e3d39ee93ab63023161d09a6c7b914798
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978574"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="5cdff-102">Exemple de code AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="5cdff-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="5cdff-103">Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5cdff-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="5cdff-104">Ce fournisseur fonctionne sur les magasins de données multicouches.</span><span class="sxs-lookup"><span data-stu-id="5cdff-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="5cdff-105">Pour ce type de banque de données, le niveau supérieur du magasin contient les éléments racine et chaque niveau suivant est désigné sous le terme de nœud d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="5cdff-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="5cdff-106">En permettant à l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir hiérarchiquement via le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="5cdff-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5cdff-107">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="5cdff-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="5cdff-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cdff-108">See Also</span></span>

[<span data-ttu-id="5cdff-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5cdff-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
