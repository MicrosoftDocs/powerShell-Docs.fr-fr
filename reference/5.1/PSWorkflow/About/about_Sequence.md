---
description: Décrit le `Sequence` mot clé qui exécute les activités sélectionnées de manière séquentielle.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207229"
---
# <a name="about-sequence"></a><span data-ttu-id="2bc6f-104">À propos de la séquence</span><span class="sxs-lookup"><span data-stu-id="2bc6f-104">About Sequence</span></span>

## <a name="short-description"></a><span data-ttu-id="2bc6f-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="2bc6f-105">Short description</span></span>

<span data-ttu-id="2bc6f-106">Décrit le `Sequence` mot clé qui exécute les activités sélectionnées de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-106">Describes the `Sequence` keyword that runs selected activities sequentially.</span></span>

## <a name="long-description"></a><span data-ttu-id="2bc6f-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="2bc6f-107">Long description</span></span>

<span data-ttu-id="2bc6f-108">Le `Sequence` mot clé exécute les activités de workflow sélectionnées de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-108">The `Sequence` keyword runs selected workflow activities sequentially.</span></span> <span data-ttu-id="2bc6f-109">Les activités de flux de travail s’exécutent dans l’ordre dans lequel elles apparaissent et ne s’exécutent pas simultanément.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-109">Workflow activities run in the order that they appear and do not run concurrently.</span></span> <span data-ttu-id="2bc6f-110">Le `Sequence` mot clé est valide uniquement dans un flux de travail PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-110">The `Sequence` keyword is only valid in a PowerShell Workflow.</span></span>

<span data-ttu-id="2bc6f-111">Le `Sequence` mot clé est utilisé dans un `Parallel` bloc de script pour exécuter les commandes sélectionnées de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-111">The `Sequence` keyword is used in a `Parallel` script block to run selected commands sequentially.</span></span>

<span data-ttu-id="2bc6f-112">Étant donné que les activités de flux de travail s’exécutent de façon séquentielle par défaut, le `Sequence` mot clé n’est effectif que dans un `Parallel` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-112">Because workflow activities run sequentially by default, the `Sequence` keyword is only effective in a `Parallel` script block.</span></span> <span data-ttu-id="2bc6f-113">Si le `Sequence` mot clé n’est pas inclus dans un `Parallel` bloc de script, il est valide mais inefficace.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-113">If the `Sequence` keyword isn't included in a `Parallel` script block, it's valid but ineffective.</span></span>

<span data-ttu-id="2bc6f-114">Le `Sequence` bloc de script vous permet d’exécuter davantage de commandes en parallèle en vous permettant d’exécuter des commandes dépendantes de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-114">The `Sequence` script block lets you run more commands in parallel by allowing you to run dependent commands sequentially.</span></span>

## <a name="syntax"></a><span data-ttu-id="2bc6f-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bc6f-115">Syntax</span></span>

### <a name="workflow-using-sequence"></a><span data-ttu-id="2bc6f-116">Workflow à l’aide d’une séquence</span><span class="sxs-lookup"><span data-stu-id="2bc6f-116">Workflow using Sequence</span></span>

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a><span data-ttu-id="2bc6f-117">Workflow utilisant Parallel et Sequence</span><span class="sxs-lookup"><span data-stu-id="2bc6f-117">Workflow using Parallel and Sequence</span></span>

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a><span data-ttu-id="2bc6f-118">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="2bc6f-118">Detailed description</span></span>

<span data-ttu-id="2bc6f-119">Les commandes figurant dans un bloc de script `Parallel` peuvent s’exécuter simultanément.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-119">The commands in a `Parallel` script block can run concurrently.</span></span> <span data-ttu-id="2bc6f-120">L'ordre dans lequel elles s'exécutent n'est pas déterminé.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-120">The order in which they run is not determined.</span></span> <span data-ttu-id="2bc6f-121">Cette fonctionnalité améliore les performances d’un workflow de script.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-121">This feature improves the performance of a script workflow.</span></span>

<span data-ttu-id="2bc6f-122">Vous pouvez utiliser un `Sequence` bloc de script pour exécuter des activités sélectionnées de manière séquentielle, même si les activités s’affichent dans un `Parallel` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-122">You can use a `Sequence` script block to run selected activities sequentially, even though the activities appear in a `Parallel` script block.</span></span>

<span data-ttu-id="2bc6f-123">Les activités d’un `Sequence` bloc de script s’exécutent consécutivement dans l’ordre dans lequel elles sont répertoriées.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-123">The activities in a `Sequence` script block run consecutively in the order that they are listed.</span></span> <span data-ttu-id="2bc6f-124">Une activité dans un `Sequence` bloc de script démarre uniquement après la fin de l’activité précédente.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-124">An activity in a `Sequence` script block starts only after the previous activity completes.</span></span>

<span data-ttu-id="2bc6f-125">Toutefois, lorsque le `Sequence` bloc de script apparaît dans un bloc de script `Parallel` , l’ordre dans lequel le `Sequence` bloc de script s’exécute n’est pas déterminé.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-125">However, when the `Sequence` script block appears in a `Parallel` script block, the order in which the `Sequence` script block runs isn't determined.</span></span> <span data-ttu-id="2bc6f-126">Elle peut s’exécuter avant, après ou simultanément avec d’autres activités dans le `Parallel` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-126">It might run before, after, or concurrent with other activities in the `Parallel` script block.</span></span>

<span data-ttu-id="2bc6f-127">Par exemple, le flux de travail suivant comprend un `Parallel` bloc de script qui exécute des activités qui obtiennent des processus et des services sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-127">For example, the following workflow includes a `Parallel` script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="2bc6f-128">Le `Parallel` bloc de script contient un `Sequence` bloc de script qui obtient des informations à partir d’un fichier et utilise les informations comme entrée d’un script.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-128">The `Parallel` script block contains a `Sequence` script block that gets information from a file and uses the information as input to a script.</span></span>

<span data-ttu-id="2bc6f-129">Les `Get-Process` `Get-Service` commandes relatives aux correctifs logiciels, et sont indépendantes les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-129">The `Get-Process`, `Get-Service`, and hotfix-related commands are independent of each other.</span></span> <span data-ttu-id="2bc6f-130">Les commandes peuvent s’exécuter simultanément ou dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-130">The commands can run concurrently or in any order.</span></span> <span data-ttu-id="2bc6f-131">Toutefois, la commande qui obtient les informations de correctif logiciel doit s’exécuter avant la commande qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="2bc6f-131">But, the command that gets the hotfix information must run before the command that uses it.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="2bc6f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bc6f-132">See also</span></span>

[<span data-ttu-id="2bc6f-133">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="2bc6f-133">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="2bc6f-134">about_ForEach-parallèle</span><span class="sxs-lookup"><span data-stu-id="2bc6f-134">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="2bc6f-135">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="2bc6f-135">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="2bc6f-136">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="2bc6f-136">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="2bc6f-137">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="2bc6f-137">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="2bc6f-138">Création d’un workflow avec un script Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bc6f-138">Creating a Workflow by Using a Windows PowerShell Script</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
