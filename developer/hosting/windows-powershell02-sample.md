---
title: Exemple de PowerShell02 Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082513"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="386f8-102">Exemple Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="386f8-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="386f8-103">Cet exemple montre comment exécuter des commandes de façon asynchrone à l’aide les instances d’exécution d’un pool de l’instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="386f8-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="386f8-104">L’exemple génère une liste de commandes, puis exécute ces commandes pendant que le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsqu’il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="386f8-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="386f8-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="386f8-105">Requirements</span></span>

- <span data-ttu-id="386f8-106">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="386f8-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="386f8-107">Montre</span><span class="sxs-lookup"><span data-stu-id="386f8-107">Demonstrates</span></span>

<span data-ttu-id="386f8-108">Cet exemple montre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="386f8-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="386f8-109">Création d’un objet RunspacePool avec un nombre minimal et maximal d’instances d’exécution peuvent être ouverts en même temps.</span><span class="sxs-lookup"><span data-stu-id="386f8-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="386f8-110">Création d’une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="386f8-110">Creating a list of commands.</span></span>

- <span data-ttu-id="386f8-111">Exécuter les commandes de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="386f8-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="386f8-112">Appel de la [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) méthode pour voir combien d’instances sont gratuits.</span><span class="sxs-lookup"><span data-stu-id="386f8-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="386f8-113">Capture la sortie de commande avec le [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (méthode).</span><span class="sxs-lookup"><span data-stu-id="386f8-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="386f8-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="386f8-114">Example</span></span>

<span data-ttu-id="386f8-115">Cet exemple montre comment ouvrir les instances d’exécution d’un pool de l’instance d’exécution et comment exécuter des commandes de façon asynchrone dans ces instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="386f8-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="386f8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="386f8-116">See Also</span></span>

[<span data-ttu-id="386f8-117">Écriture d’une Application hôte PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="386f8-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)