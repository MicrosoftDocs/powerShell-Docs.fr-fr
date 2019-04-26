---
title: Écriture d’un flux de travail Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080320"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="d029a-102">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d029a-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="d029a-103">Vous pouvez créer un flux de travail XAML en ajoutant des activités exposées par les assemblys Windows PowerShell pour le Concepteur de flux de travail dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d029a-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="d029a-104">Les assemblys de Windows PowerShell suivantes exposent des activités de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d029a-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d029a-105">Si vous souhaitez fournir une aide pour le flux de travail, un workflow XAML doit être empaqueté en tant que module.</span><span class="sxs-lookup"><span data-stu-id="d029a-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="d029a-106">Pour plus d’informations sur les modules, consultez [écrire un PowerShell Module de Windows](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="d029a-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="d029a-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="d029a-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="d029a-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="d029a-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="d029a-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="d029a-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="d029a-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="d029a-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="d029a-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="d029a-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="d029a-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="d029a-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="d029a-113">Les rubriques suivantes décrivent comment créer un flux de travail à l’aide des activités de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d029a-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="d029a-114">Ajout d’activités de Windows PowerShell à la boîte à outils Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d029a-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="d029a-115">Création d’un flux de travail avec Windows PowerShell activités</span><span class="sxs-lookup"><span data-stu-id="d029a-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="d029a-116">Création d’un Workflow à l’aide d’un Script PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="d029a-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="d029a-117">L’importation et l’appel d’un flux de travail Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d029a-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="d029a-118">Création d’une activité de flux de travail à partir d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d029a-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)