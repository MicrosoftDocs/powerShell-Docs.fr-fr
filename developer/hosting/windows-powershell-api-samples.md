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
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="56c6e-102">Exemples d’API Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56c6e-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="56c6e-103">Cette section inclut des exemples de code qui montre comment créer des instances d’exécution qui limitent les fonctionnalités et comment exécuter des commandes de façon asynchrone à l’aide d’un pool de l’instance d’exécution pour fournir les instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="56c6e-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="56c6e-104">Vous pouvez utiliser Microsoft Visual Studio pour créer une application console puis copier le code dans les rubriques de cette section dans votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="56c6e-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="56c6e-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="56c6e-105">In This Section</span></span>

<span data-ttu-id="56c6e-106">[Exemple de PowerShell01](./windows-powershell01-sample.md) cet exemple montre comment utiliser un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet pour limiter les fonctionnalités d’une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="56c6e-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="56c6e-107">La sortie de cet exemple montre comment faire pour restreindre le mode de langage de l’instance d’exécution, comment marquer une applet de commande comme privés, comment ajouter et les applets de commande remove et fournisseurs, comment ajouter une commande de proxy et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="56c6e-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="56c6e-108">[Exemple de PowerShell02](./windows-powershell02-sample.md) cet exemple montre comment exécuter des commandes de façon asynchrone à l’aide les instances d’exécution d’un pool de l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="56c6e-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="56c6e-109">L’exemple génère une liste de commandes, puis exécute ces commandes pendant que le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsqu’il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="56c6e-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>