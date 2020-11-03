---
description: Décrit la `ForEach -Parallel` construction de langage dans le workflow Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach parallèle
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207241"
---
# <a name="about-foreach-parallel"></a><span data-ttu-id="280a4-104">À propos de Foreach-Parallel</span><span class="sxs-lookup"><span data-stu-id="280a4-104">About Foreach-Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="280a4-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="280a4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="280a4-106">Décrit la `ForEach -Parallel` construction de langage dans le workflow Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="280a4-106">Describes the `ForEach -Parallel` language construct in Windows PowerShell Workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="280a4-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="280a4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="280a4-108">Le paramètre **Parallel** du `ForEach` mot clé exécute les commandes dans un `ForEach` bloc de script une fois pour chaque élément d’une collection spécifiée.</span><span class="sxs-lookup"><span data-stu-id="280a4-108">The **Parallel** parameter of the `ForEach` keyword runs the commands in a `ForEach` script block once for each item in a specified collection.</span></span>

<span data-ttu-id="280a4-109">Les éléments de la collection, tels qu’un disque dans une collection de disques, sont traités en parallèle.</span><span class="sxs-lookup"><span data-stu-id="280a4-109">The items in the collection, such as a disk in a collection of disks, are processed in parallel.</span></span> <span data-ttu-id="280a4-110">Les commandes du bloc de script s’exécutent de façon séquentielle sur chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="280a4-110">The commands in the script block run sequentially on each item in the collection.</span></span>

<span data-ttu-id="280a4-111">`ForEach -Parallel` est valide uniquement dans un flux de travail Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="280a4-111">`ForEach -Parallel` is valid only in a Windows PowerShell Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="280a4-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="280a4-112">SYNTAX</span></span>

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a><span data-ttu-id="280a4-113">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="280a4-113">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="280a4-114">À l’instar de l’instruction ForEach dans Windows PowerShell, la variable qui contient la collection `$<collection>` doit être définie avant l' `ForEach -Parallel` instruction, mais la variable qui représente l’élément actuel `$<item>` est définie dans l' `ForEach -Parallel` instruction.</span><span class="sxs-lookup"><span data-stu-id="280a4-114">Like the ForEach statement in Windows PowerShell, the variable that contains collection `$<collection>` must be defined before the `ForEach -Parallel` statement, but the variable that represents the current item `$<item>` is defined in the `ForEach -Parallel` statement.</span></span>

<span data-ttu-id="280a4-115">La `ForEach -Parallel` construction est différente du `ForEach` mot clé et du paramètre **Parallel** .</span><span class="sxs-lookup"><span data-stu-id="280a4-115">The `ForEach -Parallel` construct is different from the `ForEach` keyword and the **Parallel** parameter.</span></span> <span data-ttu-id="280a4-116">Le `ForEach` mot clé traite les éléments de la collection dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="280a4-116">The `ForEach` keyword processes the items in the collection in sequence.</span></span> <span data-ttu-id="280a4-117">Le paramètre **Parallel** exécute des commandes dans un bloc de script en parallèle.</span><span class="sxs-lookup"><span data-stu-id="280a4-117">The **Parallel** parameter runs commands in a script block in parallel.</span></span> <span data-ttu-id="280a4-118">Vous pouvez placer un bloc de script parallèle dans un `ForEach -Parallel` bloc de script.</span><span class="sxs-lookup"><span data-stu-id="280a4-118">You can enclose a Parallel script block in a `ForEach -Parallel` script block.</span></span>

<span data-ttu-id="280a4-119">Les ordinateurs cibles dans un workflow, tels que ceux spécifiés par le paramètre commun de workflow **PSComputerName** , sont toujours traités en parallèle.</span><span class="sxs-lookup"><span data-stu-id="280a4-119">The target computers in a workflow, such as those specified by the **PSComputerName** workflow common parameter, are always processed in parallel.</span></span>
<span data-ttu-id="280a4-120">Vous n’avez pas besoin de spécifier le `ForEach -Parallel` mot clé à cet effet.</span><span class="sxs-lookup"><span data-stu-id="280a4-120">You do not need to specify the `ForEach -Parallel` keyword for this purpose.</span></span>

### <a name="examples"></a><span data-ttu-id="280a4-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="280a4-121">EXAMPLES</span></span>

<span data-ttu-id="280a4-122">Le flux de travail suivant contient une `ForEach -Parallel` instruction qui traite les disques que l' `Get-Disk` activité obtient.</span><span class="sxs-lookup"><span data-stu-id="280a4-122">The following workflow contains a `ForEach -Parallel` statement that processes the disks that the `Get-Disk` activity gets.</span></span> <span data-ttu-id="280a4-123">Les commandes du `ForEach -Parallel` bloc de script s’exécutent de manière séquentielle, mais elles s’exécutent sur les disques en parallèle.</span><span class="sxs-lookup"><span data-stu-id="280a4-123">The commands in the `ForEach -Parallel` script block run sequentially, but they run on the disks in parallel.</span></span> <span data-ttu-id="280a4-124">Les disques peuvent être traités simultanément et dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="280a4-124">The disks might be processed concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="280a4-125">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="280a4-125">SEE ALSO</span></span>

[<span data-ttu-id="280a4-126">Writing a Script Workflow</span><span class="sxs-lookup"><span data-stu-id="280a4-126">Writing a Script Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[<span data-ttu-id="280a4-127">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="280a4-127">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[<span data-ttu-id="280a4-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="280a4-128">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="280a4-129">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="280a4-129">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="280a4-130">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="280a4-130">about_Workflows</span></span>](about_Workflows.md)
