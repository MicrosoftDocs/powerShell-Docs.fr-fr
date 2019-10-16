---
title: Exemple Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367298"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="047ee-102">Exemple Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="047ee-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="047ee-103">Cet exemple montre comment exécuter des commandes de manière asynchrone à l’aide du instances d’exécution d’un pool d’instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="047ee-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="047ee-104">L’exemple génère une liste de commandes, puis exécute ces commandes lorsque le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="047ee-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="047ee-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="047ee-105">Requirements</span></span>

- <span data-ttu-id="047ee-106">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="047ee-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="047ee-107">Illustré</span><span class="sxs-lookup"><span data-stu-id="047ee-107">Demonstrates</span></span>

<span data-ttu-id="047ee-108">Cet exemple illustre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="047ee-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="047ee-109">La création d’un objet RunspacePool avec un nombre minimal et maximal de instances d’exécution autorisé à être ouvert en même temps.</span><span class="sxs-lookup"><span data-stu-id="047ee-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="047ee-110">Création d’une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="047ee-110">Creating a list of commands.</span></span>

- <span data-ttu-id="047ee-111">Exécution des commandes de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="047ee-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="047ee-112">Appel de la méthode [System. Management. Automation. instances d’exécution. Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) pour connaître le nombre de instances d’exécution disponibles.</span><span class="sxs-lookup"><span data-stu-id="047ee-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="047ee-113">Capture de la sortie de commande avec la méthode [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="047ee-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="047ee-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="047ee-114">Example</span></span>

<span data-ttu-id="047ee-115">Cet exemple montre comment ouvrir le instances d’exécution d’un pool d’instances d’exécution et comment exécuter de manière asynchrone des commandes dans ces instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="047ee-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="047ee-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="047ee-116">See Also</span></span>

[<span data-ttu-id="047ee-117">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="047ee-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
