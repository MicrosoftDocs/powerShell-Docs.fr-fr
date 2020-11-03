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
# <a name="about-checkpoint-workflow"></a><span data-ttu-id="b155c-104">À propos de Checkpoint-Workflow</span><span class="sxs-lookup"><span data-stu-id="b155c-104">About Checkpoint-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="b155c-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="b155c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b155c-106">Décrit l’activité Checkpoint-Workflow, qui prend un point de contrôle dans un Workflow.</span><span class="sxs-lookup"><span data-stu-id="b155c-106">Describes the Checkpoint-Workflow activity, which takes a checkpoint in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="b155c-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="b155c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b155c-108">L’activité Checkpoint-Workflow prend un point de contrôle qui enregistre l’État et les données dans le Workflow.</span><span class="sxs-lookup"><span data-stu-id="b155c-108">The Checkpoint-Workflow activity takes a checkpoint, which saves state and data in the workflow.</span></span> <span data-ttu-id="b155c-109">Si le workflow est suspendu ou interrompu, il peut être repris à partir du point de contrôle le plus récent, au lieu de devoir être redémarré.</span><span class="sxs-lookup"><span data-stu-id="b155c-109">If the workflow is suspended or interrupted, it can be resumed from the most recent checkpoint, rather than having to be restarted.</span></span>

<span data-ttu-id="b155c-110">L’activité Checkpoint-Workflow est valide uniquement dans un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="b155c-110">The Checkpoint-Workflow activity is valid only in a workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="b155c-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b155c-111">SYNTAX</span></span>

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

<span data-ttu-id="b155c-112">L’activité Checkpoint-Workflow n’accepte aucun paramètre, y compris les paramètres communs et les paramètres communs de Workflow.</span><span class="sxs-lookup"><span data-stu-id="b155c-112">The Checkpoint-Workflow activity does not accept any parameters, including common parameters and workflow common parameters.</span></span>

<span data-ttu-id="b155c-113">Vous pouvez placer le point de contrôle Checkpoint-Activity n’importe où dans un workflow après l’instruction CmdletBinding ou param.</span><span class="sxs-lookup"><span data-stu-id="b155c-113">You can place the Checkpoint-Activity checkpoint anywhere in a workflow after the CmdletBinding or Param statement.</span></span> <span data-ttu-id="b155c-114">Toutefois, lorsque vous placez des points de contrôle, tenez compte des performances de la collecte des données et de leur écriture sur le disque de l’ordinateur qui exécute le Workflow.</span><span class="sxs-lookup"><span data-stu-id="b155c-114">However, when placing checkpoints, consider the performance cost of collecting the data and writing it to disk on the computer that is running the workflow.</span></span>

<span data-ttu-id="b155c-115">Le temps nécessaire pour relancer une section du workflow s’il est interrompu est plus long que le temps nécessaire pour écrire l’état et les données du point de contrôle sur le disque.</span><span class="sxs-lookup"><span data-stu-id="b155c-115">Be sure that the time it takes to rerun a section of the workflow if it is interrupted is greater than the time it takes to write the checkpoint state and data to disk.</span></span>

<span data-ttu-id="b155c-116">Envisagez de prendre des points de contrôle après les étapes critiques afin que le flux de travail puisse reprendre plutôt que de redémarrer.</span><span class="sxs-lookup"><span data-stu-id="b155c-116">Consider taking checkpoints after critical steps so the workflow can be resumed rather than restarted.</span></span> <span data-ttu-id="b155c-117">Par exemple, prenez un point de contrôle après des commandes qui ne sont pas idempotent.</span><span class="sxs-lookup"><span data-stu-id="b155c-117">For example, take a checkpoint after commands that are not idempotent.</span></span>

### <a name="about-checkpoints"></a><span data-ttu-id="b155c-118">À PROPOS DES POINTS DE CONTRÔLE</span><span class="sxs-lookup"><span data-stu-id="b155c-118">ABOUT CHECKPOINTS</span></span>

