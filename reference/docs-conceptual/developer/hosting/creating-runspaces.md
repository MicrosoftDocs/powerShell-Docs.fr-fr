---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’instances d’exécution
description: Création d’instances d’exécution
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649342"
---
# <a name="creating-runspaces"></a><span data-ttu-id="6d51f-103">Création d’instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="6d51f-103">Creating Runspaces</span></span>

<span data-ttu-id="6d51f-104">Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelées par une application hôte.</span><span class="sxs-lookup"><span data-stu-id="6d51f-104">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="6d51f-105">Cet environnement comprend les commandes et les données qui sont actuellement présentes, ainsi que toutes les restrictions de langue qui s’appliquent actuellement.</span><span class="sxs-lookup"><span data-stu-id="6d51f-105">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="6d51f-106">Les applications hôtes peuvent utiliser l’instance d’exécution par défaut fournie par Windows PowerShell, qui comprend toutes les commandes de base disponibles, ou créer une instance d’exécution personnalisée qui comprend uniquement un sous-ensemble des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="6d51f-106">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="6d51f-107">Pour créer une instance d’exécution personnalisée, vous devez créer un objet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) et l’assigner à votre instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6d51f-107">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="6d51f-108">Tâches d’exécution</span><span class="sxs-lookup"><span data-stu-id="6d51f-108">Runspace tasks</span></span>

1. [<span data-ttu-id="6d51f-109">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="6d51f-109">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="6d51f-110">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="6d51f-110">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="6d51f-111">Création de plusieurs instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="6d51f-111">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="6d51f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d51f-112">See Also</span></span>
