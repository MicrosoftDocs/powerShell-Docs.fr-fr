---
title: Exemples d’hôtes personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367508"
---
# <a name="custom-host-samples"></a><span data-ttu-id="5bb4a-102">Exemples d’hôtes personnalisés</span><span class="sxs-lookup"><span data-stu-id="5bb4a-102">Custom Host Samples</span></span>

<span data-ttu-id="5bb4a-103">Cette section comprend un exemple de code pour l’écriture d’un hôte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="5bb4a-104">Vous pouvez utiliser Microsoft Visual Studio pour créer une application console, puis copier le code à partir des rubriques de cette section dans votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5bb4a-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5bb4a-105">In This Section</span></span>

 <span data-ttu-id="5bb4a-106">[Exemple host01](./host01-sample.md) Cet exemple montre comment implémenter une application hôte qui utilise un hôte personnalisé de base.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="5bb4a-107">[Exemple Host02](./host02-sample.md) Cet exemple montre comment écrire une application hôte qui utilise le runtime Windows PowerShell avec une implémentation d’hôte personnalisée.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="5bb4a-108">L’application hôte définit la culture de l’hôte sur l’allemand, exécute l’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) et affiche les résultats comme vous le feriez à l’aide de pwrsh. exe, puis imprime les données actuelles et l’heure en allemand.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="5bb4a-109">[Exemple Host03](./host03-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="5bb4a-110">[Exemple Host04](./host04-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="5bb4a-111">Cette application hôte prend aussi en charge l’affichage d’invites qui permettent à l’utilisateur de spécifier plusieurs options.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="5bb4a-112">[Exemple Host05](./host05-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="5bb4a-113">Cette application hôte prend également en charge les appels à des ordinateurs distants à l’aide des applets de commande [Enter-PSSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) et [Exit-PSSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) .</span><span class="sxs-lookup"><span data-stu-id="5bb4a-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="5bb4a-114">[Exemple Host06](./host06-sample.md) Cet exemple montre comment créer une application hôte basée sur une console interactive qui lit les commandes à partir de la ligne de commande, exécute les commandes, puis affiche les résultats dans la console.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="5bb4a-115">Par ailleurs, cet exemple utilise les API génératrices de jetons pour spécifier la couleur du texte entré par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5bb4a-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb4a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bb4a-116">See Also</span></span>
