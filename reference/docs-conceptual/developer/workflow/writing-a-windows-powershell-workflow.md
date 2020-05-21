---
title: Écriture d’un workflow Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 0f8a9938a1685e9abc2f1dbfb18c3b2b9008d9be
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564924"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="0f79d-102">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f79d-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="0f79d-103">Vous pouvez créer un flux de travail XAML en ajoutant des activités exposées par les assemblys Windows PowerShell au concepteur de flux de travail dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f79d-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="0f79d-104">Les assemblys Windows PowerShell suivants exposent les activités compatibles avec les workflows.</span><span class="sxs-lookup"><span data-stu-id="0f79d-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f79d-105">Un flux de travail XAML doit être empaqueté en tant que module si vous souhaitez fournir de l’aide pour le Workflow.</span><span class="sxs-lookup"><span data-stu-id="0f79d-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="0f79d-106">Pour plus d’informations sur les modules, consultez [écriture d’un module Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="0f79d-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="0f79d-107">Microsoft. PowerShell. Activities</span><span class="sxs-lookup"><span data-stu-id="0f79d-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="0f79d-108">Microsoft. PowerShell. Core. Activities</span><span class="sxs-lookup"><span data-stu-id="0f79d-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="0f79d-109">Microsoft. PowerShell. Diagnostics. Activities</span><span class="sxs-lookup"><span data-stu-id="0f79d-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="0f79d-110">Microsoft. PowerShell. Management. Activities</span><span class="sxs-lookup"><span data-stu-id="0f79d-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="0f79d-111">Microsoft. PowerShell. Security. Activities</span><span class="sxs-lookup"><span data-stu-id="0f79d-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="0f79d-112">Microsoft. PowerShell. Utility. Activities</span><span class="sxs-lookup"><span data-stu-id="0f79d-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="0f79d-113">Les rubriques suivantes décrivent comment créer un flux de travail à l’aide d’activités Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f79d-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="0f79d-114">Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0f79d-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="0f79d-115">Création d’un workflow avec des activités Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f79d-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="0f79d-116">Création d’un workflow avec un script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f79d-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="0f79d-117">Importation et appel d’un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f79d-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="0f79d-118">Création d’une activité de workflow à partir d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f79d-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)
