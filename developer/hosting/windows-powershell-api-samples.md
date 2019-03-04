---
title: Exemples d’API PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860775"
---
# <a name="windows-powershell-api-samples"></a>Exemples d’API Windows PowerShell

Cette section inclut des exemples de code qui montre comment créer des instances d’exécution qui limitent les fonctionnalités et comment exécuter des commandes de façon asynchrone à l’aide d’un pool de l’instance d’exécution pour fournir les instances d’exécution. Vous pouvez utiliser Microsoft Visual Studio pour créer une application console puis copier le code dans les rubriques de cette section dans votre application hôte.

## <a name="in-this-section"></a>Dans cette section

[Exemple de PowerShell01](./windows-powershell01-sample.md) cet exemple montre comment utiliser un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet pour limiter les fonctionnalités d’une instance d’exécution. La sortie de cet exemple montre comment faire pour restreindre le mode de langage de l’instance d’exécution, comment marquer une applet de commande comme privés, comment ajouter et les applets de commande remove et fournisseurs, comment ajouter une commande de proxy et bien plus encore.

[Exemple de PowerShell02](./windows-powershell02-sample.md) cet exemple montre comment exécuter des commandes de façon asynchrone à l’aide les instances d’exécution d’un pool de l’instance d’exécution. L’exemple génère une liste de commandes, puis exécute ces commandes pendant que le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsqu’il est nécessaire.