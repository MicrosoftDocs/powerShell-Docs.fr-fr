---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code RunSpace08
description: Exemple de code RunSpace08
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654233"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="c8570-103">Exemple de code RunSpace08</span><span class="sxs-lookup"><span data-stu-id="c8570-103">RunSpace08 Code Sample</span></span>

<span data-ttu-id="c8570-104">Voici le code source de l’exemple Runspace08 décrit dans [création d’une application console qui ajoute des paramètres à une commande](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="c8570-104">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="c8570-105">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, ajoute deux paramètres à la deuxième commande, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c8570-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="c8570-106">Les commandes ajoutées au pipeline sont les `Get-Process` applets de commande et `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c8570-106">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c8570-107">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c8570-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="c8570-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8570-108">See Also</span></span>

[<span data-ttu-id="c8570-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c8570-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
