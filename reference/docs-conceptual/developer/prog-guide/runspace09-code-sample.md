---
title: Exemple de code RunSpace09 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fc5d8d4d182cca6bfc42d63c68a14a7a5e5f9c97
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784671"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="7fc2e-102">Exemple de code RunSpace09</span><span class="sxs-lookup"><span data-stu-id="7fc2e-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="7fc2e-103">Voici le code source de l’exemple Runspace09 décrit dans [création d’une application console qui appelle un pipeline de manière asynchrone](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="7fc2e-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="7fc2e-104">Cet exemple d’application crée et ouvre une instance d’exécution, crée et appelle de manière asynchrone un pipeline, puis utilise des événements de pipeline pour traiter le script de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7fc2e-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="7fc2e-105">Le script exécuté par cette application crée les entiers de 1 à 10 en intervalles de 0,5 secondes (500 ms).</span><span class="sxs-lookup"><span data-stu-id="7fc2e-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="7fc2e-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="7fc2e-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="7fc2e-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fc2e-107">See Also</span></span>

[<span data-ttu-id="7fc2e-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7fc2e-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
