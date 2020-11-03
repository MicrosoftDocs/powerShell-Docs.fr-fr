---
description: Décrit l’activité Checkpoint-Workflow, qui prend un point de contrôle dans un Workflow.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_checkpoint-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Flux de travail about_Checkpoint
ms.openlocfilehash: 223deb07ff6ed387cf04736116ea0ce3f998bb59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207242"
---
# <a name="about-checkpoint-workflow"></a>À propos de Checkpoint-Workflow

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit l’activité Checkpoint-Workflow, qui prend un point de contrôle dans un Workflow.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L’activité Checkpoint-Workflow prend un point de contrôle qui enregistre l’État et les données dans le Workflow. Si le workflow est suspendu ou interrompu, il peut être repris à partir du point de contrôle le plus récent, au lieu de devoir être redémarré.

L’activité Checkpoint-Workflow est valide uniquement dans un flux de travail.

### <a name="syntax"></a>SYNTAX

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

L’activité Checkpoint-Workflow n’accepte aucun paramètre, y compris les paramètres communs et les paramètres communs de Workflow.

Vous pouvez placer le point de contrôle Checkpoint-Activity n’importe où dans un workflow après l’instruction CmdletBinding ou param. Toutefois, lorsque vous placez des points de contrôle, tenez compte des performances de la collecte des données et de leur écriture sur le disque de l’ordinateur qui exécute le Workflow.

Le temps nécessaire pour relancer une section du workflow s’il est interrompu est plus long que le temps nécessaire pour écrire l’état et les données du point de contrôle sur le disque.

Envisagez de prendre des points de contrôle après les étapes critiques afin que le flux de travail puisse reprendre plutôt que de redémarrer. Par exemple, prenez un point de contrôle après des commandes qui ne sont pas idempotent.

### <a name="about-checkpoints"></a>À PROPOS DES POINTS DE CONTRÔLE

Un point de contrôle est un instantané de l’état du workflow, avec les valeurs des variables et tout résultat généré jusqu’à ce stade. Tout est enregistré sur le disque.

Si un workflow est interrompu, intentionnellement ou involontairement, le workflow Windows PowerShell utilise automatiquement les données du dernier point de contrôle pour récupérer et reprendre le flux de travail.

Lorsque vous exécutez le workflow en tant que tâche, par exemple à l’aide du paramètre commun de workflow AsJob, les points de contrôle de workflow sont conservés jusqu’à ce que vous supprimiez le travail, par exemple à l’aide de l’applet de commande Remove-Job.
Dans le cas contraire, les points de contrôle de flux de travail sont supprimés à la fin du flux de travail.

### <a name="other-checkpointing-techniques"></a>AUTRES TECHNIQUES DE POINT DE CONTRÔLE

Outre l’activité Checkpoint-Workflow, le workflow Windows PowerShell prend en charge d’autres techniques de contrôle de point de contrôle, notamment les suivantes :

- Paramètre commun de workflow PSPersist
- Paramètre commun d’activité PSPersist
- Variable PSPersistPreference (dans un flux de travail)

Pour plus d’informations sur l’ajout d’un point de contrôle à un workflow, consultez « Comment ajouter des points de contrôle à un flux de travail ».

## <a name="examples"></a>EXEMPLES

Le flux de travail suivant comprend un appel à l’activité Checkpoint-Workflow après avoir effectué une fonction longue et un script qui partagent des données.

```powershell
Workflow Test-Workflow
{
    $a = Invoke-LongRunningFunction
    InlineScript { \\Server\Share\Get-DataPacks.ps1 $Using:a}
    Checkpoint-Workflow

    Invoke-LongRunningFunction
    {
        ...
    }
}
```

## <a name="see-also"></a>VOIR AUSSI

[Écriture d'un workflow Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
