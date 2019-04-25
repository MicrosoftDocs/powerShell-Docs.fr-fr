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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081952"
---
# <a name="accessdbprovidersample04-code-sample"></a>Exemple de code AccessDbProviderSample04

Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Ce fournisseur fonctionne sur les magasins de données de plusieurs couches. Pour ce type de magasin de données, le niveau supérieur de la banque contient les éléments racine et chaque niveau suivant est appelé un nœud d’éléments enfants. En autorisant l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir de façon hiérarchique via le magasin de données.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)