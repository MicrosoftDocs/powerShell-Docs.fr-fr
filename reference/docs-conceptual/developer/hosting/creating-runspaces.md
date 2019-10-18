---
title: Création de instances d’exécution | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367578"
---
# <a name="creating-runspaces"></a><span data-ttu-id="f5109-102">Création d’instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="f5109-102">Creating Runspaces</span></span>

<span data-ttu-id="f5109-103">Une instance d’exécution est l’environnement d’exploitation pour les commandes qui sont appelées par une application hôte.</span><span class="sxs-lookup"><span data-stu-id="f5109-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="f5109-104">Cet environnement comprend les commandes et les données qui sont actuellement présentes, ainsi que toutes les restrictions de langue qui s’appliquent actuellement.</span><span class="sxs-lookup"><span data-stu-id="f5109-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="f5109-105">Les applications hôtes peuvent utiliser l’instance d’exécution par défaut fournie par Windows PowerShell, qui comprend toutes les commandes de base disponibles, ou créer une instance d’exécution personnalisée qui comprend uniquement un sous-ensemble des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="f5109-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="f5109-106">Pour créer une instance d’exécution personnalisée, vous créez un objet [System. Management. Automation. instances d’exécution. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) et vous l’affectez à votre instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f5109-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="f5109-107">Tâches d’exécution</span><span class="sxs-lookup"><span data-stu-id="f5109-107">Runspace tasks</span></span>

1. [<span data-ttu-id="f5109-108">Création d’un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="f5109-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="f5109-109">Création d’une instance d’exécution avec restriction</span><span class="sxs-lookup"><span data-stu-id="f5109-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="f5109-110">Création de plusieurs instances d’exécution</span><span class="sxs-lookup"><span data-stu-id="f5109-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="f5109-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5109-111">See Also</span></span>