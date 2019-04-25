---
title: Création d’instances d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082938"
---
# <a name="creating-runspaces"></a><span data-ttu-id="b7cf0-102">Création d’instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="b7cf0-102">Creating Runspaces</span></span>

<span data-ttu-id="b7cf0-103">Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelés par une application hôte.</span><span class="sxs-lookup"><span data-stu-id="b7cf0-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="b7cf0-104">Cet environnement inclut les commandes et les données qui sont actuellement présentes et des restrictions de langue qui s’appliquent actuellement.</span><span class="sxs-lookup"><span data-stu-id="b7cf0-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="b7cf0-105">Héberger des applications peuvent utiliser l’instance d’exécution par défaut qui est fournie par Windows PowerShell, qui inclut toutes les commandes de cœur disponible, ou créez une instance d’exécution personnalisée qui inclut uniquement un sous-ensemble des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="b7cf0-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="b7cf0-106">Pour créer une instance d’exécution personnalisée, vous créez un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de l’objet et l’assigner à votre instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b7cf0-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="b7cf0-107">Tâches de l’instance d’exécution</span><span class="sxs-lookup"><span data-stu-id="b7cf0-107">Runspace tasks</span></span>

1. [<span data-ttu-id="b7cf0-108">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="b7cf0-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="b7cf0-109">Création d’une instance d’exécution contrainte</span><span class="sxs-lookup"><span data-stu-id="b7cf0-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="b7cf0-110">Création de plusieurs instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="b7cf0-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="b7cf0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7cf0-111">See Also</span></span>
