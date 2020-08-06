---
title: Exemple de code RunSpace08 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67172a0f8d6daf2f5b9965d1a18f7698daddbe1a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784688"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="a1f95-102">Exemple de code RunSpace08</span><span class="sxs-lookup"><span data-stu-id="a1f95-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="a1f95-103">Voici le code source de l’exemple Runspace08 décrit dans [création d’une application console qui ajoute des paramètres à une commande](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="a1f95-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="a1f95-104">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, ajoute deux paramètres à la deuxième commande, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a1f95-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="a1f95-105">Les commandes ajoutées au pipeline sont les `Get-Process` applets de commande et `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="a1f95-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a1f95-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="a1f95-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="a1f95-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1f95-107">See Also</span></span>

[<span data-ttu-id="a1f95-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a1f95-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
