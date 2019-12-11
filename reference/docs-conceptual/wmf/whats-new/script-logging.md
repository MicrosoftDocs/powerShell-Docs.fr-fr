---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Traçage et journalisation de script
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147799"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="29550-103">Traçage et journalisation de script</span><span class="sxs-lookup"><span data-stu-id="29550-103">Script Tracing and Logging</span></span>

<span data-ttu-id="29550-104">Bien que PowerShell propose déjà le paramètre de stratégie de groupe **LogPipelineExecutionDetails** pour consigner l’appel des cmdlets, le langage de script PowerShell offre plusieurs fonctionnalités intéressantes dans une optique de journalisation et d’audit.</span><span class="sxs-lookup"><span data-stu-id="29550-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="29550-105">La nouvelle fonctionnalité de traçage de script détaillé assure un suivi et une analyse détaillés de l’activité des scripts PowerShell sur un système.</span><span class="sxs-lookup"><span data-stu-id="29550-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="29550-106">Lorsqu’elle est activée, PowerShell consigne tous les blocs de scripts dans le journal des événements ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="29550-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="29550-107">Si un bloc de script crée un autre bloc de script, par exemple en appelant `Invoke-Expression`, le bloc de script appelé est également enregistré.</span><span class="sxs-lookup"><span data-stu-id="29550-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="29550-108">La journalisation s’active par le biais du paramètre de stratégie de groupe **Activer la journalisation des blocs de scripts PowerShell** dans **Modèles d’administration** -> **Composants Windows** -> **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="29550-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="29550-109">Les événements sont :</span><span class="sxs-lookup"><span data-stu-id="29550-109">The events are:</span></span>

| <span data-ttu-id="29550-110">Canal</span><span class="sxs-lookup"><span data-stu-id="29550-110">Channel</span></span> |                               <span data-ttu-id="29550-111">Opérationnel</span><span class="sxs-lookup"><span data-stu-id="29550-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="29550-112">Niveau</span><span class="sxs-lookup"><span data-stu-id="29550-112">Level</span></span>   | <span data-ttu-id="29550-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="29550-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="29550-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="29550-114">Opcode</span></span>  | <span data-ttu-id="29550-115">Create</span><span class="sxs-lookup"><span data-stu-id="29550-115">Create</span></span>                                                                  |
| <span data-ttu-id="29550-116">Tâche</span><span class="sxs-lookup"><span data-stu-id="29550-116">Task</span></span>    | <span data-ttu-id="29550-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="29550-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="29550-118">Mot clé</span><span class="sxs-lookup"><span data-stu-id="29550-118">Keyword</span></span> | <span data-ttu-id="29550-119">Instance d'exécution</span><span class="sxs-lookup"><span data-stu-id="29550-119">Runspace</span></span>                                                                |
| <span data-ttu-id="29550-120">EventId</span><span class="sxs-lookup"><span data-stu-id="29550-120">EventId</span></span> | <span data-ttu-id="29550-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="29550-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="29550-122">Message</span><span class="sxs-lookup"><span data-stu-id="29550-122">Message</span></span> | <span data-ttu-id="29550-123">Création du texte Scriptblock (%1 sur %2) :</span><span class="sxs-lookup"><span data-stu-id="29550-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="29550-124">%3</span><span class="sxs-lookup"><span data-stu-id="29550-124">%3</span></span> </br> <span data-ttu-id="29550-125">ID Scriptblock : %4</span><span class="sxs-lookup"><span data-stu-id="29550-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="29550-126">Le texte incorporé dans le message est l’étendue du bloc de script compilé.</span><span class="sxs-lookup"><span data-stu-id="29550-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="29550-127">L’ID est un GUID qui est conservé pendant toute la durée de vie du bloc de script.</span><span class="sxs-lookup"><span data-stu-id="29550-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="29550-128">Quand vous activez la journalisation détaillée, la fonctionnalité écrit des marqueurs de début et de fin :</span><span class="sxs-lookup"><span data-stu-id="29550-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="29550-129">Canal</span><span class="sxs-lookup"><span data-stu-id="29550-129">Channel</span></span> |                                 <span data-ttu-id="29550-130">Opérationnel</span><span class="sxs-lookup"><span data-stu-id="29550-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="29550-131">Niveau</span><span class="sxs-lookup"><span data-stu-id="29550-131">Level</span></span>   | <span data-ttu-id="29550-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="29550-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="29550-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="29550-133">Opcode</span></span>  | <span data-ttu-id="29550-134">Open / Close</span><span class="sxs-lookup"><span data-stu-id="29550-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="29550-135">Tâche</span><span class="sxs-lookup"><span data-stu-id="29550-135">Task</span></span>    | <span data-ttu-id="29550-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="29550-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="29550-137">Mot clé</span><span class="sxs-lookup"><span data-stu-id="29550-137">Keyword</span></span> | <span data-ttu-id="29550-138">Instance d'exécution</span><span class="sxs-lookup"><span data-stu-id="29550-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="29550-139">EventId</span><span class="sxs-lookup"><span data-stu-id="29550-139">EventId</span></span> | <span data-ttu-id="29550-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="29550-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="29550-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="29550-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="29550-142">Message</span><span class="sxs-lookup"><span data-stu-id="29550-142">Message</span></span> | <span data-ttu-id="29550-143">Started / Completed invocation of ScriptBlock ID: %1</span><span class="sxs-lookup"><span data-stu-id="29550-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="29550-144">ID d’instance d’exécution : %2</span><span class="sxs-lookup"><span data-stu-id="29550-144">Runspace ID: %2</span></span> |

<span data-ttu-id="29550-145">L’ID est le GUID représentant le bloc de script (qui peut être mis en corrélation avec l’ID d’événement 0x1008), et l’ID d’instance d’exécution représente l’instance d’exécution dans laquelle ce bloc de script a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="29550-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="29550-146">Les signes de pourcentage dans le message d’appel représentent des propriétés ETW structurées.</span><span class="sxs-lookup"><span data-stu-id="29550-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="29550-147">Bien qu’ils soient remplacés par les valeurs réelles dans le texte du message, une façon plus fiable d’y accéder consiste à récupérer le message avec l’applet de commande Get-WinEvent, puis à utiliser le tableau **Propriétés** du message.</span><span class="sxs-lookup"><span data-stu-id="29550-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="29550-148">Voici un exemple qui illustre comment cette fonctionnalité peut aider à contrer une tentative malveillante de chiffrement et de brouillage de script :</span><span class="sxs-lookup"><span data-stu-id="29550-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="29550-149">L’exécution de ce code génère les entrées de journal suivantes :</span><span class="sxs-lookup"><span data-stu-id="29550-149">Running this generates the following log entries:</span></span>

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Si la longueur du bloc de script dépasse la capacité d’un seul événement, PowerShell divise le script en plusieurs parties. <span data-ttu-id="29550-151">Voici un exemple de code qui recombine un script à partir de ses messages de journal :</span><span class="sxs-lookup"><span data-stu-id="29550-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="29550-152">Comme pour tous les systèmes de journalisation dont la mémoire tampon de rétention est limitée, une attaque possible contre cette infrastructure consiste à saturer le journal de faux événements pour masquer les preuves antérieures.</span><span class="sxs-lookup"><span data-stu-id="29550-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="29550-153">Pour vous en protéger, configurez, sous une forme ou une autre, la collecte de journaux des événements dans le transfert d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="29550-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="29550-154">Pour plus d’informations, voir [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="29550-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>