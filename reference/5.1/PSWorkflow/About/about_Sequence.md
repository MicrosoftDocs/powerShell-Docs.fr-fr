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
# <a name="about-sequence"></a>À propos de la séquence

## <a name="short-description"></a>Description courte

Décrit le `Sequence` mot clé qui exécute les activités sélectionnées de manière séquentielle.

## <a name="long-description"></a>Description longue

Le `Sequence` mot clé exécute les activités de workflow sélectionnées de manière séquentielle. Les activités de flux de travail s’exécutent dans l’ordre dans lequel elles apparaissent et ne s’exécutent pas simultanément. Le `Sequence` mot clé est valide uniquement dans un flux de travail PowerShell.

Le `Sequence` mot clé est utilisé dans un `Parallel` bloc de script pour exécuter les commandes sélectionnées de manière séquentielle.

Étant donné que les activités de flux de travail s’exécutent de façon séquentielle par défaut, le `Sequence` mot clé n’est effectif que dans un `Parallel` bloc de script. Si le `Sequence` mot clé n’est pas inclus dans un `Parallel` bloc de script, il est valide mais inefficace.

Le `Sequence` bloc de script vous permet d’exécuter davantage de commandes en parallèle en vous permettant d’exécuter des commandes dépendantes de manière séquentielle.

## <a name="syntax"></a>Syntaxe

### <a name="workflow-using-sequence"></a>Workflow à l’aide d’une séquence

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

### <a name="workflow-using-parallel-and-sequence"></a>Workflow utilisant Parallel et Sequence

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

## <a name="detailed-description"></a>Description détaillée

Les commandes figurant dans un bloc de script `Parallel` peuvent s’exécuter simultanément. L'ordre dans lequel elles s'exécutent n'est pas déterminé. Cette fonctionnalité améliore les performances d’un workflow de script.

Vous pouvez utiliser un `Sequence` bloc de script pour exécuter des activités sélectionnées de manière séquentielle, même si les activités s’affichent dans un `Parallel` bloc de script.

Les activités d’un `Sequence` bloc de script s’exécutent consécutivement dans l’ordre dans lequel elles sont répertoriées. Une activité dans un `Sequence` bloc de script démarre uniquement après la fin de l’activité précédente.

Toutefois, lorsque le `Sequence` bloc de script apparaît dans un bloc de script `Parallel` , l’ordre dans lequel le `Sequence` bloc de script s’exécute n’est pas déterminé. Elle peut s’exécuter avant, après ou simultanément avec d’autres activités dans le `Parallel` bloc de script.

Par exemple, le flux de travail suivant comprend un `Parallel` bloc de script qui exécute des activités qui obtiennent des processus et des services sur l’ordinateur. Le `Parallel` bloc de script contient un `Sequence` bloc de script qui obtient des informations à partir d’un fichier et utilise les informations comme entrée d’un script.

Les `Get-Process` `Get-Service` commandes relatives aux correctifs logiciels, et sont indépendantes les unes des autres. Les commandes peuvent s’exécuter simultanément ou dans n’importe quel ordre. Toutefois, la commande qui obtient les informations de correctif logiciel doit s’exécuter avant la commande qui l’utilise.

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

## <a name="see-also"></a>Voir aussi

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-parallèle](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)

[Création d’un workflow avec un script Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
