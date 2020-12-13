---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code RunSpace09
description: Exemple de code RunSpace09
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654201"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="6a4e2-103">Exemple de code RunSpace09</span><span class="sxs-lookup"><span data-stu-id="6a4e2-103">RunSpace09 Code Sample</span></span>

<span data-ttu-id="6a4e2-104">Voici le code source de l’exemple Runspace09 décrit dans [création d’une application console qui appelle un pipeline de manière asynchrone](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="6a4e2-104">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="6a4e2-105">Cet exemple d’application crée et ouvre une instance d’exécution, crée et appelle de manière asynchrone un pipeline, puis utilise des événements de pipeline pour traiter le script de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="6a4e2-105">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="6a4e2-106">Le script exécuté par cette application crée les entiers de 1 à 10 en intervalles de 0,5 secondes (500 ms).</span><span class="sxs-lookup"><span data-stu-id="6a4e2-106">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="6a4e2-107">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="6a4e2-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="6a4e2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a4e2-108">See Also</span></span>

[<span data-ttu-id="6a4e2-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6a4e2-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
