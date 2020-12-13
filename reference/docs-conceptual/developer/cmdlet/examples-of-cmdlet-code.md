---
ms.date: 09/13/2016
ms.topic: reference
title: Exemples de code d’applet de commande
description: Exemples de code d’applet de commande
ms.openlocfilehash: 91dd2019300504697ad9a7a0c155a04600d09c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652922"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="58423-103">Exemples de code d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="58423-103">Examples of Cmdlet Code</span></span>

<span data-ttu-id="58423-104">Cette section contient des exemples de code d’applet de commande que vous pouvez utiliser pour commencer à écrire vos propres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="58423-104">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58423-105">Si vous souhaitez obtenir des instructions pas à pas pour l’écriture d’applets de commande, consultez [tutoriels pour l’écriture d’applets de](./tutorials-for-writing-cmdlets.md)commande.</span><span class="sxs-lookup"><span data-stu-id="58423-105">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="58423-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="58423-106">In This Section</span></span>

<span data-ttu-id="58423-107">[Comment écrire une applet](./how-to-write-a-simple-cmdlet.md) de commande simple Cet exemple illustre la structure de base du code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58423-107">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="58423-108">[Comment déclarer des paramètres d’applet de](./how-to-declare-cmdlet-parameters.md) commande Cet exemple montre comment déclarer les différents types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="58423-108">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="58423-109">[Comment déclarer des jeux de paramètres](./how-to-declare-parameter-sets.md) Cet exemple montre comment déclarer des ensembles de paramètres qui peuvent modifier l’action effectuée par une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58423-109">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="58423-110">[Comment valider une entrée de paramètre](./how-to-validate-parameter-input.md) Ces exemples montrent comment valider une entrée de paramètre.</span><span class="sxs-lookup"><span data-stu-id="58423-110">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="58423-111">[Comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md) Cet exemple montre comment déclarer un paramètre qui est ajouté au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="58423-111">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="58423-112">[Comment appeler des scripts dans une applet de](./how-to-invoke-scripts-within-a-cmdlet.md) commande Cet exemple montre comment appeler un script fourni à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58423-112">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="58423-113">[Comment remplacer les méthodes de traitement d’entrée](./how-to-override-input-processing-methods.md) Ces exemples illustrent la structure de base utilisée pour substituer les méthodes BeginProcessing, ProcessRecord et EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="58423-113">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="58423-114">[Comment prendre en charge les appels ShouldProcess](./how-to-request-confirmations.md) Cet exemple montre comment les méthodes [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doivent être appelées à partir d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58423-114">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="58423-115">[Comment prendre en charge les transactions](./how-to-support-transactions.md) Cet exemple montre comment indiquer que l’applet de commande prend en charge les transactions et comment implémenter l’action qui est effectuée lorsque l’applet de commande est utilisée dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="58423-115">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="58423-116">[Comment prendre en charge les travaux](./how-to-support-jobs.md) Cet exemple montre comment prendre en charge des travaux lorsque vous écrivez des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="58423-116">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="58423-117">[Comment appeler une applet de commande à partir d’une applet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) de commande Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, ce qui vous permet d’ajouter la fonctionnalité de l’applet de commande appelée à l’applet de commande que vous développez.</span><span class="sxs-lookup"><span data-stu-id="58423-117">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="58423-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58423-118">See Also</span></span>

[<span data-ttu-id="58423-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="58423-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
