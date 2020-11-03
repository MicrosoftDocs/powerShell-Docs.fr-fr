---
description: Décrit l' `Suspend-Workflow` activité, qui suspend le workflow dans lequel l’activité s’affiche.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Flux de travail about_Suspend
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207218"
---
# <a name="about-suspend-workflow"></a><span data-ttu-id="4d646-104">À propos de Suspend-Workflow</span><span class="sxs-lookup"><span data-stu-id="4d646-104">About Suspend-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="4d646-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="4d646-105">Short description</span></span>

<span data-ttu-id="4d646-106">Décrit l' `Suspend-Workflow` activité, qui suspend le workflow dans lequel l’activité s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4d646-106">Describes the `Suspend-Workflow` activity, which suspends the workflow in which the activity appears.</span></span>

## <a name="long-description"></a><span data-ttu-id="4d646-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="4d646-107">Long description</span></span>

<span data-ttu-id="4d646-108">L' `Suspend-Workflow` activité arrête temporairement le traitement du workflow à partir du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4d646-108">The `Suspend-Workflow` activity temporarily stops workflow processing from within the workflow.</span></span> <span data-ttu-id="4d646-109">Avant la suspension, le workflow Windows PowerShell prend un point de contrôle afin que l’État et les données du workflow soient conservés et que le flux de travail puisse reprendre à partir du point de suspension.</span><span class="sxs-lookup"><span data-stu-id="4d646-109">Before suspending, Windows PowerShell Workflow takes a checkpoint so the workflow's state and data are preserved and the workflow can resume from the suspension point.</span></span>

<span data-ttu-id="4d646-110">Pour reprendre le workflow, l’utilisateur qui exécute le workflow utilise l’applet de commande `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d646-110">To resume the workflow, the user running the workflow uses the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="4d646-111">Vous ne pouvez pas reprendre un workflow à partir du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4d646-111">You can't resume a workflow from within the workflow.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d646-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d646-112">Syntax</span></span>

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a><span data-ttu-id="4d646-113">Description détaillée</span><span class="sxs-lookup"><span data-stu-id="4d646-113">Detailed description</span></span>

<span data-ttu-id="4d646-114">Le `Suspend-Workflow` interrompt temporairement le workflow et retourne un objet de traitement qui représente la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="4d646-114">The `Suspend-Workflow` temporarily stops the workflow and returns a job object that represents the workflow job.</span></span> <span data-ttu-id="4d646-115">Un objet de traitement est retourné même si vous n’avez pas exécuté le workflow en tant que tâche.</span><span class="sxs-lookup"><span data-stu-id="4d646-115">A job object is returned even if you didn't run the workflow as a job.</span></span> <span data-ttu-id="4d646-116">Par exemple, en utilisant le paramètre commun de workflow **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="4d646-116">For example, such as by using the **AsJob** workflow common parameter.</span></span> <span data-ttu-id="4d646-117">L’état de la tâche est **suspendu** .</span><span class="sxs-lookup"><span data-stu-id="4d646-117">The job state is **Suspended** .</span></span>

<span data-ttu-id="4d646-118">Vous pouvez utiliser les applets de commande Job pour gérer la tâche de workflow suspendue.</span><span class="sxs-lookup"><span data-stu-id="4d646-118">You can use the job cmdlets to manage the suspended workflow job.</span></span> <span data-ttu-id="4d646-119">Pour reprendre la tâche de workflow, utilisez l’applet de commande `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d646-119">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span>

<span data-ttu-id="4d646-120">Lorsque vous reprenez la tâche de workflow, le workflow reprend à la commande qui suit l' `Suspend-Workflow` activité.</span><span class="sxs-lookup"><span data-stu-id="4d646-120">When you resume the workflow job, the workflow resumes at the command that follows the `Suspend-Workflow` activity.</span></span>

<span data-ttu-id="4d646-121">Par exemple, le flux de travail suivant comprend l' `Suspend-Workflow` activité.</span><span class="sxs-lookup"><span data-stu-id="4d646-121">For example, the following workflow includes the `Suspend-Workflow` activity.</span></span>
<span data-ttu-id="4d646-122">Lorsque vous exécutez le workflow, celui-ci exécute l' `Get-Date` activité, enregistre sa sortie dans la `$a` variable, puis suspend le workflow et retourne un objet de traitement qui représente le workflow suspendu.</span><span class="sxs-lookup"><span data-stu-id="4d646-122">When you run the workflow, it runs the `Get-Date` activity, saves its output in the `$a` variable, and then suspends the workflow, and returns a job object that represents the suspended workflow.</span></span> <span data-ttu-id="4d646-123">Le type de tâche est **PSWorkflowJob** .</span><span class="sxs-lookup"><span data-stu-id="4d646-123">The job type is **PSWorkflowJob** .</span></span>

<span data-ttu-id="4d646-124">Vous pouvez utiliser les applets de commande Job, telles que `Get-Job` , pour gérer la tâche de Workflow.</span><span class="sxs-lookup"><span data-stu-id="4d646-124">You can use the job cmdlets, such as `Get-Job`, to manage the workflow job.</span></span>

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a><span data-ttu-id="4d646-125">Reprise d’une tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="4d646-125">Resuming a workflow job</span></span>

<span data-ttu-id="4d646-126">Pour reprendre la tâche de workflow, utilisez l’applet de commande `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d646-126">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="4d646-127">L’applet de commande `Resume-Job` renvoie l’objet de traitement de workflow immédiatement, même si le workflow n’a pas encore repris.</span><span class="sxs-lookup"><span data-stu-id="4d646-127">The `Resume-Job` cmdlet returns the workflow job object immediately, even though it might not yet be resumed.</span></span> <span data-ttu-id="4d646-128">Pour attendre la reprise de la tâche, utilisez le paramètre **Wait** ou utilisez l' `Get-Job` applet de commande pour obtenir l’objet de traitement actuel.</span><span class="sxs-lookup"><span data-stu-id="4d646-128">To wait for the job to be resumed, use the **Wait** parameter, or use the `Get-Job` cmdlet to get the current job object.</span></span>

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a><span data-ttu-id="4d646-129">Obtention de la sortie d’une tâche de workflow</span><span class="sxs-lookup"><span data-stu-id="4d646-129">Getting the output of a workflow job</span></span>

<span data-ttu-id="4d646-130">Pour obtenir la sortie d’une tâche de workflow, utilisez l’applet de commande `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d646-130">To get the output of a workflow job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="4d646-131">La sortie indique que le flux de travail a repris au niveau de la commande qui a suivi l’applet de commande `Suspend-Workflow` .</span><span class="sxs-lookup"><span data-stu-id="4d646-131">The output shows that the workflow resumed at the command that followed the `Suspend-Workflow` cmdlet.</span></span> <span data-ttu-id="4d646-132">La valeur de la `$a` variable, qui a été remplie avant la suspension, est disponible pour le workflow lorsqu’elle reprend.</span><span class="sxs-lookup"><span data-stu-id="4d646-132">The value of the `$a` variable, which was populated before the suspension, is available to the workflow when it resumes.</span></span>

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a><span data-ttu-id="4d646-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d646-133">See also</span></span>

[<span data-ttu-id="4d646-134">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="4d646-134">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="4d646-135">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d646-135">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="4d646-136">Applets de commande [PSWorkflow](xref:PSWorkflow)</span><span class="sxs-lookup"><span data-stu-id="4d646-136">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="4d646-137">Guide des workflows</span><span class="sxs-lookup"><span data-stu-id="4d646-137">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="4d646-138">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d646-138">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
