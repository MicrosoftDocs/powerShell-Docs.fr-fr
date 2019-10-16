---
title: Didacticiel StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369408"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="72fa4-102">Tutoriel StopProc</span><span class="sxs-lookup"><span data-stu-id="72fa4-102">StopProc Tutorial</span></span>

<span data-ttu-id="72fa4-103">Cette section fournit un didacticiel pour la création de l’applet de commande Stop-proc, qui est très similaire à l’applet de commande [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72fa4-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="72fa4-104">Ce didacticiel fournit des fragments de code qui illustrent la façon dont les applets de commande sont implémentées, ainsi qu’une explication du code.</span><span class="sxs-lookup"><span data-stu-id="72fa4-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="72fa4-105">Rubriques de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="72fa4-105">Topics in this Tutorial</span></span>

<span data-ttu-id="72fa4-106">Les rubriques de ce didacticiel sont conçues pour être lues de manière séquentielle, chaque rubrique reposant sur ce qui a été abordé dans la rubrique précédente.</span><span class="sxs-lookup"><span data-stu-id="72fa4-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="72fa4-107">[Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md) Cette section décrit comment créer une applet de commande qui prend en charge les modifications du système, telles que l’arrêt d’un processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="72fa4-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="72fa4-108">[Ajout de messages utilisateur à votre applet de](./adding-user-messages-to-your-cmdlet.md) commande Cette section décrit comment ajouter la possibilité d’écrire des messages utilisateur, des messages de débogage, des messages d’avertissement et des informations de progression dans votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="72fa4-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="72fa4-109">[Ajouter des alias, une extension de caractères génériques et de l’aide aux paramètres de l’applet de](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) commande Cette section décrit comment créer une applet de commande qui prend en charge les alias de paramètres, l’aide et l’extension de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="72fa4-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="72fa4-110">[Ajout de jeux de paramètres à des applets de](./adding-parameter-sets-to-a-cmdlet.md) commande Cette section décrit comment ajouter des jeux de paramètres à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="72fa4-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="72fa4-111">Les jeux de paramètres permettent à l’applet de commande de fonctionner différemment selon les paramètres spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="72fa4-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="72fa4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72fa4-112">See Also</span></span>

[<span data-ttu-id="72fa4-113">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="72fa4-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="72fa4-114">Ajout de messages utilisateur à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="72fa4-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="72fa4-115">Ajouter des alias, une extension de caractères génériques et de l’aide aux paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="72fa4-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="72fa4-116">Ajout de jeux de paramètres à des applets de commande</span><span class="sxs-lookup"><span data-stu-id="72fa4-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="72fa4-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="72fa4-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
