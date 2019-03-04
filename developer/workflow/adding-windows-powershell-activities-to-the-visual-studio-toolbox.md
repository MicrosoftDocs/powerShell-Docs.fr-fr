---
title: Ajout d’activités de Windows PowerShell à la boîte à outils Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863565"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="80605-102">Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio</span><span class="sxs-lookup"><span data-stu-id="80605-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="80605-103">Avant de créer un PowerShell Workflow à l’aide du Concepteur de flux de travail, vous devez d’abord ajouter les activités de PowerShell à la boîte à outils dans un projet d’application console Visual Studio Workflow.</span><span class="sxs-lookup"><span data-stu-id="80605-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="80605-104">La procédure suivante montre comment ajouter des activités à partir de l’assembly Microsoft.PowerShell.Core.Activities à la boîte à outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80605-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="80605-105">Ajout d’activités de Windows PowerShell à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="80605-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="80605-106">Créer un nouveau projet d’application de console du flux de travail dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80605-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="80605-107">Sur le **vue** menu, cliquez sur **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="80605-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="80605-108">Ajouter un nouvel onglet dans la boîte à outils en cliquant à l’intérieur de la boîte à outils, en cliquant sur **ajouter un onglet**et nommez le nouvel onglet tels que « Activités PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="80605-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="80605-109">Ajout d’un onglet vous permet de regrouper les activités PowerShell distinct à partir d’autres outils dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="80605-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="80605-110">Dans le nouvel onglet de boîte à outils, cliquez sur **choisir des éléments...** . Le **Choose Toolbox Items** boîte de dialogue apparaît.</span><span class="sxs-lookup"><span data-stu-id="80605-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="80605-111">Dans le **Choose Toolbox Items** boîte de dialogue, cliquez sur le **System.Activities** onglet.</span><span class="sxs-lookup"><span data-stu-id="80605-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="80605-112">Cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="80605-112">Click **Browse**.</span></span>

7. <span data-ttu-id="80605-113">Accédez au dossier %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e et double-cliquez sur Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="80605-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="80605-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80605-114">Click **OK**.</span></span> <span data-ttu-id="80605-115">Les activités définies par l’assembly Microsoft.PowerShell.Core.Activities sont maintenant disponibles dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="80605-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="80605-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80605-116">See Also</span></span>

[<span data-ttu-id="80605-117">Écriture d’un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80605-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="80605-118">Création d’un flux de travail avec Windows PowerShell activités</span><span class="sxs-lookup"><span data-stu-id="80605-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)