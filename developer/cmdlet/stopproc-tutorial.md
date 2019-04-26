---
title: Didacticiel de StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067302"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="07d45-102">Tutoriel StopProc</span><span class="sxs-lookup"><span data-stu-id="07d45-102">StopProc Tutorial</span></span>

<span data-ttu-id="07d45-103">Cette section fournit un didacticiel pour la création de l’applet de commande Stop-Process, qui est très similaire à la [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) applet de commande fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07d45-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="07d45-104">Ce didacticiel fournit des fragments de code qui illustrent la façon dont les applets de commande sont implémentées et une explication du code.</span><span class="sxs-lookup"><span data-stu-id="07d45-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="07d45-105">Rubriques de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="07d45-105">Topics in this Tutorial</span></span>

<span data-ttu-id="07d45-106">Les rubriques de ce didacticiel sont conçus pour être lu de manière séquentielle, avec chaque rubrique hommage à ce qui a été présenté dans la rubrique précédente.</span><span class="sxs-lookup"><span data-stu-id="07d45-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="07d45-107">[Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md) cette section décrit comment créer une applet de commande qui prend en charge les modifications du système, tels que l’arrêt d’un processus en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="07d45-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="07d45-108">[Ajout de Messages de l’utilisateur à votre applet de commande](./adding-user-messages-to-your-cmdlet.md) cette section décrit comment ajouter la possibilité d’écrire des messages de l’utilisateur, les messages de débogage, les messages d’avertissement et les informations de progression dans votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07d45-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="07d45-109">[Ajout d’alias, le développement des caractères génériques et aux paramètres de l’applet de commande](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) cette section décrit comment créer une applet de commande qui prend en charge des alias de paramètre, d’aide et de développement des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="07d45-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="07d45-110">[Ajout de jeux de paramètres aux applets de commande](./adding-parameter-sets-to-a-cmdlet.md) cette section décrit comment ajouter des jeux de paramètres pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07d45-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="07d45-111">Jeux de paramètres permettent à l’applet de commande fonctionner différemment selon les paramètres sont spécifiés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07d45-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="07d45-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07d45-112">See Also</span></span>

[<span data-ttu-id="07d45-113">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="07d45-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="07d45-114">Ajout de Messages de l’utilisateur à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="07d45-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="07d45-115">Ajout d’alias, le développement des caractères génériques et aux paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="07d45-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="07d45-116">Ajout du paramètre définit pour les applets de commande</span><span class="sxs-lookup"><span data-stu-id="07d45-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="07d45-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="07d45-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
