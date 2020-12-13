---
ms.date: 09/13/2016
ms.topic: reference
title: Exemples d’API Windows PowerShell
description: Exemples d’API Windows PowerShell
ms.openlocfilehash: b6336ae7a2abb98cbbaa69bf6c9455f893db2d94
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657535"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="3a75b-103">Exemples d’API Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a75b-103">Windows PowerShell API Samples</span></span>

<span data-ttu-id="3a75b-104">Cette section comprend un exemple de code qui montre comment créer des instances d’exécution qui restreignent les fonctionnalités et comment exécuter de façon asynchrone des commandes à l’aide d’un pool d’instances d’exécution pour fournir le instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3a75b-104">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="3a75b-105">Vous pouvez utiliser Microsoft Visual Studio pour créer une application console, puis copier le code à partir des rubriques de cette section dans votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="3a75b-105">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3a75b-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3a75b-106">In This Section</span></span>

<span data-ttu-id="3a75b-107">[Exemple PowerShell01](./windows-powershell01-sample.md) Cet exemple montre comment utiliser un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) pour limiter les fonctionnalités d’une instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3a75b-107">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="3a75b-108">La sortie de cet exemple montre comment limiter le mode de langage de l’instance d’exécution, comment marquer une applet de commande comme étant privée, comment ajouter et supprimer des applets de commande et des fournisseurs, ajouter une commande de proxy, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="3a75b-108">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="3a75b-109">[Exemple PowerShell02](./windows-powershell02-sample.md) Cet exemple montre comment exécuter des commandes de manière asynchrone à l’aide du instances d’exécution d’un pool d’instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3a75b-109">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="3a75b-110">L’exemple génère une liste de commandes, puis exécute ces commandes lorsque le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3a75b-110">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>
