---
title: Création de instances d’exécution | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779571"
---
# <a name="creating-runspaces"></a><span data-ttu-id="c1638-102">Création d’instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="c1638-102">Creating Runspaces</span></span>

<span data-ttu-id="c1638-103">Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelées par une application hôte.</span><span class="sxs-lookup"><span data-stu-id="c1638-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="c1638-104">Cet environnement comprend les commandes et les données qui sont actuellement présentes, ainsi que toutes les restrictions de langue qui s’appliquent actuellement.</span><span class="sxs-lookup"><span data-stu-id="c1638-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="c1638-105">Les applications hôtes peuvent utiliser l’instance d’exécution par défaut fournie par Windows PowerShell, qui comprend toutes les commandes de base disponibles, ou créer une instance d’exécution personnalisée qui comprend uniquement un sous-ensemble des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="c1638-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="c1638-106">Pour créer une instance d’exécution personnalisée, vous devez créer un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) et l’assigner à votre instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c1638-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="c1638-107">Tâches d’exécution</span><span class="sxs-lookup"><span data-stu-id="c1638-107">Runspace tasks</span></span>

1. [<span data-ttu-id="c1638-108">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="c1638-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="c1638-109">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="c1638-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="c1638-110">Création de plusieurs instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="c1638-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="c1638-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1638-111">See Also</span></span>
