---
ms.date: 09/13/2016
ms.topic: reference
title: Tutoriel StopProc
description: Tutoriel StopProc
ms.openlocfilehash: 95229ee3c4905d295bd6991fe8ccf8c9840c3cdd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646427"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="f2bc2-103">Tutoriel StopProc</span><span class="sxs-lookup"><span data-stu-id="f2bc2-103">StopProc Tutorial</span></span>

<span data-ttu-id="f2bc2-104">Cette section fournit un didacticiel sur la création de l’applet de commande Stop-Proc, qui est très similaire à l’applet de commande [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-104">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="f2bc2-105">Ce didacticiel fournit des fragments de code qui illustrent la façon dont les applets de commande sont implémentées, ainsi qu’une explication du code.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="f2bc2-106">Rubriques de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="f2bc2-106">Topics in this Tutorial</span></span>

<span data-ttu-id="f2bc2-107">Les rubriques de ce didacticiel sont conçues pour être lues de manière séquentielle, chaque rubrique reposant sur ce qui a été abordé dans la rubrique précédente.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="f2bc2-108">[Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md) Cette section décrit comment créer une applet de commande qui prend en charge les modifications du système, telles que l’arrêt d’un processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-108">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="f2bc2-109">[Ajout de messages utilisateur à votre applet de](./adding-user-messages-to-your-cmdlet.md) commande Cette section décrit comment ajouter la possibilité d’écrire des messages utilisateur, des messages de débogage, des messages d’avertissement et des informations de progression dans votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-109">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="f2bc2-110">[Ajouter des alias, une extension de caractères génériques et de l’aide aux paramètres de l’applet de](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) commande Cette section décrit comment créer une applet de commande qui prend en charge les alias de paramètres, l’aide et l’extension de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-110">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="f2bc2-111">[Ajout de jeux de paramètres à des applets de](./adding-parameter-sets-to-a-cmdlet.md) commande Cette section décrit comment ajouter des jeux de paramètres à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-111">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="f2bc2-112">Les jeux de paramètres permettent à l’applet de commande de fonctionner différemment selon les paramètres spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2bc2-112">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2bc2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2bc2-113">See Also</span></span>

[<span data-ttu-id="f2bc2-114">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="f2bc2-114">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="f2bc2-115">Ajout de messages utilisateur à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="f2bc2-115">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="f2bc2-116">Ajout d’alias, d’une extension de caractère générique et d’une aide aux paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="f2bc2-116">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="f2bc2-117">Ajout de jeux de paramètres à des applets de commande</span><span class="sxs-lookup"><span data-stu-id="f2bc2-117">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="f2bc2-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f2bc2-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
