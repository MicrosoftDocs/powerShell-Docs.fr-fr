---
title: Écriture d’une Application hôte PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2039e181becd1b39fc3d6cf0cdbcf0c20e9fc206
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863175"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="017b9-102">Écriture d’une application hôte Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="017b9-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="017b9-103">Vous pouvez héberger Windows PowerShell dans votre application.</span><span class="sxs-lookup"><span data-stu-id="017b9-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="017b9-104">L’application hôte peut définir l’instance d’exécution où les commandes sont à exécuter, ouvrir des sessions sur un ordinateur local ou distant et appeler les commandes que soit synchrone ou asynchrone, en fonction des besoins de l’application.</span><span class="sxs-lookup"><span data-stu-id="017b9-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="017b9-105">Les rubriques suivantes expliquent comment créer une application qui héberge</span><span class="sxs-lookup"><span data-stu-id="017b9-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="017b9-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="017b9-106">In This Section</span></span>

<span data-ttu-id="017b9-107">[Démarrage rapide de Windows PowerShell hôte](./windows-powershell-host-quickstart.md) fournit des instructions et des exemples de code pour vous aider à démarrer la création d’applications de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="017b9-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="017b9-108">[Création d’instances d’exécution](./creating-runspaces.md) ensemble de rubriques qui expliquent comment créer des instances d’exécution pour exécuter la commande Windows PowerShell dans une application hôte.</span><span class="sxs-lookup"><span data-stu-id="017b9-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="017b9-109">[Ajout et l’appel des commandes](./adding-and-invoking-commands.md) explique comment créer et exécuter un pipeline de commande dans votre application hôte...</span><span class="sxs-lookup"><span data-stu-id="017b9-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="017b9-110">[Création d’instances d’exécution à distance](./creating-remote-runspaces.md) Expains comment connecter une instance d’exécution à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="017b9-110">[Creating remote runspaces](./creating-remote-runspaces.md) Expains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="017b9-111">[Création d’une interface utilisateur personnalisée](./creating-a-custom-user-interface.md) utilisateur personnalisée présente les interfaces et fournit des liens vers des exemples.</span><span class="sxs-lookup"><span data-stu-id="017b9-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="017b9-112">[Héberger des exemples d’applications](./host-application-samples.md) cette section inclut des exemples d’applications hôtes terminée.</span><span class="sxs-lookup"><span data-stu-id="017b9-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="017b9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="017b9-113">See Also</span></span>

[<span data-ttu-id="017b9-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="017b9-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)