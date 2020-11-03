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
# <a name="about-parallel"></a>À propos de Parallel

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit le mot clé Parallel, qui exécute les activités dans un workflow en parallèle.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le mot clé Parallel exécute les activités de workflow en parallèle. Ce mot clé est valide uniquement dans le workflow Windows PowerShell.

### <a name="syntax"></a>SYNTAX

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

## <a name="detailed-description"></a>DESCRIPTION DÉTAILLÉE

Les commandes figurant dans un bloc de script Parallel peuvent s'exécuter simultanément. L'ordre dans lequel elles s'exécutent n'est pas déterminé.

Par exemple, le workflow suivant inclut un bloc de script Parallel qui exécute des activités qui obtiennent des processus et des services sur l'ordinateur. Étant donné que les commandes Get-Process et Get-Service sont indépendantes les unes des autres, elles peuvent s’exécuter simultanément et dans n’importe quel ordre.

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

L’exécution de commandes en parallèle est très efficace et réduit le temps nécessaire pour effectuer un flux de travail de manière significative.

Pour exécuter des commandes sélectionnées dans un bloc de script parallèle dans l’ordre séquentiel, utilisez le mot clé Sequence. Pour plus d’informations, consultez about_Sequence.

Pour exécuter un bloc de script parallèle sur les éléments d’une collection, utilisez les mots clés ForEach ou ForEach-Parallel.

## <a name="see-also"></a>VOIR AUSSI

[« Écriture d’un workflow de script »](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-parallèle](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Sequence](about_Sequence.md)

[about_Workflows](about_workflows.md)
