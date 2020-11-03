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
# <a name="about-foreach-parallel"></a>À propos de Foreach-Parallel

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit la `ForEach -Parallel` construction de langage dans le workflow Windows PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le paramètre **Parallel** du `ForEach` mot clé exécute les commandes dans un `ForEach` bloc de script une fois pour chaque élément d’une collection spécifiée.

Les éléments de la collection, tels qu’un disque dans une collection de disques, sont traités en parallèle. Les commandes du bloc de script s’exécutent de façon séquentielle sur chaque élément de la collection.

`ForEach -Parallel` est valide uniquement dans un flux de travail Windows PowerShell.

### <a name="syntax"></a>SYNTAX

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a>DESCRIPTION DÉTAILLÉE

À l’instar de l’instruction ForEach dans Windows PowerShell, la variable qui contient la collection `$<collection>` doit être définie avant l' `ForEach -Parallel` instruction, mais la variable qui représente l’élément actuel `$<item>` est définie dans l' `ForEach -Parallel` instruction.

La `ForEach -Parallel` construction est différente du `ForEach` mot clé et du paramètre **Parallel** . Le `ForEach` mot clé traite les éléments de la collection dans l’ordre. Le paramètre **Parallel** exécute des commandes dans un bloc de script en parallèle. Vous pouvez placer un bloc de script parallèle dans un `ForEach -Parallel` bloc de script.

Les ordinateurs cibles dans un workflow, tels que ceux spécifiés par le paramètre commun de workflow **PSComputerName** , sont toujours traités en parallèle.
Vous n’avez pas besoin de spécifier le `ForEach -Parallel` mot clé à cet effet.

### <a name="examples"></a>EXEMPLES

Le flux de travail suivant contient une `ForEach -Parallel` instruction qui traite les disques que l' `Get-Disk` activité obtient. Les commandes du `ForEach -Parallel` bloc de script s’exécutent de manière séquentielle, mais elles s’exécutent sur les disques en parallèle. Les disques peuvent être traités simultanément et dans n’importe quel ordre.

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

## <a name="see-also"></a>VOIR AUSSI

[Writing a Script Workflow](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)
