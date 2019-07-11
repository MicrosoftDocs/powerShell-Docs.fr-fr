---
title: Exemple de Code RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 1a21af4b48a414d9c9fee57871eacb0a39c9ab11
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734898"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="4ed03-102">Exemple de code RunSpace09</span><span class="sxs-lookup"><span data-stu-id="4ed03-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="4ed03-103">Voici le code source pour l’exemple Runspace09 décrit dans [création d’un Pipeline de façon asynchrone une Console Application qu’appelle](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="4ed03-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="4ed03-104">Cet exemple d’application crée et ouvre une instance d’exécution, crée et appelle un pipeline de manière asynchrone, puis utilise les événements pour traiter de façon asynchrone le script de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4ed03-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="4ed03-105">Le script est exécuté par cette application crée les entiers entre 1 et 10 dans toutes les 0,5 secondes (500 ms).</span><span class="sxs-lookup"><span data-stu-id="4ed03-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="4ed03-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="4ed03-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="4ed03-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ed03-107">See Also</span></span>

[<span data-ttu-id="4ed03-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4ed03-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)