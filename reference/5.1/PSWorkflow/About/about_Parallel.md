---
description: Décrit le mot clé Parallel, qui exécute les activités dans un workflow en parallèle.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207233"
---
# <a name="about-parallel"></a><span data-ttu-id="8be8b-104">À propos de Parallel</span><span class="sxs-lookup"><span data-stu-id="8be8b-104">About Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="8be8b-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="8be8b-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8be8b-106">Décrit le mot clé Parallel, qui exécute les activités dans un workflow en parallèle.</span><span class="sxs-lookup"><span data-stu-id="8be8b-106">Describes the Parallel keyword, which runs the activities in a workflow in parallel.</span></span>

## <a name="long-description"></a><span data-ttu-id="8be8b-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="8be8b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8be8b-108">Le mot clé Parallel exécute les activités de workflow en parallèle.</span><span class="sxs-lookup"><span data-stu-id="8be8b-108">The Parallel keyword runs workflow activities in parallel.</span></span> <span data-ttu-id="8be8b-109">Ce mot clé est valide uniquement dans le workflow Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8be8b-109">This keyword is valid only in  Windows PowerShell  Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="8be8b-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8be8b-110">SYNTAX</span></span>

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a><span data-ttu-id="8be8b-111">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="8be8b-111">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="8be8b-112">Les commandes figurant dans un bloc de script Parallel peuvent s'exécuter simultanément.</span><span class="sxs-lookup"><span data-stu-id="8be8b-112">The commands in a Parallel script block can run concurrently.</span></span> <span data-ttu-id="8be8b-113">L'ordre dans lequel elles s'exécutent n'est pas déterminé.</span><span class="sxs-lookup"><span data-stu-id="8be8b-113">The order in which they run is not determined.</span></span>

<span data-ttu-id="8be8b-114">Par exemple, le workflow suivant inclut un bloc de script Parallel qui exécute des activités qui obtiennent des processus et des services sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8be8b-114">For example, the following workflow includes a Parallel script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="8be8b-115">Étant donné que les commandes Get-Process et Get-Service sont indépendantes les unes des autres, elles peuvent s’exécuter simultanément et dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="8be8b-115">Because the Get-Process and Get-Service commands are independent of each other, they can run concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

<span data-ttu-id="8be8b-116">L’exécution de commandes en parallèle est très efficace et réduit le temps nécessaire pour effectuer un flux de travail de manière significative.</span><span class="sxs-lookup"><span data-stu-id="8be8b-116">Running commands in parallel is very efficient and reduces the time it takes to complete a workflow significantly.</span></span>

<span data-ttu-id="8be8b-117">Pour exécuter des commandes sélectionnées dans un bloc de script parallèle dans l’ordre séquentiel, utilisez le mot clé Sequence.</span><span class="sxs-lookup"><span data-stu-id="8be8b-117">To run selected commands in a Parallel script block in sequential order, use the Sequence keyword.</span></span> <span data-ttu-id="8be8b-118">Pour plus d’informations, consultez about_Sequence.</span><span class="sxs-lookup"><span data-stu-id="8be8b-118">For more information, see about_Sequence.</span></span>

<span data-ttu-id="8be8b-119">Pour exécuter un bloc de script parallèle sur les éléments d’une collection, utilisez les mots clés ForEach ou ForEach-Parallel.</span><span class="sxs-lookup"><span data-stu-id="8be8b-119">To run a Parallel script block on items in a collection, use the ForEach or ForEach -Parallel keywords.</span></span>

## <a name="see-also"></a><span data-ttu-id="8be8b-120">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="8be8b-120">SEE ALSO</span></span>

<span data-ttu-id="8be8b-121">[« Écriture d’un workflow de script »](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="8be8b-121">["Writing a Script Workflow"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span></span>

[<span data-ttu-id="8be8b-122">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="8be8b-122">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="8be8b-123">about_ForEach-parallèle</span><span class="sxs-lookup"><span data-stu-id="8be8b-123">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="8be8b-124">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="8be8b-124">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="8be8b-125">about_Sequence</span><span class="sxs-lookup"><span data-stu-id="8be8b-125">about_Sequence</span></span>](about_Sequence.md)

[<span data-ttu-id="8be8b-126">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="8be8b-126">about_Workflows</span></span>](about_workflows.md)
