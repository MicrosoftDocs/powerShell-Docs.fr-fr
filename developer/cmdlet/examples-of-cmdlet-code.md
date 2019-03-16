---
title: Exemples de Code de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056258"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="d8ac4-102">Exemples de code d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="d8ac4-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="d8ac4-103">Cette section contient des exemples de code d’applet de commande que vous pouvez utiliser pour commencer à écrire vos propres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8ac4-104">Si vous souhaitez obtenir des instructions détaillées pour l’écriture des applets de commande, consultez [didacticiels pour écrire les applets de commande](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="d8ac4-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d8ac4-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d8ac4-105">In This Section</span></span>

<span data-ttu-id="d8ac4-106">[Comment écrire une applet de commande Simple](./how-to-write-a-simple-cmdlet.md) cet exemple montre la structure de base de code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="d8ac4-107">[Comment déclarer des paramètres d’applet de commande](./how-to-declare-cmdlet-parameters.md) cet exemple montre comment déclarer les différents types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="d8ac4-108">[Comment déclarer des jeux de paramètres](./how-to-declare-parameter-sets.md) cet exemple montre comment déclarer des jeux de paramètres qui peuvent changer l’action effectue une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="d8ac4-109">[Comment valider l’entrée paramètre](./how-to-validate-parameter-input.md) ces exemples montrent comment valider les entrées de paramètre.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="d8ac4-110">[Comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md) cet exemple montre comment déclarer un paramètre qui est ajouté à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="d8ac4-111">[Comment appeler des Scripts au sein d’une applet de commande](./how-to-invoke-scripts-within-a-cmdlet.md) cet exemple montre comment appeler un script qui est fourni à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="d8ac4-112">[Comment substituer les méthodes de traitement de l’entrée](./how-to-override-input-processing-methods.md) ces exemples montrent la structure de base utilisée pour substituer les méthodes BeginProcessing, ProcessRecord et EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="d8ac4-113">[Comment la prise en charge les appels de ShouldProcess](./how-to-request-confirmations.md) cet exemple montre comment la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes doivent être appelées à partir une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="d8ac4-114">[Comment la prise en charge des Transactions](./how-to-support-transactions.md) cet exemple montre comment indiquer que l’applet de commande prend en charge les transactions et l’implémentation de l’action qui est effectuée lorsque l’applet de commande est utilisée dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="d8ac4-115">[Comment prendre en charge les travaux](./how-to-support-jobs.md) cet exemple montre comment prendre en charge des travaux lorsque vous écrivez des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="d8ac4-116">[L’appel d’une applet de commande à partir d’au sein d’une applet de commande](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, qui vous permet d’ajouter les fonctionnalités de l’applet de commande appelée à l’applet de commande que vous développez.</span><span class="sxs-lookup"><span data-stu-id="d8ac4-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8ac4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8ac4-117">See Also</span></span>

[<span data-ttu-id="d8ac4-118">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8ac4-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
