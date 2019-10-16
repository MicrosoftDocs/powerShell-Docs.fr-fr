---
title: Écriture d’une application hôte Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367278"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="007c7-102">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="007c7-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="007c7-103">Vous pouvez héberger Windows PowerShell dans votre application.</span><span class="sxs-lookup"><span data-stu-id="007c7-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="007c7-104">L’application hôte peut définir l’instance d’exécution dans laquelle les commandes sont exécutées, ouvrir des sessions sur un ordinateur local ou distant et appeler les commandes de manière synchrone ou asynchrone en fonction des besoins de l’application.</span><span class="sxs-lookup"><span data-stu-id="007c7-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="007c7-105">Les rubriques suivantes expliquent comment créer une application qui héberge Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="007c7-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="007c7-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="007c7-106">In This Section</span></span>

<span data-ttu-id="007c7-107">[Démarrage rapide de l’hôte Windows PowerShell](./windows-powershell-host-quickstart.md) Fournit des instructions et des exemples de code pour vous aider à créer des applications hôtes.</span><span class="sxs-lookup"><span data-stu-id="007c7-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="007c7-108">[Création de instances d’exécution](./creating-runspaces.md) Ensemble de rubriques qui expliquent comment créer des instances d’exécution pour exécuter une commande Windows PowerShell dans une application hôte.</span><span class="sxs-lookup"><span data-stu-id="007c7-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="007c7-109">[Ajout et appel de commandes](./adding-and-invoking-commands.md) Explique comment créer et exécuter un pipeline de commande dans votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="007c7-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="007c7-110">[Création de instances d’exécution distants](./creating-remote-runspaces.md) Explique comment connecter une instance d’exécution à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="007c7-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="007c7-111">[Création d’une interface utilisateur personnalisée](./creating-a-custom-user-interface.md) Présente des interfaces utilisateur personnalisées et fournit des liens vers des exemples.</span><span class="sxs-lookup"><span data-stu-id="007c7-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="007c7-112">[Exemples d’applications hôtes](./host-application-samples.md) Cette section contient des exemples d’applications hôtes complètes.</span><span class="sxs-lookup"><span data-stu-id="007c7-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="007c7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="007c7-113">See Also</span></span>

[<span data-ttu-id="007c7-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="007c7-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
