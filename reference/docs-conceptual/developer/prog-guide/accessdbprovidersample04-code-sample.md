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
# <a name="accessdbprovidersample04-code-sample"></a>Exemple de code AccessDbProviderSample04

Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).
Ce fournisseur fonctionne sur les magasins de données multicouches. Pour ce type de banque de données, le niveau supérieur du magasin contient les éléments racine et chaque niveau suivant est désigné sous le terme de nœud d’éléments enfants. En permettant à l’utilisateur de travailler sur ces nœuds enfants, un utilisateur peut interagir hiérarchiquement via le magasin de données.

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
