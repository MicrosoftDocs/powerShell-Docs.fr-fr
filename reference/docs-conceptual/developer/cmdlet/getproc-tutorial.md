---
title: Didacticiel GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364438"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="f3537-102">Tutoriel GetProc</span><span class="sxs-lookup"><span data-stu-id="f3537-102">GetProc Tutorial</span></span>

<span data-ttu-id="f3537-103">Cette section fournit un didacticiel sur la création d’une applet de commande obtenir-proc qui est très similaire à l’applet de commande [« obtenir-traiter »](/powershell/module/Microsoft.PowerShell.Management/Get-Process) fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3537-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="f3537-104">Ce didacticiel fournit des fragments de code qui illustrent la façon dont les applets de commande sont implémentées, ainsi qu’une explication du code.</span><span class="sxs-lookup"><span data-stu-id="f3537-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="f3537-105">Rubriques de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="f3537-105">Topics in this Tutorial</span></span>

<span data-ttu-id="f3537-106">Les rubriques de ce didacticiel sont conçues pour être lues de manière séquentielle, chaque rubrique reposant sur ce qui a été abordé dans la rubrique précédente.</span><span class="sxs-lookup"><span data-stu-id="f3537-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="f3537-107">[Création d’une applet de commande sans paramètres](./creating-a-cmdlet-without-parameters.md) Cette section décrit comment créer une applet de commande qui récupère des informations à partir de l’ordinateur local sans utiliser de paramètres, puis écrit les informations dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3537-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f3537-108">[Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md) Cette section décrit comment ajouter un paramètre à l’applet de commande obtenir-proc afin que l’applet de commande puisse traiter l’entrée en fonction d’objets explicites passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3537-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="f3537-109">L’implémentation décrite ici récupère les processus en fonction de leur nom, puis écrit les informations dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3537-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f3537-110">[Ajout de paramètres qui traitent l’entrée de pipeline](./adding-parameters-that-process-pipeline-input.md) Cette section décrit comment ajouter un paramètre à l’applet de commande obtenir-proc afin que l’applet de commande puisse traiter les objets qui lui sont transmis via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3537-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="f3537-111">L’applet de commande d’implémentation décrite ici récupère les processus en fonction des objets passés à l’applet de commande, puis écrit les informations dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3537-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f3537-112">[Ajout d’un rapport d’erreurs qui ne se termine pas à votre applet de](./adding-non-terminating-error-reporting-to-your-cmdlet.md) commande Cette section décrit comment ajouter un rapport d’erreurs qui ne se termine pas à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3537-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="f3537-113">L’implémentation décrite ici détecte les erreurs de non-terminaison qui se produisent lors du traitement de l’entrée et écrit un enregistrement d’erreur dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="f3537-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3537-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3537-114">See Also</span></span>

[<span data-ttu-id="f3537-115">Création d’une applet de commande sans paramètres</span><span class="sxs-lookup"><span data-stu-id="f3537-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="f3537-116">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="f3537-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f3537-117">Ajout de paramètres qui traitent l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="f3537-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="f3537-118">Ajout d’un rapport d’erreurs qui ne se termine pas à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="f3537-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="f3537-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f3537-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
