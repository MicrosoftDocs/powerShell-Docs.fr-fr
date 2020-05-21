---
title: Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: ecd23d3eb722137bdda0498fc71e0e966c57a589
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561187"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="93617-102">Ajout d’activités Windows PowerShell à la boîte à outils Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93617-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="93617-103">Avant de créer un flux de travail PowerShell à l’aide de Concepteur de flux de travail, vous devez d’abord ajouter les activités PowerShell à la boîte à outils dans un projet d’application console de flux de travail Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93617-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="93617-104">La procédure suivante montre comment ajouter les activités de l’assembly Microsoft. PowerShell. Core. Activities à la boîte à outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93617-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="93617-105">Ajout d’activités Windows PowerShell à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="93617-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="93617-106">Créez un projet d’application console de workflow dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93617-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="93617-107">Dans le menu **Affichage** , cliquez sur **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="93617-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="93617-108">Ajoutez un nouvel onglet dans la boîte à outils en cliquant avec le bouton droit dans la boîte à outils, puis en cliquant sur **Ajouter un onglet**, et donnez un nom au nouvel onglet, par exemple « activités PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="93617-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="93617-109">L’ajout d’un onglet vous permet de regrouper les activités PowerShell séparées des autres outils de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="93617-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="93617-110">Dans l’onglet nouvelle boîte à outils, cliquez sur **choisir les éléments...**. La boîte de dialogue **choisir des éléments de boîte à outils** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="93617-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="93617-111">Dans la boîte de dialogue **choisir des éléments de boîte à outils** , cliquez sur l’onglet **System. Activities** .</span><span class="sxs-lookup"><span data-stu-id="93617-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="93617-112">Cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="93617-112">Click **Browse**.</span></span>

7. <span data-ttu-id="93617-113">Accédez au dossier%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e, puis double-cliquez sur Microsoft. PowerShell. Core. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="93617-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="93617-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="93617-114">Click **OK**.</span></span> <span data-ttu-id="93617-115">Les activités définies par l’assembly Microsoft. PowerShell. Core. Activities sont désormais disponibles dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="93617-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="93617-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93617-116">See Also</span></span>

[<span data-ttu-id="93617-117">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="93617-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="93617-118">Création d’un workflow avec des activités Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="93617-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)