<span data-ttu-id="b155c-119">Un point de contrôle est un instantané de l’état du workflow, avec les valeurs des variables et tout résultat généré jusqu’à ce stade. Tout est enregistré sur le disque.</span><span class="sxs-lookup"><span data-stu-id="b155c-119">A checkpoint is a snapshot of the current state of the workflow, including the current values of variables, and any output generated up to that point, and it saves it to disk.</span></span>

<span data-ttu-id="b155c-120">Si un workflow est interrompu, intentionnellement ou involontairement, le workflow Windows PowerShell utilise automatiquement les données du dernier point de contrôle pour récupérer et reprendre le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="b155c-120">If a workflow is interrupted, intentionally or unintentionally, Windows PowerShell Workflow automatically uses the data in newest checkpoint to recover and resume the workflow.</span></span>

<span data-ttu-id="b155c-121">Lorsque vous exécutez le workflow en tant que tâche, par exemple à l’aide du paramètre commun de workflow AsJob, les points de contrôle de workflow sont conservés jusqu’à ce que vous supprimiez le travail, par exemple à l’aide de l’applet de commande Remove-Job.</span><span class="sxs-lookup"><span data-stu-id="b155c-121">When you run the workflow as a job, such as by using the AsJob workflow common parameter, the workflow checkpoints are retained until you delete the job, such as by using the Remove-Job cmdlet.</span></span>
<span data-ttu-id="b155c-122">Dans le cas contraire, les points de contrôle de flux de travail sont supprimés à la fin du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="b155c-122">Otherwise, workflow checkpoints are deleted when the workflow completes.</span></span>

### <a name="other-checkpointing-techniques"></a><span data-ttu-id="b155c-123">AUTRES TECHNIQUES DE POINT DE CONTRÔLE</span><span class="sxs-lookup"><span data-stu-id="b155c-123">OTHER CHECKPOINTING TECHNIQUES</span></span>

<span data-ttu-id="b155c-124">Outre l’activité Checkpoint-Workflow, le workflow Windows PowerShell prend en charge d’autres techniques de contrôle de point de contrôle, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b155c-124">In addition to the Checkpoint-Workflow activity, Windows PowerShell Workflow supports other checkpointing techniques, including the following:</span></span>

- <span data-ttu-id="b155c-125">Paramètre commun de workflow PSPersist</span><span class="sxs-lookup"><span data-stu-id="b155c-125">PSPersist workflow common parameter</span></span>
- <span data-ttu-id="b155c-126">Paramètre commun d’activité PSPersist</span><span class="sxs-lookup"><span data-stu-id="b155c-126">PSPersist activity common parameter</span></span>
- <span data-ttu-id="b155c-127">Variable PSPersistPreference (dans un flux de travail)</span><span class="sxs-lookup"><span data-stu-id="b155c-127">PSPersistPreference variable (in a workflow)</span></span>

<span data-ttu-id="b155c-128">Pour plus d’informations sur l’ajout d’un point de contrôle à un workflow, consultez « Comment ajouter des points de contrôle à un flux de travail ».</span><span class="sxs-lookup"><span data-stu-id="b155c-128">For more information about adding a checkpoint to a workflow, see "How to Add Checkpoints to a Workflow."</span></span>

## <a name="examples"></a><span data-ttu-id="b155c-129">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b155c-129">EXAMPLES</span></span>

<span data-ttu-id="b155c-130">Le flux de travail suivant comprend un appel à l’activité Checkpoint-Workflow après avoir effectué une fonction longue et un script qui partagent des données.</span><span class="sxs-lookup"><span data-stu-id="b155c-130">The following workflow includes a call to the Checkpoint-Workflow activity after completing a long-running function and a script that share data.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b155c-131">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="b155c-131">SEE ALSO</span></span>

[<span data-ttu-id="b155c-132">Écriture d'un workflow Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b155c-132">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
