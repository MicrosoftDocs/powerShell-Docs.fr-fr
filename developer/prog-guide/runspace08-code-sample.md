---
title: Exemple de Code RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081272"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="ea105-102">Exemple de code RunSpace08</span><span class="sxs-lookup"><span data-stu-id="ea105-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="ea105-103">Voici le code source pour l’exemple Runspace08 décrit dans [création d’une Application qu’ajoute des paramètres de la Console à une commande](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="ea105-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="ea105-104">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute les deux commandes au pipeline, ajoute deux paramètres à la deuxième commande, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ea105-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="ea105-105">Les commandes qui sont ajoutés au pipeline sont le `Get-Process` et `Sort-Object` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="ea105-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ea105-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="ea105-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="ea105-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea105-107">See Also</span></span>

[<span data-ttu-id="ea105-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ea105-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)