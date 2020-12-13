---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple Windows PowerShell02
description: Exemple Windows PowerShell02
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657362"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="9d53e-103">Exemple Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="9d53e-103">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="9d53e-104">Cet exemple montre comment exécuter des commandes de manière asynchrone à l’aide du instances d’exécution d’un pool d’instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d53e-104">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="9d53e-105">L’exemple génère une liste de commandes, puis exécute ces commandes lorsque le moteur Windows PowerShell ouvre une instance d’exécution à partir du pool lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9d53e-105">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d53e-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d53e-106">Requirements</span></span>

- <span data-ttu-id="9d53e-107">Cet exemple requiert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="9d53e-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9d53e-108">Illustre le</span><span class="sxs-lookup"><span data-stu-id="9d53e-108">Demonstrates</span></span>

<span data-ttu-id="9d53e-109">Cet exemple indique :</span><span class="sxs-lookup"><span data-stu-id="9d53e-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="9d53e-110">La création d’un objet RunspacePool avec un nombre minimal et maximal de instances d’exécution autorisé à être ouvert en même temps.</span><span class="sxs-lookup"><span data-stu-id="9d53e-110">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="9d53e-111">Création d’une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="9d53e-111">Creating a list of commands.</span></span>
- <span data-ttu-id="9d53e-112">Exécution des commandes de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9d53e-112">Running the commands asynchronously.</span></span>
- <span data-ttu-id="9d53e-113">Appel de la méthode [System. Management. Automation. instances d’exécution. Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) pour connaître le nombre de instances d’exécution disponibles.</span><span class="sxs-lookup"><span data-stu-id="9d53e-113">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="9d53e-114">Capture de la sortie de commande avec la méthode [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="9d53e-114">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="9d53e-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d53e-115">Example</span></span>

<span data-ttu-id="9d53e-116">Cet exemple montre comment ouvrir le instances d’exécution d’un pool d’instances d’exécution et comment exécuter de manière asynchrone des commandes dans ces instances d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d53e-116">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="9d53e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d53e-117">See Also</span></span>

[<span data-ttu-id="9d53e-118">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d53e-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
