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
ms.openlocfilehash: fe0393634a1e5bb1a3d4a98ccf245e199beb0f16
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869909"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="b1dea-102">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b1dea-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="b1dea-103">Vous pouvez héberger Windows PowerShell dans votre application.</span><span class="sxs-lookup"><span data-stu-id="b1dea-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="b1dea-104">L’application hôte peut définir l’instance d’exécution dans laquelle les commandes sont exécutées, ouvrir des sessions sur un ordinateur local ou distant et appeler les commandes de manière synchrone ou asynchrone en fonction des besoins de l’application.</span><span class="sxs-lookup"><span data-stu-id="b1dea-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="b1dea-105">Les rubriques suivantes expliquent comment créer une application qui héberge Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1dea-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b1dea-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b1dea-106">In This Section</span></span>

<span data-ttu-id="b1dea-107">[Démarrage rapide de l’hôte Windows PowerShell](./windows-powershell-host-quickstart.md) Fournit des instructions et des exemples de code pour vous aider à créer des applications hôtes.</span><span class="sxs-lookup"><span data-stu-id="b1dea-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="b1dea-108">[Création de instances d’exécution](./creating-runspaces.md) Ensemble de rubriques qui expliquent comment créer des instances d’exécution pour exécuter une commande Windows PowerShell dans une application hôte.</span><span class="sxs-lookup"><span data-stu-id="b1dea-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="b1dea-109">[Ajout et appel de commandes](./adding-and-invoking-commands.md) Explique comment créer et exécuter un pipeline de commande dans votre application hôte.</span><span class="sxs-lookup"><span data-stu-id="b1dea-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="b1dea-110">[Création de instances d’exécution distants](./creating-remote-runspaces.md) Explique comment connecter une instance d’exécution à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b1dea-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="b1dea-111">[Création d’une interface utilisateur personnalisée](./creating-a-custom-user-interface.md) Présente des interfaces utilisateur personnalisées et fournit des liens vers des exemples.</span><span class="sxs-lookup"><span data-stu-id="b1dea-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="b1dea-112">[Exemples d’applications hôtes](./host-application-samples.md) Cette section contient des exemples d’applications hôtes complètes.</span><span class="sxs-lookup"><span data-stu-id="b1dea-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>
